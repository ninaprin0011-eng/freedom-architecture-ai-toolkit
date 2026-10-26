# Prompt 04 Test Run — Verification & Troubleshooting Assistant

> This is an illustrative prompt test using a fictional local Kubernetes lab. It is not professional production-incident evidence. Commands and outputs below are supplied fixture evidence for testing the reasoning behavior; this example does not claim they were executed against a real cluster during prompt evaluation.

## Test objective

Verify that Prompt 04 separates facts from hypotheses, chooses low-risk discriminating diagnostics, avoids blind restarts/destructive fixes, requires causal evidence before declaring root cause, and requires actual recovery evidence before declaring success.

## Fixture: failing Kubernetes readiness probe

**Milestone:** Kubernetes deployment validation.

**Expected behavior:** Deployment `portfolio-api` should become Available and its pod should become Ready.

**Actual behavior:** Pod is Running but remains `0/1 Ready`.

**Environment:** local `kind` cluster; namespace `portfolio`; application image from the portfolio project.

**Recent change:** readiness probe was added to the Deployment.

### Initial supplied evidence

```text
$ kubectl -n portfolio get pods
NAME                             READY   STATUS    RESTARTS   AGE
portfolio-api-6d8c7b9d5f-abcde   0/1     Running   0          2m

$ kubectl -n portfolio describe pod portfolio-api-6d8c7b9d5f-abcde
...
Readiness probe failed: HTTP probe failed with statuscode: 404
```

Relevant Deployment excerpt:

```yaml
readinessProbe:
  httpGet:
    path: /ready
    port: 8000
```

Known application behavior from the earlier milestone:

```text
GET /health  -> 200
GET /version -> 200
unknown path -> 404
```

## Expected reasoning from Prompt 04

### Confirmed facts

- The pod process is Running but the container is not Ready.
- Kubernetes reports the readiness HTTP probe receives status 404.
- The configured probe path is `/ready` on port 8000.
- The supplied application behavior documents `/health` and `/version`, while unknown paths return 404.

### Hypothesis

The readiness probe path does not match an implemented application endpoint. This is strongly supported, but the next check should inspect the live Deployment configuration rather than immediately editing it.

### Next discriminating diagnostic

```text
kubectl -n portfolio get deployment portfolio-api -o yaml
```

Purpose: confirm the live Deployment—not merely a local file—actually contains `path: /ready` and `port: 8000`.

State changing: **No**.

Interpretation:
- If the live probe is `/ready`, the configuration mismatch hypothesis gains direct support.
- If the live probe differs, investigate rendered/applied configuration and pod-template history instead of changing the application.

### Additional supplied evidence

```yaml
readinessProbe:
  httpGet:
    path: /ready
    port: 8000
```

At this point, the root cause is **supported**: the live readiness probe requests `/ready`, while the supplied application behavior has no `/ready` route and returns 404 for unknown routes.

## Minimal remediation

Change only the readiness probe path from `/ready` to the existing `/health` endpoint. Do not restart pods manually, delete the pod, weaken the probe, or disable readiness checking.

Example manifest change:

```diff
 readinessProbe:
   httpGet:
-    path: /ready
+    path: /health
     port: 8000
```

Before applying, save or commit the previous manifest so the change is reversible. Rollback is to restore `/ready` if the change causes an unexpected result.

## Recovery verification fixture

After the corrected manifest is applied, the following actual-result fixture is supplied to the prompt:

```text
$ kubectl -n portfolio rollout status deployment/portfolio-api
 deployment "portfolio-api" successfully rolled out

$ kubectl -n portfolio get pods
NAME                             READY   STATUS    RESTARTS   AGE
portfolio-api-7b79d58c84-fghij   1/1     Running   0          42s

$ kubectl -n portfolio get deployment portfolio-api
NAME            READY   UP-TO-DATE   AVAILABLE   AGE
portfolio-api   1/1     1            1           12m
```

Recovery can now be labeled **verified within this fixture** because the original readiness symptom is gone and the Deployment independently reports an Available replica. In a real learner lab, these labels require the learner's actual command outputs.

## Troubleshooting record

| Field | Result |
|---|---|
| Symptom | Pod Running but `0/1 Ready` |
| Key evidence | Readiness probe returned HTTP 404 |
| Supported cause | Live probe requested `/ready`; application did not implement that route |
| Remediation | Changed readiness path to `/health` |
| Original-failure verification | Pod became `1/1 Ready` |
| Independent recovery check | Deployment reported `1/1 Available` |
| Prevention | Keep probe endpoints aligned with application API contract; validate rendered manifests before deployment |
| Scope | Fictional local Kubernetes lab only |

## Prompt quality review

**PASS for this fixture.** The revised prompt encourages a causal chain rather than a restart-first response: observe the 404, inspect the live probe, compare it with known application behavior, make one reversible configuration correction, then verify both readiness and Deployment availability.

The example deliberately does **not** recommend deleting pods, increasing privileges, disabling the readiness probe, or changing multiple variables at once. It also distinguishes supplied fixture output from commands actually executed during prompt development.

## Next boundary

Do not generalize this diagnosis to every `0/1 Ready` pod. A different failure requires its own evidence. The next toolkit prompt should not treat this fictional lab as production experience.