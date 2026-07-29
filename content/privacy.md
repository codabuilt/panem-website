---
title: "Privacy Policy"
date: 2026-07-29
draft: false
---

Panem is a personal pantry-management app built to help people track what
food they have at home, reduce waste, and manage grocery shopping. This
policy explains what data the app collects, why, and how it's protected.

Panem is a solo, independently-built project — not a company with a data
team, not funded by advertising, and not in the business of monetizing your
information. This policy is written plainly, in that spirit.

## 1. Information We Collect

**Account information.** When you create an account, we collect your email
address and a password (stored securely, hashed — we never see or store
your password in plain text). This is handled by our authentication
provider, Supabase, on our behalf.

**Pantry and shopping data.** The food items, quantities, storage locations,
expiration dates, and shopping lists you enter are stored so the app can
show them back to you and keep them in sync across your sessions. This data
is tied to your account and is not visible to other users.

**Barcode lookups.** When you scan a product barcode, the barcode is sent to
Open Food Facts (an open, independent product database) to retrieve product
information. No personal information is included in that request.

**Usage analytics.** We collect anonymous, aggregate usage data — which
screens are visited, which features are used, and error events — to
understand how the app is used and to fix bugs. This data is linked to an
internal account ID, not to your name or email address, in our analytics
records.

**Feedback you submit.** If you use the in-app feedback button, the message
you write (along with the screen you were on and the app version) is stored
so we can review and act on it.

## 2. How We Use Your Information

We use the information above only to:

- Provide and operate the app's core features (pantry tracking, shopping
  lists, sync across app launches)
- Diagnose bugs and understand which features are and aren't working
- Respond to feedback and support requests

We do not sell your information. We do not share it with advertisers. We do
not use third-party advertising or tracking SDKs.

## 3. Who Can See Your Data

Your pantry entries and shopping lists are private to your account,
enforced at the database level (Row Level Security) — not just by the
app's interface, but by rules the database itself checks on every request.
Other users of the app cannot query or see your data.

The food product database (name, brand, barcode, nutrition info) is shared
across all users, the same way a grocery store's product catalog is shared
— it does not contain anything specific to you, only to the products
themselves.

As the developer, database-level access exists for maintaining the service
(for example, diagnosing a sync bug), but pantry contents are not reviewed,
browsed, or used for anything beyond what's described in this policy.

## 4. Where Your Data Is Stored

Your data is stored on Supabase, a hosted database provider, in United
States data centers. Data is encrypted in transit (HTTPS/TLS) and at rest.

## 5. Third-Party Services

Panem relies on a small number of third-party services to operate:

- **Supabase** — authentication, database, and file storage
- **Open Food Facts** — public product/barcode lookups (no account or
  personal data is shared with this service)
- **Apple** — App Store distribution and TestFlight beta delivery

None of these services are used for advertising, and none receive your
pantry or shopping data beyond what's needed to provide the app (i.e.,
Supabase storing it because it's our database).

## 6. Your Choices and Data Deletion

You can stop using the app and request account deletion at any time by
emailing **support@panemapp.com**. Once requested, your account and all
associated data (pantry entries, shopping lists, feedback) will be
permanently deleted from our servers within 30 days.

## 7. Children's Privacy

Panem is not directed at children under 13, and we do not knowingly collect
information from children under 13.

## 8. Changes to This Policy

If this policy changes in a meaningful way, we'll update the date above.
Continued use of the app after a change means you accept the updated
policy.

## 9. Contact

Questions about this policy or your data? Email **support@panemapp.com**.
