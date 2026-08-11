# Product decisions

## 1. Put the user problem before the feature list

The initial idea was not “another portfolio tracker.” It was a place where a private investment group could keep a shared understanding of positions, transactions, and market context without relying on screenshots or inconsistent spreadsheets.

That framing led to three core product objects:

- **portfolio:** holdings, cash, transactions, allocation, and completed trades;
- **context:** earnings, dividends, news, public activity, and market movements;
- **relationships:** friends, private circles, discussion, and selective sharing.

## 2. Treat privacy as an access contract

Financial privacy has several dimensions. A user may be comfortable showing which companies they follow but not how much money they hold. InvestCircles therefore separates identity, holdings, portfolio percentages, monetary amounts, and activity visibility.

The product design assumes the client is untrusted. Visibility is evaluated against the owner/friend/circle/stranger relationship at the data boundary rather than relying only on hidden interface elements.

## 3. Normalize transactions before calculating performance

Broker exports vary in dates, symbols, decimal formats, fees, currencies, and transaction labels. Imports are mapped to a common transaction model before they can affect cash, cost basis, holdings, rankings, or completed trades.

The acceptance criteria cover common failure modes: duplicate rows, reversals, unsupported formats, missing symbols, inconsistent signs, and transaction order.

## 4. Separate evidence from explanation

A price move near an earnings release is not automatically caused by that release. The product distinguishes:

- a reported financial event with a canonical fiscal period;
- an observed market move;
- a possible relationship between the two;
- a case where no verified catalyst has been found.

Provider variants are merged by symbol and fiscal period. If reported actual values conflict, the event is marked as disputed and is not eligible to generate a confident notification.

## 5. Design background jobs to fail safely

Scheduled jobs can be expensive or noisy when they overlap, retry unpredictably, or reprocess the same data. The worker design uses signed requests, timestamps, one-time nonces, short leases, cursors, and idempotent writes. Data-retention rules keep detailed market snapshots bounded while preserving the daily history and the financial events referenced by the product.

## 6. Share one product across web and iOS

The iOS application uses a Capacitor shell around the same authenticated Next.js product. This avoided building two independent feature sets while still requiring native-specific work around launch behavior, safe areas, permissions, privacy manifests, universal links, and build configuration.

The iOS build is a tested simulator artifact, not an App Store release.

## 7. Make AI assistance reviewable

AI coding tools accelerated implementation, debugging, testing, and documentation. Product rules and acceptance criteria were used to constrain the work. Generated changes were reviewed against observed behavior, automated checks, data contracts, and explicit limitations.

The important capability demonstrated here is not “one-shot prompting.” It is the full loop from problem definition and context, through implementation and failure analysis, to verification and a decision about what is ready to claim.
