TKP AgencyPro — Vercel Account Deletion Route Patch

This is a PATCH for the existing Vercel project, not a replacement for the whole site.

Copy these directories into the ROOT of the existing Vercel project, merging/overwriting only matching files:
- delete-account/index.html
- delete-account/verify-email/index.html

DO NOT overwrite or delete the existing root index.html, verify-email/, reset-password/, Flutter build files, vercel.json, or any other routes/configuration.

Public Account deletion URL (same domain; no separate domain purchase is needed):
https://www.tkpagencypro.com/delete-account/

Supabase Auth > URL Configuration must allow this callback:
https://www.tkpagencypro.com/delete-account/verify-email/

Keep the existing signup verification and password reset redirect URLs and email templates unchanged. The Magic Link template should use {{ .ConfirmationURL }}. Do not place service_role keys or secrets in this static deployment.

After deployment, test with a disposable account: request link, open the latest email, verify callback, return to /delete-account/, submit final request. Do not test with a production account.
