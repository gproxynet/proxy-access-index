# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-16 06:40 UTC · **History:** 355 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 27.7% |
| YouTube | 22.0% |
| LinkedIn | 21.8% |
| Qzone | 21.4% |
| TikTok | 20.6% |
| X (Twitter) | 20.5% |
| Instagram | 19.9% |
| VK | 18.1% |
| OK.ru | 17.2% |
| Telegram | 14.3% |
| Reddit | 11.8% |
| Yandex | 8.8% |
| Mail.ru | 8.1% |
| Avito | 6.1% |
| Facebook | 0.6% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.6% of live proxies get through
- **Avito** — 6.1% of live proxies get through
- **Mail.ru** — 8.1% of live proxies get through
- **Yandex** — 8.8% of live proxies get through
- **Reddit** — 11.8% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 29.0% | 21.2% | 19.8% | 20.8% | 20.7% | 20.0% |
| hosting | 23.8% | 22.3% | 19.1% | 18.5% | 21.6% | 19.5% |
| mobile | 43.8% | 45.3% | 34.4% | 46.9% | 60.9% | 50.0% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| Indonesia (ID) | 24.9% | 31.5% | 31.7% | 28.2% |
| United States (US) | 22.4% | 14.7% | 14.2% | 15.6% |
| Türkiye (TR) | 71.3% | 6.4% | 8.0% | 9.0% |
| Russia (RU) | 34.8% | 0.6% | 22.6% | 6.7% |
| China (CN) | 4.6% | 2.0% | 1.3% | 16.6% |
| Germany (DE) | 30.4% | 27.7% | 26.8% | 27.7% |
| Brazil (BR) | 43.9% | 14.0% | 15.9% | 17.8% |
| Colombia (CO) | 16.3% | 22.4% | 21.4% | 22.4% |
| India (IN) | 23.1% | 23.1% | 23.1% | 26.4% |
| Vietnam (VN) | 42.9% | 36.3% | 41.8% | 42.9% |
| Philippines (PH) | 19.0% | 22.6% | 19.0% | 23.8% |
| Mexico (MX) | 23.1% | 21.8% | 19.2% | 21.8% |
| France (FR) | 24.4% | 28.2% | 20.5% | 33.3% |
| Singapore (SG) | 31.2% | 24.7% | 18.2% | 22.1% |
| The Netherlands (NL) | 27.8% | 30.6% | 29.2% | 36.1% |
| South Korea (KR) | 7.2% | 7.2% | 8.7% | 8.7% |
| Hong Kong (HK) | 22.2% | 35.2% | 27.8% | 29.6% |
| Venezuela (VE) | 23.5% | 11.8% | 15.7% | 17.6% |
| Bangladesh (BD) | 31.2% | 39.6% | 35.4% | 35.4% |
| Japan (JP) | 42.2% | 26.7% | 35.6% | 35.6% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 355 daily snapshots since 2025-04-09 |

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
