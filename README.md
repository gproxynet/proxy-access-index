# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-20 06:40 UTC · **History:** 359 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 30.5% |
| YouTube | 25.8% |
| TikTok | 25.4% |
| X (Twitter) | 24.6% |
| LinkedIn | 24.5% |
| Instagram | 23.6% |
| Qzone | 20.7% |
| VK | 19.4% |
| OK.ru | 18.3% |
| Reddit | 18.1% |
| Telegram | 18.0% |
| Yandex | 10.8% |
| Mail.ru | 8.8% |
| Avito | 8.0% |
| Facebook | 0.6% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.6% of live proxies get through
- **Avito** — 8.0% of live proxies get through
- **Mail.ru** — 8.8% of live proxies get through
- **Yandex** — 10.8% of live proxies get through
- **Telegram** — 18.0% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 32.3% | 24.8% | 24.0% | 23.9% | 24.2% | 24.1% |
| hosting | 27.7% | 27.4% | 23.1% | 27.9% | 24.8% | 25.2% |
| mobile | 27.0% | 21.6% | 18.9% | 21.6% | 27.0% | 27.0% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| Indonesia (ID) | 36.0% | 39.1% | 36.2% | 37.2% |
| United States (US) | 24.5% | 12.7% | 13.8% | 13.2% |
| Türkiye (TR) | 72.6% | 6.8% | 7.4% | 8.4% |
| Russia (RU) | 39.4% | 1.8% | 23.6% | 8.5% |
| Switzerland (CH) | 87.3% | 87.3% | 87.9% | 87.3% |
| India (IN) | 21.8% | 18.4% | 23.8% | 19.7% |
| China (CN) | 5.6% | 0.0% | 0.0% | 14.6% |
| Brazil (BR) | 39.7% | 14.0% | 13.2% | 11.0% |
| Germany (DE) | 28.3% | 22.0% | 26.8% | 22.0% |
| Mexico (MX) | 27.0% | 30.6% | 32.4% | 36.0% |
| Singapore (SG) | 42.7% | 32.7% | 34.5% | 36.4% |
| France (FR) | 30.4% | 32.4% | 24.5% | 21.6% |
| Colombia (CO) | 23.0% | 24.0% | 21.0% | 24.0% |
| Hong Kong (HK) | 24.5% | 28.6% | 25.5% | 30.6% |
| South Korea (KR) | 11.5% | 12.5% | 18.8% | 13.5% |
| The Netherlands (NL) | 38.3% | 31.9% | 41.5% | 40.4% |
| Philippines (PH) | 34.8% | 34.8% | 34.8% | 33.7% |
| Japan (JP) | 17.3% | 14.7% | 16.0% | 13.3% |
| Bangladesh (BD) | 21.5% | 29.2% | 29.2% | 32.3% |
| Canada (CA) | 13.8% | 9.2% | 15.4% | 10.8% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 359 daily snapshots since 2025-04-09 |

```bash
curl -s https://raw.githubusercontent.com/gproxynet/proxy-access-index/main/latest.json
```

## Method and scope

Daily history uses that day's measured base -- the larger of the network-type totals and the biggest single-site count -- so every rate stays a share of the pool actually measured that day.

Every proxy in the pool is rechecked continuously. For each target the checker makes a real request through the proxy and records whether the response is served or blocked. Everything here is a **rate over that pool** — a percentage, never a guarantee for any individual IP, and it moves as sites tighten or relax detection. That drift is why the daily history is published next to the snapshot.

Only rates are published. No IP addresses, no per-proxy access flags and no pool volumes — this is a reference for sizing a job, not a proxy list. For a list of actual (public, unstable) proxies see [free-proxy-list](https://github.com/gproxynet/free-proxy-list).

## Where the numbers come from

The pool behind them is [GProxy](https://gproxy.net/?utm_source=github&utm_medium=readme&utm_campaign=proxy-access-index) — residential, mobile, ISP and datacenter proxies, filterable by country, protocol and by the site-access checks measured above, so you can request only IPs that still pass your target.

- [Pricing](https://gproxy.net/en/pricing/?utm_source=github&utm_medium=repo&utm_campaign=proxy-access-index) — residential from $0.70/GB, unlimited public pool from $3/day
- [free-proxy-list](https://github.com/gproxynet/free-proxy-list) — public sample, refreshed every 30 minutes
- [proxyspin](https://github.com/gproxynet/proxyspin) — rotating proxy pool for Scrapy, Playwright and requests
- [Proxy Switcher & Manager](https://github.com/gproxynet/proxy-switcher) — one-click proxy switcher for Chrome

---
*Auto-generated daily. Do not edit by hand.*
