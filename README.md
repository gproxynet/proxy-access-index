# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-07-24 21:39 UTC · **History:** 332 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| YouTube | 38.3% |
| Google | 38.1% |
| LinkedIn | 36.9% |
| X (Twitter) | 36.4% |
| Qzone | 35.1% |
| TikTok | 34.9% |
| Instagram | 34.7% |
| Mail.ru | 29.8% |
| VK | 28.4% |
| Telegram | 27.5% |
| OK.ru | 27.0% |
| Reddit | 17.8% |
| Yandex | 14.6% |
| Avito | 9.5% |
| Facebook | 3.2% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 3.2% of live proxies get through
- **Avito** — 9.5% of live proxies get through
- **Yandex** — 14.6% of live proxies get through
- **Reddit** — 17.8% of live proxies get through
- **OK.ru** — 27.0% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 47.8% | 46.1% | 43.4% | 42.6% | 44.5% | 45.8% |
| hosting | 20.8% | 22.3% | 17.3% | 22.0% | 21.3% | 21.0% |
| unknown | 36.1% | 43.9% | 38.1% | 28.1% | 40.8% | 27.9% |
| mobile | 38.8% | 38.8% | 43.7% | 42.7% | 47.6% | 42.7% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 28.4% | 34.6% | 18.9% | 33.2% |
| Indonesia (ID) | 47.8% | 57.9% | 59.6% | 61.0% |
| Albania (AL) | 89.3% | 82.1% | 76.0% | 88.2% |
| Russia (RU) | 49.8% | 5.5% | 32.1% | 12.2% |
| Brazil (BR) | 50.3% | 27.4% | 32.5% | 28.9% |
| Germany (DE) | 29.2% | 33.0% | 33.0% | 35.1% |
| India (IN) | 28.3% | 22.8% | 23.9% | 24.4% |
| Türkiye (TR) | 86.8% | 11.9% | 11.9% | 11.3% |
| China (CN) | 5.3% | 0.7% | 0.7% | 18.7% |
| Singapore (SG) | 30.9% | 28.1% | 35.3% | 33.8% |
| Colombia (CO) | 45.5% | 43.2% | 45.5% | 46.2% |
| Mexico (MX) | 41.5% | 41.5% | 46.2% | 41.5% |
| The Netherlands (NL) | 15.7% | 18.1% | 22.0% | 18.9% |
| Japan (JP) | 27.2% | 21.6% | 22.4% | 20.8% |
| France (FR) | 17.6% | 26.1% | 31.9% | 30.3% |
| South Korea (KR) | 10.3% | 12.8% | 18.8% | 12.8% |
| Vietnam (VN) | 39.2% | 35.3% | 35.3% | 34.3% |
| Bangladesh (BD) | 55.6% | 61.6% | 63.6% | 62.6% |
| Hong Kong (HK) | 23.5% | 23.5% | 29.6% | 30.6% |
| United Kingdom (GB) | 12.2% | 20.0% | 20.0% | 21.1% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 332 daily snapshots since 2025-04-09 |

```bash
curl -s https://raw.githubusercontent.com/gproxynet/proxy-access-index/main/latest.json
```

## Method and scope

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
