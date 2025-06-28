## Budget Cost Module – Section 1: Intro

### 🌱 Thriving Life Rules

* **Decent food should be accessible.**
* **Planning a meal shouldn’t be a luxury.**
* **Budget choices should come without shame.**

---
### 🧽 Budget Cost Module Purpose

**Bring clarity to the most basic human need:**
Feeding yourself and others with dignity—by empowering financial choices to **plan**, **stretch**, and **substitute** ingredients in meals.


## Budget Cost Module – Business Rule Statements

### 🎜️ Business Rule: PriceSource

> A **PriceSource** is a single recorded price for a specific **CulinaryItem**, offered by a specific **retail source**, in a defined **unit of measure** and **package size** at a specific **date/time**.
---

### 🎜️ Business Rule: PriceAggregator

> A **PriceAggregator** is a business logic unit that consolidates multiple `PriceSource` records for the same **CulinaryItem**, **unit of measure**, and **package size** into a single computed price summary, which contains **mathematical aggregation** and **price grouping criteria**.

---
### 🎜️ Business Rule: IngredientDensityBridge

> An **IngredientDensityBridge** is a fixed ratio that defines the relationship between a **volume-based unit** and a **weight-based unit** for a specific **RawIngredient**.
---

### 🎜️ Business Rule: Density

> Every **CulinaryItem** has a **Density** that defines the quantity of **mass within a volume**.
> The **base density unit** is **`lb/cup`**.
---

### 🎜️ Business Rule: Pantry Savings

> **Pantry Savings** is the avoided cost of using an ingredient already owned at the time of cooking.
> It is calculated based on the **PriceAggregate** of the amount used, regardless of when or how the ingredient was acquired.
> Pantry Savings reflects the **financial value preserved** by not needing to repurchase the ingredient at today’s price.

---
### 🎜️ Business Rule: Effective Purchase Cost

> **Effective Purchase Cost** is the proportional amount of a purchased ingredient’s price that corresponds to the quantity used in a recipe, using the **PriceAggregate** of an ingredient.
> Effective Purchase Cost reflects the **actual financial cost incurred** for the portion of an ingredient used from a purchase.

---

### 🎜️ Business Rule: Pantry Cost Delta

> **Pantry Cost Delta** is the difference between the original purchase price of an ingredient and its current market at the time it is used.
> It is calculated by comparing the **Effective Purchase Cost** to the **Pantry Savings** for the same quantity.
> Pantry Cost Delta reflects the **change in ingredient value** between the time of purchase and the time of use.

---
## EXAMPLE🧲 Budget Cost Evaluation: Breakfast Sandwich

---

### 🧠 Scenario-Based Summary

*High-level planning logic based on current pantry and budget inputs. No substitutions are applied here.*

* **How many can I make with no cost today?**
  → ✅ *1 batch*
  → Based on pantry:

  * Cheddar Cheese: 0.25 lb
  * Eggs: 3 each
  * English Muffins: 2 each

* **How many can I make with a spending budget of \$5.00 + panty items**
  → ✅ *3 batches*
  → Requires buying 6 egg carton at \$2.43

---

### 💡 Recommended Substitutions for Minimum Spending

*Substitution rules applied strictly for cost reduction, based on lower-priced ingredients from the same culinary group. This affects only the Substitution Purchases section.*

| Original Ingredient | Substituted With  | Rule Applied      |
| ------------------- | ----------------- | ----------------- |
| Cheddar Cheese      | American Cheese   | Lower-cost cheese |
| English Muffin      | White Bread Slice | Lower-cost bread  |

---

### 🏠 Pantry-Based Insights

*Applies to all calculations that factor in current inventory.*

* **Pantry Inventory**:

  * Cheddar Cheese: 0.25 lb
  * Eggs: 3 each
  * English Muffins: 2 each

* **Pantry Savings**: \$2.27

* **Pantry Cost Delta**: +\$0.19

---

### 🛒 No Substitution Purchases

*Buy everything exactly as written in the recipe.*

| Ingredient      | Package Bought | Price  | Qty Used per Batch | Max Batches | Left After 1 Batch |
| --------------- | -------------- | ------ | ------------------ | ----------- | ------------------ |
| Cheddar Cheese  | 1 lb block     | \$5.83 | 0.125 lb           | 8           | 0.875 lb           |
| Eggs            | 12-egg carton  | \$5.15 | 2 eggs             | 6           | 10 eggs            |
| English Muffins | 12-pack        | \$2.63 | 1 muffin           | 12          | 11 muffins         |

* **Purchase Total**: **\$13.61**
* **Effective Cost (Used)**: **\$1.81**
* **Max Batches from Purchase**: **6**
* **Limiting Ingredient**: **Eggs**

---

### 💸 Substitution Purchases

*Buy everything but use alternate ingredients from the recipe.*

| Original Ingredient | Substitution      | Package Bought   | Price  | Qty Used per Batch | Max Batches | Left After 1 Batch |
| ------------------- | ----------------- | ---------------- | ------ | ------------------ | ----------- | ------------------ |
| Cheddar Cheese      | American Cheese   | 1 lb pack        | \$4.60 | 0.125 lb           | 8           | 0.875 lb           |
| Eggs                | —                 | 12-egg carton    | \$5.15 | 2 eggs             | 6           | 10 eggs            |
| English Muffin      | White Bread Slice | Loaf (24 slices) | \$2.10 | 2 slices           | 12          | 22 slices          |

* **Purchase Total**: **\$11.85**
* **Effective Cost (Used)**: **\$1.61**
* **Max Batches from Purchase**: **6**
* **Limiting Ingredient**: **Eggs**




