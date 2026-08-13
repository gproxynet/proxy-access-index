# Proxy Access Index

What share of a live, continuously-rechecked proxy pool still gets through to each major website — measured every day, published as rates.

**Updated:** 2026-08-13 06:40 UTC · **History:** 352 daily snapshots since 2025-04-09

Most proxy lists tell you an IP is *alive*. That is the easy part. What decides whether a scrape or an automation run works is whether the IP is still *accepted* by the site you are targeting. This dataset publishes that second number, so you can size a job before paying for it.

## Pass rate by target site

| Target site | Share of live pool that gets through |
|---|---:|
| Google | 26.0% |
| YouTube | 17.8% |
| Qzone | 17.3% |
| TikTok | 17.0% |
| LinkedIn | 16.4% |
| X (Twitter) | 15.7% |
| VK | 15.1% |
| Instagram | 15.0% |
| OK.ru | 14.4% |
| Telegram | 11.5% |
| Reddit | 9.6% |
| Yandex | 7.5% |
| Mail.ru | 7.4% |
| Avito | 4.6% |
| Facebook | 2.0% |

## Hardest targets right now

These run the strictest proxy detection — datacenter IPs mostly bounce, so plan on residential or mobile:

- **Facebook** — 2.0% of live proxies get through
- **Avito** — 4.6% of live proxies get through
- **Mail.ru** — 7.4% of live proxies get through
- **Yandex** — 7.5% of live proxies get through
- **Reddit** — 9.6% of live proxies get through

## Datacenter vs residential vs mobile

The single biggest factor in whether a proxy survives a check is what kind of network it sits on:

| Network type | Google | YouTube | Instagram | TikTok | LinkedIn | X (Twitter) |
|---|---:|---:|---:|---:|---:|---:|
| residential | 26.6% | 14.2% | 11.8% | 13.2% | 12.8% | 11.8% |
| hosting | 24.5% | 21.7% | 18.2% | 21.0% | 20.1% | 20.0% |
| mobile | 47.7% | 36.4% | 38.6% | 43.2% | 43.2% | 31.8% |

All 15 targets: [`by-network-type.csv`](by-network-type.csv)

## By country

Pass rates differ by where the IP is. Countries are listed only where the sample is large enough for the rate to be meaningful:

| Country | Google | Instagram | TikTok | LinkedIn |
|---|---:|---:|---:|---:|
| United States (US) | 23.3% | 9.9% | 10.6% | 9.9% |
| Indonesia (ID) | 17.4% | 17.7% | 18.0% | 17.7% |
| Türkiye (TR) | 75.3% | 5.7% | 6.9% | 6.3% |
| Russia (RU) | 41.8% | 1.3% | 25.3% | 8.9% |
| China (CN) | 5.7% | 0.7% | 0.7% | 7.1% |
| Germany (DE) | 28.0% | 20.8% | 19.2% | 20.0% |
| India (IN) | 20.5% | 14.8% | 22.1% | 19.7% |
| Brazil (BR) | 43.3% | 6.7% | 10.8% | 9.2% |
| France (FR) | 28.4% | 25.5% | 22.5% | 25.5% |
| Singapore (SG) | 40.0% | 30.5% | 35.8% | 32.6% |
| Switzerland (CH) | 87.2% | 86.0% | 88.4% | 88.4% |
| Hong Kong (HK) | 8.4% | 10.8% | 7.2% | 13.3% |
| The Netherlands (NL) | 30.8% | 29.5% | 26.9% | 33.3% |
| Mexico (MX) | 7.8% | 10.4% | 10.4% | 9.1% |
| South Korea (KR) | 10.5% | 6.6% | 11.8% | 6.6% |
| Japan (JP) | 16.7% | 8.3% | 9.7% | 12.5% |
| Colombia (CO) | 14.5% | 7.2% | 10.1% | 8.7% |
| Vietnam (VN) | 42.0% | 37.7% | 27.5% | 37.7% |
| Philippines (PH) | 18.3% | 18.3% | 15.0% | 16.7% |
| Canada (CA) | 13.0% | 5.6% | 7.4% | 9.3% |

All 15 targets × 40 countries: [`by-country.csv`](by-country.csv)

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | today's pass rates, structured |
| [`site-access-latest.csv`](site-access-latest.csv) | pass rate per target site |
| [`by-country.csv`](by-country.csv) | pass rate per site, per country |
| [`by-network-type.csv`](by-network-type.csv) | residential vs mobile vs datacenter |
| [`history.csv`](history.csv) | 352 daily snapshots since 2025-04-09 |

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
