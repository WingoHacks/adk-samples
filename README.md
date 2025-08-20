https://github.com/WingoHacks/adk-samples/releases

# ADK Sample Agents Collection — Ready-to-Run Agent Demos 🚀🤖

[![Releases](https://img.shields.io/badge/Releases-download-blue?logo=github)](https://github.com/WingoHacks/adk-samples/releases) [![Topics](https://img.shields.io/badge/topics-adk%2Cagent--samples%2Cagents-yellowgreen)](https://github.com/WingoHacks/adk-samples)

![Agent illustration](https://images.unsplash.com/photo-1581093588401-1b6e7df8c2f8?auto=format&fit=crop&w=1600&q=60)

A focused collection of practical agents built with the Agent Development Kit (ADK). These samples show common patterns, runtime wiring, and safe defaults you can copy into your projects. Each sample is small, documented, and runnable.

Badges
- Build: GitHub Actions (branches and checks)
- Releases: linked above for downloadable assets
- License: MIT

Core keywords: adk, agent-samples, agents

Table of contents
- Overview
- What you get
- Sample agents (with images)
- Quick start — download and run
- Run from source
- Architecture and patterns
- Configuration and secrets
- Testing and CI
- Contributing
- License
- Contact

Overview
The repository bundles ready-to-run agents and example code. Use them to learn ADK concepts or to form a starting point for production agents. Each sample focuses on one capability: conversation, task automation, integration, or observation.

What you get
- Minimal runnable agents with clear structure.
- Sample configs for local and container runs.
- Unit and integration tests.
- CI workflows for lint, test, and build.
- Release assets for direct download.

Included samples
1. chat-agent
   - Purpose: conversational assistant with context memory.
   - Tech: ADK runtime, local memory store, HTTP bridge.
   - Use: adapt for customer support workflows.

2. scheduler-agent
   - Purpose: run scheduled tasks and webhooks.
   - Tech: cron-like scheduler, task queue, logging.
   - Use: automation, reminders, batch jobs.

3. integration-agent
   - Purpose: demonstrate external API calls and rate control.
   - Tech: plugin adapters, retry policy, circuit breaker.
   - Use: connect to external services safely.

4. watcher-agent
   - Purpose: observe events and emit alerts.
   - Tech: event stream, filters, rule engine.
   - Use: monitoring and automated responses.

5. demo-bot
   - Purpose: small demo combining chat and action.
   - Tech: ephemeral memory, action handlers, UI sample.
   - Use: quick demo or proof of concept.

Screenshots and visuals
- Demo UI: https://raw.githubusercontent.com/WingoHacks/adk-samples/main/docs/demo-ui.png
- Architecture diagram: https://raw.githubusercontent.com/WingoHacks/adk-samples/main/docs/arch-diagram.svg

Quick start — download and run
Download the release asset and execute it. Visit the Releases page and get the prebuilt binary or archive for your platform:
https://github.com/WingoHacks/adk-samples/releases

Steps
1. Visit the releases URL above.
2. Download the agent file or archive that matches your OS.
3. Extract if needed.
4. Make the binary executable (Linux/macOS):
   chmod +x ./agent-sample
5. Run:
   ./agent-sample --config ./config/sample.yml

Examples
- Run chat-agent:
  ./chat-agent --config configs/chat.yml
- Run scheduler-agent:
  ./scheduler-agent --config configs/scheduler.yml

If a release asset is a tarball:
- Extract:
  tar -xzf adk-samples-v1.0.0.tar.gz
- Then run the binary inside.

Run from source
Clone and run locally to customize or debug.

1. Clone
   git clone https://github.com/WingoHacks/adk-samples.git
   cd adk-samples

2. Install toolchain
   - Node sample: Node.js >=16, yarn
   - Go sample: Go >=1.20
   - Python sample: Python 3.10, pip

3. Install dependencies
   - Node:
     cd samples/chat-agent
     yarn install
   - Python:
     cd samples/integration-agent
     pip install -r requirements.txt

4. Build and run
   - Node:
     yarn build
     yarn start --config ./configs/dev.yml
   - Go:
     go build ./cmd/watcher-agent
     ./watcher-agent --config ./configs/dev.yml

Configuration
Each sample reads a YAML file in configs/ or ./config. The common keys:
- server.port — port for HTTP bridge
- runtime.env — dev | staging | prod
- memory.store — memory adapter (in-memory | redis)
- log.level — debug | info | warn | error

Secrets
Keep secrets out of repo. Use environment variables or a secrets file outside source control.
- Examples:
  ADK_API_KEY=xxx
  REDIS_URL=redis://localhost:6379

Patterns and architecture
These samples illustrate ADK patterns you will use in real agents.

Core concepts
- Runtime: lifecycle and plugin registration.
- Intent handlers: map input to actions.
- Memory: short-term and long-term stores.
- Action adapters: external connectors (HTTP, DB, queues).
- Policies: rate limits and retry policies.
- Observability: structured logs and metrics.

Design decisions
- Keep handlers small and testable.
- Use explicit config for adapters.
- Separate runtime and business logic.
- Prefer typed contracts for actions.

Testing
Each sample includes tests.
- Unit tests cover handlers and adapters.
- Integration tests run in Docker or with test doubles.

Run tests
- Node:
  yarn test
- Python:
  pytest

CI
We include GitHub Actions workflows:
- lint.yml — runs linters and format checks.
- test.yml — runs unit and integration tests per sample.
- release.yml — builds artifacts and creates release assets.

Releases and binaries
Release assets appear on the Releases page. Download the file, extract if needed, and execute. Use the releases link:
https://github.com/WingoHacks/adk-samples/releases

Release naming convention
- adk-samples-v1.0.0-linux-amd64
- adk-samples-v1.0.0-darwin-arm64
- adk-samples-v1.0.0-windows-amd64.zip

Security
- Run samples in isolated environments.
- Rotate keys and tokens.
- Use policies and rate limits on adapters.

Contributing
We welcome pull requests and issues. Use the template files in .github/ to guide your submission.

How to contribute
1. Open an issue describing your idea or bug.
2. Fork the repo and create a branch.
3. Add tests for new behavior.
4. Run linters and tests.
5. Open a pull request and reference the issue.

Code style
- Keep handlers small.
- Use typed interfaces.
- Document configs and env vars.

Release process
- Bump version following semver.
- Run release workflow to build assets.
- Upload binaries to GitHub Releases.

Example PR checklist
- Tests added
- Lint passed
- Docs updated
- Changelog entry

Common commands
- Run a sample:
  ./chat-agent --config ./configs/chat.yml
- Run tests:
  yarn test
- Build:
  yarn build

Ecosystem and integrations
- Databases: Redis, Postgres
- Messaging: Kafka, RabbitMQ
- Observability: Prometheus, OpenTelemetry
- Storage: S3-compatible stores

Roadmap
- Add more agent patterns (analytics, RL loop).
- Add a web UI sample with live events.
- Add more language bindings for ADK.

Frequently asked topics
- How to swap memory store?
  Change memory.store in config and provide connection string.
- How to test external APIs?
  Use adapter mocks found in tests/mocks.
- How to secure endpoints?
  Use API keys or OAuth and enable TLS in config.

Files of interest
- samples/ — agent sample code
- configs/ — sample configuration files
- docs/ — architecture and how-to docs
- .github/workflows/ — CI configs
- LICENSE — license file

License
MIT License. See LICENSE file.

Contact
Open issues in the repo for bug reports, feature requests, or help. For quick questions, create an issue and tag it with help-wanted or discussion.

Images and media credits
- Unsplash robot image: https://unsplash.com/photos/ (licensed for free use)
- Architecture diagrams live in docs/

Releases link again for download and execution:
https://github.com/WingoHacks/adk-samples/releases

Use the Releases page to pick the asset that matches your OS, download it, and run the binary or extract the archive to run the sample agents.