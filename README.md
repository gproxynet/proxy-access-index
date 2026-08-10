# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-10 06:40 UTC · **History:** 349 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 28.5% |
| YouTube | 17.9% |
| Qzone | 17.2% |
| LinkedIn | 16.7% |
| TikTok | 16.4% |
| X (Twitter) | 16.3% |
| Instagram | 15.9% |
| VK | 14.7% |
| Mail.ru | 14.7% |
| OK.ru | 14.6% |
| Telegram | 11.4% |
| Yandex | 8.5% |
| Reddit | 5.8% |
| Avito | 4.5% |
| Facebook | 0.5% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.5% of live proxies get through
- **Avito** — 4.5% of live proxies get through
- **Reddit** — 5.8% of live proxies get through
- **Yandex** — 8.5% of live proxies get through
- **Telegram** — 11.4% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 28.5% | 15.3% | 13.8% | 13.9% | 14.6% | 13.7% |
| hosting | 28.6% | 22.4% | 19.8% | 20.7% | 20.3% | 20.7% |
| mobile | 26.9% | 19.2% | 11.5% | 15.4% | 19.2% | 19.2% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 27.1% | 11.6% | 11.3% | 10.8% |
| Indonesia (ID) | 18.0% | 19.2% | 17.6% | 18.8% |
| Türkiye (TR) | 79.2% | 0.6% | 4.4% | 4.4% |
| Russia (RU) | 36.1% | 4.2% | 28.5% | 10.4% |
| China (CN) | 5.0% | 0.0% | 0.8% | 9.1% |
| Germany (DE) | 23.8% | 25.7% | 22.8% | 23.8% |
| Brazil (BR) | 49.5% | 7.4% | 7.4% | 9.5% |
| France (FR) | 33.0% | 33.0% | 27.5% | 35.2% |
| Singapore (SG) | 41.9% | 40.7% | 40.7% | 39.5% |
| Vietnam (VN) | 50.6% | 42.4% | 38.8% | 40.0% |
| India (IN) | 26.2% | 15.0% | 10.0% | 13.8% |
| The Netherlands (NL) | 33.3% | 34.6% | 34.6% | 34.6% |
| Colombia (CO) | 9.6% | 8.2% | 8.2% | 6.8% |
| South Korea (KR) | 12.5% | 9.4% | 6.2% | 7.8% |
| Philippines (PH) | 15.5% | 17.2% | 19.0% | 15.5% |
| Hong Kong (HK) | 28.3% | 22.6% | 17.0% | 28.3% |
| United Kingdom (GB) | 23.1% | 10.3% | 10.3% | 10.3% |
| Mexico (MX) | 5.4% | 13.5% | 16.2% | 10.8% |
| Japan (JP) | 31.2% | 15.6% | 18.8% | 21.9% |
| Venezuela (VE) | 25.0% | 18.8% | 18.8% | 12.5% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 349 daily snapshots since 2025-04-09 |

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
