# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-07 06:40 UTC · **History:** 346 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 33.0% |
| YouTube | 30.1% |
| TikTok | 29.4% |
| LinkedIn | 29.4% |
| X (Twitter) | 28.1% |
| Qzone | 27.9% |
| Instagram | 27.3% |
| VK | 23.3% |
| Mail.ru | 22.9% |
| OK.ru | 22.2% |
| Telegram | 19.8% |
| Reddit | 16.2% |
| Yandex | 10.6% |
| Avito | 8.7% |
| Facebook | 0.6% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.6% of live proxies get through
- **Avito** — 8.7% of live proxies get through
- **Yandex** — 10.6% of live proxies get through
- **Reddit** — 16.2% of live proxies get through
- **Telegram** — 19.8% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 35.9% | 32.9% | 30.3% | 31.9% | 32.1% | 31.1% |
| hosting | 27.5% | 24.7% | 21.7% | 24.7% | 24.4% | 22.4% |
| mobile | 48.6% | 43.2% | 32.4% | 40.5% | 37.8% | 40.5% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| Indonesia (ID) | 34.9% | 46.6% | 49.1% | 48.3% |
| United States (US) | 31.7% | 18.6% | 20.5% | 20.7% |
| Russia (RU) | 45.5% | 4.5% | 34.2% | 14.4% |
| Türkiye (TR) | 76.5% | 12.5% | 12.0% | 11.0% |
| China (CN) | 6.6% | 0.0% | 0.6% | 16.3% |
| Germany (DE) | 36.8% | 30.1% | 35.0% | 29.4% |
| Brazil (BR) | 50.3% | 28.7% | 25.9% | 25.2% |
| Colombia (CO) | 27.0% | 37.3% | 35.7% | 38.9% |
| India (IN) | 28.6% | 20.6% | 23.8% | 23.0% |
| Mexico (MX) | 19.0% | 28.4% | 27.6% | 25.9% |
| France (FR) | 41.1% | 37.5% | 43.8% | 39.3% |
| Singapore (SG) | 41.8% | 37.3% | 40.0% | 40.0% |
| The Netherlands (NL) | 44.7% | 44.7% | 44.7% | 44.7% |
| Philippines (PH) | 40.2% | 45.1% | 45.1% | 41.2% |
| Vietnam (VN) | 35.0% | 30.0% | 20.0% | 28.0% |
| South Korea (KR) | 12.2% | 10.0% | 12.2% | 12.2% |
| Hong Kong (HK) | 19.0% | 17.9% | 21.4% | 23.8% |
| Japan (JP) | 30.1% | 21.7% | 22.9% | 22.9% |
| South Africa (ZA) | 24.2% | 30.3% | 36.4% | 24.2% |
| Bangladesh (BD) | 41.7% | 46.7% | 55.0% | 48.3% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 346 daily snapshots since 2025-04-09 |

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
