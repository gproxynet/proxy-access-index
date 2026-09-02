# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-09-02 06:40 UTC · **History:** 372 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 27.7% |
| TikTok | 24.3% |
| LinkedIn | 24.3% |
| Qzone | 24.3% |
| X (Twitter) | 23.2% |
| YouTube | 23.0% |
| Instagram | 19.9% |
| VK | 19.6% |
| OK.ru | 18.0% |
| Telegram | 16.2% |
| Reddit | 14.7% |
| Yandex | 9.2% |
| Mail.ru | 8.8% |
| Avito | 7.3% |
| Facebook | 0.4% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.4% of live proxies get through
- **Avito** — 7.3% of live proxies get through
- **Mail.ru** — 8.8% of live proxies get through
- **Yandex** — 9.2% of live proxies get through
- **Reddit** — 14.7% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 37.3% | 27.7% | 26.4% | 29.1% | 29.2% | 27.1% |
| hosting | 17.9% | 18.4% | 13.3% | 19.3% | 19.0% | 19.2% |
| mobile | 19.4% | 16.1% | 16.1% | 19.4% | 32.3% | 16.1% |
| unknown | 20.0% | 20.0% | 40.0% | 20.0% | 60.0% | 40.0% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 21.8% | 12.4% | 16.1% | 15.9% |
| Indonesia (ID) | 39.1% | 38.2% | 43.6% | 40.9% |
| Germany (DE) | 37.9% | 34.5% | 34.0% | 35.9% |
| Russia (RU) | 35.0% | 1.8% | 22.7% | 5.5% |
| China (CN) | 3.2% | 0.6% | 0.6% | 26.3% |
| India (IN) | 21.1% | 13.2% | 17.8% | 17.8% |
| Türkiye (TR) | 82.3% | 8.5% | 7.8% | 8.5% |
| Brazil (BR) | 43.5% | 18.1% | 17.4% | 17.4% |
| France (FR) | 25.9% | 24.1% | 29.3% | 30.2% |
| Japan (JP) | 16.1% | 8.9% | 28.6% | 19.6% |
| Canada (CA) | 14.3% | 8.0% | 11.6% | 10.7% |
| Mexico (MX) | 24.8% | 21.1% | 30.3% | 22.0% |
| Singapore (SG) | 34.3% | 25.0% | 32.4% | 31.5% |
| The Netherlands (NL) | 33.0% | 38.3% | 39.4% | 39.4% |
| Hong Kong (HK) | 14.4% | 11.1% | 18.9% | 20.0% |
| Colombia (CO) | 24.1% | 20.7% | 23.0% | 21.8% |
| United Kingdom (GB) | 15.0% | 11.2% | 8.8% | 10.0% |
| Philippines (PH) | 41.6% | 36.4% | 39.0% | 36.4% |
| Vietnam (VN) | 41.4% | 40.0% | 30.0% | 34.3% |
| Australia (AU) | 0.0% | 0.0% | 14.3% | 4.3% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 372 daily snapshots since 2025-04-09 |

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
