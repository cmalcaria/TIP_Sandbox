# Café Enchancia — Business Discovery Call

**Fictional workshop scenario**  
**Estimated reading time:** 7–9 minutes  
**Updated:** October 26, 2026

**Participants**

- **Dawn Lim — Business Owner**
- **Chris Alacaria — Data Architect**
- **Daniel Brooks — Operations Manager, New York Headquarters**
- **Mia Santos — Regional Store Coordinator**

**Meeting objective:** Understand Café Enchancia’s business challenges, reporting needs, daily operations, and expectations.

---

### Business Background

**Chris:** Thank you for joining. Dawn, could you tell us about Café Enchancia and what led you to request this project?

**Dawn:** Café Enchancia sells coffee, specialty drinks, and pastries. We have multiple branches around the world. As the business grows, it is becoming harder to understand what is happening across all our stores.

**Chris:** What are you finding difficult to understand?

**Dawn:** I want to know how much we are selling, which products customers prefer, and how our stores are performing. At the moment, I need to ask different people for different reports. I want to see the business in real time.

**Daniel:** Our headquarters is in New York. We start every morning by reviewing store performance, but we often spend hours collecting and combining files before we can discuss the results.

**Mia:** Each store prepares its own report. Sometimes files arrive late. Sometimes the store manager sends a corrected version after we have already prepared the consolidated report.

**Chris:** What impact does that have on the business?

**Dawn:** It delays decisions. We struggle to tell whether a promotion is working across all branches.

**Daniel:** There is also a trust issue. When the numbers change, people ask which report is correct. We spend meeting time explaining the spreadsheet instead of discussing the business.

### Store Coverage

**Chris:** Which stores should this project cover?

**Mia:** Seven stores. We have three in the Philippines: Luzon, Visayas, and Mindanao. We have three in the United States: New York, Queens, and New Jersey. We also have one in Seoul, South Korea.

**Chris:** Are New York and Queens treated as separate branches?

**Daniel:** Yes. The store we call New York is our Manhattan location. Queens is a separate branch with its own sales records.

**Chris:** Do all seven stores sell the same products?

**Mia:** All countries share Americano, Cafe Latte, Butter Croissant, and Chocolate Muffin. Each country has exactly one additional local drink and one local pastry. The Philippines has Ube Latte and Ensaymada; the US has Maple Latte and Apple Danish; Korea has Black Sesame Latte and Sweet Potato Bread. Stores within a country share the same menu. Prices differ between countries.

**Dawn:** We want to compare common products, but we also need to understand local preferences. A product that performs well in Seoul may not perform the same way in the Philippines.

**Chris:** Are more stores expected?

**Dawn:** Yes. Seven is the initial scope, but we expect to expand. We want this reporting process to remain useful as the business grows.

### Current Daily Submissions

**Chris:** Could you walk me through what each store submits today?

**Dawn:** We cannot share access to our POS system or our actual business data with you yet. We can first agree on the file structure and use fictional examples for the workshop.

**Chris:** Once data sharing is approved, how can the team receive the daily files?

**Mia:** The only available options are CSV attachments through email or picking up the CSV files from the network drive where we store them daily. We cannot offer a direct POS connection at this stage. Each store provides one daily CSV: three from the Philippines, three from the US, and one from Seoul.

**Chris:** Are the transaction times already adjusted to headquarters time?

**Mia:** No. The timestamps show the store's local time. We identify the store and its time zone so the time is unambiguous for these sample dates.

**Chris:** When is each file prepared?

**Mia:** At **12:00 midnight in the store’s local time zone**, every day.

**Chris:** What period does that file cover?

**Mia:** The previous local calendar day. For example, the file prepared at the start of Tuesday contains Monday’s activity for that store.

**Chris:** Does that schedule include weekends?

**Mia:** Yes. All seven stores operate 24 hours a day, seven days a week, including every weekend and holiday. Midnight is a reporting cutoff, not a store closing time. Daily submissions continue every day.

**Chris:** Is midnight the time the file is prepared or the time headquarters receives it?

**Mia:** It is the time the file is prepared. Normally, it is sent shortly afterward. If the store has a connection problem or someone forgets to submit it, headquarters receives it later.

**Daniel:** That distinction matters. We sometimes assume a store had no sales when the real problem is that we have not received its file.

**Chris:** Should we ever treat a missing file as a scheduled holiday closure?

**Daniel:** No. We have no scheduled holiday or weekend closures. A missing file is a submission issue that Operations must investigate.

### Daily Reporting and Real-Time Expectations

**Chris:** Dawn, you mentioned real time. What would that allow you to do?

**Dawn:** Ideally, I could see sales as they happen and compare product demand across stores. But the immediate problem is that our information is not consistently updated every day.

**Chris:** What is the minimum frequency that would make the first release useful?

**Dawn:** Daily. Sales must update every day. Real time is the longer-term goal.

**Daniel:** A dependable daily report would already save us significant effort.

**Chris:** When does headquarters need that report?

**Daniel:** By **8:00 a.m. New York time every day**, including weekends. That is when our morning review begins.

**Chris:** What date should that morning report represent?

**Daniel:** The previous day in New York. If we open it on Tuesday morning, we want to review Monday’s sales.

**Dawn:** Headquarters should use one consistent reporting day. New York is where we start the daily business review.

**Chris:** Is that how the stores currently define their daily reports?

**Mia:** No. Each store uses its own local calendar day. Monday in Seoul does not cover the same hours as Monday in New York.

**Chris:** Which requirement takes priority for headquarters: comparing each store’s local business day, or reviewing activity that falls within the same New York calendar day?

**Daniel:** The New York calendar day should be the main headquarters view. Store managers will still need their local-day figures when checking their own records.

**Chris:** If some information needed for that New York day has not arrived by 8:00 a.m., what would you expect?

**Dawn:** I would rather see the available information than receive nothing. But it must be clear that the numbers are incomplete.

**Daniel:** We also need to know which stores or periods are affected. A report should not look final when more information is expected.

**Chris:** When additional information arrives, should previously reported figures be updated?

**Daniel:** Yes. Accuracy matters more than keeping the first published number unchanged, provided we can understand why it changed.

### Sales and Business Measures

**Chris:** What are the most important questions the sales report should answer?

**Dawn:** Which store has the highest sales? Which coffee and pastry products sell best? Are sales improving or declining? Are we selling more because of a promotion, or are we simply giving larger discounts?

**Daniel:** We need sales by store, country, product, and day. We also need quantities sold and the number of customer transactions.

**Chris:** Will the files contain cancelled orders?

**Mia:** Yes. They contain COMPLETED and CANCELLED orders. The data is already cleaned, with no duplicate records, invalid values, or deliberate noise. A cancellation is a legitimate business event, not a data-quality error.

**Daniel:** Keep cancelled orders for traceability, but exclude them from sales revenue, units sold, and completed transaction counts. Cancelled orders in this exercise were never fulfilled.

**Chris:** When you say sales, should that include discounts and refunds?

**Daniel:** We want the amount after discounts and refunds, but we should also be able to see those adjustments separately.

**Chris:** Are refunds included in the workshop sample?

**Daniel:** No. For the workshop, calculate completed sales after discounts only. Refund handling is a follow-up requirement. Keep discounts visible separately.

**Chris:** Should taxes be included?

**Daniel:** Finance still needs to confirm tax treatment for real reporting. For the fictional workshop, the supplied prices exclude tax and no tax calculation is required.

**Chris:** What currency should the headquarters report use?

**Dawn:** Philippine pesos. I want the report in PHP for every store, even though headquarters uses New York time for the reporting day.

**Chris:** Should the same product have the same peso price in every country?

**Dawn:** No. Prices differ by market. For example, one Americano should be ₱600 in our US stores, ₱300 in Seoul, and ₱165 in the Philippines, before discounts.

**Chris:** Will the source files use pesos for every store, or each store's local currency?

**Mia:** Each store's local currency. Philippine files use PHP, US files use USD, and Seoul files use KRW. Unit prices and discount amounts will remain in that currency. Transaction timestamps will also remain in the store's local time.

**Chris:** How should we interpret the Americano examples you gave?

**Dawn:** Those are the peso amounts I want to see in the workshop report, before discounts. The sample source prices are ₱165 in the Philippines, US$10 in the US, and ₩7,500 in Korea. The report should show ₱165, ₱600, and ₱300 respectively using the sample rates agreed for the exercise.

**Daniel:** For this fictional workshop, use fixed rates of ₱60 per US dollar and ₱0.04 per Korean won. PHP stays at one peso per peso. These are teaching assumptions, not current market rates. Finance would need to approve the rates and their effective dates for real reporting.

**Chris:** So the source retains local amounts, but headquarters compares the converted sales in PHP?

**Dawn:** Correct. Keep the original amounts traceable. I want the report in pesos and the reporting day based on New York time.

**Chris:** What historical comparisons matter?

**Dawn:** Daily trends and comparisons with previous weeks or months. We need to retain history, not just replace yesterday’s report with today’s.

### Exceptions and Ownership

**Chris:** What should happen if one store’s submission is missing?

**Daniel:** Headquarters should still receive the report on time, with a clear indication of what is missing. Operations should be notified so we can follow up.

**Chris:** Who owns that follow-up?

**Mia:** I will coordinate with the store managers.

**Chris:** What happens when a store discovers an error in a submitted file?

**Mia:** The manager sends a corrected file containing the complete day again.

**Chris:** How should that affect the business report?

**Daniel:** The corrected figures should replace the incorrect figures for that store’s day. They should not be treated as additional sales.

**Chris:** Should we expect duplicate records in the files for this exercise?

**Mia:** No. The supplied files are already clean and contain no duplicates. Resending or correcting a file is a separate operational concern for a later release.

**Chris:** What would you need to investigate a disputed total?

**Daniel:** The store’s original submission, any corrected submission, and an explanation of what was included in the report.

**Chris:** Who can confirm whether the final numbers are correct?

**Mia:** Store managers can verify their own results.

**Daniel:** I will validate the consolidated headquarters report.

### Success and Next Steps

**Chris:** Dawn, what would make you consider this project successful?

**Dawn:** I can begin the day with one dependable view of the business. I can see sales performance and popular products without asking someone to combine spreadsheets.

**Daniel:** The report is ready by 8:00 a.m. New York time. It clearly shows whether the information is complete and when it was last updated.

**Mia:** Stores understand what they need to submit, and we can identify missing or incorrect submissions without checking everything manually.

**Chris:** What information can you provide after this meeting?

**Mia:** An agreed file layout, the product list, and current sales reporting practices. Actual POS data remains unavailable for now; the workshop will use fictional CSVs matching that layout.

**Daniel:** I will confirm the sales definitions, tax treatment and cancellation handling with the appropriate business owners.

**Chris:** My understanding is that the first release needs daily sales reporting in Philippine pesos for seven stores. Each store prepares its file at local midnight. Headquarters reviews the business by New York reporting day and needs the report every morning, even when some information is incomplete.

**Dawn:** Correct. Real time remains the longer-term ambition, but dependable daily reporting is our first priority.

**Chris:** Thank you. We will document these requirements and the open questions for your review before the team begins implementation.


