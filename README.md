# AntiNude

Privacy-first, light-themed image protection experiment. Open the GitHub Pages site, upload a JPG/PNG/WebP (20 MB / 22 MP maximum), adjust intensity, apply protection and download the PNG plus verification files.

All processing runs locally in your browser.

## Three experimental layers

1. Refusal policy in PNG text metadata and three redundant blue-channel LSB copies.
2. Adjustable seeded RGB pixel perturbations. **These are not optimized adversarial attacks and are not proven to resist AI edits.**
3. SHA-256 digest and detached ECDSA P-256 signed manifest, with a fresh public verification key per export. This does not prove creator identity or implement C2PA.

**No protection is guaranteed.** AI tools can ignore policies, remove metadata and bypass noise. Resizing, cropping and JPEG recompression can destroy hidden LSB text.

## Deploy

The GitHub Actions workflow at `.github/workflows/pages.yml` deploys the root site. If needed, configure repository **Settings → Pages → Build and deployment → Source: GitHub Actions**.

## Verify

Compare the downloaded PNG SHA-256 with `record.sha256` in the manifest. Verify `signature_base64` over the UTF-8 bytes of `JSON.stringify(record)` with the supplied public JWK and ECDSA P-256 SHA-256. A self-generated public key is not proof of identity.
