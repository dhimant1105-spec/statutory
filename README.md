# PF Statutory – EPFO ECR Manager

A static, browser-based employee master and monthly PF contribution tracker. It can be published using GitHub Pages.

## Publish on GitHub Pages
1. Create a new GitHub repository.
2. Upload `index.html`, `styles.css`, `app.js` and this README to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**.
5. Select branch `main` and folder `/ (root)`, then Save.
6. Wait for GitHub Pages to publish the site.

## Features
- Employee master with employee code, 12-digit UAN, joining/exit dates, pension-member flag, EPF eligibility and active/inactive status.
- Add/edit employees individually or import a CSV.
- Monthly employee-wise contribution records with wage month, PF wages, pension wages, days worked, non-contributing days, filing status and filing date.
- Duplicate employee/UAN checks and duplicate employee-month contribution prevention.
- Configurable MPF, non-pension CPF, pension/EPS and EDLI rates, EPS ceiling, EDLI wage cap and admin charge rate.
- Contribution preview, monthly summaries, CSV export and JSON backup/restore.
- Data stored in the browser's local storage.

## Calculation logic implemented
- MPF = PF wages × MPF rate.
- Pension member: EPS = min(Pension wages, EPS wage ceiling) × pension rate; CPF = MPF − EPS.
- Non-pension member: CPF = PF wages × non-pension CPF rate; EPS = zero.
- EDLI = min(PF wages, EDLI wage cap) × EDLI rate.
- Admin charges = PF wages × admin charge rate.
- Amounts rounded to 2 decimal places.

## Important operational notes
- The application is a calculation and record-keeping tool. It does **not** connect to EPFO, submit ECR files, authenticate UANs, validate members against EPFO, or make payments.
- The CSV export is a review/reporting CSV, **not** an EPFO-compliant ECR upload file. Confirm the current EPFO ECR format and all statutory rules before filing.
- Default rates/ceilings are starter values only. Verify current applicability and statutory notifications before use.
- Data remains in the browser profile on the device where it was entered. Use **Backup data** regularly. Clearing browser data or changing browsers/devices can remove access to locally stored records.
- For multi-user or client production use, add a secure backend, authentication, role-based access, encrypted database, audit logs and tested EPFO-format export before relying on it operationally.

## CSV employee import
Required headers (case-insensitive): `Employee Code`, `Employee Name`, `UAN`.
Optional headers: `Joining Date`, `Date of Exit`, `Pension Member`.
For `Pension Member`, use `Yes` or `No`. Dates should be `YYYY-MM-DD`.
