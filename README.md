# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-06 06:40 UTC · **History:** 345 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 28.7% |
| YouTube | 22.1% |
| Qzone | 20.9% |
| X (Twitter) | 20.4% |
| TikTok | 20.1% |
| LinkedIn | 20.0% |
| Instagram | 18.4% |
| VK | 17.0% |
| Mail.ru | 15.7% |
| OK.ru | 15.6% |
| Telegram | 13.0% |
| Reddit | 9.9% |
| Yandex | 8.3% |
| Avito | 6.2% |
| Facebook | 0.4% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.4% of live proxies get through
- **Avito** — 6.2% of live proxies get through
- **Yandex** — 8.3% of live proxies get through
- **Reddit** — 9.9% of live proxies get through
- **Telegram** — 13.0% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 31.1% | 22.2% | 19.4% | 20.3% | 20.1% | 20.6% |
| hosting | 24.4% | 21.5% | 16.7% | 19.4% | 19.6% | 19.7% |
| mobile | 39.3% | 35.7% | 21.4% | 35.7% | 25.0% | 32.1% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 27.7% | 14.6% | 14.1% | 16.7% |
| Indonesia (ID) | 25.5% | 28.9% | 28.6% | 27.8% |
| Türkiye (TR) | 79.3% | 6.0% | 7.6% | 6.0% |
| Russia (RU) | 38.6% | 5.1% | 30.1% | 8.5% |
| Germany (DE) | 31.3% | 28.0% | 34.7% | 30.7% |
| China (CN) | 4.5% | 0.8% | 1.5% | 12.0% |
| Brazil (BR) | 45.8% | 16.0% | 13.0% | 13.0% |
| India (IN) | 23.2% | 14.3% | 13.4% | 20.5% |
| Singapore (SG) | 41.7% | 35.4% | 36.5% | 38.5% |
| South Korea (KR) | 8.5% | 8.5% | 6.4% | 7.4% |
| France (FR) | 39.8% | 37.5% | 33.0% | 38.6% |
| Colombia (CO) | 14.9% | 16.1% | 12.6% | 16.1% |
| The Netherlands (NL) | 31.7% | 35.4% | 34.1% | 29.3% |
| Vietnam (VN) | 32.0% | 18.7% | 14.7% | 17.3% |
| Hong Kong (HK) | 24.3% | 15.7% | 21.4% | 18.6% |
| Mexico (MX) | 23.1% | 18.5% | 18.5% | 23.1% |
| Bangladesh (BD) | 37.3% | 35.6% | 35.6% | 30.5% |
| Japan (JP) | 32.1% | 16.1% | 17.9% | 14.3% |
| Philippines (PH) | 31.4% | 31.4% | 29.4% | 29.4% |
| Canada (CA) | 19.1% | 12.8% | 10.6% | 14.9% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 345 daily snapshots since 2025-04-09 |

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
