# Café Enchancia — Facilitator Notes

Use `Discovery_Call.md` as the single discovery transcript. These notes define the classroom implementation and follow-up backlog.

## Workshop contract

- Ten groups of four to five students, matching the slide agenda. Each group processes one assigned store in an isolated schema. See `../README.md`.
- Seven store CSVs contain seven local dates, October 19–25, 2026. Each store/day has 500–550 orders. Each file bundles seven daily exports for upload convenience; actual operations use one daily file per store.
- 25,824 unique orders: 24,747 COMPLETED and 1,077 CANCELLED. There are no deliberate duplicates or invalid records. One row is one order containing one product and a positive quantity.
- Four common products plus one local drink and one local pastry per country. See `../Sample Data/Product_Menu.csv`.
- Source timestamps and amounts remain local. Currency values are PHP, USD or KRW. Silver derives UTC timestamps and New York reporting dates.
- Discount is a whole-order amount. Completed local net sales = quantity × unit_price − discount_amount. Multiply by PHP-per-local-unit rate and round to two decimals per order. Rates: PHP 1, USD 60, KRW 0.04. Cancelled orders contribute zero sales, sold units and completed count.
- Prices exclude tax. Refunds are not present. Real tax treatment and refund handling require follow-up business approval.
- Bronze preserves 14 string source columns and adds source_file, source_path and ingested_at_utc. Silver validates and types records, retains cancellations, and calculates net_sales_php. No deduplication or quarantine exercise is required.
- Each store has its own Bronze and Silver table. Gold unions selected Silver tables into ONE `ec_gold_sales` table at store_id + transaction_id grain. Daily, store, country and product summaries are queries, not additional saved tables.
- One store creates three tables. All seven stores in one schema create 15 tables. Gold ALL requires all seven Silver tables in that same schema.
- Reruns rebuild the complete selected store batch. Gold ALL replaces all Gold rows; single-store Gold replaces only that store. This is not daily incremental ingestion.
- Data sharing is limited to email attachments or a network drive once approved. No direct POS access. The instructor stages fictional CSVs in Volumes; students do not connect to email or the drive.

## Reporting-time constraint

Headquarters wants the previous New York calendar day by 8 a.m. New York. Local-midnight exports cannot make that view complete by the deadline. For the October fixture, the Asian Tuesday export prepared at the start of Wednesday local time becomes available Tuesday at 11 a.m. New York for Seoul and noon for the Philippines, before delivery delays. It contains the final hours of Monday's New York reporting day. Publish the morning report as provisional in a production implementation, then refresh it when later files arrive.

For the fully loaded archive, New York October 19–24 have full scheduled global coverage. October 18 and 25 are partial boundary days. This does not establish historical 8 a.m. arrival completeness. The lab has no arrival monitor or as-of reconstruction.

## Classroom schedule

The agenda is 240 minutes: 215 minutes of activities and 25 minutes of breaks. Bronze has 25 minutes, Silver 30, and Gold 25. The 20-minute requirements activity reserves eight minutes for reading, eight for requirements/stories, and four for questions and the access request. Group 1 demonstrates task breakdown; Groups 2 and 3 demonstrate the Silver and Gold checkpoints. Groups 4–10 each get a two-minute final demo, with remaining time for transitions and questions.

## Follow-up backlog, not implemented in this lab

1. Scheduled ingestion and an 8 a.m. New York report refresh.
2. Missing-store/period flags, report last-update status and Operations alerts owned by Mia.
3. Incremental historical retention, complete-day corrections, source-version traceability and replay.
4. Refund calculations, approved real tax rules and date-effective FX rates.
5. A published reporting dashboard and longer historical comparisons.

## Validation and teaching evidence

Use `../VALIDATION.md` for independent dataset controls. Students capture source/target counts, sample time and FX conversions, cancellation checks and rerun evidence. Customer preferences here mean aggregate product demand; there is no customer identity or customer-segmentation dataset.
