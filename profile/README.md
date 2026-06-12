<div align="center">

<h1>KosovoPay</h1>

### Kosovo's banks don't speak the same language.<br/>**We translate.**

**One payment API for every bank in Kosovo.** Wire it up once — accept cards and bank
transfers from all of them. Hosted checkout, refunds, multi-currency, signed webhooks.
No per-bank plumbing. No surprises.

<sub><em>Pranoni pagesa online në Kosovë — me një API të vetëm.</em></sub>

<br/>

[![Website](https://img.shields.io/badge/kosovo.sh-2563eb?style=flat-square&logo=icloud&logoColor=white)](https://kosovo.sh)
[![API Docs](https://img.shields.io/badge/API_reference-1f2937?style=flat-square&logo=readthedocs&logoColor=white)](https://pay.kosovo.sh/docs)
[![Free to use](https://img.shields.io/badge/free_to_use-%E2%82%AC0-22c55e?style=flat-square)](#free-to-use)
[![License](https://img.shields.io/badge/license-KosovoPay_1.0-3da639?style=flat-square)](https://github.com/kosovopay/php-sdk/blob/master/LICENSE)

[![PHP](https://img.shields.io/badge/PHP-php--sdk-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://github.com/kosovopay/php-sdk)
&nbsp;[![Python](https://img.shields.io/badge/Python-kosovopay-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://github.com/kosovopay/python-sdk)
&nbsp;[![Go](https://img.shields.io/badge/Go-go--sdk-00ADD8?style=for-the-badge&logo=go&logoColor=white)](https://github.com/kosovopay/go-sdk)
&nbsp;[![.NET](https://img.shields.io/badge/.NET-KosovoPay-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)](https://github.com/kosovopay/dotnet-sdk)
&nbsp;[![TypeScript](https://img.shields.io/badge/TypeScript-server--sdk-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://github.com/kosovopay/js-server-sdk)

</div>

---

## The problem, in one line

Seven banks. Seven gateways. Seven sets of quirks. Integrate them one by one and you'll
ship a *payment integration* instead of a *product*. KosovoPay is the one API that already
speaks all of them — so **accepting online payments in Kosovo** stops being a project and
starts being a single function call.

## What you get

|  |  |
|---|---|
| 💳 **Two ways to get paid** | A branded hosted page, or straight to the customer's bank. Your call, same call. |
| 🔁 **Refunds without the runaround** | Full or partial, every cent reconciled on a tamper-evident, event-sourced ledger. |
| 🌍 **155 currencies, fixed at checkout** | Full ISO 4217. The rate locks when the order is created — customers pay what they see, to the cent. |
| 🔔 **Webhooks you can trust** | Every event signed with HMAC-SHA256 and retried until it lands. |
| 🔐 **Your keys, your rules** | Bring your own bank credentials — envelope-encrypted, never shared, never ours. |
| ⚡ **Idempotent by design** | Lightning never charges twice. A network blip can't double-bill your customer. |

## Get paid in five lines

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

header("Location: {$payment->hostedUrl}");   // and they're off to checkout
```

## Pick your language

Five SDKs, one contract. Typed end-to-end, statically analysed, tested, CI-gated.

| Language | Package | Install |
|---|---|---|
| **PHP** | [`kosovopay/php-sdk`](https://github.com/kosovopay/php-sdk) | `composer require kosovopay/php-sdk` |
| **Python** | [`kosovopay`](https://github.com/kosovopay/python-sdk) | `pip install kosovopay` |
| **Go** | [`github.com/kosovopay/go-sdk`](https://github.com/kosovopay/go-sdk) | `go get github.com/kosovopay/go-sdk` |
| **.NET** | [`KosovoPay`](https://github.com/kosovopay/dotnet-sdk) | `dotnet add package KosovoPay` |
| **TypeScript / Node** | [`@kosovopay/server-sdk`](https://github.com/kosovopay/js-server-sdk) | `npm i @kosovopay/server-sdk` |

---

## Coverage — Kosovo's banks &amp; payment providers

Integrate **ProCredit, Raiffeisen, NLB, BKT, TEB, BPB and Banka Ekonomike** — plus fintech
wallets like **Onefor** and **Paysera** — through one API. Names and official sites below,
listed **for reference and interoperability only** (see the [disclaimer](#%EF%B8%8F-disclaimer)).

### Banks &nbsp;<sub>(licensed by the Central Bank of the Republic of Kosovo)</sub>

| | Bank | Website |
|:--:|---|---|
| <img src="https://www.google.com/s2/favicons?domain=raiffeisen-kosovo.com&sz=128" width="22" height="22" alt=""> | **Raiffeisen Bank Kosovo** | [raiffeisen-kosovo.com](https://www.raiffeisen-kosovo.com) |
| <img src="https://www.google.com/s2/favicons?domain=procreditbank-kos.com&sz=128" width="22" height="22" alt=""> | **ProCredit Bank Kosovo** | [procreditbank-kos.com](https://www.procreditbank-kos.com) |
| <img src="https://www.google.com/s2/favicons?domain=nlb-kos.com&sz=128" width="22" height="22" alt=""> | **NLB Banka Kosovo** | [nlb-kos.com](https://www.nlb-kos.com) |
| <img src="https://www.google.com/s2/favicons?domain=bkt-ks.com&sz=128" width="22" height="22" alt=""> | **Banka Kombëtare Tregtare — BKT Kosova** | [bkt-ks.com](https://bkt-ks.com) |
| 🏦 | **TEB Sh.A.** | [teb-kos.com](https://teb-kos.com) |
| <img src="https://www.google.com/s2/favicons?domain=bpbbank.com&sz=128" width="22" height="22" alt=""> | **Banka për Biznes — BPB** | [bpbbank.com](https://www.bpbbank.com) |
| 🏦 | **Banka Ekonomike** | [bankaekonomike.com](https://bankaekonomike.com) |

### Payment institutions &amp; fintech wallets

| | Provider | Website |
|:--:|---|---|
| <img src="https://www.google.com/s2/favicons?domain=onefor.com&sz=128" width="22" height="22" alt=""> | **Onefor** | [onefor.com](https://onefor.com) |
| <img src="https://www.google.com/s2/favicons?domain=paysera.com&sz=128" width="22" height="22" alt=""> | **Paysera** | [paysera.com](https://www.paysera.com) |

> Regulator: **Central Bank of the Republic of Kosovo (BQK)** — [bqk-kos.org](https://bqk-kos.org).
> The complete, authoritative list of licensed institutions is published by the BQK.

---

## Free to use

**Every SDK is free to use — including commercially — at no charge.** The source is public, so you can
read and audit every line. The libraries are maintained **solely by KosovoPay**.

- ✅ Use, run, and integrate — commercial use included, **€0**, no per-seat fees, no paywalls.
- ✅ Read the full source — nothing hidden.
- ✅ No lock-in: your bank keys stay yours.
- ❌ No forking, modifying, redistributing, or reverse-engineering — KosovoPay maintains the SDKs.

| Libraries | License | Cost |
|---|---|---|
| [php-sdk](https://github.com/kosovopay/php-sdk) · [python-sdk](https://github.com/kosovopay/python-sdk) · [go-sdk](https://github.com/kosovopay/go-sdk) · [dotnet-sdk](https://github.com/kosovopay/dotnet-sdk) · [js-server-sdk](https://github.com/kosovopay/js-server-sdk) | **KosovoPay License 1.0** | **€0, forever** |

---

## ⚖️ Disclaimer

> **KosovoPay is an independent project.** It is **not sponsored, endorsed, owned, operated, or
> maintained by any bank, by any bank employee, or by any financial institution or company.**
>
> All bank and provider names, logos, trademarks, and domains shown above are the property of
> their respective owners and appear **purely for reference and interoperability**. Their
> inclusion implies **no** partnership, affiliation, or endorsement.
>
> **All source code in this organization is the exclusive property of the KosovoPay organization.**
> To be 100% clear: nothing here is produced on behalf of, or under the direction of, any bank or its staff.

---

<div align="center">

One API. Every bank. Get paid.

**[kosovo.sh](https://kosovo.sh)** · **[Docs](https://pay.kosovo.sh/docs)** · made in Kosovo 🇽🇰 for developers everywhere

</div>
