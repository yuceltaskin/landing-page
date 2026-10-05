# Cinema8 landing pages: tracking setup

Each page has one inline script at the top of <head> (search for `GTM_ID=''`).

## To do for the dev team
1. Set `GTM_ID='GTM-XXXXXXX'` on all 5 pages.
2. Set `HS_ID='1234567'` (HubSpot portal ID) if HubSpot tracking is wanted.
3. Rebuild/upload the HTML files.

## dataLayer events
- `lp_view` on page load
- `signup_click`, `demo_click`, `outbound_click` on any cinema8.com link

Fields on every event: `lp_id`, `lp_variant`, `lp_experiment`. Click events add `cta_text`, `cta_location` (section id), `cta_plan` (starter / pro / pro_plus / free).

## A/B test
- vimeo-alternative-1.html → lp_experiment=vimeo-alternative, lp_variant=a
- vimeo-alternative-2.html → lp_experiment=vimeo-alternative, lp_variant=b
- `?variant=xyz` in the URL overrides the variant.

## Link decoration
On click, cinema8.com links get the visitor's utm_*, gclid, gbraid, wbraid plus lp_id and lp_variant appended, so sign-ups can be attributed to a page and variant. The signup app should store these on the account.

## Signup schema
/signup?licence-prev=smart_{starter|pro|pro_plus}&payment-plan=annual&trial=1
Free CTAs go to /signup.
