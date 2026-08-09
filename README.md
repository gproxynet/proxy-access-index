# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-09 06:40 UTC · **History:** 348 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 27.0% |
| YouTube | 17.7% |
| LinkedIn | 16.8% |
| Qzone | 16.4% |
| TikTok | 15.9% |
| Instagram | 15.7% |
| X (Twitter) | 15.7% |
| Mail.ru | 14.0% |
| VK | 13.5% |
| OK.ru | 12.4% |
| Telegram | 11.3% |
| Reddit | 7.6% |
| Yandex | 7.4% |
| Avito | 5.0% |
| Facebook | 0.8% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.8% of live proxies get through
- **Avito** — 5.0% of live proxies get through
- **Yandex** — 7.4% of live proxies get through
- **Reddit** — 7.6% of live proxies get through
- **Telegram** — 11.3% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 26.6% | 15.0% | 13.7% | 13.3% | 14.5% | 13.3% |
| hosting | 27.7% | 22.5% | 19.3% | 20.6% | 20.8% | 19.9% |
| mobile | 28.6% | 25.0% | 17.9% | 17.9% | 25.0% | 21.4% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 23.2% | 9.8% | 11.2% | 11.5% |
| Indonesia (ID) | 17.4% | 20.7% | 18.7% | 19.7% |
| Türkiye (TR) | 77.0% | 5.2% | 2.9% | 2.9% |
| Russia (RU) | 34.8% | 4.3% | 23.8% | 7.9% |
| China (CN) | 4.7% | 0.0% | 0.0% | 11.7% |
| Germany (DE) | 31.0% | 25.7% | 29.2% | 26.5% |
| Brazil (BR) | 47.3% | 13.4% | 9.8% | 11.6% |
| Singapore (SG) | 48.2% | 41.2% | 38.8% | 41.2% |
| The Netherlands (NL) | 34.5% | 34.5% | 35.7% | 34.5% |
| France (FR) | 30.7% | 30.7% | 26.7% | 28.0% |
| Colombia (CO) | 13.5% | 10.8% | 9.5% | 9.5% |
| Vietnam (VN) | 20.3% | 24.3% | 21.6% | 27.0% |
| India (IN) | 21.9% | 12.3% | 8.2% | 21.9% |
| South Korea (KR) | 10.4% | 9.0% | 11.9% | 10.4% |
| Mexico (MX) | 7.9% | 9.5% | 9.5% | 9.5% |
| Philippines (PH) | 31.4% | 27.5% | 23.5% | 27.5% |
| Japan (JP) | 34.1% | 18.2% | 18.2% | 15.9% |
| Hong Kong (HK) | 28.6% | 23.8% | 23.8% | 21.4% |
| United Kingdom (GB) | 19.4% | 8.3% | 8.3% | 8.3% |
| Iran (IR) | 17.6% | 5.9% | 5.9% | 8.8% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 348 daily snapshots since 2025-04-09 |

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
