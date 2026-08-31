# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-31 06:40 UTC · **History:** 370 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| LinkedIn | 23.5% |
| X (Twitter) | 23.5% |
| TikTok | 23.4% |
| Qzone | 23.1% |
| YouTube | 22.8% |
| Instagram | 21.3% |
| VK | 20.1% |
| Google | 18.1% |
| OK.ru | 18.0% |
| Telegram | 15.7% |
| Reddit | 15.1% |
| Yandex | 9.1% |
| Mail.ru | 8.8% |
| Avito | 7.6% |
| Facebook | 0.7% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.7% of live proxies get through
- **Avito** — 7.6% of live proxies get through
- **Mail.ru** — 8.8% of live proxies get through
- **Yandex** — 9.1% of live proxies get through
- **Reddit** — 15.1% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 19.2% | 23.4% | 23.7% | 23.6% | 24.7% | 24.1% |
| hosting | 17.0% | 22.2% | 18.9% | 23.0% | 22.1% | 22.9% |
| mobile | 11.5% | 19.2% | 15.4% | 26.9% | 38.5% | 23.1% |
| unknown | 80.0% | 60.0% | 60.0% | 80.0% | 40.0% | 80.0% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 19.8% | 19.7% | 20.4% | 21.1% |
| Indonesia (ID) | 11.4% | 35.5% | 33.5% | 34.7% |
| Germany (DE) | 37.3% | 38.3% | 39.4% | 41.5% |
| Türkiye (TR) | 69.0% | 9.7% | 8.4% | 9.0% |
| Russia (RU) | 27.7% | 3.9% | 20.6% | 9.7% |
| Brazil (BR) | 35.3% | 17.3% | 16.5% | 16.5% |
| India (IN) | 15.2% | 13.6% | 18.2% | 20.5% |
| China (CN) | 0.8% | 0.8% | 0.8% | 16.7% |
| France (FR) | 9.6% | 26.4% | 28.0% | 31.2% |
| Japan (JP) | 8.4% | 5.6% | 15.0% | 12.1% |
| Hong Kong (HK) | 13.0% | 18.0% | 21.0% | 17.0% |
| Colombia (CO) | 17.0% | 20.0% | 17.0% | 18.0% |
| Singapore (SG) | 18.9% | 31.6% | 31.6% | 33.7% |
| Mexico (MX) | 16.1% | 20.4% | 22.6% | 23.7% |
| Canada (CA) | 9.8% | 7.6% | 18.5% | 14.1% |
| Philippines (PH) | 13.3% | 28.9% | 28.9% | 27.8% |
| The Netherlands (NL) | 23.6% | 36.0% | 34.8% | 36.0% |
| United Kingdom (GB) | 19.4% | 18.1% | 18.1% | 15.3% |
| Vietnam (VN) | 15.3% | 40.3% | 34.7% | 44.4% |
| Thailand (TH) | 10.0% | 32.9% | 47.1% | 37.1% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 370 daily snapshots since 2025-04-09 |

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
