# 📊 Budget Cost Module – Core Data Sets

This document defines the **minimum data sets** required to support the Budget Cost Module, including all relevant fields and notes for usage. These form the foundation for computing pantry savings, effective purchase cost, cost deltas, and substitution budgeting.

---

## 📦 PriceAggregate Table

*Represents current market prices for each ingredient by package size and unit.*

| Ingredient        | Unit  | Package Size | Avg Price | Store Count | Latest Price | Notes                   |
| ----------------- | ----- | ------------ | --------- | ----------- | ------------ | ----------------------- |
| Cheddar Cheese    | lb    | 0.5          | \$3.20    | 1           | 2025-06-14   | Sliced half block       |
| Cheddar Cheese    | lb    | 1            | \$5.83    | 2           | 2025-06-14   | Shredded or block       |
| Cheddar Cheese    | lb    | 2            | \$10.00   | 1           | 2025-06-14   | Warehouse club price    |
| American Cheese   | lb    | 0.5          | \$2.50    | 1           | 2025-06-14   | Processed cheese slices |
| American Cheese   | lb    | 1            | \$4.60    | 1           | 2025-06-14   | Family pack             |
| American Cheese   | lb    | 2            | \$8.95    | 1           | 2025-06-14   | Warehouse club price    |
| Eggs              | each  | 6            | \$2.80    | 1           | 2025-06-14   | Small carton            |
| Eggs              | each  | 12           | \$5.15    | 1           | 2025-06-14   | Standard carton         |
| Eggs              | each  | 18           | \$7.20    | 1           | 2025-06-14   | Large family size       |
| Eggs              | each  | 24           | \$9.50    | 1           | 2025-06-14   | Bulk pack               |
| English Muffin    | each  | 6            | \$1.45    | 1           | 2025-06-14   | Small pack              |
| English Muffin    | each  | 12           | \$2.63    | 1           | 2025-06-14   | Standard pack           |
| English Muffin    | each  | 18           | \$3.75    | 1           | 2025-06-14   | Bulk pack               |
| White Bread Slice | slice | 24           | \$2.10    | 1           | 2025-06-14   | Whole loaf              |

---

## 🏠 Pantry Inventory

*User’s currently owned ingredients, including original purchase metadata.*

| Ingredient      | Purchase Amount | Unit | Remaining | Store        | Date Purchased | Purchase Price | Notes                      |
| --------------- | --------------- | ---- | --------- | ------------ | -------------- | -------------- | -------------------------- |
| Cheddar Cheese  | 1 lb            | lb   | 0.25 lb   | Kroger       | 2025-06-01     | \$5.83         | Sliced block, refrigerated |
| Eggs            | 12              | each | 3 each    | Amazon Fresh | 2025-06-10     | \$5.15         | Large eggs, carton         |
| English Muffins | 6               | each | 2 each    | User Entry   | 2025-06-08     | \$1.45         | Leftovers from 6-pack      |

---

## 📋 Recipe Ingredient Table – Breakfast Sandwich

*Ingredient requirements to produce one batch.*

| Ingredient     | Quantity Needed | Unit | Notes                      |
| -------------- | --------------- | ---- | -------------------------- |
| Cheddar Cheese | 0.125           | lb   | Equals about 2 slices      |
| Eggs           | 2               | each | Standard large eggs        |
| English Muffin | 1               | each | Split in half for sandwich |

---

## ❌ Out of Scope

* **Shelf Life Tracker** is out of scope for all budget cost calculations.

---

Let me know when you're ready to evaluate this structure, run test data, or integrate into another module (e.g. Substitution).
