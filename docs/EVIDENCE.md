# Evidence and limitations

## Verification snapshot

The source product was checked locally on 10 August 2026. This public case study records the outcome without publishing private source code, environment values, production data, or access credentials.

| Claim | Evidence | Interpretation |
| --- | --- | --- |
| Core TypeScript behavior is covered by automated tests | 194 of 194 tests passed | A dated local test result, not production reliability |
| The source is type-safe and linted | TypeScript and source ESLint checks passed | Local static checks |
| The application builds | Next.js production build completed and generated 85 static pages | Build used command-local non-production values |
| Public flows work in two browser contexts | 8 of 8 Playwright journeys passed in Chromium and iPhone WebKit | Public login, recovery, accessibility, redirects, and association-file checks |
| The iOS shell compiles | Unsigned Debug and Release simulator builds passed with Xcode 26.6 and the iOS 26.5 SDK | Not a signed device build or App Store approval |
| The dependency audit was clean | 0 known vulnerabilities at moderate severity or above | A point-in-time package audit, not a security guarantee |
| Selected security boundaries have negative tests | Redirect, SSRF, replay, privacy, parser, and notification-eligibility tests | Coverage of defined cases, not exhaustive security validation |

## Product media

The screenshots and walkthrough were captured from the real application running in iOS Simulator. The authenticated session belongs to a dedicated demo account and all balances, names, holdings, transactions, circles, and messages shown are synthetic.

Product media demonstrates interface behavior and product scope. It does not demonstrate active customers, real investment activity, production scale, or investment returns.

## Open gates

- No App Store publication is claimed.
- Signed-device, TestFlight, OAuth, APNs, universal-link, and deletion acceptance remain separate gates.
- One observed launch time is not a p95 measurement.
- Production reliability and cost targets require sustained observation and are not reported as achieved.
- User adoption, revenue, retention, and investment outcomes have not been demonstrated.

## Claim rule

Every number in the public README is paired with its scope. A local check is described as local; a simulator build is described as unsigned; a synthetic product demonstration is described as synthetic.
