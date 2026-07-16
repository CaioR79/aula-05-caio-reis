# Backend C# — FullStackPractice.Api

API REST simples em **ASP.NET Core 8** para prática de integração full stack, contratos HTTP, status codes, CORS e visualização via Swagger.

## Executar com Docker

```bash
docker compose up --build
```

Acesse:

- API: http://localhost:8080
- Swagger: http://localhost:8080/swagger
- Health check: http://localhost:8080/health

## Executar localmente sem Docker

```bash
dotnet restore
dotnet run
```

Acesse o Swagger em:

```text
http://localhost:8080/swagger
```

## Endpoints

- `GET /health`
- `GET /api/test-results`
- `GET /api/test-results/{id}`
- `POST /api/test-results`
- `PUT /api/test-results/{id}`
- `DELETE /api/test-results/{id}`

## Contrato principal

### POST `/api/test-results`

```json
{
  "serialNumber": "400T0193A003",
  "station": "TEST_01",
  "status": "PASS"
}
```

Status aceitos:

- `PASS`
- `FAIL`
- `PENDING`

## Exemplos de retorno

### 201 Created

```json
{
  "id": 3,
  "serialNumber": "400T0193A003",
  "station": "TEST_01",
  "status": "PASS",
  "createdAt": "2026-07-08T19:30:00Z",
  "updatedAt": "2026-07-08T19:30:00Z"
}
```

### 400 Bad Request

```json
{
  "message": "O campo serialNumber é obrigatório."
}
```

### 409 Conflict

```json
{
  "message": "Já existe um resultado para este serial nesta estação."
}
```
