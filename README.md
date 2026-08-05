# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-05 06:40 UTC · **History:** 344 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 34.9% |
| YouTube | 26.6% |
| LinkedIn | 26.1% |
| Qzone | 25.5% |
| X (Twitter) | 24.8% |
| Instagram | 24.1% |
| TikTok | 24.1% |
| Mail.ru | 20.9% |
| VK | 20.6% |
| OK.ru | 19.6% |
| Telegram | 17.3% |
| Reddit | 15.4% |
| Yandex | 11.1% |
| Avito | 7.3% |
| Facebook | 0.9% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.9% of live proxies get through
- **Avito** — 7.3% of live proxies get through
- **Yandex** — 11.1% of live proxies get through
- **Reddit** — 15.4% of live proxies get through
- **Telegram** — 17.3% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 37.7% | 26.2% | 23.7% | 24.2% | 25.2% | 24.2% |
| hosting | 30.5% | 26.9% | 24.8% | 23.8% | 27.2% | 25.5% |
| mobile | 40.6% | 37.5% | 28.1% | 34.4% | 40.6% | 37.5% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 36.9% | 28.2% | 25.6% | 31.6% |
| Indonesia (ID) | 36.4% | 35.2% | 34.3% | 33.8% |
| Russia (RU) | 50.8% | 4.1% | 26.4% | 8.1% |
| Türkiye (TR) | 80.2% | 13.0% | 12.5% | 11.5% |
| China (CN) | 3.6% | 0.0% | 0.0% | 17.2% |
| Germany (DE) | 37.1% | 29.5% | 28.8% | 25.0% |
| India (IN) | 29.8% | 21.9% | 20.2% | 22.8% |
| Brazil (BR) | 49.6% | 18.6% | 19.5% | 21.2% |
| France (FR) | 36.4% | 32.7% | 38.3% | 42.1% |
| South Korea (KR) | 8.5% | 8.5% | 6.6% | 6.6% |
| Colombia (CO) | 22.1% | 25.0% | 16.3% | 25.0% |
| The Netherlands (NL) | 38.9% | 44.2% | 36.8% | 40.0% |
| Singapore (SG) | 41.5% | 39.0% | 37.8% | 39.0% |
| Mexico (MX) | 23.8% | 28.8% | 33.8% | 33.8% |
| Vietnam (VN) | 31.6% | 26.6% | 16.5% | 25.3% |
| Hong Kong (HK) | 23.4% | 20.8% | 18.2% | 26.0% |
| Japan (JP) | 39.5% | 27.6% | 27.6% | 26.3% |
| Philippines (PH) | 33.3% | 34.8% | 30.3% | 40.9% |
| Bangladesh (BD) | 38.2% | 34.5% | 38.2% | 38.2% |
| South Africa (ZA) | 24.0% | 20.0% | 22.0% | 28.0% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 344 daily snapshots since 2025-04-09 |

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
