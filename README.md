# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-07-31 06:40 UTC · **History:** 339 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 30.3% |
| YouTube | 24.2% |
| TikTok | 24.2% |
| X (Twitter) | 23.3% |
| LinkedIn | 22.8% |
| Qzone | 22.7% |
| Instagram | 19.8% |
| Mail.ru | 18.5% |
| OK.ru | 18.1% |
| VK | 17.5% |
| Telegram | 15.7% |
| Reddit | 15.5% |
| Yandex | 10.5% |
| Avito | 6.9% |
| Facebook | 0.1% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.1% of live proxies get through
- **Avito** — 6.9% of live proxies get through
- **Yandex** — 10.5% of live proxies get through
- **Reddit** — 15.5% of live proxies get through
- **Telegram** — 15.7% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 36.1% | 25.3% | 22.7% | 24.5% | 24.9% | 24.9% |
| hosting | 24.1% | 22.4% | 15.2% | 22.2% | 18.9% | 20.2% |
| unknown | 23.0% | 25.7% | 21.8% | 29.7% | 26.0% | 27.5% |
| mobile | 29.3% | 22.2% | 21.2% | 27.3% | 24.2% | 23.2% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 26.1% | 16.2% | 18.6% | 17.7% |
| Indonesia (ID) | 36.9% | 40.1% | 42.0% | 40.5% |
| Russia (RU) | 50.8% | 4.0% | 21.6% | 10.6% |
| Germany (DE) | 29.8% | 25.5% | 34.2% | 32.3% |
| China (CN) | 3.2% | 0.6% | 0.6% | 18.8% |
| India (IN) | 23.4% | 12.4% | 13.8% | 14.5% |
| Brazil (BR) | 47.4% | 15.8% | 16.5% | 15.8% |
| Türkiye (TR) | 84.7% | 6.1% | 6.9% | 4.6% |
| Japan (JP) | 34.6% | 23.8% | 32.3% | 28.5% |
| Singapore (SG) | 38.3% | 30.8% | 38.3% | 29.2% |
| South Korea (KR) | 10.4% | 10.4% | 15.7% | 12.2% |
| Hong Kong (HK) | 26.5% | 19.4% | 24.5% | 25.5% |
| France (FR) | 24.7% | 25.8% | 29.9% | 26.8% |
| Mexico (MX) | 29.5% | 23.2% | 27.4% | 29.5% |
| Philippines (PH) | 30.5% | 28.4% | 31.6% | 27.4% |
| Colombia (CO) | 26.6% | 23.4% | 24.5% | 26.6% |
| Vietnam (VN) | 32.3% | 26.9% | 26.9% | 25.8% |
| The Netherlands (NL) | 42.5% | 30.0% | 41.2% | 33.8% |
| Australia (AU) | 4.4% | 5.9% | 16.2% | 13.2% |
| Canada (CA) | 13.4% | 6.0% | 13.4% | 7.5% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 339 daily snapshots since 2025-04-09 |

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
