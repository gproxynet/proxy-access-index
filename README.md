# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-18 06:40 UTC · **History:** 357 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 25.7% |
| YouTube | 17.8% |
| TikTok | 16.9% |
| X (Twitter) | 16.0% |
| LinkedIn | 15.9% |
| Qzone | 15.7% |
| Instagram | 14.2% |
| VK | 13.2% |
| OK.ru | 11.9% |
| Telegram | 10.7% |
| Reddit | 8.7% |
| Mail.ru | 6.4% |
| Yandex | 6.4% |
| Avito | 4.7% |
| Facebook | 0.6% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.6% of live proxies get through
- **Avito** — 4.7% of live proxies get through
- **Yandex** — 6.4% of live proxies get through
- **Mail.ru** — 6.4% of live proxies get through
- **Reddit** — 8.7% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 27.4% | 15.7% | 13.5% | 14.5% | 15.0% | 14.3% |
| hosting | 23.0% | 20.9% | 15.6% | 20.4% | 16.9% | 18.3% |
| mobile | 32.4% | 20.6% | 5.9% | 17.6% | 32.4% | 23.5% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 27.3% | 13.4% | 12.9% | 13.6% |
| Indonesia (ID) | 19.9% | 20.5% | 19.7% | 20.5% |
| Türkiye (TR) | 75.5% | 5.5% | 6.7% | 6.1% |
| Russia (RU) | 36.8% | 3.0% | 18.8% | 7.5% |
| China (CN) | 3.8% | 0.0% | 0.8% | 16.2% |
| Brazil (BR) | 44.5% | 8.2% | 7.3% | 8.2% |
| India (IN) | 28.0% | 13.1% | 23.4% | 13.1% |
| Singapore (SG) | 37.6% | 30.7% | 34.7% | 32.7% |
| Germany (DE) | 32.7% | 21.8% | 25.7% | 24.8% |
| Colombia (CO) | 15.1% | 10.5% | 12.8% | 14.0% |
| France (FR) | 30.1% | 27.7% | 32.5% | 27.7% |
| South Korea (KR) | 8.2% | 6.8% | 13.7% | 6.8% |
| Mexico (MX) | 7.4% | 8.8% | 11.8% | 11.8% |
| The Netherlands (NL) | 29.7% | 26.6% | 26.6% | 28.1% |
| Vietnam (VN) | 36.5% | 28.6% | 28.6% | 23.8% |
| Philippines (PH) | 19.7% | 13.1% | 14.8% | 13.1% |
| Japan (JP) | 15.0% | 8.3% | 16.7% | 11.7% |
| Hong Kong (HK) | 24.1% | 20.7% | 22.4% | 20.7% |
| Bangladesh (BD) | 21.6% | 25.5% | 21.6% | 17.6% |
| United Kingdom (GB) | 23.5% | 15.7% | 21.6% | 17.6% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 357 daily snapshots since 2025-04-09 |

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
