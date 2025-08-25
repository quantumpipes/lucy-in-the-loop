## Settings & Configuration

This document defines the initial, versioned configuration interface for Lucy in the Loop. It covers:

- Network access opt-in to expose the local service to your LAN
- Model selection, including quick access to new frontier models
- Local-only mode to keep all activity offline

Until the application code is published, these settings represent the planned interface and schema for the first MVP. File paths and flags are stable commitments for the MVP.

### Where configuration lives

- Default file: `~/.lucy/local-config.yaml`
- Override via environment: set `LUCY_CONFIG=/absolute/path/to/config.yaml`
- Planned CLI precedence: CLI flags > environment variables > config file > built-in defaults

See the JSON Schema at `config/schema/settings.schema.json` for formal validation.

### Network access (opt-in)

Lucy binds to `127.0.0.1` by default and is only reachable from the local machine. To allow other devices on your local network to access Lucy, explicitly opt-in:

```yaml
server:
  port: 5829
  bind_host: 0.0.0.0
  expose_on_local_network: true
  require_auth_for_non_local: true
  auth_token_env_var: LUCY_ACCESS_TOKEN
  allowed_origins: ["http://localhost:5829"]
```

Security notes:

- Exposing Lucy on your LAN can reveal an interface with elevated capabilities. Keep `require_auth_for_non_local` enabled and provide a strong token via the `LUCY_ACCESS_TOKEN` environment variable.
- Use a firewall to restrict access to trusted subnets only. Do not port-forward to the public internet.
- If you disable authentication, Lucy should remain bound to `127.0.0.1`.

### Model selection and frontier models

You can pin the primary model and control which providers are allowed. Lucy will surface newly available frontier models as they become available when not in offline mode.

```yaml
models:
  preferred_model: "llama-3.1-8b-instruct-q4"
  storage_dir: "~/.lucy/models"
  allowed_providers: ["local", "huggingface", "openai", "anthropic", "google", "meta"]
  auto_offer_frontier: true
  frontier_channels: ["stable", "beta"]
```

Behavior:

- If `auto_offer_frontier` is true and offline mode is disabled, Lucy will fetch a curated, signed registry of newly supported models and present them in the UI for one-click switching. No user data is transmitted during this check.
- In offline mode, only locally installed models will be offered.
- Model names are provider-specific and documented in the future runtime manual. Local models are identified by directory names within `storage_dir`.

### Local-only (offline) mode

Offline mode is the default and enforces a strict deny-by-default egress posture:

```yaml
privacy:
  offline_only: true
```

When `offline_only` is true:

- No network requests are performed (including model registry lookups or model downloads).
- Only models already present on disk are available.
- Any features that would require internet access are disabled or stubbed until explicitly opted-in.

If you later set `offline_only: false`, you can selectively allow model downloads by provider while keeping other network features disabled.

### Full example

```yaml
version: 1
server:
  port: 5829
  bind_host: 127.0.0.1
  expose_on_local_network: false
  require_auth_for_non_local: true
  auth_token_env_var: LUCY_ACCESS_TOKEN
  allowed_origins: ["http://localhost:5829"]

privacy:
  offline_only: true

models:
  preferred_model: "llama-3.1-8b-instruct-q4"
  storage_dir: "~/.lucy/models"
  allowed_providers: ["local"]
  auto_offer_frontier: true
  frontier_channels: ["stable", "beta"]
```

### Environment variables (planned)

- `LUCY_CONFIG` — Absolute path to the config file
- `LUCY_ACCESS_TOKEN` — Bearer token required when accessing Lucy from non-localhost clients (only used when `require_auth_for_non_local` is true)

### CLI flags (planned)

These flags will override configuration values at runtime:

- `--port <int>`
- `--bind-host <ip>`
- `--expose-on-local-network`
- `--no-expose-on-local-network`
- `--model <name>`
- `--offline-only` / `--no-offline-only`

### Validation

Use the JSON Schema in `config/schema/settings.schema.json` to validate any `local-config.yaml` file. YAML is interpreted as JSON for schema validation.


