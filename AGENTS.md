<!-- agent.protocol reference: https://github.com/AlloVince/agent.protocol commit 0f98a089a5f3b176171a9059cc9968cbb5c1dd0f (v0.3.0 source, clean worktree; no release tag verified). -->

# OpenSearch image

## Project and entry points

- Goal: build the custom OpenSearch base image and verify its analysis plugins for YinXing local development and NAS use.
- Boundaries: this repository owns only image build/release configuration and image documentation. Compose, runtime configuration, ports, persistent data, and deployment belong to `local.ops` or `nas.ops`; application mappings, indexes, aliases, and data migrations do not belong here.
- Read by task: start with `README.md`, then inspect `Dockerfile` and `.github/workflows/docker-build.yml` for build or release work. Do not scan unrelated repositories.
- Official operations: use the documented Docker build command and the GitHub Actions workflow; runtime Compose commands live in the operations owners, not this repository. Do not create Agent-only build or release paths.
- Existing capability: retain the pinned OpenSearch base image and its analysis plugin installation. The Dockerfile version and CI workflow are the source of truth for build/release behavior.
- System: `/Users/allovince/Developer/yinxing.super`; ownership is in `../yinxing.super/docs/architecture/repositories.md`, routing is in `../yinxing.super/docs/architecture/subprojects.md`, and search ownership/contracts are under `../yinxing.super/docs/contracts/`.

Before work, record HEAD, branch, and status. Preserve existing work; do not reset, overwrite, commit, push, tag, publish, or release without explicit human authorization.

## Authority and facts

Current human instruction takes precedence, followed by relevant long-lived `owner/` intent and applicable `AGENTS.md` rules. `owner/` is read-only unless the current human explicitly asks to change a specific file.

Verify actual behavior from Dockerfile, workflow configuration, image build results, plugin inspection, and the owning runtime environment. Docs, old plans, reports, and Git history cannot substitute for verification. Report conflicts rather than assuming current behavior is the target.

## Image constraints

- Preserve the Dockerfile's pinned OpenSearch compatibility baseline. Do not update the base image, plugins, platforms, image tags, or workflow behavior merely because a newer version exists.
- Image acceptance verifies the intended pinned image can build and contains the required analysis plugins. A successful image build does not verify Compose, host-kernel compatibility, runtime ports, persistence, mappings, indices, aliases, migrations, or application behavior.
- Do not commit generated image layers, local data, credentials, or runtime configuration. Secrets remain GitHub Actions secrets or operations-owner configuration.

## Reuse and official operations

- Before adding CLI, logger, config, storage, queue, HTTP, validation, deployment, or image capabilities, inspect this repository, its system workspace, existing services, and declared shared capabilities.
- Extend existing layers first. Add a new capability only when reuse is insufficient or would violate explicit dependency, deployment, or data boundaries; explain the reason and do not leave a parallel permanent implementation.
- Humans and Agents use the same official paths for build, test, release, deployment, maintenance, and diagnostics. One-off investigation may be temporary; repeated or formal work must converge on existing entry points.

## Readability and change discipline

- Use clear names, direct control flow, and explicit data and side effects; follow established patterns and comment non-obvious constraints.
- Avoid over-abstraction, complex generic machinery, metaprogramming, hidden magic, layered helpers, and speculative dependencies. Do not silently change public behavior, data semantics, or system boundaries.
- Do not mix unrelated refactors, major dependency upgrades, or formatting. Necessary refactoring for the current feature during a long task is allowed. Do not accumulate oversized functions/files, mixed responsibilities, duplicate implementations, or obsolete branches; at each verifiable long-task stage, restructure this task's accumulated work and validate it.
- Never delete tests or ignore failures to obtain a green result. Before architecture, core-model, technology, or cross-repo changes, state the problem, existing-capability gap, smallest solution, impact, and acceptance. Unapproved cross-repo API/Event/Storage, ownership, breaking changes, or Domain/Product semantics must be reported for human decision.

## Engineering defaults

- Node defaults to fnm + pnpm and uses the latest LTS for new projects or explicit runtime upgrades; do not add historical compatibility without a business requirement. Python defaults to pyenv + uv, with venv when needed, and uses the latest stable release for new projects or explicit upgrades. Native configuration and lockfiles determine actual runtimes, package managers, and builds; defaults do not authorize changing tooling, runtime, package manager, branch, or Git history.
- Use SemVer and Conventional Commits; `main` is the integration branch and work stays focused on one feature. Local explicit constraints take precedence.
- Check applicable low-cost production defaults: configuration validation, production mode, reproducible build, errors/timeouts, secrets management, sensible cache, and static/text response compression. Do not duplicate capabilities owned by a registry, CDN, proxy, or operations owner; state why a baseline does not apply.
- CLI, batch, and long-running tasks use existing logging and give phases/progress, failure reasons, final summary, and exit status.

## Documentation

`README.md` and `owner/` are human-facing. `docs/` holds only stable knowledge that code, tests, schemas, configuration, or CLI help cannot express and that reduces future misjudgment, rediscovery, context, or reconstruction cost.

Do not store session history, current focus, progress, next steps, one-off debugging, or Git-visible changes. Use the current conversation or existing task carrier for progress; do not create memory/workflow replacements. Write normal docs only for durable guidance and ADRs only for high-rework decisions with lasting alternatives.

## Long tasks and delivery

- Define the final user result and observable acceptance before work; inspect current code, data, and artifacts every round, and treat old plans as non-authoritative. Continue when the next action is clear, authorized, and unblocked.
- Bound intermediate data, logs, binaries, and multi-stage outputs with streaming, chunking, or existing storage. Preserve forced single-file input/output formats but keep processing resources bounded. Do not overwrite irrecoverable input; remove rebuildable unused temporary artifacts.
- Stage results must be reviewable. Retain source input, generation command, and checksums only when reconstruction has value, using existing artifact mechanisms.
- Provide evidence against the agreed acceptance condition, run matching checks, and report completed work, verification, unverified items, and real blockers. Do not commit, push, or release without explicit human instruction.
