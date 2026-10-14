# Prompt 03 Test Run — DevOps Project Scaffolder

> This is a test of the prompt and an illustrative generated milestone. The learner profile and project are fictional. The local test results below were actually produced in the assistant's isolated working environment; they are not evidence of a learner machine, a GitHub CI run, or production deployment.

## Test objective

Verify that Prompt 03 produces one coherent milestone, complete mutually consistent files, meaningful local tests, safe defaults, exact validation steps, and honest status reporting—without generating the container, Kubernetes, Helm, or CI milestones prematurely.

## Input supplied to Prompt 03

**Selected milestone:** Milestone 1 — API and tests.

**Plan acceptance criteria:**
- Implement a small HTTP API with `GET /health` and `GET /version`.
- Return JSON and correct HTTP status codes.
- Test expected behavior and an unknown route.
- Use a no-cloud, no-cluster, no-paid-service local workflow.
- Keep the scope small enough to fit the API-and-tests milestone.

**Environment and constraints:**
- Example runtime: Python 3.13.5 in an isolated Linux environment.
- Use Python standard library only; no dependency installation.
- Assume a new/empty project directory for this test.
- Bind only to loopback (`127.0.0.1`) by default.
- Do not generate container files, Kubernetes manifests, Helm charts, CI workflows, or cloud infrastructure.
- No previous test results were supplied to the prompt.

## Expected scaffold

```text
.
├── app.py
└── tests/
    └── test_app.py
```

No dependency manifest is required because the implementation uses only the Python standard library.

## Generated file: `app.py`

```python
"""Minimal standard-library HTTP API for the first portfolio milestone."""
from http.server import BaseHTTPRequestHandler, HTTPServer
import json
import os

HOST = "127.0.0.1"
PORT = int(os.environ.get("PORT", "8000"))


class ApiHandler(BaseHTTPRequestHandler):
    def do_GET(self):
        routes = {
            "/health": {"status": "ok"},
            "/version": {"version": "0.1.0"},
        }
        payload = routes.get(self.path)
        if payload is None:
            self.send_error(404, "Not Found")
            return
        body = json.dumps(payload).encode("utf-8")
        self.send_response(200)
        self.send_header("Content-Type", "application/json; charset=utf-8")
        self.send_header("Content-Length", str(len(body)))
        self.end_headers()
        self.wfile.write(body)

    def log_message(self, format, *args):
        # Keep the demo quiet; production services should use structured logging.
        return


def main():
    server = HTTPServer((HOST, PORT), ApiHandler)
    print(f"Listening on http://{HOST}:{PORT}")
    try:
        server.serve_forever()
    except KeyboardInterrupt:
        pass
    finally:
        server.server_close()


if __name__ == "__main__":
    main()
```

## Generated file: `tests/test_app.py`

```python
import json
import threading
import unittest
from http.client import HTTPConnection
from http.server import HTTPServer

from app import ApiHandler


class ApiTests(unittest.TestCase):
    @classmethod
    def setUpClass(cls):
        cls.server = HTTPServer(("127.0.0.1", 0), ApiHandler)
        cls.thread = threading.Thread(target=cls.server.serve_forever, daemon=True)
        cls.thread.start()
        cls.port = cls.server.server_address[1]

    @classmethod
    def tearDownClass(cls):
        cls.server.shutdown()
        cls.server.server_close()
        cls.thread.join(timeout=2)

    def request(self, path):
        connection = HTTPConnection("127.0.0.1", self.port, timeout=2)
        connection.request("GET", path)
        response = connection.getresponse()
        result = (response.status, response.getheader("Content-Type"), response.read())
        connection.close()
        return result

    def test_health_returns_ok_json(self):
        status, content_type, body = self.request("/health")
        self.assertEqual(status, 200)
        self.assertTrue(content_type.startswith("application/json"))
        self.assertEqual(json.loads(body), {"status": "ok"})

    def test_version_returns_version_json(self):
        status, content_type, body = self.request("/version")
        self.assertEqual(status, 200)
        self.assertTrue(content_type.startswith("application/json"))
        self.assertEqual(json.loads(body), {"version": "0.1.0"})

    def test_unknown_path_returns_404(self):
        status, _, _ = self.request("/missing")
        self.assertEqual(status, 404)


if __name__ == "__main__":
    unittest.main()
```

## Acceptance-criteria mapping

| Criterion | Implementation / test | Evidence |
|---|---|---|
| `GET /health` returns `200` and JSON | `app.py`; `test_health_returns_ok_json` | Test output below |
| `GET /version` returns `200` and JSON | `app.py`; `test_version_returns_version_json` | Test output below |
| Unknown path returns `404` | `test_unknown_path_returns_404` | Test output below |
| Local-only, no-cloud execution | Server and test bind to `127.0.0.1`; test chooses an ephemeral port | Source review and local run |
| One milestone only | Only API and unit/integration tests are included | File tree |
| No third-party dependency | Python standard library only | Imports and successful command |

## Validation commands

From the project root:

1. Check runtime: `python3 --version`
2. Run tests: `python3 -m unittest discover -s tests -v`
3. Optional manual smoke test in one terminal: `python3 app.py`
4. In a second terminal: `curl -i http://127.0.0.1:8000/health` and `curl -i http://127.0.0.1:8000/version`
5. Stop the manual server with Ctrl+C.

Expected test result: three tests pass. Expected manual requests return HTTP 200 and JSON bodies for the two known routes. A request to an unknown route should return HTTP 404.

If port 8000 is occupied, choose an available port with `PORT=8001 python3 app.py` and adjust the manual URL. The automated tests use an ephemeral local port. No cleanup beyond stopping the process is required; no cloud resources are created.

## Actual validation performed for this test

Environment: isolated Linux working directory, Python 3.13.5.

Command run:

```text
python3 --version
python3 -m unittest discover -s tests -v
```

Observed result:

```text
Python 3.13.5
test_health_returns_ok_json (test_app.ApiTests.test_health_returns_ok_json) ... ok
test_unknown_path_returns_404 (test_app.ApiTests.test_unknown_path_returns_404) ... ok
test_version_returns_version_json (test_app.ApiTests.test_version_returns_version_json) ... ok

----------------------------------------------------------------------
Ran 3 tests in 0.506s

OK
```

These results apply only to the exact files above in this isolated environment. No CI run, learner-machine run, container build, Kubernetes deployment, or production validation was performed.

## Review findings and limitations

**Passed**
- Milestone boundary was respected: no Dockerfile, Kubernetes, Helm, cloud, or CI files were generated.
- File paths and imports are consistent.
- Tests exercise actual HTTP requests against a server bound to loopback and cover both successful routes plus a missing route.
- The tests choose an ephemeral port, avoiding dependency on port 8000.
- No external packages, credentials, or cloud services are needed.
- Test status is based on a real local command, not inferred from code generation.

**Limitations to retain in project documentation**
- This is a learning scaffold, not a production server. Python's basic `HTTPServer` is single-threaded and is not intended as a production deployment server.
- The version is currently hard-coded.
- Request logging is suppressed for a quiet demo; a real service should provide appropriate structured logs.
- No authentication, rate limiting, TLS termination, deployment, or operational monitoring is implemented; those are outside this milestone and should not be implied.
- The loopback binding is intentional for local use. A later container milestone must deliberately revisit listener binding and network exposure rather than silently changing it now.

## Prompt quality verdict

**PASS for this fixture.** The revised prompt yields a small, internally consistent API-and-tests scaffold and requires validation evidence without overstating it. The generated code passed three local tests in the stated environment. Next, the learner should run the commands in their own checkout and record their own results before starting the container milestone.
