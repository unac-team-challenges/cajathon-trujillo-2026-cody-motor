# AGENTS.md — cajathon-trujillo-2026-cody-motor

Repo **público** del equipo Cody (Cajathon Trujillo 2026). Contiene el **motor**: IA, analítica y API. Es dueño del contrato OpenAPI.

Es parte de un metarepo. Si tienes acceso al repo padre privado `cajathon-trujillo-2026-cody`, su `AGENTS.md` y su `docs/INDICE.md` mandan sobre este archivo.

## Reglas

1. **Repo público:** nunca pegues aquí texto de las fichas de los desafíos, del Solution Concept ni de documentos del repo padre. Refiérete al desafío solo por su código.
2. Nunca hagas push a `main` ni a `develop`. Todo entra por PR contra `develop`.
3. Un agente nunca aprueba ni hace merge.
4. Solo datos sintéticos. Sin secretos: usa `.env` (ignorado) y documenta en `.env.example`.
5. Sin atribución de IA en el historial (`Co-Authored-By` de agentes, "Generated with…").
6. No agregues `LICENSE` sin acuerdo del equipo.

## Flujo

1. Issue en este repo, con criterio de aceptación.
2. Rama desde `develop`: `<tipo>/<issue>-<slug>`, por ejemplo `feat/12-grafo-de-relaciones`.
   ```bash
   gh issue develop 12 --base develop --name feat/12-grafo-de-relaciones --checkout
   ```
3. Commits en formato Conventional Commits. PR contra `develop` con un título `tipo(alcance): descripción` (lo valida la CI) y `Closes #12`.
4. 1 aprobación de otra persona y **Squash and merge**.
5. Release: PR `develop → main` titulado `release: vX.Y.Z`, con **merge commit** (nunca squash), y después tag.

## Verificaciones locales

```bash
cargo fmt --check
cargo clippy --all-targets -- -D warnings
cargo nextest run
```

## Estado

Stack: Rust (edición 2024) con `axum`, `utoipa` (publica `openapi.json`), `petgraph` y `polars`. El detalle y las versiones están en el ADR-0003 del repo padre; aún no hay código.
