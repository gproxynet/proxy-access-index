# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-27 06:40 UTC · **History:** 366 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 28.8% |
| TikTok | 22.3% |
| YouTube | 22.2% |
| LinkedIn | 21.5% |
| X (Twitter) | 21.5% |
| Qzone | 21.4% |
| Instagram | 19.8% |
| VK | 18.8% |
| OK.ru | 17.4% |
| Telegram | 14.7% |
| Reddit | 11.9% |
| Yandex | 8.8% |
| Mail.ru | 8.7% |
| Avito | 6.4% |
| Facebook | 0.6% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.6% of live proxies get through
- **Avito** — 6.4% of live proxies get through
- **Mail.ru** — 8.7% of live proxies get through
- **Yandex** — 8.8% of live proxies get through
- **Reddit** — 11.9% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 34.9% | 22.5% | 21.4% | 22.4% | 22.0% | 22.1% |
| hosting | 21.4% | 21.6% | 17.7% | 21.9% | 20.7% | 20.6% |
| mobile | 34.5% | 31.0% | 20.7% | 37.9% | 34.5% | 27.6% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 23.8% | 15.0% | 17.9% | 16.1% |
| Indonesia (ID) | 24.9% | 26.8% | 26.2% | 22.8% |
| Türkiye (TR) | 74.7% | 7.4% | 7.4% | 6.2% |
| Germany (DE) | 36.5% | 32.4% | 34.5% | 35.8% |
| China (CN) | 2.1% | 0.0% | 0.0% | 15.2% |
| Russia (RU) | 36.4% | 2.1% | 20.3% | 8.4% |
| India (IN) | 23.2% | 18.3% | 15.5% | 21.1% |
| Brazil (BR) | 48.1% | 12.0% | 12.0% | 13.0% |
| The Netherlands (NL) | 38.5% | 39.6% | 38.5% | 39.6% |
| Singapore (SG) | 36.7% | 34.4% | 31.1% | 33.3% |
| France (FR) | 28.7% | 25.3% | 28.7% | 25.3% |
| Japan (JP) | 17.8% | 12.3% | 21.9% | 16.4% |
| Hong Kong (HK) | 13.0% | 18.8% | 21.7% | 24.6% |
| United Kingdom (GB) | 16.9% | 18.5% | 23.1% | 24.6% |
| Vietnam (VN) | 34.4% | 40.6% | 37.5% | 40.6% |
| Colombia (CO) | 25.0% | 14.1% | 17.2% | 18.8% |
| Philippines (PH) | 30.6% | 22.6% | 27.4% | 21.0% |
| Thailand (TH) | 52.5% | 40.7% | 50.8% | 49.2% |
| South Korea (KR) | 12.1% | 10.3% | 15.5% | 12.1% |
| Mexico (MX) | 36.2% | 29.3% | 34.5% | 36.2% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 366 daily snapshots since 2025-04-09 |

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
