# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-04 06:40 UTC · **History:** 343 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 33.6% |
| YouTube | 24.3% |
| TikTok | 22.9% |
| LinkedIn | 22.3% |
| Qzone | 22.2% |
| Instagram | 21.6% |
| X (Twitter) | 21.5% |
| Mail.ru | 19.5% |
| VK | 18.8% |
| OK.ru | 17.9% |
| Telegram | 15.1% |
| Reddit | 13.2% |
| Yandex | 9.7% |
| Avito | 7.2% |
| Facebook | 0.4% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.4% of live proxies get through
- **Avito** — 7.2% of live proxies get through
- **Yandex** — 9.7% of live proxies get through
- **Reddit** — 13.2% of live proxies get through
- **Telegram** — 15.1% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 34.0% | 23.7% | 21.6% | 22.5% | 21.9% | 20.8% |
| hosting | 32.8% | 25.5% | 21.7% | 23.4% | 23.2% | 22.8% |
| mobile | 34.4% | 25.0% | 25.0% | 28.1% | 21.9% | 28.1% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| Indonesia (ID) | 34.1% | 34.3% | 35.0% | 33.2% |
| United States (US) | 31.9% | 16.8% | 18.4% | 17.8% |
| Türkiye (TR) | 80.0% | 7.5% | 8.0% | 8.0% |
| Russia (RU) | 50.9% | 4.0% | 24.6% | 6.9% |
| China (CN) | 5.1% | 0.0% | 0.6% | 14.6% |
| Brazil (BR) | 45.5% | 12.4% | 10.7% | 9.9% |
| Germany (DE) | 31.9% | 28.4% | 27.6% | 26.7% |
| India (IN) | 28.3% | 17.2% | 17.2% | 19.2% |
| Singapore (SG) | 45.8% | 33.3% | 40.6% | 39.6% |
| France (FR) | 38.9% | 37.8% | 43.3% | 36.7% |
| Colombia (CO) | 27.6% | 21.8% | 25.3% | 21.8% |
| South Korea (KR) | 12.9% | 11.8% | 11.8% | 14.1% |
| Mexico (MX) | 21.8% | 20.5% | 20.5% | 20.5% |
| Philippines (PH) | 33.3% | 29.5% | 26.9% | 25.6% |
| The Netherlands (NL) | 30.8% | 26.9% | 32.1% | 29.5% |
| Vietnam (VN) | 23.9% | 22.5% | 9.9% | 21.1% |
| Japan (JP) | 53.1% | 37.5% | 35.9% | 39.1% |
| Hong Kong (HK) | 33.3% | 38.3% | 31.7% | 35.0% |
| Venezuela (VE) | 30.4% | 17.9% | 32.1% | 28.6% |
| Bangladesh (BD) | 25.0% | 30.4% | 30.4% | 30.4% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 343 daily snapshots since 2025-04-09 |

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
