# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-09-03 06:40 UTC · **History:** 373 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 31.4% |
| Qzone | 27.0% |
| LinkedIn | 26.7% |
| TikTok | 26.1% |
| X (Twitter) | 25.8% |
| YouTube | 25.4% |
| Instagram | 23.6% |
| VK | 21.0% |
| OK.ru | 19.9% |
| Reddit | 16.8% |
| Telegram | 16.3% |
| Mail.ru | 9.4% |
| Yandex | 9.0% |
| Avito | 8.6% |
| Facebook | 0.3% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.3% of live proxies get through
- **Avito** — 8.6% of live proxies get through
- **Yandex** — 9.0% of live proxies get through
- **Mail.ru** — 9.4% of live proxies get through
- **Telegram** — 16.3% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 41.6% | 30.4% | 30.0% | 32.0% | 31.6% | 30.2% |
| hosting | 20.0% | 19.7% | 16.3% | 19.4% | 21.2% | 21.0% |
| mobile | 28.6% | 25.0% | 28.6% | 28.6% | 39.3% | 25.0% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 26.3% | 18.9% | 18.5% | 20.7% |
| Indonesia (ID) | 39.5% | 42.5% | 42.9% | 43.6% |
| Germany (DE) | 29.2% | 21.4% | 25.0% | 29.8% |
| Türkiye (TR) | 79.2% | 4.7% | 6.0% | 5.4% |
| Russia (RU) | 41.8% | 0.0% | 30.8% | 4.8% |
| Brazil (BR) | 49.3% | 22.9% | 22.1% | 23.6% |
| France (FR) | 25.2% | 26.0% | 29.0% | 26.0% |
| Mexico (MX) | 24.4% | 23.6% | 26.0% | 27.6% |
| India (IN) | 31.1% | 22.7% | 21.0% | 27.7% |
| Canada (CA) | 12.5% | 7.1% | 8.0% | 12.5% |
| China (CN) | 2.7% | 0.9% | 0.9% | 17.1% |
| Singapore (SG) | 35.2% | 26.9% | 33.3% | 34.3% |
| Colombia (CO) | 33.7% | 28.6% | 28.6% | 33.7% |
| Hong Kong (HK) | 23.1% | 17.6% | 19.8% | 23.1% |
| United Kingdom (GB) | 10.5% | 5.8% | 8.1% | 5.8% |
| Philippines (PH) | 38.1% | 42.9% | 39.3% | 36.9% |
| Australia (AU) | 1.2% | 1.2% | 13.4% | 14.6% |
| The Netherlands (NL) | 37.8% | 35.1% | 33.8% | 41.9% |
| Japan (JP) | 20.0% | 12.9% | 17.1% | 21.4% |
| Bangladesh (BD) | 42.0% | 42.0% | 44.9% | 42.0% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 373 daily snapshots since 2025-04-09 |

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
