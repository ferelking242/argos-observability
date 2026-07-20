# Argos Observability

<p align="center">
  <img src="web/src/assets/images/common/argos_logo.svg" alt="Argos Observability" width="300" />
</p>

<p align="center">
  <strong>Open-source observability platform for logs, traces, metrics and application intelligence.</strong>
</p>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#quick-start">Quick Start</a> •
  <a href="#architecture">Architecture</a> •
  <a href="#contributing">Contributing</a> •
  <a href="#license">License</a>
</p>

---

## Overview

Argos Observability is a high-performance, open-source observability platform built for modern engineering teams. It provides real-time visibility into your logs, metrics, traces, and application intelligence — all in one place.

Inspired by **Argus Panoptes**, the all-seeing giant of Greek mythology, Argos Observability watches everything in your infrastructure so you don't have to.

> **Built for production. Designed for engineers.**

---

## Features

- 🔍 **Logs** — Full-text search and structured log analytics at scale
- 📊 **Metrics** — PromQL-compatible metrics ingestion and dashboards
- 🔗 **Traces** — Distributed tracing with OpenTelemetry support
- 🤖 **AI Observability** — Monitor LLM applications and AI agent pipelines
- 🚨 **Alerting** — Multi-channel alerts (Slack, PagerDuty, email, webhooks)
- 📈 **Dashboards** — Rich, interactive dashboards with 20+ chart types
- 🔄 **Pipelines** — Real-time data transformation and routing
- 🏢 **Multi-tenant** — Organization-level isolation and access control

---

## Quick Start

### Docker (recommended)

```bash
docker run -v $PWD/data:/data \
  -e ZO_ROOT_USER_EMAIL="admin@example.com" \
  -e ZO_ROOT_USER_PASSWORD="YourPassword#123" \
  -p 5080:5080 \
  --name argos-observability \
  argos-observability/argos-observability:latest
```

Then open: http://localhost:5080

### Local Build

**Prerequisites:**
- Rust 1.80+ (`rustup`)
- Node.js 20+
- `npm`

**Backend:**
```bash
cargo build --release
./target/release/openobserve
```

**Frontend:**
```bash
cd web
npm install
npm run dev
```

---

## Architecture

```
┌─────────────────────────────────────────────────┐
│                  Argos Observability             │
├───────────────────┬─────────────────────────────┤
│   Frontend (Vue)  │   Backend (Rust / Actix)    │
│   ─ Dashboard     │   ─ Ingestion API            │
│   ─ Alerts UI     │   ─ Query Engine (Arrow)     │
│   ─ Pipeline UI   │   ─ Storage Layer            │
│   ─ Settings      │   ─ Alert Engine             │
└───────────────────┴─────────────────────────────┘
        │                        │
        └────────────────────────┘
              Single binary
```

**Stack:**
- **Backend**: Rust, Actix-web, Apache Arrow/DataFusion
- **Frontend**: Vue 3, TypeScript, Vite, TailwindCSS
- **Storage**: Local disk or S3-compatible object storage
- **Protocol**: OpenTelemetry (OTLP), Prometheus, Loki

---

## Configuration

Key environment variables:

| Variable | Default | Description |
|---|---|---|
| `ZO_ROOT_USER_EMAIL` | `root@example.com` | Admin user email |
| `ZO_ROOT_USER_PASSWORD` | `Complexpass#123` | Admin user password |
| `ZO_LOCAL_MODE` | `true` | Use local storage |
| `ZO_S3_BUCKET_NAME` | - | S3 bucket (if not local) |
| `ZO_MAX_FILE_SIZE_ON_DISK` | `32` | Max file size (MB) |
| `RUST_LOG` | `info` | Log level |

---

## Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md) and submit pull requests.

---

## License

Argos Observability is licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**.

This is a community fork and derivative work, maintaining full compliance with the upstream AGPL-3.0 license.

See [LICENSE](LICENSE) for details.

---

<p align="center">
  Built with ❤️ for the open-source observability community
</p>
