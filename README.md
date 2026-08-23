# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-23 06:40 UTC · **History:** 362 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 29.1% |
| YouTube | 22.4% |
| LinkedIn | 22.3% |
| TikTok | 21.5% |
| X (Twitter) | 21.3% |
| Qzone | 20.9% |
| Instagram | 20.8% |
| VK | 18.2% |
| OK.ru | 17.2% |
| Telegram | 14.0% |
| Reddit | 12.6% |
| Yandex | 8.9% |
| Mail.ru | 7.8% |
| Avito | 6.2% |
| Facebook | 0.6% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.6% of live proxies get through
- **Avito** — 6.2% of live proxies get through
- **Mail.ru** — 7.8% of live proxies get through
- **Yandex** — 8.9% of live proxies get through
- **Reddit** — 12.6% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 29.7% | 22.2% | 20.9% | 21.8% | 22.2% | 21.2% |
| hosting | 28.1% | 22.9% | 20.7% | 21.3% | 22.5% | 21.7% |
| mobile | 23.7% | 15.8% | 18.4% | 15.8% | 23.7% | 15.8% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| Indonesia (ID) | 25.3% | 31.9% | 32.8% | 33.3% |
| United States (US) | 28.4% | 13.6% | 14.8% | 16.2% |
| Türkiye (TR) | 72.5% | 8.8% | 8.8% | 9.4% |
| Russia (RU) | 35.1% | 1.4% | 18.9% | 8.8% |
| China (CN) | 4.4% | 0.0% | 0.7% | 14.7% |
| Germany (DE) | 33.1% | 24.0% | 27.3% | 25.6% |
| Brazil (BR) | 50.9% | 16.4% | 15.5% | 12.7% |
| India (IN) | 29.2% | 14.6% | 15.6% | 19.8% |
| Colombia (CO) | 18.5% | 16.3% | 18.5% | 20.7% |
| Philippines (PH) | 28.7% | 29.9% | 31.0% | 28.7% |
| Singapore (SG) | 34.6% | 32.1% | 34.6% | 30.9% |
| Mexico (MX) | 21.0% | 24.7% | 23.5% | 22.2% |
| France (FR) | 34.6% | 35.9% | 33.3% | 33.3% |
| The Netherlands (NL) | 38.9% | 36.1% | 36.1% | 38.9% |
| Vietnam (VN) | 30.4% | 30.4% | 26.1% | 27.5% |
| South Korea (KR) | 8.2% | 9.8% | 8.2% | 8.2% |
| Bangladesh (BD) | 24.1% | 27.8% | 27.8% | 27.8% |
| Hong Kong (HK) | 31.4% | 31.4% | 27.5% | 33.3% |
| Venezuela (VE) | 24.4% | 8.9% | 17.8% | 17.8% |
| United Kingdom (GB) | 22.2% | 20.0% | 20.0% | 22.2% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 362 daily snapshots since 2025-04-09 |

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
