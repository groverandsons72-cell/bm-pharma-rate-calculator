# B&M Pharma Rate & Order Calculator — No Database Version

## How this version works
- No Supabase, SQL, Firebase, or external database is used.
- The 27 products from the supplied `rate list(1).xlsx` are embedded directly in `index.html`.
- The visible rate-list timestamp is `17 October 2026, 6:05 pm IST`, taken from the workbook's generated date.
- MRs can search products, enter quantities, see line values and the order total, export the current rates, and print.
- Monthly target and quantities are saved only in each MR's own browser using localStorage. The Clear monthly data button clears them.
- There is no live admin upload in this version. A new rate list must be embedded into the app files and redeployed.

## Deploy through your existing GitHub + Vercel setup
1. Back up your current calculator repository before changing it.
2. Copy `index.html` and `logo.png` from this folder into the root of the repository connected to the calculator's Vercel project. Replace the old versions.
3. Do not delete unrelated project files. This version is a static HTML page and does not need Supabase credentials or `schema.sql`.
4. Commit and push the changes. Vercel should deploy automatically if the repository integration is configured.
5. Open the public URL in a private/incognito window and check rates, target tracking, clearing monthly data, and the last-updated date.

## How to update rates next time
1. Provide the latest Excel rate list.
2. Update the embedded `seedProducts` array and `RATE_LIST_UPDATED` value in `index.html` using the product columns `Item Name`, `PACK`, `GST`, `S.RATE`, and `MRP`.
3. Replace `index.html` in the connected GitHub repository and push it to trigger a new Vercel deployment.

## Important limitation
The admin page cannot upload rates to the live site in this no-database architecture. A static public website cannot securely accept an Excel upload and distribute it to every visitor without some shared server-side storage or a deployment step. The MR target/quantity data stays local to each browser and is not shared between MRs.
