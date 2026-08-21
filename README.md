# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-21 06:40 UTC · **History:** 360 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 23.4% |
| YouTube | 17.7% |
| TikTok | 17.4% |
| LinkedIn | 16.5% |
| X (Twitter) | 16.1% |
| Instagram | 14.2% |
| VK | 14.0% |
| OK.ru | 12.2% |
| Qzone | 12.1% |
| Telegram | 10.7% |
| Reddit | 10.3% |
| Yandex | 5.9% |
| Mail.ru | 4.9% |
| Avito | 4.5% |
| Facebook | 0.5% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.5% of live proxies get through
- **Avito** — 4.5% of live proxies get through
- **Mail.ru** — 4.9% of live proxies get through
- **Yandex** — 5.9% of live proxies get through
- **Reddit** — 10.3% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 26.1% | 16.7% | 14.3% | 14.8% | 15.8% | 14.1% |
| hosting | 19.8% | 19.2% | 14.0% | 21.0% | 17.2% | 18.9% |
| mobile | 12.9% | 12.9% | 9.7% | 16.1% | 29.0% | 12.9% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 27.5% | 11.8% | 17.4% | 16.0% |
| Indonesia (ID) | 19.6% | 20.9% | 24.5% | 24.8% |
| Türkiye (TR) | 73.6% | 3.4% | 2.3% | 2.3% |
| India (IN) | 22.1% | 12.8% | 22.8% | 14.8% |
| China (CN) | 4.4% | 0.0% | 0.0% | 16.2% |
| Russia (RU) | 29.0% | 3.2% | 12.1% | 8.1% |
| Germany (DE) | 21.8% | 15.1% | 19.3% | 12.6% |
| Brazil (BR) | 41.9% | 5.1% | 7.7% | 6.8% |
| France (FR) | 30.8% | 29.7% | 30.8% | 28.6% |
| Singapore (SG) | 43.3% | 37.8% | 33.3% | 32.2% |
| South Korea (KR) | 8.0% | 8.0% | 17.0% | 13.6% |
| Hong Kong (HK) | 20.5% | 20.5% | 26.5% | 24.1% |
| Philippines (PH) | 19.5% | 22.1% | 14.3% | 22.1% |
| Colombia (CO) | 9.2% | 10.5% | 9.2% | 10.5% |
| The Netherlands (NL) | 23.7% | 28.9% | 22.4% | 26.3% |
| Japan (JP) | 14.9% | 8.1% | 21.6% | 10.8% |
| Mexico (MX) | 13.0% | 10.1% | 13.0% | 11.6% |
| Canada (CA) | 10.9% | 4.7% | 9.4% | 7.8% |
| Vietnam (VN) | 33.9% | 37.1% | 32.3% | 37.1% |
| United Kingdom (GB) | 22.2% | 16.7% | 16.7% | 16.7% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 360 daily snapshots since 2025-04-09 |

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
