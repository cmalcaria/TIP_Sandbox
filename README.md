# Café Enchancia — Day 1 as a Data Engineer

## Start here

1. Read `Discovery Call/Discovery_Call.md`. The instructor uses `Discovery Call/Facilitator_Notes.md`.
2. Use the updated presentation in `Presentation/`.
3. The instructor provisions the target schemas and Spark compute, grants access, and uploads source CSVs to the shared source Volumes.
4. Each group imports the three notebooks from `Sample Code/`. Set **store** and **target_schema** as assigned below. Run Bronze, Silver and Gold in order.
5. Capture acceptance evidence using `VALIDATION.md`, then rerun the same batch to confirm stable business counts and totals.

## Source staging

Use catalog `ws_tip_demo`. Create the `korea`, `philippines` and `usa` Volumes under source schema `tip_demo_schema` before uploading files. Bronze's **source_path** widget is the BASE `/Volumes/ws_tip_demo/tip_demo_schema`; it adds the country Volume name automatically.

- `KR_SEOUL_*.csv` goes into `/Volumes/ws_tip_demo/tip_demo_schema/korea`.
- All `PH_*.csv` go into `/Volumes/ws_tip_demo/tip_demo_schema/philippines`.
- All `US_*.csv` go into `/Volumes/ws_tip_demo/tip_demo_schema/usa`.
- `Product_Menu.csv` is reference-only and is not an ingestion input.

Provision group schemas and permissions before class. Participants need source catalog/schema usage and READ VOLUME; target catalog/schema usage, CREATE TABLE, and permission to read/write their own tables. Check access using an actual participant account. No direct POS, email or network-drive access is needed for the lab.

## Group assignments

These assignments match the ten-group agenda; repeated stores are intentional and use separate target schemas.

| Group | store widget | target_schema widget |
|---|---|---|
| 01 | PH_LUZON | tip_group_01 |
| 02 | PH_VIS | tip_group_02 |
| 03 | PH_MIND | tip_group_03 |
| 04 | US_NY | tip_group_04 |
| 05 | US_QUEENS | tip_group_05 |
| 06 | US_NJ | tip_group_06 |
| 07 | KR_SEOUL | tip_group_07 |
| 08 | PH_LUZON | tip_group_08 |
| 09 | US_NY | tip_group_09 |
| 10 | KR_SEOUL | tip_group_10 |

Each group runs Gold for its assigned store, not ALL. The instructor default target is `tip_demo_schema`; students must change target_schema to their group value. The shared source path does not change when the target schema changes.

## Instructor all-store demonstration

Use one instructor schema. Run Bronze and Silver for each of the seven unique stores in that schema. Then set Gold store to ALL and run it. Gold does not search across group schemas. Missing Silver tables stop ALL before writing. The full schema has seven Bronze tables, seven Silver tables and one `ec_gold_sales` table.

## Business rules and scope

One input row is one single-product order. Both COMPLETED and CANCELLED are retained. Only completed orders contribute sales, units sold and completed counts. Revenue is after whole-order discounts, converted with fixed teaching rates (PHP 1, USD 60, KRW 0.04), rounded per order. Source amounts and local timestamps remain traceable. Report by New York date and retain local business_date.

The seven-day files are a classroom archive. Reruns replace the full selected store's batch, so keep all intended files present. No ongoing history, corrected-file processing, scheduled 8 a.m. publication, completeness monitoring, alerts, refunds or tax calculation is implemented. These are documented follow-up requirements. The source data contains no deliberate invalid values or duplicates.

Gold stores one detail table, including cancelled orders with zero sales measures. Summary queries create no extra tables. Use net_sales_php, units_sold and completed_orders for reporting. Do not sum local amounts across currencies or raw quantity across cancellations.

## Timing

The agenda is exactly four hours including 25 minutes of breaks. At 8 a.m. New York the previous reporting day would still be provisional under the daily Asian export schedule. Archive totals do not simulate file arrival. October 19–24 are the complete global New York dates in this archive; October 18 and 25 have partial boundary coverage.
