# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-26 06:40 UTC · **History:** 365 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 26.0% |
| LinkedIn | 16.8% |
| YouTube | 16.7% |
| TikTok | 16.7% |
| X (Twitter) | 16.1% |
| VK | 14.9% |
| Instagram | 14.2% |
| OK.ru | 13.7% |
| Qzone | 13.3% |
| Telegram | 10.3% |
| Reddit | 8.6% |
| Yandex | 6.9% |
| Mail.ru | 6.0% |
| Avito | 4.6% |
| Facebook | 0.6% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.6% of live proxies get through
- **Avito** — 4.6% of live proxies get through
- **Mail.ru** — 6.0% of live proxies get through
- **Yandex** — 6.9% of live proxies get through
- **Reddit** — 8.6% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 28.7% | 15.7% | 14.2% | 15.8% | 16.1% | 15.1% |
| hosting | 21.9% | 18.0% | 14.2% | 17.9% | 17.6% | 17.6% |
| mobile | 25.0% | 25.0% | 14.3% | 25.0% | 28.6% | 10.7% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 26.6% | 9.3% | 9.0% | 8.5% |
| Indonesia (ID) | 17.3% | 19.5% | 17.0% | 18.6% |
| Türkiye (TR) | 71.9% | 3.5% | 7.6% | 5.3% |
| Russia (RU) | 37.5% | 1.3% | 14.5% | 5.9% |
| Germany (DE) | 40.6% | 32.3% | 30.1% | 31.6% |
| China (CN) | 1.6% | 0.8% | 0.8% | 16.3% |
| India (IN) | 31.1% | 18.5% | 17.6% | 24.4% |
| Brazil (BR) | 51.3% | 11.3% | 17.4% | 13.0% |
| Singapore (SG) | 35.8% | 29.5% | 34.7% | 27.4% |
| France (FR) | 27.2% | 25.9% | 28.4% | 28.4% |
| Colombia (CO) | 21.0% | 14.8% | 12.3% | 16.0% |
| The Netherlands (NL) | 27.4% | 26.0% | 28.8% | 28.8% |
| Mexico (MX) | 12.9% | 12.9% | 15.7% | 12.9% |
| South Korea (KR) | 7.2% | 8.7% | 13.0% | 14.5% |
| Hong Kong (HK) | 14.7% | 10.3% | 13.2% | 11.8% |
| Vietnam (VN) | 29.9% | 23.9% | 26.9% | 34.3% |
| Philippines (PH) | 19.0% | 22.2% | 22.2% | 22.2% |
| Japan (JP) | 25.4% | 11.9% | 16.9% | 13.6% |
| Canada (CA) | 11.9% | 6.8% | 11.9% | 10.2% |
| United Kingdom (GB) | 16.4% | 9.1% | 10.9% | 10.9% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 365 daily snapshots since 2025-04-09 |

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
