# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-09-01 06:40 UTC · **History:** 371 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 21.7% |
| YouTube | 18.3% |
| LinkedIn | 18.3% |
| X (Twitter) | 18.1% |
| Qzone | 18.0% |
| TikTok | 17.9% |
| VK | 16.2% |
| Instagram | 15.5% |
| OK.ru | 14.6% |
| Telegram | 11.7% |
| Reddit | 10.8% |
| Yandex | 7.4% |
| Mail.ru | 6.9% |
| Avito | 5.5% |
| Facebook | 0.4% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.4% of live proxies get through
- **Avito** — 5.5% of live proxies get through
- **Mail.ru** — 6.9% of live proxies get through
- **Yandex** — 7.4% of live proxies get through
- **Reddit** — 10.8% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 27.5% | 18.3% | 17.6% | 18.1% | 18.2% | 17.4% |
| hosting | 15.8% | 18.5% | 13.5% | 18.0% | 18.4% | 18.9% |
| mobile | 19.2% | 7.7% | 11.5% | 7.7% | 19.2% | 15.4% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 17.8% | 12.0% | 14.8% | 13.1% |
| Indonesia (ID) | 21.0% | 23.7% | 21.2% | 23.7% |
| Russia (RU) | 34.5% | 1.2% | 21.4% | 7.1% |
| Germany (DE) | 34.0% | 30.8% | 30.8% | 33.3% |
| Türkiye (TR) | 78.5% | 4.0% | 2.7% | 2.7% |
| India (IN) | 19.1% | 12.5% | 14.7% | 16.2% |
| China (CN) | 1.7% | 0.8% | 0.8% | 10.7% |
| Brazil (BR) | 41.2% | 5.0% | 7.6% | 8.4% |
| France (FR) | 17.6% | 26.1% | 32.8% | 30.3% |
| Japan (JP) | 14.2% | 7.5% | 10.4% | 15.1% |
| Singapore (SG) | 33.3% | 31.4% | 27.6% | 29.5% |
| Hong Kong (HK) | 6.7% | 16.3% | 17.3% | 26.9% |
| South Korea (KR) | 7.6% | 10.9% | 14.1% | 16.3% |
| Canada (CA) | 8.7% | 7.6% | 8.7% | 13.0% |
| The Netherlands (NL) | 29.1% | 36.0% | 38.4% | 37.2% |
| Mexico (MX) | 9.5% | 4.8% | 14.3% | 9.5% |
| Philippines (PH) | 15.9% | 17.1% | 22.0% | 20.7% |
| Thailand (TH) | 33.3% | 26.1% | 33.3% | 30.4% |
| Vietnam (VN) | 39.7% | 41.2% | 30.9% | 41.2% |
| Australia (AU) | 1.5% | 3.0% | 13.4% | 11.9% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 371 daily snapshots since 2025-04-09 |

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
