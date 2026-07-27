# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-07-27 06:40 UTC · **History:** 335 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 42.5% |
| YouTube | 38.2% |
| LinkedIn | 37.9% |
| Qzone | 36.4% |
| Instagram | 35.8% |
| X (Twitter) | 35.7% |
| TikTok | 35.3% |
| Mail.ru | 30.9% |
| VK | 29.4% |
| OK.ru | 28.1% |
| Telegram | 27.7% |
| Reddit | 16.5% |
| Yandex | 14.5% |
| Avito | 11.6% |
| Facebook | 1.9% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 1.9% of live proxies get through
- **Avito** — 11.6% of live proxies get through
- **Yandex** — 14.5% of live proxies get through
- **Reddit** — 16.5% of live proxies get through
- **Telegram** — 27.7% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 43.8% | 39.3% | 37.1% | 37.5% | 38.9% | 37.7% |
| hosting | 38.1% | 32.3% | 28.7% | 29.4% | 32.3% | 30.9% |
| unknown | 48.8% | 51.8% | 48.8% | 36.5% | 48.0% | 35.1% |
| mobile | 36.8% | 36.8% | 41.9% | 40.2% | 44.4% | 39.3% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| Indonesia (ID) | 39.3% | 49.8% | 50.9% | 50.7% |
| United States (US) | 45.7% | 37.8% | 31.1% | 40.2% |
| Albania (AL) | 85.9% | 69.7% | 68.5% | 79.2% |
| Russia (RU) | 52.6% | 5.7% | 23.9% | 8.6% |
| Brazil (BR) | 47.5% | 24.9% | 24.9% | 24.9% |
| China (CN) | 1.7% | 0.6% | 0.6% | 18.8% |
| Germany (DE) | 43.3% | 32.7% | 34.7% | 36.7% |
| Türkiye (TR) | 80.8% | 8.9% | 8.2% | 8.2% |
| Colombia (CO) | 28.0% | 31.5% | 32.2% | 30.1% |
| India (IN) | 34.0% | 29.1% | 26.2% | 34.0% |
| Philippines (PH) | 47.8% | 48.5% | 46.3% | 50.0% |
| Mexico (MX) | 22.2% | 26.2% | 26.2% | 25.4% |
| The Netherlands (NL) | 32.2% | 26.4% | 30.6% | 28.9% |
| Bangladesh (BD) | 46.6% | 48.3% | 46.6% | 44.0% |
| Singapore (SG) | 46.7% | 40.0% | 42.9% | 41.9% |
| Vietnam (VN) | 37.5% | 37.5% | 30.8% | 40.4% |
| Japan (JP) | 63.2% | 48.3% | 47.1% | 49.4% |
| South Korea (KR) | 12.3% | 15.1% | 13.7% | 15.1% |
| France (FR) | 37.1% | 35.7% | 31.4% | 31.4% |
| United Kingdom (GB) | 18.2% | 21.2% | 22.7% | 21.2% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 335 daily snapshots since 2025-04-09 |

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
