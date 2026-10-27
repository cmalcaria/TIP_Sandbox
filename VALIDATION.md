# Café Enchancia — Expected Results

Calculated independently from the supplied CSVs. One row is one order. Net sales include completed orders only, subtract whole-order discounts, apply fixed PHP FX rates and round per order.

| Store | All orders | Completed | Cancelled | Units sold | Net sales PHP |
|---|---:|---:|---:|---:|---:|
| KR_SEOUL | 3656 | 3514 | 142 | 6965 | 2146053.00 |
| PH_LUZON | 3732 | 3586 | 146 | 7148 | 1057550.00 |
| PH_MIND | 3693 | 3544 | 149 | 7095 | 1051804.50 |
| PH_VIS | 3722 | 3572 | 150 | 7211 | 1069012.00 |
| US_NJ | 3673 | 3519 | 154 | 7021 | 3771558.00 |
| US_NY | 3645 | 3472 | 173 | 6958 | 3714090.00 |
| US_QUEENS | 3703 | 3540 | 163 | 7094 | 3807960.00 |

**All seven stores:** 25,824 total orders; 24,747 completed; 1,077 cancelled; 49,492 units sold; **PHP 16,618,027.50** net sales. Totals cover the entire supplied archive, including partial New York boundary dates.

## Acceptance evidence

- Bronze: expected 14 source columns plus source_file, source_path and ingested_at_utc; all source fields are strings; values and row multiplicities match the selected CSV.
- Silver: count matches that store's Bronze count; transaction IDs are unique; types, required fields, local dates, statuses and source currency/timezone pass validation. Local amounts are retained. UTC time, report_date_ny and net_sales_php are derived.
- FX examples before discounts: PHP 165 → PHP 165; USD 10 → PHP 600; KRW 7,500 → PHP 300. Currency conversion and timezone conversion are separate operations.
- Time examples: 2026-10-19 00:00 Seoul → 2026-10-18 15:00 UTC → New York date 2026-10-18. The same Manila wall clock → 2026-10-18 16:00 UTC → New York date 2026-10-18.
- Gold: one row per store_id + transaction_id, retaining every selected Silver order. Cancellation net_sales_php, units_sold and completed_orders are zero. cancelled_orders is one for cancellations.
- Gold summary totals reconcile to eligible Silver records. Only converted PHP amounts can be consolidated across countries.
- A same-batch rerun preserves counts and business totals. The full ALL result remains 25,824 rows. A group running one store uses its own row count above.
- Single-store Gold refresh: record the other stores' counts and totals before and after; they should not change.

## Validation limits

Local checks cover notebook Python syntax, fixture counts, source contracts, independent calculations, package references and presentation rendering. They do not prove Databricks access, compute compatibility, permissions or Delta overwrite behavior. Run all three notebooks and the rerun checks in the workshop workspace before class. Notebook outputs have been cleared to avoid presenting old runs as proof of this revision.
