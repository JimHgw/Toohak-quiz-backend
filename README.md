# Toohak Quiz Backend

A classroom quiz administration REST API built with **TypeScript, Express and Jest** as a team coursework project for **UNSW College DPST1093, 24T3** (August–December 2024).

This repository is a curated portfolio snapshot maintained by **Guangwei Hu**. It includes team-written code and course scaffolding. It is not solely my work; see [CREDITS.md](CREDITS.md) for attribution and provenance.

## Implemented scope

- Administrator registration, login, logout and user profile management.
- Quiz creation, listing, editing, removal, trash management, restoration and ownership transfer.
- Question creation, editing, reordering, duplication and deletion.
- HTTP API tests covering successful requests, invalid input and authorization errors.
- JSON-file persistence and Swagger UI for the supplied API specification.

The player router is a placeholder. This snapshot does **not** implement a complete live multiplayer quiz experience, and the supplied Swagger specification covers more functionality than the implementation.

## My contributions

The original Git history records my work on:

- **Question updates:** implementation, Express endpoint integration and API tests, including invalid input handling.
- **Quiz ownership transfer:** implementation, endpoint integration and test fixes.
- **User details updates:** implementation, endpoint integration and HTTP tests.
- **Quiz removal:** implementation, endpoint integration and HTTP tests.

Selected original commit identifiers are recorded in [CREDITS.md](CREDITS.md). These statements describe my contributions within the team project, not ownership of every file.

## Run locally

Use a Node.js environment and npm. Dependency installation and verification results for this snapshot are recorded in [VERIFICATION.md](VERIFICATION.md).

```sh
npm ci
npm start
```

Open http://127.0.0.1:3200/docs. Run commands from the repository root. The server listens on localhost by default and creates an empty `src/data.json` on the first API request. Local data and logs are ignored by Git.

In another terminal, while the server is running:

```sh
npm test -- --runInBand
npm run tsc
npm run lint
```

Tests use port 3200 from `src/config.json` and repeatedly clear the demo datastore. Use only disposable local test data.

## Structure

```text
src/routers/    Express endpoints
src/services/   Authentication and quiz business logic
src/models/     Data types and classes
src/utils/      Validation, errors and shared helpers
tests/api/     Jest HTTP API tests
swagger.yaml   Course API specification
```

## Limitations

This is an educational local demo, not a production service. The inherited implementation stores passwords in plaintext, uses stored session-token lookup for authorization and exposes a test reset endpoint. Do not use real credentials or expose it to the internet. JSON persistence does not restore class prototypes after a restart, which may affect operations that use instance methods.

`JWT_SECRET` can be supplied through the environment. Without it, the demo generates a random signing secret for the current process. This change removes a committed secret; it does not redesign the inherited authentication model.

## Snapshot preparation

The September 2026 portfolio preparation excludes dependencies, runtime data, logs, meeting notes, generated reports and the original Git metadata. It adds this documentation, initializes an empty datastore when absent, removes the committed signing key and stops logging request bodies and query strings. Core coursework features remain team work from 2024. See [CREDITS.md](CREDITS.md).
