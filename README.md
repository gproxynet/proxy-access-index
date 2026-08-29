# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-29 06:40 UTC · **History:** 368 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 23.4% |
| YouTube | 17.7% |
| TikTok | 17.2% |
| Qzone | 16.8% |
| X (Twitter) | 16.3% |
| LinkedIn | 15.7% |
| VK | 15.1% |
| Instagram | 13.8% |
| OK.ru | 12.9% |
| Reddit | 10.7% |
| Telegram | 10.6% |
| Yandex | 7.0% |
| Mail.ru | 6.7% |
| Avito | 4.5% |
| Facebook | 0.5% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.5% of live proxies get through
- **Avito** — 4.5% of live proxies get through
- **Mail.ru** — 6.7% of live proxies get through
- **Yandex** — 7.0% of live proxies get through
- **Telegram** — 10.6% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 29.9% | 18.7% | 16.3% | 17.9% | 17.5% | 17.2% |
| hosting | 16.4% | 16.6% | 11.0% | 16.3% | 13.6% | 15.4% |
| mobile | 22.2% | 18.5% | 11.1% | 25.9% | 25.9% | 14.8% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 19.9% | 8.4% | 12.4% | 9.3% |
| Indonesia (ID) | 21.0% | 21.0% | 22.2% | 21.6% |
| Russia (RU) | 28.6% | 1.3% | 19.5% | 3.9% |
| Türkiye (TR) | 78.0% | 2.0% | 2.0% | 2.7% |
| Germany (DE) | 27.4% | 17.8% | 19.3% | 17.0% |
| China (CN) | 2.3% | 0.0% | 0.0% | 12.9% |
| India (IN) | 24.2% | 16.1% | 17.7% | 17.7% |
| France (FR) | 30.8% | 26.0% | 27.9% | 24.0% |
| Japan (JP) | 12.7% | 8.8% | 15.7% | 8.8% |
| Brazil (BR) | 35.7% | 9.2% | 12.2% | 12.2% |
| Singapore (SG) | 37.1% | 29.9% | 29.9% | 28.9% |
| Mexico (MX) | 13.3% | 12.2% | 14.4% | 14.4% |
| Hong Kong (HK) | 12.7% | 8.9% | 16.5% | 16.5% |
| United Kingdom (GB) | 18.9% | 10.8% | 17.6% | 14.9% |
| Vietnam (VN) | 38.9% | 36.1% | 34.7% | 36.1% |
| Canada (CA) | 14.3% | 7.1% | 18.6% | 10.0% |
| South Korea (KR) | 9.4% | 7.8% | 10.9% | 12.5% |
| Thailand (TH) | 41.9% | 35.5% | 45.2% | 43.5% |
| Colombia (CO) | 19.0% | 15.5% | 15.5% | 15.5% |
| The Netherlands (NL) | 17.9% | 26.8% | 21.4% | 25.0% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 368 daily snapshots since 2025-04-09 |

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
