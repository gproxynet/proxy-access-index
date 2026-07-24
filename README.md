# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-07-24 21:43 UTC · **History:** 332 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| YouTube | 38.5% |
| Google | 38.1% |
| LinkedIn | 37.3% |
| X (Twitter) | 36.9% |
| Qzone | 35.5% |
| Instagram | 35.1% |
| TikTok | 35.1% |
| Mail.ru | 29.8% |
| VK | 28.5% |
| Telegram | 27.6% |
| OK.ru | 26.9% |
| Reddit | 18.1% |
| Yandex | 14.5% |
| Avito | 9.4% |
| Facebook | 3.4% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 3.4% of live proxies get through
- **Avito** — 9.4% of live proxies get through
- **Yandex** — 14.5% of live proxies get through
- **Reddit** — 18.1% of live proxies get through
- **OK.ru** — 26.9% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 47.7% | 46.5% | 44.0% | 42.9% | 45.2% | 46.5% |
| hosting | 20.9% | 22.5% | 17.5% | 22.3% | 21.5% | 21.3% |
| unknown | 35.9% | 43.3% | 37.9% | 28.2% | 40.6% | 28.3% |
| mobile | 38.5% | 38.5% | 43.3% | 42.3% | 46.2% | 42.3% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 28.2% | 36.7% | 19.8% | 35.5% |
| Indonesia (ID) | 47.4% | 58.2% | 60.1% | 61.5% |
| Albania (AL) | 89.3% | 82.4% | 76.1% | 88.2% |
| Russia (RU) | 49.4% | 3.9% | 29.9% | 11.7% |
| Brazil (BR) | 51.0% | 26.8% | 32.5% | 28.9% |
| Germany (DE) | 29.5% | 33.9% | 33.3% | 35.5% |
| India (IN) | 28.5% | 22.9% | 24.6% | 25.1% |
| China (CN) | 4.5% | 0.6% | 0.6% | 18.5% |
| Türkiye (TR) | 86.2% | 11.8% | 11.8% | 11.2% |
| Singapore (SG) | 31.9% | 27.7% | 34.8% | 33.3% |
| Colombia (CO) | 46.6% | 44.4% | 46.6% | 47.4% |
| Mexico (MX) | 41.1% | 41.9% | 45.0% | 41.1% |
| The Netherlands (NL) | 15.6% | 18.0% | 21.9% | 18.8% |
| Japan (JP) | 27.2% | 22.4% | 24.0% | 21.6% |
| France (FR) | 17.5% | 26.7% | 30.8% | 30.0% |
| South Korea (KR) | 10.3% | 12.1% | 19.8% | 12.1% |
| Vietnam (VN) | 39.8% | 36.9% | 36.9% | 33.0% |
| Hong Kong (HK) | 24.0% | 24.0% | 30.0% | 29.0% |
| Bangladesh (BD) | 56.1% | 62.2% | 64.3% | 63.3% |
| Philippines (PH) | 55.4% | 55.4% | 51.1% | 53.3% |

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
