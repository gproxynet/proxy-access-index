# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-28 06:40 UTC · **History:** 367 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 25.7% |
| TikTok | 17.4% |
| YouTube | 17.3% |
| Qzone | 17.2% |
| X (Twitter) | 16.5% |
| LinkedIn | 16.1% |
| VK | 14.8% |
| Instagram | 13.7% |
| OK.ru | 12.9% |
| Telegram | 10.3% |
| Reddit | 8.9% |
| Yandex | 7.5% |
| Mail.ru | 6.8% |
| Avito | 4.5% |
| Facebook | 0.5% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.5% of live proxies get through
- **Avito** — 4.5% of live proxies get through
- **Mail.ru** — 6.8% of live proxies get through
- **Yandex** — 7.5% of live proxies get through
- **Reddit** — 8.9% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 30.9% | 17.7% | 15.7% | 17.0% | 16.4% | 16.1% |
| hosting | 19.6% | 16.7% | 11.5% | 17.8% | 15.7% | 17.0% |
| mobile | 29.6% | 22.2% | 11.1% | 22.2% | 18.5% | 14.8% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 24.3% | 9.5% | 13.6% | 9.8% |
| Indonesia (ID) | 16.8% | 14.9% | 19.0% | 16.5% |
| Türkiye (TR) | 78.2% | 4.2% | 2.8% | 3.5% |
| China (CN) | 2.1% | 0.7% | 0.7% | 14.2% |
| Russia (RU) | 36.7% | 1.4% | 20.1% | 5.8% |
| India (IN) | 29.5% | 23.3% | 20.9% | 22.5% |
| Germany (DE) | 28.6% | 23.0% | 25.4% | 23.0% |
| Brazil (BR) | 47.1% | 9.8% | 10.8% | 8.8% |
| Singapore (SG) | 38.5% | 22.9% | 31.2% | 31.2% |
| Japan (JP) | 18.8% | 5.2% | 15.6% | 10.4% |
| France (FR) | 28.9% | 24.4% | 21.1% | 26.7% |
| The Netherlands (NL) | 36.7% | 26.6% | 36.7% | 32.9% |
| Canada (CA) | 5.3% | 2.7% | 16.0% | 10.7% |
| Hong Kong (HK) | 18.7% | 13.3% | 22.7% | 20.0% |
| South Korea (KR) | 10.4% | 11.9% | 17.9% | 17.9% |
| Vietnam (VN) | 34.8% | 28.8% | 27.3% | 30.3% |
| Thailand (TH) | 37.7% | 34.4% | 31.1% | 34.4% |
| United Kingdom (GB) | 20.0% | 13.3% | 18.3% | 20.0% |
| Mexico (MX) | 16.9% | 15.3% | 15.3% | 18.6% |
| Philippines (PH) | 20.7% | 17.2% | 17.2% | 15.5% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 367 daily snapshots since 2025-04-09 |

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
