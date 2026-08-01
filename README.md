# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-01 06:40 UTC · **History:** 340 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 33.4% |
| YouTube | 22.5% |
| LinkedIn | 22.5% |
| Qzone | 21.9% |
| X (Twitter) | 20.4% |
| Instagram | 20.1% |
| TikTok | 20.0% |
| Mail.ru | 19.2% |
| VK | 17.3% |
| OK.ru | 16.5% |
| Telegram | 15.5% |
| Reddit | 11.6% |
| Yandex | 9.9% |
| Avito | 6.3% |
| Facebook | 0.3% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.3% of live proxies get through
- **Avito** — 6.3% of live proxies get through
- **Yandex** — 9.9% of live proxies get through
- **Reddit** — 11.6% of live proxies get through
- **Telegram** — 15.5% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 34.5% | 21.5% | 19.8% | 20.1% | 21.7% | 20.2% |
| hosting | 31.9% | 22.7% | 18.9% | 18.7% | 22.3% | 19.1% |
| unknown | 33.8% | 30.9% | 29.9% | 26.0% | 30.9% | 29.4% |
| mobile | 23.9% | 23.9% | 16.4% | 19.4% | 23.9% | 17.9% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 27.9% | 16.0% | 13.5% | 15.7% |
| Indonesia (ID) | 29.2% | 33.3% | 30.8% | 33.1% |
| Russia (RU) | 52.9% | 2.3% | 19.8% | 6.4% |
| China (CN) | 2.0% | 0.7% | 0.7% | 22.3% |
| Türkiye (TR) | 82.4% | 3.1% | 3.8% | 4.6% |
| Germany (DE) | 37.2% | 33.1% | 30.6% | 33.9% |
| Brazil (BR) | 49.6% | 9.7% | 12.4% | 12.4% |
| India (IN) | 32.3% | 21.5% | 18.3% | 21.5% |
| Vietnam (VN) | 32.9% | 23.7% | 13.2% | 22.4% |
| Colombia (CO) | 27.0% | 20.3% | 21.6% | 23.0% |
| Singapore (SG) | 51.4% | 41.9% | 40.5% | 47.3% |
| The Netherlands (NL) | 35.2% | 32.4% | 29.6% | 35.2% |
| Mexico (MX) | 26.9% | 20.9% | 29.9% | 32.8% |
| South Korea (KR) | 21.9% | 18.8% | 14.1% | 12.5% |
| Japan (JP) | 45.2% | 33.9% | 33.9% | 32.3% |
| Philippines (PH) | 21.3% | 13.1% | 23.0% | 21.3% |
| France (FR) | 35.6% | 25.4% | 22.0% | 28.8% |
| Turkey (TR) | 74.1% | 3.7% | 11.1% | 3.7% |
| United Kingdom (GB) | 25.0% | 15.4% | 15.4% | 17.3% |
| Hong Kong (HK) | 44.2% | 34.6% | 30.8% | 44.2% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 340 daily snapshots since 2025-04-09 |

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
