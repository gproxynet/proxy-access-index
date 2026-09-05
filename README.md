# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-09-05 06:40 UTC · **History:** 375 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 27.7% |
| Qzone | 23.2% |
| LinkedIn | 23.0% |
| X (Twitter) | 22.8% |
| TikTok | 22.0% |
| YouTube | 21.5% |
| Instagram | 19.4% |
| VK | 19.2% |
| OK.ru | 17.8% |
| Telegram | 15.3% |
| Reddit | 13.3% |
| Yandex | 9.3% |
| Mail.ru | 8.8% |
| Avito | 6.9% |
| Facebook | 0.0% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.0% of live proxies get through
- **Avito** — 6.9% of live proxies get through
- **Mail.ru** — 8.8% of live proxies get through
- **Yandex** — 9.3% of live proxies get through
- **Reddit** — 13.3% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| hosting | 17.8% | 17.6% | 14.0% | 17.8% | 19.3% | 19.5% |
| residential | 38.8% | 25.9% | 25.5% | 26.7% | 27.0% | 26.5% |
| mobile | 26.1% | 17.4% | 17.4% | 21.7% | 26.1% | 13.0% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 21.7% | 13.3% | 15.4% | 15.7% |
| Indonesia (ID) | 32.5% | 31.7% | 33.5% | 36.3% |
| Germany (DE) | 30.6% | 26.0% | 28.3% | 24.9% |
| Russia (RU) | 38.9% | 3.1% | 24.1% | 6.8% |
| Türkiye (TR) | 79.9% | 8.1% | 8.1% | 6.0% |
| India (IN) | 27.9% | 22.1% | 24.3% | 24.3% |
| Brazil (BR) | 46.0% | 16.1% | 16.8% | 16.8% |
| Singapore (SG) | 36.5% | 32.8% | 36.5% | 38.0% |
| China (CN) | 2.4% | 0.8% | 0.8% | 26.0% |
| Japan (JP) | 14.3% | 6.7% | 15.1% | 20.2% |
| France (FR) | 27.4% | 28.2% | 24.8% | 28.2% |
| Canada (CA) | 13.3% | 9.5% | 15.2% | 16.2% |
| Mexico (MX) | 17.5% | 13.6% | 16.5% | 17.5% |
| Hong Kong (HK) | 12.0% | 9.0% | 13.0% | 11.0% |
| The Netherlands (NL) | 51.0% | 40.6% | 49.0% | 50.0% |
| South Korea (KR) | 9.7% | 9.7% | 20.4% | 19.4% |
| Australia (AU) | 0.0% | 2.2% | 12.0% | 12.0% |
| United Kingdom (GB) | 14.1% | 10.6% | 9.4% | 10.6% |
| Thailand (TH) | 32.5% | 29.9% | 29.9% | 28.6% |
| South Africa (ZA) | 5.6% | 7.0% | 7.0% | 9.9% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 375 daily snapshots since 2025-04-09 |

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
