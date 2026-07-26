# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-07-26 06:40 UTC · **History:** 334 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 32.2% |
| YouTube | 29.2% |
| LinkedIn | 28.5% |
| Instagram | 26.0% |
| X (Twitter) | 25.3% |
| TikTok | 25.1% |
| Qzone | 25.1% |
| Mail.ru | 24.5% |
| VK | 21.7% |
| OK.ru | 20.1% |
| Telegram | 19.9% |
| Yandex | 11.1% |
| Reddit | 9.2% |
| Avito | 7.3% |
| Facebook | 2.9% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 2.9% of live proxies get through
- **Avito** — 7.3% of live proxies get through
- **Reddit** — 9.2% of live proxies get through
- **Yandex** — 11.1% of live proxies get through
- **Telegram** — 19.9% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 31.7% | 28.0% | 25.1% | 26.2% | 27.4% | 26.2% |
| hosting | 30.4% | 26.5% | 22.0% | 22.6% | 25.4% | 23.2% |
| unknown | 47.6% | 50.8% | 49.5% | 27.0% | 48.5% | 27.4% |
| mobile | 18.4% | 24.5% | 24.5% | 23.5% | 30.6% | 23.5% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 35.7% | 28.3% | 19.2% | 29.8% |
| Indonesia (ID) | 14.0% | 25.8% | 27.5% | 28.4% |
| Albania (AL) | 86.1% | 77.1% | 66.1% | 80.4% |
| Russia (RU) | 45.9% | 5.2% | 21.1% | 9.8% |
| China (CN) | 1.9% | 0.0% | 0.0% | 17.4% |
| Türkiye (TR) | 77.9% | 5.3% | 6.1% | 6.1% |
| Brazil (BR) | 43.0% | 14.8% | 14.8% | 13.3% |
| Germany (DE) | 31.2% | 32.0% | 32.0% | 33.6% |
| The Netherlands (NL) | 30.4% | 27.7% | 28.6% | 27.7% |
| Vietnam (VN) | 50.9% | 47.2% | 41.5% | 43.4% |
| Singapore (SG) | 41.9% | 35.5% | 36.6% | 39.8% |
| India (IN) | 21.8% | 18.4% | 16.1% | 17.2% |
| Colombia (CO) | 15.3% | 15.3% | 24.7% | 22.4% |
| Mexico (MX) | 19.5% | 19.5% | 20.7% | 19.5% |
| Bangladesh (BD) | 28.0% | 36.6% | 35.4% | 39.0% |
| Japan (JP) | 55.7% | 50.6% | 48.1% | 50.6% |
| South Korea (KR) | 14.3% | 14.3% | 16.9% | 14.3% |
| Philippines (PH) | 23.3% | 34.2% | 34.2% | 37.0% |
| United Kingdom (GB) | 17.9% | 19.4% | 19.4% | 20.9% |
| France (FR) | 23.1% | 21.5% | 30.8% | 29.2% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 334 daily snapshots since 2025-04-09 |

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
