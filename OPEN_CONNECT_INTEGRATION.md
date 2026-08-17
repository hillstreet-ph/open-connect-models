# Open-Connect Models Service

This repository is the upstream-derived LiteLLM model gateway for Open-Connect.

## Product boundary

Users interact with https://open-connect.site. This service remains an internal model runtime behind the Open-Connect gateway.

## Public routing contract

- UI: `https://open-connect.site/models`
- OpenAI-compatible gateway: `https://open-connect.site/v1/*`

Open-Connect should expose supported LiteLLM providers/models through one catalog and one scoped gateway while retaining routing, retries/fallbacks, load balancing, usage controls, budgets, guardrails, and other supported open-source LiteLLM gateway capabilities.

## Security invariants

- Never expose the LiteLLM master key to browsers or community AI clients.
- Never commit model-provider API credentials.
- User-facing Open-Connect keys must be scoped and revocable.
- Provider credentials stay server-side.
- Toolkits may restrict models, aliases, budgets, and permissions.

## Runtime

LiteLLM is a server/container workload. Do not compile this repository into the Open-Connect Vite frontend. Cloudflare remains the public edge/domain and routes `/v1/*` to this runtime through the Open-Connect gateway architecture.

## Upstream policy

Keep upstream LiteLLM source history intact. Preserve applicable upstream licenses/notices and do not assume enterprise-only features are open-source.
