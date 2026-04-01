# Pending Data Records

Data gaps identified during the 2026-03-28 audit that require manual input — documents not found on Google Drive or in any automated data source.

---

## Missing FD Maturity Dates

| Owner | Institution | Principal (INR) | Interest Rate | Invested | Maturity Date | Status |
|-------|------------|----------------|---------------|----------|---------------|--------|
| Papa | HDFC | 5,00,000 | 7.10% | ~Sep 2025 | **UNKNOWN** | Need deposit receipt |
| Mom | HDFC | 5,00,000 | 6.50% | ~Sep 2025 | **UNKNOWN** | Need deposit receipt |
| Me | HDFC | 15,00,000 | 7.40% | Unknown | **UNKNOWN** | Need deposit receipt |
| Papa | IndusInd | 13,00,000 | 7.75% | ~Sep 2025 | **UNKNOWN** | Need deposit receipt |
| Mom | IndusInd | 50,00,000 | 7.75% | ~Sep 2025 | **UNKNOWN** | Need deposit receipt |

**Source:** Wealth Strategy spreadsheet (PAPA, MOM, ME tabs). No PDFs found in Google Drive `Fixed Deposits` folder — only SBI and Axis FDs had uploaded receipts.

**Action:** Upload HDFC and IndusInd FD deposit advices to Google Drive > Fixed Deposits folder, then update the `fixed_deposits` table:
```sql
UPDATE fixed_deposits SET maturity_date = 'YYYY-MM-DD'
WHERE institution_name ILIKE '%HDFC%' AND principal = XXXXX;
```

---

## Verified FDs (already in migration)

| Owner | Institution | Principal (INR) | Rate | Maturity | Source |
|-------|------------|----------------|------|----------|--------|
| Papa | SBI FD | 5,00,000 | 7.05% | 2035-09-01 | PDF (Acc 44427242053) |
| Papa | Axis Bank | 3,50,000 | 7.35% | 2035-09-08 | PDF (Acc 925040097415552) |
| Papa | Axis Bank | 1,50,000 | 7.35% | 2035-10-01 | PDF (Acc 925040101291163) |
| Papa | SBI SCSS | 30,00,000 | 8.20% | 2030-09-01 | Spreadsheet (60 months) |
| Papa | RBI Bond | 50,00,000 | 8.05% | 2032-09-01 | Spreadsheet (84 months) |
| Mom+Papa | Post Office MIS x2 | 9,00,000 ea | 7.40% | 2030-09-01 | Spreadsheet (60 months) |
| Mom | Post Office NSC x5 | ~50,00,000 | 7.70% | 2030-09-01 | Spreadsheet (60 months) |

---

## Other Pending Items

### ~~Daemon Not Running (Gap 4)~~ RESOLVED 2026-03-29
- Ran `sync-now` locally: 41 prices fetched, 127 IBKR prices updated, 3 FX rates
- PPFD (EUR 57.34) and SNDE (EUR 3.13) now pricing for first time
- Still need to restart daemon on server for ongoing refresh

### ~~March 2026 IBKR Transactions (Gap 12)~~ PARTIALLY RESOLVED
- IBKR Flex sync ran: 183 transactions (all duplicates = already imported)
- Revolut/Trading212 still need manual CSV export + import
- Kite sync needs credentials in local `.env` (only on server)

### March 2026 Payslip Missing (Gap 15)
- **Action:** Enter when available (end of month)

---

*Last updated: 2026-03-29*
