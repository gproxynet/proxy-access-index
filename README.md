# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-15 06:40 UTC · **History:** 354 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 27.3% |
| YouTube | 23.7% |
| TikTok | 23.3% |
| X (Twitter) | 22.7% |
| LinkedIn | 22.6% |
| Qzone | 22.3% |
| Instagram | 20.1% |
| VK | 19.0% |
| OK.ru | 16.3% |
| Telegram | 14.9% |
| Reddit | 13.2% |
| Yandex | 9.1% |
| Mail.ru | 8.9% |
| Avito | 6.9% |
| Facebook | 1.9% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 1.9% of live proxies get through
- **Avito** — 6.9% of live proxies get through
- **Mail.ru** — 8.9% of live proxies get through
- **Yandex** — 9.1% of live proxies get through
- **Reddit** — 13.2% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 30.9% | 22.4% | 20.9% | 21.2% | 22.3% | 22.0% |
| hosting | 22.1% | 24.3% | 18.3% | 24.9% | 21.8% | 22.7% |
| mobile | 49.1% | 54.7% | 45.3% | 50.9% | 62.3% | 50.9% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 27.5% | 17.6% | 19.0% | 17.1% |
| Indonesia (ID) | 27.9% | 33.9% | 29.3% | 32.7% |
| Türkiye (TR) | 73.9% | 4.4% | 5.6% | 5.0% |
| China (CN) | 3.6% | 0.0% | 0.6% | 19.5% |
| Russia (RU) | 34.4% | 2.5% | 26.2% | 9.4% |
| India (IN) | 23.6% | 18.1% | 20.1% | 20.1% |
| Germany (DE) | 26.8% | 21.1% | 31.7% | 24.6% |
| France (FR) | 28.0% | 35.2% | 29.6% | 34.4% |
| Brazil (BR) | 43.0% | 11.6% | 11.6% | 14.9% |
| Singapore (SG) | 36.9% | 31.5% | 35.1% | 29.7% |
| Japan (JP) | 19.1% | 13.6% | 27.3% | 20.9% |
| South Korea (KR) | 8.4% | 10.5% | 14.7% | 13.7% |
| The Netherlands (NL) | 25.5% | 27.7% | 28.7% | 30.9% |
| Vietnam (VN) | 48.3% | 43.8% | 48.3% | 46.1% |
| Hong Kong (HK) | 14.6% | 18.0% | 28.1% | 19.1% |
| Colombia (CO) | 22.5% | 19.1% | 24.7% | 28.1% |
| Mexico (MX) | 16.9% | 22.9% | 18.1% | 21.7% |
| Switzerland (CH) | 73.0% | 74.3% | 78.4% | 74.3% |
| Canada (CA) | 14.7% | 10.3% | 14.7% | 14.7% |
| Philippines (PH) | 24.2% | 28.8% | 31.8% | 28.8% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 354 daily snapshots since 2025-04-09 |

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
