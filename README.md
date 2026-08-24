# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-24 06:40 UTC · **History:** 363 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 28.3% |
| YouTube | 17.9% |
| LinkedIn | 17.6% |
| Qzone | 17.1% |
| TikTok | 16.7% |
| X (Twitter) | 15.9% |
| Instagram | 15.2% |
| VK | 14.6% |
| OK.ru | 13.7% |
| Telegram | 10.5% |
| Reddit | 8.8% |
| Yandex | 6.8% |
| Mail.ru | 6.1% |
| Avito | 4.9% |
| Facebook | 0.6% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.6% of live proxies get through
- **Avito** — 4.9% of live proxies get through
- **Mail.ru** — 6.1% of live proxies get through
- **Yandex** — 6.8% of live proxies get through
- **Reddit** — 8.8% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 28.8% | 15.9% | 13.9% | 16.1% | 16.1% | 14.6% |
| hosting | 27.2% | 21.9% | 17.8% | 18.1% | 20.2% | 18.6% |
| mobile | 30.8% | 11.5% | 11.5% | 7.7% | 34.6% | 11.5% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| Indonesia (ID) | 20.2% | 21.1% | 20.5% | 20.8% |
| United States (US) | 29.4% | 9.3% | 10.5% | 12.2% |
| Türkiye (TR) | 69.1% | 3.7% | 4.3% | 4.9% |
| Russia (RU) | 35.8% | 2.0% | 21.6% | 8.1% |
| China (CN) | 2.3% | 0.0% | 0.0% | 11.5% |
| Germany (DE) | 30.7% | 31.5% | 26.8% | 29.1% |
| Brazil (BR) | 51.0% | 8.8% | 6.9% | 8.8% |
| India (IN) | 38.0% | 21.7% | 18.5% | 27.2% |
| Singapore (SG) | 41.8% | 29.1% | 29.1% | 30.4% |
| France (FR) | 25.6% | 25.6% | 28.2% | 25.6% |
| Philippines (PH) | 25.8% | 16.7% | 16.7% | 22.7% |
| The Netherlands (NL) | 26.2% | 26.2% | 30.8% | 30.8% |
| Colombia (CO) | 20.3% | 18.8% | 20.3% | 18.8% |
| Vietnam (VN) | 36.2% | 25.9% | 22.4% | 27.6% |
| South Korea (KR) | 6.9% | 8.6% | 6.9% | 8.6% |
| Mexico (MX) | 12.5% | 12.5% | 17.9% | 12.5% |
| United Kingdom (GB) | 25.0% | 16.7% | 22.9% | 18.8% |
| Hong Kong (HK) | 21.7% | 17.4% | 15.2% | 21.7% |
| Bangladesh (BD) | 25.6% | 14.0% | 23.3% | 16.3% |
| Dominican Republic (DO) | 13.5% | 8.1% | 16.2% | 13.5% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 363 daily snapshots since 2025-04-09 |

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
