<div align="center">

# KosovoPay

### One payment API for every bank in Kosovo

**KosovoPay** is a payment-orchestration platform that unifies Kosovo's bank gateways behind a single,
developer-first API — hosted &amp; direct checkout, refunds, multi-currency FX, and signed webhooks.
Integrate once; reach every bank.

[![Website](https://img.shields.io/badge/website-kosovo.sh-2563eb?style=flat-square)](https://kosovo.sh)
[![API Docs](https://img.shields.io/badge/docs-api.kosovo.sh%2Fdocs-1f2937?style=flat-square)](https://api.kosovo.sh/docs)
[![PyPI](https://img.shields.io/pypi/v/kosovopay?style=flat-square&label=pypi&color=3776AB)](https://pypi.org/project/kosovopay/)

</div>

---

## What we build

KosovoPay is the orchestration layer between Kosovan banks and the businesses that accept payments from them.
Every bank exposes a different gateway — different session formats, currencies, refund rules, and failure
modes. We hide all of it behind **one Stripe-grade API** so merchants integrate a single time.

- 💳 **Hosted &amp; direct checkout** — redirect to a branded payment page, or straight to the customer's bank.
- 🔁 **Refunds &amp; reconciliation** — full and partial refunds, with a tamper-evident, event-sourced audit trail.
- 🌍 **155 currencies, exact FX** — full ISO 4217 coverage; rates lock at create time, so the customer pays what they saw.
- 🔔 **Signed webhooks** — HMAC-SHA256 events for every lifecycle change, delivered with retries.
- 🔐 **Bring your own keys (BYOK)** — you own the bank relationship; credentials are envelope-encrypted and never shared.
- ⚡ **Idempotent &amp; resilient** — automatic idempotency keys and safe retries so a network blip never double-charges.

> **Keywords:** payment gateway Kosovo · payment orchestration · online payments Kosovo ·
> pagesa online Kosovë · bank API Kosovo · merchant payments · payment SDK · checkout API.

---

## Official SDKs

Strongly-typed, production-grade client libraries — pick your language and ship in minutes.

| Language | Package | Install | Repository |
|----------|---------|---------|------------|
| **PHP** | `kosovopay/php-sdk` | `composer require kosovopay/php-sdk` | [php-sdk](https://github.com/kosovopay/php-sdk) |
| **Python** | `kosovopay` | `pip install kosovopay` | [python-sdk](https://github.com/kosovopay/python-sdk) |
| **Go** | `github.com/kosovopay/go-sdk` | `go get github.com/kosovopay/go-sdk` | [go-sdk](https://github.com/kosovopay/go-sdk) |
| **.NET** | `KosovoPay` | `dotnet add package KosovoPay` | [dotnet-sdk](https://github.com/kosovopay/dotnet-sdk) |

Every SDK ships the same contract: typed models, forward-compatible enums, cursor pagination, automatic
idempotency, a typed error hierarchy, and webhook signature verification.

```php
use KosovoPay\KosovoPay;
use KosovoPay\Enums\CurrencyCode;
use KosovoPay\Params\CreatePaymentParams;

$kp = new KosovoPay($_ENV['KOSOVOPAY_SECRET_KEY']);

$payment = $kp->payments->create(new CreatePaymentParams(
    amount:     4990,                 // €49.90 in minor units
    currency:   CurrencyCode::EUR,
    successUrl: 'https://shop.test/thank-you',
), idempotencyKey: 'order-1024');

header("Location: {$payment->hostedUrl}");
```

---

## Developer resources

| Resource | Link |
|----------|------|
| 📘 API reference (interactive) | **https://api.kosovo.sh/docs** |
| 🌐 Website | **https://kosovo.sh** |
| 🧩 SDKs | [php-sdk](https://github.com/kosovopay/php-sdk) · [python-sdk](https://github.com/kosovopay/python-sdk) · [go-sdk](https://github.com/kosovopay/go-sdk) · [dotnet-sdk](https://github.com/kosovopay/dotnet-sdk) |

---

## Banks in Kosovo

Commercial banks licensed by the **Central Bank of the Republic of Kosovo (BQK)**. Names and official
domains are provided for reference and convenience only.

| Bank | Official website |
|------|------------------|
| <img src="https://www.google.com/s2/favicons?domain=raiffeisen-kosovo.com&sz=64" width="18" align="absmiddle" alt=""> **Raiffeisen Bank Kosovo** | [raiffeisen-kosovo.com](https://www.raiffeisen-kosovo.com) |
| <img src="https://www.google.com/s2/favicons?domain=procreditbank-kos.com&sz=64" width="18" align="absmiddle" alt=""> **ProCredit Bank Kosovo** | [procreditbank-kos.com](https://www.procreditbank-kos.com) |
| <img src="https://www.google.com/s2/favicons?domain=nlb-kos.com&sz=64" width="18" align="absmiddle" alt=""> **NLB Banka Kosovo** | [nlb-kos.com](https://www.nlb-kos.com) |
| <img src="https://www.google.com/s2/favicons?domain=bkt-ks.com&sz=64" width="18" align="absmiddle" alt=""> **Banka Kombëtare Tregtare (BKT Kosova)** | [bkt-ks.com](https://bkt-ks.com) |
| <img src="https://www.google.com/s2/favicons?domain=teb-kos.com&sz=64" width="18" align="absmiddle" alt=""> **TEB Sh.A. (TEB Bank)** | [teb-kos.com](https://teb-kos.com) |
| <img src="https://www.google.com/s2/favicons?domain=bpbbank.com&sz=64" width="18" align="absmiddle" alt=""> **Banka për Biznes (BPB)** | [bpbbank.com](https://www.bpbbank.com) |
| <img src="https://www.google.com/s2/favicons?domain=bankaekonomike.com&sz=64" width="18" align="absmiddle" alt=""> **Banka Ekonomike** | [bankaekonomike.com](https://bankaekonomike.com) |

> Regulator: **Central Bank of the Republic of Kosovo (BQK)** — [bqk-kos.org](https://bqk-kos.org).
> The full, authoritative list of licensed banks and financial institutions is published by the BQK.

---

## ⚖️ Disclaimer

> **This project is independent.** KosovoPay is **not sponsored, endorsed, owned, operated, or maintained
> by any bank, by any bank employee, or by any financial institution or company.**
>
> All bank names, logos, trademarks, and domains shown above are the property of their respective owners and
> are listed **for reference and interoperability purposes only**. Their inclusion does **not** imply any
> partnership, affiliation, or endorsement.
>
> **All source code in this organization is the exclusive property of the KosovoPay organization.** To make
> it 100% clear: nothing here is produced on behalf of, or under the direction of, any bank or its staff.

---

<div align="center">

© KosovoPay — built in Kosovo 🇽🇰 for developers everywhere.

</div>
