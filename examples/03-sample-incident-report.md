# Illustrative Incident: Service Has No Ready Endpoints

> Hypothetical lab example. The diagnosis and results below are not real execution evidence.

## Expected vs actual
Expected: a client can reach the API through a Kubernetes Service.
Actual: requests fail and the Service has no ready endpoints.

## Evidence to collect
- `kubectl get pods -o wide`
- `kubectl describe service <service-name>`
- `kubectl get endpoints <service-name>`
- `kubectl describe pods`
- Sanitized application logs

## Hypothesis
The Service selector may not match the Pod labels, or the Pods may not be ready. This remains unconfirmed until observed.

## Recovery
Compare Service selectors to Pod labels; correct the smallest mismatch if confirmed; re-check endpoints and perform a repeatable request test. Record actual outputs before calling recovery verified.