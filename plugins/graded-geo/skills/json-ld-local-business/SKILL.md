---
name: json-ld-local-business
description: Add or fix LocalBusiness (or a subtype like Plumber, Dentist, Attorney) JSON-LD on the homepage and contact page using only facts the site already states. Use when asked "add schema", "add JSON-LD", "add LocalBusiness markup", or when the checklist reports JSON-LD missing.
---

# LocalBusiness JSON-LD

## Set expectations first

JSON-LD is hygiene. On Graded's rubric it has zero score weight, and no engine has documented
that it changes AI answers. We add it because it is the correct, machine-readable statement of
the facts — not for points. Say that in the PR. Never write that schema increases citations.

## Collect facts from the site itself

From existing pages only: legal name, street address, city, region, postal code, country,
phone, opening hours, URL, logo path, price range if stated, geo coordinates if the site shows a
map pin, `sameAs` links the footer already has. Anything not on the site: ask the owner or
leave it out. An empty field is better than a guessed one.

## Pick the type

Use the most specific schema.org subtype that is true: `Plumber`, `Dentist`, `Attorney`,
`Electrician`, `HVACBusiness`, `MedicalClinic`, `RealEstateAgent`, `Restaurant`, otherwise
`LocalBusiness`.

## Write it

One `<script type="application/ld+json">` in the `<head>` of the homepage and the contact page.
Server-rendered. Example shape:

```json
{
  "@context": "https://schema.org",
  "@type": "Plumber",
  "name": "Acme Plumbing",
  "url": "https://acmeplumbing.example/",
  "telephone": "+1-512-555-0100",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "100 Main St",
    "addressLocality": "Austin",
    "addressRegion": "TX",
    "postalCode": "78701",
    "addressCountry": "US"
  },
  "openingHoursSpecification": [
    { "@type": "OpeningHoursSpecification", "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"], "opens": "07:00", "closes": "19:00" }
  ],
  "areaServed": "Travis County, TX"
}
```

Next.js: render it from the page component with `dangerouslySetInnerHTML` on a `<script>` tag,
built from one shared `business` object so the contact page and footer cannot drift.

## Verify

- Paste the page into <https://validator.schema.org/>; zero errors.
- Re-run `retrieval_gate_checklist`: the JSON-LD row reads "present".
- Every value in the JSON appears verbatim somewhere visible on the site.

## Say in the PR

"Adds LocalBusiness JSON-LD with the name, address, phone and hours already shown on the site.
Hygiene only: zero score weight, no claimed effect on rankings or citations."

## Receipt

Append a row to `.graded/runs/<date>/03_fix.md` — fix skill, branch, PR URL, rows targeted — and
stop until the owner merges or closes. Stage contract: `skills/03_fix/CONTEXT.md`.
