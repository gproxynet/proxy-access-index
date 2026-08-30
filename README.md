# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-30 06:40 UTC · **History:** 369 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 28.9% |
| YouTube | 20.9% |
| LinkedIn | 20.8% |
| Qzone | 19.9% |
| TikTok | 19.6% |
| X (Twitter) | 19.6% |
| Instagram | 18.7% |
| VK | 16.8% |
| OK.ru | 15.9% |
| Telegram | 13.3% |
| Reddit | 11.3% |
| Mail.ru | 8.9% |
| Yandex | 7.6% |
| Avito | 6.0% |
| Facebook | 0.7% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.7% of live proxies get through
- **Avito** — 6.0% of live proxies get through
- **Yandex** — 7.6% of live proxies get through
- **Mail.ru** — 8.9% of live proxies get through
- **Reddit** — 11.3% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 29.8% | 15.5% | 14.1% | 14.9% | 15.7% | 14.6% |
| hosting | 28.0% | 27.7% | 24.6% | 25.3% | 26.9% | 25.9% |
| mobile | 22.2% | 7.4% | 0.0% | 14.8% | 18.5% | 11.1% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 26.5% | 25.7% | 27.4% | 28.1% |
| Indonesia (ID) | 17.6% | 14.5% | 16.8% | 16.0% |
| Türkiye (TR) | 83.2% | 2.9% | 2.2% | 3.6% |
| Russia (RU) | 31.9% | 2.2% | 17.8% | 7.4% |
| Germany (DE) | 43.5% | 33.6% | 35.1% | 35.1% |
| China (CN) | 2.4% | 0.8% | 0.8% | 14.2% |
| India (IN) | 28.9% | 17.5% | 12.4% | 17.5% |
| Brazil (BR) | 46.9% | 5.2% | 6.2% | 6.2% |
| The Netherlands (NL) | 23.2% | 25.6% | 26.8% | 28.0% |
| France (FR) | 33.3% | 27.2% | 29.6% | 29.6% |
| Singapore (SG) | 44.0% | 34.7% | 30.7% | 34.7% |
| Colombia (CO) | 21.9% | 16.4% | 17.8% | 16.4% |
| Vietnam (VN) | 34.9% | 38.1% | 27.0% | 34.9% |
| Mexico (MX) | 15.8% | 8.8% | 14.0% | 15.8% |
| Philippines (PH) | 23.6% | 16.4% | 14.5% | 23.6% |
| Hong Kong (HK) | 26.1% | 15.2% | 13.0% | 26.1% |
| United Kingdom (GB) | 19.0% | 7.1% | 7.1% | 7.1% |
| Japan (JP) | 34.3% | 17.1% | 11.4% | 14.3% |
| Dominican Republic (DO) | 11.4% | 8.6% | 11.4% | 11.4% |
| Thailand (TH) | 62.9% | 60.0% | 57.1% | 54.3% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 369 daily snapshots since 2025-04-09 |

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
