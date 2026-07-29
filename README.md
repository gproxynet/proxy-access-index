# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-07-29 06:40 UTC · **History:** 337 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 38.9% |
| YouTube | 32.7% |
| LinkedIn | 31.9% |
| TikTok | 30.7% |
| X (Twitter) | 29.7% |
| Qzone | 29.3% |
| Instagram | 28.9% |
| Mail.ru | 27.6% |
| VK | 26.1% |
| OK.ru | 25.3% |
| Telegram | 24.5% |
| Yandex | 16.3% |
| Reddit | 10.7% |
| Avito | 8.6% |
| Facebook | 1.7% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 1.7% of live proxies get through
- **Avito** — 8.6% of live proxies get through
- **Reddit** — 10.7% of live proxies get through
- **Yandex** — 16.3% of live proxies get through
- **Telegram** — 24.5% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 43.3% | 33.1% | 31.3% | 32.7% | 32.9% | 32.3% |
| hosting | 30.7% | 28.2% | 21.5% | 26.8% | 25.5% | 25.3% |
| unknown | 44.0% | 46.4% | 42.8% | 33.0% | 47.2% | 31.0% |
| mobile | 35.7% | 28.6% | 20.2% | 33.3% | 32.1% | 27.4% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 43.8% | 35.5% | 26.7% | 37.3% |
| Indonesia (ID) | 35.1% | 34.3% | 34.9% | 34.7% |
| Albania (AL) | 87.1% | 80.7% | 80.5% | 82.3% |
| Russia (RU) | 54.0% | 4.7% | 28.4% | 8.8% |
| Germany (DE) | 35.2% | 27.7% | 34.0% | 32.1% |
| Brazil (BR) | 52.3% | 20.8% | 24.8% | 21.5% |
| India (IN) | 24.5% | 14.7% | 18.9% | 16.8% |
| China (CN) | 2.1% | 0.0% | 0.7% | 18.3% |
| Türkiye (TR) | 78.1% | 7.0% | 8.6% | 7.8% |
| Unknown (??) | 64.8% | 61.7% | 66.4% | 64.8% |
| Japan (JP) | 37.1% | 25.8% | 29.0% | 29.8% |
| Singapore (SG) | 38.3% | 32.2% | 35.7% | 29.6% |
| South Korea (KR) | 19.3% | 14.7% | 19.3% | 22.0% |
| Colombia (CO) | 24.7% | 28.9% | 25.8% | 24.7% |
| France (FR) | 17.0% | 19.1% | 34.0% | 28.7% |
| Mexico (MX) | 15.1% | 18.3% | 16.1% | 20.4% |
| Hong Kong (HK) | 20.9% | 16.5% | 27.5% | 24.2% |
| The Netherlands (NL) | 43.9% | 34.1% | 43.9% | 43.9% |
| Philippines (PH) | 34.2% | 29.1% | 34.2% | 34.2% |
| Vietnam (VN) | 34.6% | 30.8% | 21.8% | 30.8% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 337 daily snapshots since 2025-04-09 |

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
