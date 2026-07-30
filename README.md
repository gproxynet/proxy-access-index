# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-07-30 06:40 UTC · **History:** 338 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 32.9% |
| YouTube | 25.1% |
| LinkedIn | 25.0% |
| TikTok | 22.6% |
| Instagram | 22.1% |
| Qzone | 22.1% |
| X (Twitter) | 21.9% |
| Mail.ru | 21.8% |
| VK | 19.6% |
| OK.ru | 18.7% |
| Telegram | 17.9% |
| Yandex | 11.9% |
| Reddit | 11.6% |
| Avito | 7.3% |
| Facebook | 0.9% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.9% of live proxies get through
- **Avito** — 7.3% of live proxies get through
- **Reddit** — 11.6% of live proxies get through
- **Yandex** — 11.9% of live proxies get through
- **Telegram** — 17.9% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 37.5% | 25.0% | 22.8% | 24.0% | 24.9% | 23.9% |
| hosting | 25.9% | 21.6% | 17.6% | 20.7% | 21.3% | 19.2% |
| unknown | 35.5% | 38.4% | 34.2% | 19.8% | 38.4% | 19.8% |
| mobile | 29.8% | 32.1% | 28.6% | 33.3% | 35.7% | 29.8% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 36.7% | 28.2% | 19.3% | 30.3% |
| Indonesia (ID) | 27.6% | 29.0% | 30.0% | 29.2% |
| Russia (RU) | 52.0% | 4.5% | 20.3% | 9.9% |
| Germany (DE) | 29.2% | 26.1% | 30.4% | 28.6% |
| China (CN) | 4.5% | 0.0% | 0.0% | 18.6% |
| Brazil (BR) | 45.1% | 13.4% | 14.8% | 16.9% |
| India (IN) | 21.7% | 8.7% | 12.3% | 15.2% |
| Türkiye (TR) | 84.8% | 5.1% | 5.8% | 6.5% |
| Albania (AL) | 86.3% | 66.9% | 62.9% | 72.6% |
| Japan (JP) | 35.8% | 30.1% | 35.8% | 34.1% |
| Singapore (SG) | 37.7% | 31.6% | 33.3% | 31.6% |
| South Korea (KR) | 11.0% | 11.0% | 15.6% | 12.8% |
| France (FR) | 24.2% | 25.3% | 23.2% | 28.4% |
| Mexico (MX) | 23.7% | 16.1% | 21.5% | 21.5% |
| Hong Kong (HK) | 26.4% | 23.1% | 23.1% | 26.4% |
| Colombia (CO) | 30.1% | 26.5% | 27.7% | 26.5% |
| Vietnam (VN) | 35.5% | 36.8% | 25.0% | 31.6% |
| The Netherlands (NL) | 40.5% | 35.1% | 37.8% | 35.1% |
| Philippines (PH) | 33.3% | 31.8% | 31.8% | 27.3% |
| Canada (CA) | 15.4% | 10.8% | 12.3% | 15.4% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 338 daily snapshots since 2025-04-09 |

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
