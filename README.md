# Fantastic Floors — Card Template

Company-locked template for Fantastic Floors digital business cards. **Only person-level fields are tokenized.** Company assets (logo, office phone, address, tagline, brand copy, accent colors) are baked in.

## How to spawn a new FF employee card

```bash
gh repo create sharkitect-cards/{person-slug} \
  --template sharkitect-cards/_template-fantastic-floors \
  --public
```

Then fill the 4 person tokens in the spawned repo's `index.html` and `manifest.json`.

## Tokens

Person-level placeholders that need to be replaced per-card:

| Token | Example (Juan) | Notes |
|---|---|---|
| `{{PERSON_FULL_NAME}}` | `Juan Bernal` | Display + meta + vCard FN |
| `{{PERSON_FIRST_NAME}}` | `Juan` | vCard N field |
| `{{PERSON_LAST_NAME}}` | `Bernal` | vCard N field |
| `{{PERSON_TITLE}}` | `Owner` | Display + meta + vCard TITLE |
| `{{PERSON_PHONE_DISPLAY}}` | `(913) 953-9941` | Span + vCard TEL |
| `{{PERSON_PHONE_E164}}` | `+19139539941` | `tel:` href |
| `{{PERSON_EMAIL}}` | `juan@fantasticfloorskc.com` | `mailto:` href + span + vCard EMAIL |
| `{{PERSON_PHOTO_B64}}` | (optional) | JPEG base64 headshot — leave empty if none |

That's it. Four inputs (name, title, phone, email) produce all seven display tokens. Photo is optional.

## What is NOT a token (baked in, do not change)

- Company name: `Fantastic Floors`
- Office phone: `(913) 399-5437`
- Office address: `1370 N Winchester St, Olathe, KS, 66061`
- Website: `https://www.fantasticfloorsks.com`
- Tagline: `We're All You Need`
- Descriptor: `Olathe's Preferred Family-Owned Flooring and Remodeling Partner Since 2017`
- Logo: `logo.svg` (512×512 square)

If any of those change, update this template — the change propagates to every FF card spawned afterward.

## Files

- `index.html` — card HTML with 8 person tokens
- `logo.svg` — FF logo, 512×512 square (canonical company logo)
- `manifest.json` — PWA manifest with 2 person tokens (name, description); `short_name` is `"My Card"` per the owner-phone-perspective rule
- `README.md` — this file

## Do not serve this repo directly

This repo is the template. GitHub Pages is NOT enabled on it — it would render with literal `{{TOKENS}}` visible to users. Always spawn via `--template`, fill the tokens, enable Pages on the spawned repo.
