# Samsung IAP setup for Weather World

Package: `app.weather.usa.forecast.world26`

Seller Portal Content ID: `000009331844`

Support: `ahmetefeerdal3@gmail.com`

Remote config: https://github.com/metosapps/weather-ceircle-world26-config

## Registered catalog

The following four products were created and confirmed Active in this app's Samsung Seller Portal record on 2026-10-16. These USD prices were approved by the owner; Galaxy Store supplies the localized price and final purchase terms shown in the app.

| Benefit | Samsung product type | Billing period | Product ID | Base USD price | Status |
| --- | --- | --- | --- | --- | --- |
| Remove ads weekly | Subscription | 1 week | `world26_pro_weekly` | $0.99 | Active |
| Remove ads monthly | Subscription | 1 month | `world26_pro_monthly` | $1.99 | Active |
| Remove ads yearly | Subscription | 1 year | `world26_pro_yearly` | $9.99 | Active |
| Remove ads permanently | Item (nonconsumable use) | One-time | `world26_pro_lifetime` | $19.99 | Active |

Subscriptions have no free trial, introductory offer or grace period configured; start/end dates are blank. The app acknowledges lifetime purchases and never consumes them. Do not sell that ID as an unrelated consumable through another client.

## Remote configuration

Config 16 (`2026-10-16.world26.16`) connects these exact IDs. The three subscriptions use `type: subscription`; the lifetime item uses `type: lifetime`. All four entries have `enabled: true`, `iap.enabled` is true, and `kill_switches.iap_enabled` remains true. Catalog titles, localized prices and subscription periods come from Samsung rather than this JSON. No APK rebuild is needed to connect these IDs to the existing v28 billing implementation.

Ads are independent: `ads.enabled` remains true for QA, while `ads.production_enabled` remains false. Ad IDs, placements, pacing and all unrelated config are unchanged.

For later catalog changes, edit `config.json`, increase `config_version`, change `revision`, run `python3 validate.py config.json`, and publish. Keep retired product IDs configured with `enabled: false` so existing purchases remain recognizable and restorable. To stop new purchases, publish a higher config version with `iap.enabled: false`; do not roll back the config version.

## Validation still required

Use Samsung's licensed tester setup with the Galaxy Store-installed release. QA is fixed TEST mode; Beta and production builds use PRODUCTION mode. Do not assume an unlicensed production checkout is free.

Verify all four store-supplied titles/prices/periods, cancelled checkout, completed purchase, receipt verification, restart, same-account Restore, subscription expiry/cancellation and all-format ad removal. Active products and published configuration do not establish successful checkout, paid entitlement, Restore, app approval or publication.

A network or Samsung error keeps the last verified purchase. An authoritative successful ownership result can revoke a missing purchase. TEST purchases cannot grant production Premium. This client-only implementation is not a server entitlement service; no refund webhook or backend account sync is claimed.

The v28 release is signed with the owner's selected Android release keystore. Keep that signing identity for future app updates. The separate QA build retains its local QA signer and cannot replace the store release identity.

## Official references

- https://developer.samsung.com/iap/release-note.html
- https://developer.samsung.com/iap/programming-guide.html
- https://developer.samsung.com/iap/programming-guide/iap-helper-programming.html
- https://developer.samsung.com/iap/programming-guide/samsung-iap-server-api.html
- https://developer.samsung.com/iap/test-guide/prepare-to-test.html
