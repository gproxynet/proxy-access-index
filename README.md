# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-22 06:40 UTC · **History:** 361 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 24.8% |
| YouTube | 17.1% |
| LinkedIn | 16.5% |
| TikTok | 16.4% |
| X (Twitter) | 15.7% |
| Qzone | 15.7% |
| Instagram | 13.8% |
| VK | 13.5% |
| OK.ru | 11.3% |
| Telegram | 10.1% |
| Reddit | 8.1% |
| Yandex | 6.2% |
| Mail.ru | 5.9% |
| Avito | 4.3% |
| Facebook | 0.6% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 0.6% of live proxies get through
- **Avito** — 4.3% of live proxies get through
- **Mail.ru** — 5.9% of live proxies get through
- **Yandex** — 6.2% of live proxies get through
- **Reddit** — 8.1% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 28.7% | 17.5% | 15.2% | 16.5% | 17.6% | 16.2% |
| hosting | 19.7% | 16.7% | 12.1% | 16.3% | 15.0% | 15.2% |
| mobile | 25.9% | 11.1% | 7.4% | 14.8% | 22.2% | 11.1% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 25.8% | 11.4% | 14.0% | 11.6% |
| Indonesia (ID) | 16.1% | 21.3% | 23.4% | 26.2% |
| Türkiye (TR) | 82.0% | 4.0% | 5.3% | 2.7% |
| China (CN) | 2.8% | 1.4% | 1.4% | 15.5% |
| India (IN) | 17.1% | 11.4% | 16.4% | 12.9% |
| Russia (RU) | 31.2% | 2.4% | 15.2% | 4.8% |
| Brazil (BR) | 44.2% | 7.1% | 8.8% | 9.7% |
| Germany (DE) | 32.3% | 21.2% | 20.2% | 24.2% |
| Japan (JP) | 13.3% | 3.6% | 18.1% | 7.2% |
| Singapore (SG) | 37.7% | 31.2% | 28.6% | 32.5% |
| France (FR) | 38.4% | 28.8% | 27.4% | 32.9% |
| Hong Kong (HK) | 23.5% | 11.8% | 20.6% | 16.2% |
| Canada (CA) | 10.8% | 4.6% | 7.7% | 7.7% |
| South Korea (KR) | 13.1% | 13.1% | 13.1% | 13.1% |
| The Netherlands (NL) | 26.7% | 25.0% | 23.3% | 25.0% |
| Mexico (MX) | 16.9% | 27.1% | 27.1% | 27.1% |
| Vietnam (VN) | 28.6% | 28.6% | 17.9% | 21.4% |
| United Kingdom (GB) | 24.1% | 11.1% | 18.5% | 16.7% |
| Philippines (PH) | 26.4% | 17.0% | 22.6% | 20.8% |
| Colombia (CO) | 20.0% | 18.0% | 26.0% | 24.0% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 361 daily snapshots since 2025-04-09 |

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
