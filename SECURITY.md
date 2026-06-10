# Security Policy

KosovoPay moves money. We take security seriously and appreciate responsible disclosure.

## Reporting a vulnerability

**Please do not open public issues for security problems.**

Email **security@kosovo.sh** with:

- a description of the issue and its impact,
- steps to reproduce (proof-of-concept if possible),
- affected SDK / endpoint / version.

You can expect:

| Stage | Target |
|---|---|
| Acknowledgement | within **48 hours** |
| Triage & severity | within **5 business days** |
| Fix & coordinated disclosure | as fast as severity warrants |

If you prefer encrypted email, request our PGP key in your first message.

## Supported versions

Security fixes land on the **latest minor** of each official SDK and the live API.
Older majors are supported on a best-effort basis only.

| Component | Supported |
|---|---|
| `kosovopay/php-sdk` | latest `1.x` |
| `kosovopay/python-sdk` | latest `1.x` |
| `kosovopay/go-sdk` | latest `1.x` |
| `kosovopay/dotnet-sdk` | latest `1.x` |
| KosovoPay API (`api.kosovo.sh`) | current |

## Scope

In scope: the official SDKs and the KosovoPay API. Out of scope: third-party bank
gateways, and any system not operated by KosovoPay.

## Safe harbor

We will not pursue or support legal action against researchers who act in good faith,
avoid privacy violations and service disruption, and give us reasonable time to remediate
before any disclosure.
