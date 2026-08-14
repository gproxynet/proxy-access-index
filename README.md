# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-14 06:40 UTC · **History:** 353 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 26.8% |
| TikTok | 24.9% |
| YouTube | 24.7% |
| LinkedIn | 24.1% |
| Qzone | 23.7% |
| X (Twitter) | 23.3% |
| Instagram | 21.7% |
| VK | 19.4% |
| OK.ru | 18.5% |
| Telegram | 15.4% |
| Reddit | 15.3% |
| Yandex | 8.5% |
| Mail.ru | 7.8% |
| Avito | 7.3% |
| Facebook | 0.8% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.8% of live proxies get through
- **Avito** — 7.3% of live proxies get through
- **Mail.ru** — 7.8% of live proxies get through
- **Yandex** — 8.5% of live proxies get through
- **Reddit** — 15.3% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 29.7% | 26.8% | 24.6% | 25.6% | 25.6% | 25.1% |
| hosting | 21.3% | 20.3% | 16.2% | 22.7% | 20.7% | 19.6% |
| mobile | 54.4% | 52.6% | 43.9% | 52.6% | 52.6% | 45.6% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| Indonesia (ID) | 27.0% | 37.4% | 38.1% | 36.7% |
| United States (US) | 26.1% | 14.5% | 17.5% | 15.5% |
| Türkiye (TR) | 68.2% | 11.1% | 12.6% | 8.1% |
| Russia (RU) | 38.5% | 2.4% | 24.3% | 7.1% |
| India (IN) | 25.3% | 20.8% | 23.4% | 24.7% |
| Germany (DE) | 25.5% | 22.0% | 27.0% | 24.1% |
| Brazil (BR) | 43.9% | 19.4% | 22.3% | 21.6% |
| China (CN) | 3.7% | 1.5% | 1.5% | 17.6% |
| France (FR) | 31.1% | 28.6% | 28.6% | 30.3% |
| Colombia (CO) | 17.3% | 19.1% | 20.9% | 22.7% |
| Mexico (MX) | 21.3% | 28.7% | 25.0% | 28.7% |
| Singapore (SG) | 35.2% | 33.3% | 41.9% | 38.1% |
| South Korea (KR) | 10.9% | 10.9% | 18.5% | 15.2% |
| Vietnam (VN) | 53.8% | 44.0% | 46.2% | 46.2% |
| The Netherlands (NL) | 41.1% | 37.8% | 36.7% | 37.8% |
| Philippines (PH) | 34.8% | 33.7% | 32.6% | 30.3% |
| Japan (JP) | 14.5% | 12.0% | 19.3% | 21.7% |
| Hong Kong (HK) | 17.1% | 14.6% | 18.3% | 26.8% |
| Bangladesh (BD) | 20.6% | 33.8% | 36.8% | 35.3% |
| Thailand (TH) | 33.3% | 31.7% | 31.7% | 28.6% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 353 daily snapshots since 2025-04-09 |

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
