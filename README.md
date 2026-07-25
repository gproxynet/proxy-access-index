# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-07-25 06:40 UTC · **History:** 333 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| YouTube | 33.1% |
| LinkedIn | 32.0% |
| Google | 30.8% |
| X (Twitter) | 29.4% |
| Instagram | 29.3% |
| Qzone | 29.3% |
| TikTok | 28.7% |
| Mail.ru | 25.5% |
| VK | 24.3% |
| Telegram | 23.7% |
| OK.ru | 22.8% |
| Yandex | 12.5% |
| Reddit | 10.3% |
| Avito | 8.5% |
| Facebook | 4.2% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 4.2% of live proxies get through
- **Avito** — 8.5% of live proxies get through
- **Reddit** — 10.3% of live proxies get through
- **Yandex** — 12.5% of live proxies get through
- **OK.ru** — 22.8% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 38.0% | 38.4% | 35.6% | 34.2% | 37.7% | 36.4% |
| hosting | 19.2% | 22.7% | 16.7% | 20.8% | 20.3% | 19.6% |
| unknown | 29.3% | 37.4% | 34.3% | 22.0% | 37.8% | 20.2% |
| mobile | 21.9% | 32.3% | 30.2% | 31.2% | 33.3% | 29.2% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 29.9% | 29.2% | 16.3% | 29.8% |
| Indonesia (ID) | 21.3% | 35.3% | 36.6% | 37.9% |
| Albania (AL) | 74.2% | 87.4% | 77.4% | 90.4% |
| Russia (RU) | 44.6% | 5.7% | 21.8% | 10.4% |
| India (IN) | 20.2% | 20.8% | 18.0% | 21.9% |
| China (CN) | 2.4% | 0.0% | 0.6% | 16.4% |
| Brazil (BR) | 46.2% | 22.2% | 22.2% | 23.4% |
| Germany (DE) | 24.7% | 34.8% | 37.3% | 37.3% |
| Japan (JP) | 31.9% | 26.4% | 34.7% | 35.4% |
| Türkiye (TR) | 83.5% | 5.0% | 5.0% | 5.0% |
| South Korea (KR) | 6.5% | 10.6% | 17.1% | 13.8% |
| Singapore (SG) | 28.2% | 24.8% | 29.1% | 29.1% |
| The Netherlands (NL) | 24.5% | 33.6% | 34.5% | 35.5% |
| Colombia (CO) | 22.0% | 28.4% | 27.5% | 26.6% |
| France (FR) | 16.3% | 20.4% | 18.4% | 20.4% |
| Vietnam (VN) | 28.7% | 30.9% | 26.6% | 30.9% |
| Hong Kong (HK) | 15.9% | 18.2% | 19.3% | 22.7% |
| United Kingdom (GB) | 10.6% | 17.6% | 16.5% | 15.3% |
| Bangladesh (BD) | 43.0% | 48.1% | 49.4% | 49.4% |
| Mexico (MX) | 24.4% | 28.2% | 29.5% | 30.8% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 333 daily snapshots since 2025-04-09 |

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
