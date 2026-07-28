# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-07-28 06:40 UTC · **History:** 336 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 32.4% |
| YouTube | 25.5% |
| LinkedIn | 23.9% |
| TikTok | 23.0% |
| Qzone | 22.7% |
| X (Twitter) | 22.4% |
| Instagram | 22.3% |
| Mail.ru | 21.3% |
| VK | 18.7% |
| OK.ru | 17.9% |
| Telegram | 15.4% |
| Yandex | 10.9% |
| Reddit | 10.5% |
| Avito | 7.1% |
| Facebook | 0.4% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.4% of live proxies get through
- **Avito** — 7.1% of live proxies get through
- **Reddit** — 10.5% of live proxies get through
- **Yandex** — 10.9% of live proxies get through
- **Telegram** — 15.4% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 35.4% | 26.0% | 24.2% | 25.4% | 24.7% | 24.9% |
| hosting | 26.9% | 21.2% | 16.0% | 19.2% | 19.2% | 19.7% |
| unknown | 35.8% | 38.7% | 33.6% | 22.5% | 35.1% | 17.6% |
| mobile | 29.6% | 21.4% | 23.5% | 25.5% | 26.5% | 23.5% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 36.5% | 27.6% | 16.8% | 27.9% |
| Indonesia (ID) | 23.6% | 28.9% | 29.3% | 27.7% |
| Russia (RU) | 54.3% | 3.9% | 31.5% | 8.6% |
| China (CN) | 4.9% | 0.6% | 0.6% | 18.3% |
| Germany (DE) | 38.1% | 29.0% | 30.3% | 30.3% |
| Brazil (BR) | 48.6% | 19.0% | 21.8% | 19.0% |
| Türkiye (TR) | 78.6% | 10.0% | 9.3% | 7.9% |
| India (IN) | 20.4% | 12.4% | 13.9% | 15.3% |
| Japan (JP) | 37.5% | 25.0% | 31.7% | 29.2% |
| The Netherlands (NL) | 28.2% | 23.6% | 23.6% | 24.5% |
| South Korea (KR) | 15.2% | 12.4% | 15.2% | 14.3% |
| Singapore (SG) | 44.0% | 31.0% | 34.0% | 37.0% |
| Philippines (PH) | 22.1% | 22.1% | 21.1% | 26.3% |
| Colombia (CO) | 28.7% | 20.2% | 28.7% | 24.5% |
| France (FR) | 27.9% | 25.6% | 23.3% | 20.9% |
| Mexico (MX) | 15.3% | 22.4% | 16.5% | 16.5% |
| Bangladesh (BD) | 44.0% | 45.2% | 40.5% | 41.7% |
| Vietnam (VN) | 37.0% | 33.3% | 29.6% | 34.6% |
| Albania (AL) | 65.0% | 45.0% | 41.2% | 50.0% |
| Hong Kong (HK) | 27.8% | 26.4% | 23.6% | 27.8% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 336 daily snapshots since 2025-04-09 |

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
