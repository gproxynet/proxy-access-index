# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-07-24 21:44 UTC · **History:** 332 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| YouTube | 38.5% |
| Google | 38.0% |
| LinkedIn | 37.4% |
| X (Twitter) | 36.9% |
| Qzone | 35.5% |
| Instagram | 35.2% |
| TikTok | 35.1% |
| Mail.ru | 29.7% |
| VK | 28.3% |
| Telegram | 27.7% |
| OK.ru | 26.8% |
| Reddit | 18.1% |
| Yandex | 14.6% |
| Avito | 9.4% |
| Facebook | 3.4% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 3.4% of live proxies get through
- **Avito** — 9.4% of live proxies get through
- **Yandex** — 14.6% of live proxies get through
- **Reddit** — 18.1% of live proxies get through
- **OK.ru** — 26.8% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 47.6% | 46.6% | 44.2% | 42.9% | 45.3% | 46.5% |
| hosting | 20.8% | 22.4% | 17.5% | 22.2% | 21.5% | 21.2% |
| unknown | 35.5% | 43.1% | 37.6% | 28.4% | 40.3% | 28.4% |
| mobile | 38.5% | 38.5% | 43.3% | 42.3% | 46.2% | 42.3% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 28.1% | 36.6% | 19.8% | 35.5% |
| Indonesia (ID) | 47.6% | 58.8% | 61.0% | 62.1% |
| Albania (AL) | 89.3% | 82.5% | 76.2% | 88.2% |
| Russia (RU) | 48.7% | 3.9% | 28.7% | 11.7% |
| Brazil (BR) | 50.5% | 27.0% | 32.1% | 28.6% |
| Germany (DE) | 29.3% | 33.7% | 33.1% | 35.4% |
| India (IN) | 28.5% | 22.9% | 24.6% | 25.1% |
| China (CN) | 4.4% | 0.6% | 0.6% | 19.4% |
| Türkiye (TR) | 86.2% | 11.8% | 11.8% | 11.2% |
| Singapore (SG) | 31.9% | 27.7% | 34.8% | 33.3% |
| Colombia (CO) | 46.7% | 45.2% | 46.7% | 48.1% |
| Mexico (MX) | 39.7% | 39.7% | 42.7% | 39.7% |
| The Netherlands (NL) | 15.7% | 18.1% | 22.0% | 18.9% |
| Japan (JP) | 27.0% | 22.2% | 23.8% | 21.4% |
| France (FR) | 17.4% | 26.4% | 30.6% | 29.8% |
| South Korea (KR) | 10.3% | 12.1% | 19.8% | 12.1% |
| Vietnam (VN) | 39.8% | 36.9% | 36.9% | 33.0% |
| Hong Kong (HK) | 25.0% | 25.0% | 30.0% | 29.0% |
| Bangladesh (BD) | 56.1% | 62.2% | 64.3% | 63.3% |
| Philippines (PH) | 54.8% | 54.8% | 50.5% | 52.7% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 332 daily snapshots since 2025-04-09 |

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
