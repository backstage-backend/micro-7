# micro-7

Prueba de integración entre Backstage y GitHub

## API

The service exposes an in-memory REST API for `items`. The OpenAPI contract is available at [`docs/openapi.yaml`](docs/openapi.yaml).

| Method | Path | Description |
| --- | --- | --- |
| `GET` | `/api/v1/items` | List all items |
| `POST` | `/api/v1/items` | Create an item |
| `GET` | `/api/v1/items/{id}` | Get an item |
| `PUT` | `/api/v1/items/{id}` | Replace an item |
| `DELETE` | `/api/v1/items/{id}` | Delete an item |

An item requires a non-empty `name` and accepts an optional `description`. Data is stored in memory and is lost when the service restarts.

## CI configuration

The CI workflow runs a SonarCloud scan. Configure the repository secret
`SONAR_TOKEN` before enabling the workflow. SonarCloud is used by default; for
a self-hosted SonarQube server, define the repository variable
`SONAR_HOST_URL` with the complete URL, including `https://`.

The scan uses the GitHub repository as the SonarCloud project key and
`backstage-backend` as the SonarCloud organization. If your SonarCloud
organization is different, update `sonar.organization` in the generated
workflow.

## Local development

### Node.js

```bash
npm install
npm start
```

### Python

```bash
python -m venv .venv
. .venv/bin/activate
pip install -r requirements.txt
python src/app.py
```