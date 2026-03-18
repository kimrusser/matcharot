# Matcharot — GoTyme Fund Transparency Site

A live transparency website for Matcharot partners to track the GoTyme Go Save account in real time.

**Live site pulls data directly from a Google Sheet — just update the sheet and the site updates automatically.**

---

## Setup (one-time, ~15 minutes)

### Step 1 — Create the Google Sheet

1. Go to [sheets.google.com](https://sheets.google.com) and create a new spreadsheet
2. Name it: `Matcharot Fund Tracker`
3. Create **3 tabs** with these exact names:
   - `Summary`
   - `Transactions`
   - `Running Balance`

---

### Step 2 — Fill in the sheet data

#### Tab: `Summary`
| balance | total_in | total_out | interest | as_of |
|---------|----------|-----------|----------|-------|
| 1968.98 | 15007.97 | 17038.99  | 7.97     | Mar 18, 2026 |

> Row 1 = headers, Row 2 = your values. Update Row 2 whenever there's a new transaction.

---

#### Tab: `Transactions`
| date | description | note | amount | type |
|------|-------------|------|--------|------|
| Mar 18, 2026 | Funds Moved (Business Use) | Withdrawal for operations | 151.00 | OUT |
| Mar 13, 2026 | Funds Moved (Business Use) | Withdrawal for operations | 439.00 | OUT |
| Mar 02, 2026 | Funds Moved (Business Use) | Withdrawal for operations | 13468.99 | OUT |
| Mar 01, 2026 | Interest Earned — February | GoTyme Go Save interest | 7.97 | INTEREST |
| Feb 24, 2026 | Funds Added — Capital | Partner capital contribution | 5000.00 | IN |
| Feb 23, 2026 | Funds Moved (Business Use) | Withdrawal for operations | 3980.00 | OUT |
| Feb 21, 2026 | Funds Added — Capital | Partner capital contribution | 5000.00 | IN |
| Feb 21, 2026 | Funds Added — Capital | Partner capital contribution | 5000.00 | IN |
| Feb 21, 2026 | Funds Added — Capital | Partner capital contribution (3rd) | 7.97 | IN |

> **Type** must be one of: `IN`, `OUT`, or `INTEREST`
> Add new rows at the bottom as new transactions happen. Most recent first is recommended.

---

#### Tab: `Running Balance`
| date | event | change | balance |
|------|-------|--------|---------|
| Feb 21, 2026 | 3 × Capital Contributions | 15000 | 15000.00 |
| Feb 23, 2026 | Withdrawal — Operations | -3980 | 11020.00 |
| Feb 24, 2026 | Capital Contribution | 5000 | 16020.00 |
| Mar 01, 2026 | Interest — February | 7.97 | 16027.97 |
| Mar 02, 2026 | Withdrawal — Operations | -13468.99 | 2558.98 |
| Mar 13, 2026 | Withdrawal — Operations | -439 | 2119.98 |
| Mar 18, 2026 | Withdrawal — Operations | -151 | 1968.98 |

> Negative `change` values = withdrawals. Positive = deposits.

---

### Step 3 — Publish the Sheet

1. In your Google Sheet, go to **File → Share → Publish to web**
2. Select **Entire Document**
3. Change format to **Comma-separated values (.csv)**
4. Click **Publish** → confirm
5. Close the dialog (you don't need the published URL)

---

### Step 4 — Get your Sheet ID

Your Sheet URL looks like:
```
https://docs.google.com/spreadsheets/d/XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX/edit
```
Copy the long string between `/d/` and `/edit` — that's your **Sheet ID**.

---

### Step 5 — Update index.html

Open `index.html` and find this line near the top of the `<script>`:

```js
const SHEET_ID = 'YOUR_SHEET_ID_HERE';
```

Replace `YOUR_SHEET_ID_HERE` with your actual Sheet ID. Save the file.

---

### Step 6 — Deploy to GitHub Pages

1. Go to [github.com](https://github.com) and create a new repository
   - Name it something like `matcharot-fund`
   - Set it to **Public**
2. Upload `index.html` to the repository
3. Go to **Settings → Pages**
4. Under **Source**, select `main` branch → `/ (root)` → Save
5. GitHub will give you a URL like: `https://yourusername.github.io/matcharot-fund`

Share that link with Aira, Nicka, and Jan. 🎉

---

## Updating the site going forward

You **only need to update the Google Sheet**. No re-deploying needed.

When there's a new GoTyme transaction:
1. Add a row to the `Transactions` tab
2. Add a row to the `Running Balance` tab
3. Update the `Summary` tab (Row 2) with the new balance, totals, and date

The website refreshes automatically — your partners will see the latest data the next time they open the link.

---

## Files

- `index.html` — the live website
- `README.md` — this setup guide
