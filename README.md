# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-02 06:40 UTC · **History:** 341 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 41.1% |
| LinkedIn | 31.7% |
| YouTube | 31.6% |
| Qzone | 31.5% |
| TikTok | 30.8% |
| X (Twitter) | 30.8% |
| Instagram | 29.6% |
| Mail.ru | 26.1% |
| OK.ru | 24.6% |
| VK | 24.3% |
| Telegram | 22.0% |
| Reddit | 21.0% |
| Yandex | 13.5% |
| Avito | 10.3% |
| Facebook | 0.6% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.6% of live proxies get through
- **Avito** — 10.3% of live proxies get through
- **Yandex** — 13.5% of live proxies get through
- **Reddit** — 21.0% of live proxies get through
- **Telegram** — 22.0% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 44.3% | 32.5% | 31.5% | 32.9% | 33.0% | 32.6% |
| hosting | 33.9% | 26.9% | 22.5% | 23.3% | 25.7% | 23.9% |
| unknown | 47.0% | 46.6% | 44.2% | 45.0% | 44.6% | 46.2% |
| mobile | 31.6% | 29.6% | 27.6% | 28.6% | 35.7% | 27.6% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| Indonesia (ID) | 52.6% | 51.2% | 53.0% | 51.5% |
| United States (US) | 33.5% | 22.8% | 20.8% | 21.2% |
| Russia (RU) | 49.8% | 2.8% | 24.9% | 8.8% |
| Brazil (BR) | 53.8% | 24.4% | 27.5% | 26.9% |
| China (CN) | 4.5% | 1.3% | 1.3% | 27.4% |
| Türkiye (TR) | 86.5% | 8.3% | 9.8% | 9.0% |
| Germany (DE) | 41.1% | 33.3% | 30.2% | 32.6% |
| Mexico (MX) | 31.9% | 33.6% | 29.3% | 31.0% |
| Philippines (PH) | 41.9% | 41.0% | 45.7% | 43.8% |
| India (IN) | 38.8% | 26.5% | 19.4% | 27.6% |
| Colombia (CO) | 29.8% | 26.6% | 26.6% | 25.5% |
| Vietnam (VN) | 30.1% | 24.7% | 24.7% | 25.8% |
| France (FR) | 35.6% | 31.0% | 34.5% | 34.5% |
| Singapore (SG) | 46.5% | 44.2% | 44.2% | 44.2% |
| The Netherlands (NL) | 42.2% | 37.3% | 41.0% | 39.8% |
| Bangladesh (BD) | 60.8% | 60.8% | 55.4% | 55.4% |
| Japan (JP) | 64.3% | 48.6% | 48.6% | 50.0% |
| Venezuela (VE) | 47.8% | 47.8% | 49.3% | 46.4% |
| South Korea (KR) | 14.7% | 8.8% | 10.3% | 10.3% |
| United Kingdom (GB) | 29.5% | 24.6% | 23.0% | 24.6% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 341 daily snapshots since 2025-04-09 |

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
