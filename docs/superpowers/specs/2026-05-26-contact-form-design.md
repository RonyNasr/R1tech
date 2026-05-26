# Contact Form Design

**Goal:** Replace the Cal.com booking button in the `#cta` section with an inline contact form.

**Architecture:** The existing `#cta` section (already linked from the nav as "Contact") becomes the contact form. The Cal.com button is removed from this section only — the FAB and other page buttons are untouched. The form submits to the same Netlify form (`name="waitlist"`) as the popup, adding a `message` textarea. Submissions with and without a message field both land in the same Netlify dashboard.

**Changes to `index.html`:**
- Subtext updated to "Send us a message — we'll get back to you within one business day."
- `.cta-actions` contents replaced with `<form id="contact-form">` containing: name input, email input, message textarea, submit button, error `<p>`, success `<div>`
- `.cta-actions` CSS updated: `align-items:stretch; flex:1; min-width:320px` so the form fills the right column
- New CSS block for `#contact-form`, `.cf-row`, `.cf-field`, `#cf-submit`, `#cf-error`, `#cf-success`
- New `<script>` block handling `#contact-form` submit: validates, POSTs URL-encoded to `/`, shows inline success, re-enables button on error
- `cta-email` "Or email us directly" line removed (already present in footer)

**Netlify:** No new form registration needed — Netlify will recognise the additional `message` field automatically on next deploy.
