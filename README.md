# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-09-04 06:40 UTC · **History:** 374 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 27.4% |
| Qzone | 23.1% |
| LinkedIn | 22.7% |
| X (Twitter) | 22.7% |
| TikTok | 21.5% |
| YouTube | 21.0% |
| VK | 19.4% |
| Instagram | 19.1% |
| OK.ru | 17.7% |
| Telegram | 14.7% |
| Reddit | 13.3% |
| Yandex | 8.9% |
| Mail.ru | 8.5% |
| Avito | 6.8% |
| Facebook | 0.1% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.1% of live proxies get through
- **Avito** — 6.8% of live proxies get through
- **Mail.ru** — 8.5% of live proxies get through
- **Yandex** — 8.9% of live proxies get through
- **Reddit** — 13.3% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| hosting | 17.1% | 16.7% | 13.0% | 16.6% | 18.6% | 18.9% |
| residential | 39.1% | 26.0% | 25.9% | 27.1% | 27.2% | 27.1% |
| mobile | 30.4% | 21.7% | 21.7% | 26.1% | 30.4% | 17.4% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 22.5% | 13.1% | 15.9% | 15.3% |
| Indonesia (ID) | 32.2% | 32.2% | 33.7% | 36.1% |
| Germany (DE) | 30.2% | 21.8% | 25.7% | 25.1% |
| Russia (RU) | 39.0% | 2.5% | 23.3% | 6.3% |
| India (IN) | 24.3% | 20.4% | 21.7% | 21.7% |
| Türkiye (TR) | 79.7% | 8.1% | 7.4% | 6.1% |
| Singapore (SG) | 31.0% | 30.3% | 33.1% | 35.9% |
| Brazil (BR) | 46.1% | 17.0% | 17.0% | 17.0% |
| China (CN) | 2.3% | 0.8% | 0.8% | 24.8% |
| France (FR) | 25.0% | 25.8% | 22.7% | 28.1% |
| Mexico (MX) | 17.9% | 15.2% | 17.0% | 17.9% |
| Japan (JP) | 15.2% | 7.1% | 15.2% | 20.5% |
| Canada (CA) | 11.8% | 10.0% | 11.8% | 15.5% |
| Hong Kong (HK) | 11.1% | 10.1% | 10.1% | 11.1% |
| South Korea (KR) | 14.3% | 11.2% | 20.4% | 20.4% |
| Australia (AU) | 2.2% | 2.2% | 9.0% | 7.9% |
| The Netherlands (NL) | 48.9% | 38.6% | 46.6% | 47.7% |
| United Kingdom (GB) | 12.3% | 9.9% | 11.1% | 9.9% |
| South Africa (ZA) | 4.9% | 6.2% | 9.9% | 12.3% |
| Thailand (TH) | 33.3% | 30.7% | 29.3% | 30.7% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 374 daily snapshots since 2025-04-09 |

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
