# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-17 06:40 UTC · **History:** 356 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 25.9% |
| YouTube | 18.6% |
| LinkedIn | 17.9% |
| Qzone | 17.5% |
| TikTok | 17.1% |
| X (Twitter) | 16.3% |
| Instagram | 16.2% |
| VK | 14.7% |
| OK.ru | 14.1% |
| Telegram | 10.6% |
| Yandex | 8.0% |
| Mail.ru | 7.5% |
| Reddit | 6.0% |
| Avito | 5.3% |
| Facebook | 0.5% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.5% of live proxies get through
- **Avito** — 5.3% of live proxies get through
- **Reddit** — 6.0% of live proxies get through
- **Mail.ru** — 7.5% of live proxies get through
- **Yandex** — 8.0% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 27.3% | 16.2% | 13.7% | 15.7% | 15.2% | 14.4% |
| hosting | 23.6% | 22.6% | 20.5% | 19.6% | 21.8% | 19.5% |
| mobile | 19.0% | 19.0% | 14.3% | 9.5% | 38.1% | 14.3% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 26.4% | 15.5% | 14.7% | 15.2% |
| Indonesia (ID) | 14.4% | 17.1% | 16.0% | 15.2% |
| Türkiye (TR) | 77.4% | 3.8% | 4.4% | 4.4% |
| Russia (RU) | 36.3% | 2.1% | 25.3% | 8.2% |
| China (CN) | 4.0% | 0.8% | 0.0% | 17.5% |
| Germany (DE) | 21.2% | 24.0% | 17.3% | 23.1% |
| Brazil (BR) | 54.3% | 15.2% | 13.0% | 16.3% |
| Singapore (SG) | 23.6% | 30.3% | 33.7% | 36.0% |
| India (IN) | 20.9% | 18.6% | 11.6% | 16.3% |
| France (FR) | 30.6% | 32.9% | 25.9% | 35.3% |
| The Netherlands (NL) | 18.8% | 21.7% | 27.5% | 27.5% |
| South Korea (KR) | 8.1% | 8.1% | 6.5% | 9.7% |
| Colombia (CO) | 18.3% | 25.0% | 21.7% | 18.3% |
| Mexico (MX) | 10.0% | 8.3% | 6.7% | 11.7% |
| Vietnam (VN) | 23.6% | 34.5% | 29.1% | 34.5% |
| Philippines (PH) | 18.8% | 14.6% | 16.7% | 16.7% |
| United Kingdom (GB) | 13.0% | 17.4% | 15.2% | 15.2% |
| Finland (FI) | 36.4% | 34.1% | 34.1% | 38.6% |
| Hong Kong (HK) | 26.2% | 21.4% | 19.0% | 21.4% |
| Pakistan (PK) | 56.1% | 63.4% | 68.3% | 61.0% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 356 daily snapshots since 2025-04-09 |

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
