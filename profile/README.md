<div align="center">

<h1>KosovoPay</h1>

### Every bank in Kosovo speaks a different protocol.<br/>We speak all of them — so you write <em>one</em> integration.

A payment-orchestration platform that puts a single, developer-first API in front of
Kosovo's banks and payment providers: **hosted &amp; direct checkout, refunds, multi-currency
FX, and signed webhooks.**

<br/>

[![Website](https://img.shields.io/badge/kosovo.sh-2563eb?style=flat-square&logo=icloud&logoColor=white)](https://kosovo.sh)
[![API Docs](https://img.shields.io/badge/API_reference-1f2937?style=flat-square&logo=readthedocs&logoColor=white)](https://api.kosovo.sh/docs)
[![100% Free](https://img.shields.io/badge/100%25_free_%26_open_source-22c55e?style=flat-square)](#-pricing--license)
[![License: MIT](https://img.shields.io/badge/license-MIT-3da639?style=flat-square)](https://opensource.org/licenses/MIT)

<br/>

**One SDK per language — install and ship in minutes:**

[![PHP](https://img.shields.io/badge/PHP-php--sdk-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://github.com/kosovopay/php-sdk)
&nbsp;[![Python](https://img.shields.io/badge/Python-kosovopay-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://github.com/kosovopay/python-sdk)
&nbsp;[![Go](https://img.shields.io/badge/Go-go--sdk-00ADD8?style=for-the-badge&logo=go&logoColor=white)](https://github.com/kosovopay/go-sdk)
&nbsp;[![.NET](https://img.shields.io/badge/.NET-KosovoPay-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)](https://github.com/kosovopay/dotnet-sdk)

</div>

---

## Why it exists

Accepting card and bank payments in Kosovo means integrating each bank's gateway by hand —
every one with its own session format, currency rules, refund semantics, and failure modes.
KosovoPay collapses that into **one Stripe-grade API**. Integrate once; reach every provider.

|  | |
|---|---|
| 💳 **Two checkout modes** | Redirect to a branded hosted page, or send the customer straight to their bank (direct mode). |
| 🔁 **Refunds + audit trail** | Full and partial refunds over an event-sourced, tamper-evident ledger. |
| 🌍 **155 currencies** | Full ISO 4217 coverage; FX locks at create-time, so the customer pays exactly what they saw. |
| 🔔 **Signed webhooks** | HMAC-SHA256 events for every lifecycle change, delivered with retries. |
| 🔐 **BYOK** | You own the bank relationship; credentials are envelope-encrypted and never shared. |
| ⚡ **Idempotent by default** | Automatic idempotency keys + safe retries — a network blip can never double-charge. |

---

## Quickstart

The same typed contract in every language. Here it is in PHP:

```php
use KosovoPay\KosovoPay;
use KosovoPay\Enums\CurrencyCode;
use KosovoPay\Params\CreatePaymentParams;

$kp = new KosovoPay($_ENV['KOSOVOPAY_SECRET_KEY']);

$payment = $kp->payments->create(new CreatePaymentParams(
    amount:     4990,                 // €49.90, in minor units
    currency:   CurrencyCode::EUR,
    successUrl: 'https://shop.test/thank-you',
), idempotencyKey: 'order-1024');

header("Location: {$payment->hostedUrl}");   // off to checkout
```

## Official SDKs

| Language | Package | Install |
|----------|---------|---------|
| **PHP** | [`kosovopay/php-sdk`](https://github.com/kosovopay/php-sdk) | `composer require kosovopay/php-sdk` |
| **Python** | [`kosovopay`](https://github.com/kosovopay/python-sdk) | `pip install kosovopay` |
| **Go** | [`github.com/kosovopay/go-sdk`](https://github.com/kosovopay/go-sdk) | `go get github.com/kosovopay/go-sdk` |
| **.NET** | [`KosovoPay`](https://github.com/kosovopay/dotnet-sdk) | `dotnet add package KosovoPay` |

Every SDK ships the identical contract: strongly-typed models, forward-compatible enums,
cursor pagination, automatic idempotency, a typed error hierarchy, and webhook verification —
each statically analysed, tested, and CI-gated.

---

## Coverage — Kosovo's banks &amp; payment providers

Institutions in the Kosovo market, with their official websites. Listed **for reference and
interoperability only** (see the [disclaimer](#%EF%B8%8F-disclaimer)).

### Banks &nbsp;<sub>(licensed by the Central Bank of the Republic of Kosovo)</sub>

| | Bank | Website |
|:--:|---|---|
| <img src="https://raiffeisen-kosovo.com/favicon.ico" height="22" alt=""> | **Raiffeisen Bank Kosovo** | [raiffeisen-kosovo.com](https://www.raiffeisen-kosovo.com) |
| <img src="https://www.procreditbank-kos.com/favicon.ico" height="22" alt=""> | **ProCredit Bank Kosovo** | [procreditbank-kos.com](https://www.procreditbank-kos.com) |
| <img src="https://www.nlb-kos.com/favicon.ico" height="22" alt=""> | **NLB Banka Kosovo** | [nlb-kos.com](https://www.nlb-kos.com) |
| <img src="https://bkt-ks.com/favicon.ico" height="22" alt=""> | **Banka Kombëtare Tregtare — BKT Kosova** | [bkt-ks.com](https://bkt-ks.com) |
| <img src="https://teb-kos.com/favicon.ico" height="22" alt=""> | **TEB Sh.A.** | [teb-kos.com](https://teb-kos.com) |
| <img src="https://www.bpbbank.com/favicon.ico" height="22" alt=""> | **Banka për Biznes — BPB** | [bpbbank.com](https://www.bpbbank.com) |
| 🏦 | **Banka Ekonomike** | [bankaekonomike.com](https://bankaekonomike.com) |

### Payment institutions &amp; fintech wallets

| | Provider | Website |
|:--:|---|---|
| <img src="https://onefor.com/favicon.ico" height="22" alt=""> | **Onefor** | [onefor.com](https://onefor.com) |
| <img src="https://www.paysera.com/favicon.ico" height="22" alt=""> | **Paysera** | [paysera.com](https://www.paysera.com) |

> Regulator: **Central Bank of the Republic of Kosovo (BQK)** — [bqk-kos.org](https://bqk-kos.org).
> The authoritative, complete list of licensed institutions is published by the BQK.

---

## 💚 Pricing &amp; license

**The SDKs and developer libraries are 100% free and open source — forever — under the [MIT License](https://opensource.org/licenses/MIT).**

- ✅ Free to use, modify, and ship — commercially or otherwise.
- ✅ No license fees, no per-seat costs, no paywalls on the libraries.
- ✅ No vendor lock-in — bring your own bank keys.

| Library | License | Cost |
|---|---|---|
| [php-sdk](https://github.com/kosovopay/php-sdk) · [python-sdk](https://github.com/kosovopay/python-sdk) · [go-sdk](https://github.com/kosovopay/go-sdk) · [dotnet-sdk](https://github.com/kosovopay/dotnet-sdk) | **MIT** | **Free forever** |

---

## ⚖️ Disclaimer

> **KosovoPay is an independent project.** It is **not sponsored, endorsed, owned, operated, or
> maintained by any bank, by any bank employee, or by any financial institution or company.**
>
> All bank and provider names, logos, trademarks, and domains above are the property of their
> respective owners and appear **purely for reference and interoperability**. Their inclusion
> implies **no** partnership, affiliation, or endorsement.
>
> **All source code in this organization is the exclusive property of the KosovoPay organization.**
> To be 100% clear: nothing here is produced on behalf of, or under the direction of, any bank or its staff.

---

<div align="center">

**[kosovo.sh](https://kosovo.sh)** · **[API Docs](https://api.kosovo.sh/docs)** · built in Kosovo 🇽🇰 for developers everywhere

</div>
