# EbookCo Reading & Coupon Behavior Analysis  
*Data-Driven Insights from Demographics, Completion Patterns, and Coupon Usage*

## 📌 Project Overview
This project investigates how reading behavior (completion levels) relates to coupon usage, repurchase tendencies, customer tiers, and demographic characteristics within EbookCo’s platform.  
We analyze ~6.6K member–book reading records (fact table built via SQL) and apply statistical tests (t-tests, ANOVA) to identify meaningful behavioral patterns.

## 🗂️ Data Processing (SQL Pipeline)
We constructed a clean analysis dataset through the following steps:

1. **Demographic preprocessing**  
   - Parsed inconsistent DOB formats  
   - Derived age, age_group (10s, 20s, 30s, 40s, 50s, 60+)  

2. **Reading behavior extraction**  
   - Completed_flag = 1 if Percentage_Comp ≥ 90  
   - One row per (member_id, book_id)

3. **Purchase & coupon features**  
   - Total_orders per member  
   - Coupon usage at the member–book level  
   - Repurchase_flag based on order count  
   - Book price from Ebooks

4. **Final fact table**:  
   `fact_member_book_reading` (6,6xx rows)  
   Contains: demographics, completion, coupon usage, book price, tier, repurchase behavior.

## 📊 Statistical Analysis
We applied:
- **Independent t-tests** (e.g., completion vs coupon usage, completion vs repurchase)
- **One-way ANOVA** (completion deciles, price quartiles, tiers)
- **Two-factor ANOVA** (gender × coupon, age_group × coupon)

The goal: identify how reading engagement and price sensitivity relate to coupon behavior across user segments.

## 🔍 Key Findings
### 1. Completion is the strongest behavioral separator
High-completion users:  
- Lower coupon usage  
- Higher repurchase rates  
- More stable purchasing patterns  

Low-completion users:  
- Higher coupon usage  
- Lower repurchase rates  
- More price-driven behavior  

### 2. Demographics shape engagement, not coupon effects
- Women and older readers show higher completion.
- Across all groups, coupon users consistently show lower completion *on average*  
  (descriptive, not causal).

### 3. Price & tier reveal two distinct user types
- **New/light users** pay more per book and use more coupons.  
- **Heavy users** buy lower-priced titles and rely less on coupons.

### 4. Completion, price sensitivity, and retention are closely linked  
Higher price + low completion + high coupon usage frequently cluster together.

## 🎯 Strategic Implications
- **Coupons as onboarding tools**  
  Best used for early-stage or low-engagement users, not as repeated discounts.

- **Shift toward engagement-linked rewards**  
  Completion-based or progress-based benefits instead of pre-purchase coupons.

- **Loyal (high-completion / multi-order) users**  
  Benefit more from non-price incentives such as personalized recommendations, series follow-ups, and subscription-style features.

- **Younger or low-completion users**  
  Respond better to shorter content, progress reminders, or improved content-fit guidance.

## 📝 Project Deliverables
- SQL ETL pipeline  
- Cleaned fact table  
- ANOVA & t-test statistical analysis  
- Behavioral segmentation  
- Strategic recommendations for coupon and engagement policies