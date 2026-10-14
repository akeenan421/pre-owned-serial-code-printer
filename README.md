# Pre-owned label printer

Prints barcode labels (Code 128) for pre-owned shoes, straight from the product Google Sheet.
Pick items by tab, search, or paste/scan serial codes (ranges work: `PO21-010 to PO21-020`),
then print to a 2.25×1.25, 2×1 or 4×6 thermal label, or an Avery 5160 sheet, or save a PDF.

## 1. Put it on GitHub Pages

1. On GitHub, create a new repository (e.g. `label-printer`).
2. Choose **Add file → Upload files**, drag in everything from this folder, and commit.
3. Go to **Settings → Pages**, set **Source** to *Deploy from a branch*, branch `main`, folder `/ (root)`, and save.
4. After a minute your printer is live at `https://<your-username>.github.io/label-printer/`.

## 2. Connect your Google Sheet (one-time)

1. Open the product sheet and choose **Extensions → Apps Script**.
2. Delete what's there, paste in the contents of `apps-script/Code.gs`, and save.
3. Click **Deploy → New deployment**, choose the gear → **Web app**.
   - Execute as: **Me**
   - Who has access: **Anyone**
4. Click **Deploy**, approve the permissions, and copy the **Web app URL** (ends in `/exec`).
5. Open your GitHub Pages site, click **Connect sheet**, and paste the URL. It's remembered on that computer.

To connect every computer automatically, put the URL in `index.html` on the line
`const DEFAULT_SCRIPT_URL = "";` and commit.

**What's shared:** the script returns only serial code, SKU, title, size, condition and list price.
Cost, minimum offer and StockX columns never leave the sheet. Anyone who has the `/exec`
URL can read those label fields, so treat it like a private link. To revoke it, go to
**Deploy → Manage deployments** and archive it.

If you edit `Code.gs` later, use **Deploy → Manage deployments → Edit → New version**,
or the old code keeps running.

## No setup option

Skip step 2 and use **Open .xlsx / .csv** instead (Google Sheets: *File → Download → Microsoft Excel*).

## Printing tips

- Print at **100% / Actual size**. Scaling to fit makes barcodes harder to scan.
- In the print dialog, pick the paper size that matches the label size you chose.
- If your browser print adds headers or margins, use **Download PDF** and print the PDF instead.
