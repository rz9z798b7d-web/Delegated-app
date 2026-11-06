# Production integration map

## Identity — Persona
Mobile app calls Supabase Edge Function.
Edge Function creates/returns a provider inquiry/session.
User completes provider-hosted verification.
Webhook updates `identity_records`.
Store provider subject/status/risk metadata; avoid storing raw ID documents.

## Background screening — Checkr
Use the hosted candidate flow when possible.
Capture required disclosures/authorizations.
Webhook receives report state.
Perform individualized review and legally required adverse-action workflow.
Do not make a blanket rule that a criminal record equals automatic job denial.

## Payments + banking — Stripe Connect
Customer payment:
customer -> Delegate checkout/payment intent -> marketplace ledger -> worker payout.

Worker banking:
worker -> Stripe-hosted Connect onboarding -> Stripe handles bank details/verification -> Delegate stores only connected-account ID/status.

Do not collect bank credentials in the Delegate mobile app.

## GPS
Use foreground location for normal job check-in.
Request background location only when genuinely needed for an active job.
Use a job-specific geofence, not continuous unnecessary tracking.
Record check-in/out coordinates and timestamps with retention limits.

## Anti-duplicate account
Create an internal immutable identity subject reference.
Use identity provider subject + verified phone/email + device/security signals.
Never use IP address alone.
A duplicate signal should trigger review, not automatic proof.
Keep enforcement history and appeals separate from public profile data.

## Store readiness
- Privacy Policy URL
- Terms of Service
- Community/Safety Policies
- Account deletion flow
- Support contact
- Accurate App Store privacy disclosures
- Accurate Google Play Data Safety disclosures
- Location permission explanations
- Payment and background-check disclosures
- Age/eligibility rules
- Content moderation/reporting flow
- Test accounts for review
- Screenshots, app icon, description and categories
