# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-03 06:40 UTC · **History:** 342 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 38.9% |
| YouTube | 28.8% |
| LinkedIn | 27.9% |
| Qzone | 27.9% |
| TikTok | 26.8% |
| Instagram | 25.8% |
| X (Twitter) | 25.8% |
| VK | 21.9% |
| Mail.ru | 21.9% |
| OK.ru | 20.6% |
| Telegram | 19.5% |
| Reddit | 17.0% |
| Yandex | 13.4% |
| Avito | 9.5% |
| Facebook | 0.7% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.7% of live proxies get through
- **Avito** — 9.5% of live proxies get through
- **Yandex** — 13.4% of live proxies get through
- **Reddit** — 17.0% of live proxies get through
- **Telegram** — 19.5% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 40.8% | 29.5% | 27.3% | 28.1% | 28.8% | 26.6% |
| hosting | 34.6% | 26.8% | 22.4% | 23.7% | 25.4% | 23.8% |
| mobile | 43.6% | 38.5% | 25.6% | 35.9% | 43.6% | 28.2% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| Indonesia (ID) | 47.8% | 48.0% | 44.8% | 48.2% |
| United States (US) | 30.1% | 13.7% | 14.8% | 15.6% |
| Russia (RU) | 52.1% | 2.4% | 27.0% | 8.5% |
| Türkiye (TR) | 79.7% | 6.4% | 8.7% | 7.6% |
| China (CN) | 4.5% | 0.6% | 0.6% | 18.6% |
| Brazil (BR) | 48.1% | 14.8% | 13.3% | 14.1% |
| Germany (DE) | 36.6% | 31.7% | 32.5% | 27.6% |
| India (IN) | 36.1% | 20.4% | 21.3% | 25.0% |
| Colombia (CO) | 32.0% | 27.2% | 28.2% | 29.1% |
| The Netherlands (NL) | 40.4% | 37.4% | 39.4% | 45.5% |
| France (FR) | 42.2% | 41.1% | 37.8% | 36.7% |
| Singapore (SG) | 47.1% | 34.5% | 34.5% | 41.4% |
| Mexico (MX) | 28.0% | 29.3% | 29.3% | 29.3% |
| South Korea (KR) | 14.7% | 13.2% | 16.2% | 14.7% |
| Vietnam (VN) | 35.9% | 31.2% | 17.2% | 29.7% |
| Bangladesh (BD) | 55.7% | 55.7% | 54.1% | 52.5% |
| Philippines (PH) | 32.2% | 23.7% | 28.8% | 33.9% |
| Hong Kong (HK) | 32.8% | 34.5% | 32.8% | 31.0% |
| Venezuela (VE) | 19.6% | 17.9% | 19.6% | 23.2% |
| Japan (JP) | 48.9% | 31.9% | 29.8% | 31.9% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 342 daily snapshots since 2025-04-09 |

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
