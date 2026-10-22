# The Canopy Labs — website

Static placeholder site for [thecanopylabs.in](https://thecanopylabs.in), hosted on Firebase Hosting.

## Structure

```
public/
├── index.html     # landing page
├── 404.html       # not-found page
├── styles.css
├── favicon.svg
└── sellers.json   # IAB sellers.json, served at /sellers.json
```

No build step: everything in `public/` is deployed as-is.

## sellers.json

Served at `https://thecanopylabs.in/sellers.json`, the same way the pixelverge site serves its file.
To add a seller, append an entry to the `sellers` array:

```json
{
  "seller_id": "123456",
  "name": "Example Publisher",
  "domain": "example.com",
  "seller_type": "PUBLISHER"
}
```

`seller_type` is one of `PUBLISHER`, `INTERMEDIARY` or `BOTH`. `contact_email` / `contact_address`
are optional top-level fields. Check that the JSON is valid before pushing, because a broken file breaks
buyer crawlers.

## Local preview

```bash
firebase emulators:start --only hosting   # http://localhost:5000
```

## Deploy

Pushing to `main` deploys automatically via `.github/workflows/firebase-hosting-deploy.yml`.
To deploy manually:

```bash
firebase deploy --only hosting
```
