# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-12 06:40 UTC · **History:** 351 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 38.4% |
| YouTube | 29.6% |
| LinkedIn | 28.4% |
| X (Twitter) | 28.2% |
| Qzone | 27.5% |
| TikTok | 27.3% |
| Instagram | 27.1% |
| Mail.ru | 23.6% |
| VK | 23.3% |
| OK.ru | 22.4% |
| Telegram | 18.6% |
| Reddit | 18.3% |
| Yandex | 10.0% |
| Avito | 9.0% |
| Facebook | 0.5% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.5% of live proxies get through
- **Avito** — 9.0% of live proxies get through
- **Yandex** — 10.0% of live proxies get through
- **Reddit** — 18.3% of live proxies get through
- **Telegram** — 18.6% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 40.6% | 30.5% | 28.8% | 29.0% | 29.5% | 29.4% |
| hosting | 33.7% | 27.7% | 23.4% | 23.0% | 25.7% | 25.4% |
| mobile | 29.2% | 27.1% | 22.9% | 33.3% | 33.3% | 29.2% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| Indonesia (ID) | 46.2% | 45.4% | 44.6% | 47.0% |
| United States (US) | 35.0% | 17.3% | 16.8% | 19.0% |
| Türkiye (TR) | 73.8% | 12.4% | 14.8% | 11.4% |
| Russia (RU) | 40.8% | 1.7% | 22.4% | 5.7% |
| China (CN) | 3.9% | 0.0% | 0.7% | 16.4% |
| Germany (DE) | 35.4% | 30.8% | 25.4% | 26.2% |
| Brazil (BR) | 47.7% | 16.2% | 12.3% | 11.5% |
| Colombia (CO) | 33.3% | 27.5% | 30.0% | 34.2% |
| France (FR) | 42.9% | 32.1% | 34.8% | 33.9% |
| Philippines (PH) | 38.5% | 34.9% | 40.4% | 30.3% |
| Mexico (MX) | 31.4% | 39.0% | 33.3% | 30.5% |
| India (IN) | 40.4% | 27.3% | 25.3% | 27.3% |
| Singapore (SG) | 54.3% | 44.7% | 43.6% | 43.6% |
| The Netherlands (NL) | 33.3% | 34.4% | 29.0% | 38.7% |
| South Korea (KR) | 14.5% | 15.9% | 14.5% | 11.6% |
| Bangladesh (BD) | 33.3% | 40.9% | 37.9% | 39.4% |
| Vietnam (VN) | 42.4% | 39.4% | 30.3% | 37.9% |
| Venezuela (VE) | 27.3% | 19.7% | 25.8% | 25.8% |
| Japan (JP) | 50.9% | 38.6% | 35.1% | 38.6% |
| Hong Kong (HK) | 23.2% | 16.1% | 19.6% | 25.0% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 351 daily snapshots since 2025-04-09 |

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
