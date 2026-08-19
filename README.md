# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-19 06:40 UTC · **History:** 358 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 24.5% |
| YouTube | 16.4% |
| TikTok | 15.4% |
| LinkedIn | 15.4% |
| X (Twitter) | 14.8% |
| Instagram | 13.1% |
| Qzone | 12.5% |
| VK | 12.5% |
| OK.ru | 11.9% |
| Telegram | 9.4% |
| Reddit | 7.4% |
| Yandex | 6.2% |
| Mail.ru | 6.1% |
| Avito | 4.1% |
| Facebook | 0.5% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.5% of live proxies get through
- **Avito** — 4.1% of live proxies get through
- **Mail.ru** — 6.1% of live proxies get through
- **Yandex** — 6.2% of live proxies get through
- **Reddit** — 7.4% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 29.2% | 14.3% | 12.8% | 13.2% | 14.3% | 13.1% |
| hosting | 18.8% | 18.4% | 13.3% | 17.6% | 16.1% | 16.6% |
| mobile | 33.3% | 33.3% | 22.2% | 29.6% | 40.7% | 22.2% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 26.6% | 13.6% | 13.2% | 14.5% |
| Indonesia (ID) | 16.3% | 14.7% | 11.5% | 15.9% |
| Türkiye (TR) | 76.4% | 2.4% | 3.6% | 3.0% |
| Russia (RU) | 39.3% | 3.4% | 21.4% | 9.7% |
| China (CN) | 4.0% | 0.8% | 0.8% | 16.7% |
| India (IN) | 19.8% | 10.3% | 15.9% | 11.1% |
| Germany (DE) | 24.3% | 17.1% | 22.5% | 19.8% |
| Brazil (BR) | 38.7% | 3.8% | 3.8% | 4.7% |
| Singapore (SG) | 31.0% | 35.0% | 37.0% | 34.0% |
| France (FR) | 23.1% | 24.2% | 19.8% | 20.9% |
| The Netherlands (NL) | 28.8% | 30.0% | 30.0% | 27.5% |
| South Korea (KR) | 4.0% | 4.0% | 13.3% | 9.3% |
| Hong Kong (HK) | 17.8% | 12.3% | 20.5% | 17.8% |
| Japan (JP) | 14.9% | 7.5% | 14.9% | 16.4% |
| Vietnam (VN) | 26.3% | 26.3% | 17.5% | 28.1% |
| Colombia (CO) | 16.1% | 10.7% | 14.3% | 12.5% |
| United Kingdom (GB) | 19.6% | 10.7% | 10.7% | 12.5% |
| Canada (CA) | 17.3% | 5.8% | 11.5% | 11.5% |
| South Africa (ZA) | 9.8% | 9.8% | 15.7% | 15.7% |
| Mexico (MX) | 10.2% | 8.2% | 10.2% | 6.1% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 358 daily snapshots since 2025-04-09 |

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
