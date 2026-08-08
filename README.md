# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-08 06:40 UTC · **History:** 347 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 31.3% |
| YouTube | 24.8% |
| LinkedIn | 24.5% |
| TikTok | 24.1% |
| Qzone | 24.0% |
| X (Twitter) | 23.7% |
| Instagram | 22.6% |
| Mail.ru | 19.4% |
| VK | 19.0% |
| OK.ru | 18.7% |
| Telegram | 17.8% |
| Reddit | 12.7% |
| Yandex | 9.9% |
| Avito | 6.7% |
| Facebook | 0.7% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.7% of live proxies get through
- **Avito** — 6.7% of live proxies get through
- **Yandex** — 9.9% of live proxies get through
- **Reddit** — 12.7% of live proxies get through
- **Telegram** — 17.8% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 35.4% | 26.4% | 25.0% | 26.0% | 25.7% | 25.3% |
| hosting | 25.6% | 22.4% | 19.3% | 21.4% | 22.2% | 21.3% |
| mobile | 30.0% | 36.7% | 26.7% | 20.0% | 56.7% | 30.0% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 30.2% | 17.3% | 18.6% | 18.6% |
| Indonesia (ID) | 31.9% | 39.5% | 39.0% | 39.0% |
| Türkiye (TR) | 78.5% | 8.8% | 8.8% | 9.9% |
| Russia (RU) | 42.4% | 3.5% | 31.4% | 11.6% |
| Germany (DE) | 33.8% | 33.1% | 31.8% | 31.8% |
| China (CN) | 5.1% | 0.7% | 0.7% | 17.4% |
| Brazil (BR) | 42.3% | 17.5% | 17.5% | 21.2% |
| India (IN) | 25.6% | 19.5% | 17.3% | 21.1% |
| France (FR) | 29.9% | 30.8% | 27.1% | 30.8% |
| The Netherlands (NL) | 36.8% | 41.5% | 38.7% | 40.6% |
| Singapore (SG) | 50.0% | 40.2% | 39.2% | 39.2% |
| South Korea (KR) | 6.7% | 5.6% | 10.1% | 10.1% |
| Vietnam (VN) | 37.9% | 31.0% | 29.9% | 34.5% |
| Japan (JP) | 29.1% | 22.8% | 22.8% | 24.1% |
| Hong Kong (HK) | 19.7% | 18.4% | 15.8% | 22.4% |
| Colombia (CO) | 28.8% | 34.8% | 28.8% | 31.8% |
| Mexico (MX) | 24.6% | 29.2% | 29.2% | 35.4% |
| Canada (CA) | 15.4% | 13.8% | 18.5% | 10.8% |
| Bangladesh (BD) | 42.4% | 40.7% | 37.3% | 39.0% |
| Philippines (PH) | 41.4% | 44.8% | 44.8% | 39.7% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 347 daily snapshots since 2025-04-09 |

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
