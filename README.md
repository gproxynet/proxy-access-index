# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-25 06:40 UTC · **History:** 364 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 28.2% |
| YouTube | 19.4% |
| Qzone | 18.9% |
| TikTok | 18.6% |
| LinkedIn | 18.5% |
| X (Twitter) | 18.3% |
| Instagram | 17.4% |
| VK | 15.1% |
| OK.ru | 14.8% |
| Telegram | 12.2% |
| Reddit | 9.9% |
| Yandex | 7.2% |
| Mail.ru | 6.9% |
| Avito | 5.6% |
| Facebook | 0.6% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.6% of live proxies get through
- **Avito** — 5.6% of live proxies get through
- **Mail.ru** — 6.9% of live proxies get through
- **Yandex** — 7.2% of live proxies get through
- **Reddit** — 9.9% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 31.2% | 18.9% | 18.0% | 17.7% | 17.8% | 17.5% |
| hosting | 23.8% | 20.3% | 16.4% | 19.8% | 19.3% | 19.5% |
| mobile | 24.3% | 21.6% | 21.6% | 24.3% | 29.7% | 13.5% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| Indonesia (ID) | 26.1% | 27.4% | 25.1% | 24.3% |
| United States (US) | 28.4% | 13.0% | 12.4% | 12.4% |
| Türkiye (TR) | 72.0% | 8.2% | 9.9% | 7.1% |
| Russia (RU) | 35.1% | 2.0% | 19.6% | 8.1% |
| India (IN) | 31.5% | 28.1% | 23.3% | 26.0% |
| Germany (DE) | 35.6% | 28.8% | 33.3% | 34.1% |
| China (CN) | 1.6% | 0.8% | 0.8% | 11.5% |
| Brazil (BR) | 46.7% | 14.8% | 12.3% | 9.0% |
| Singapore (SG) | 40.0% | 32.9% | 30.6% | 31.8% |
| Philippines (PH) | 16.7% | 17.9% | 19.0% | 11.9% |
| France (FR) | 33.8% | 31.2% | 31.2% | 33.8% |
| South Korea (KR) | 6.8% | 8.1% | 13.5% | 10.8% |
| Vietnam (VN) | 37.8% | 32.4% | 28.4% | 33.8% |
| The Netherlands (NL) | 37.1% | 35.7% | 37.1% | 38.6% |
| Colombia (CO) | 16.2% | 10.3% | 10.3% | 8.8% |
| Mexico (MX) | 16.2% | 13.2% | 16.2% | 10.3% |
| Hong Kong (HK) | 16.9% | 12.3% | 18.5% | 26.2% |
| Japan (JP) | 22.8% | 10.5% | 15.8% | 14.0% |
| United Kingdom (GB) | 25.9% | 14.8% | 18.5% | 16.7% |
| Thailand (TH) | 18.8% | 14.6% | 22.9% | 12.5% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 364 daily snapshots since 2025-04-09 |

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
