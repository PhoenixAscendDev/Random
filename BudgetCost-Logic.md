## 🔁 Budget Cost Evaluation Logic

### Pantry-Only Yield
Calculate how many full batches can be made using only pantry inventory.  
➕ **Record this as** `PantryOnlyYield`.

---

### Find Limiting Ingredient
Identify the ingredient preventing additional batches  
(i.e., lowest `Can Make` in pantry-to-batch table).

---

### Determine Minimum Purchase Needed
For the limiting ingredient, find the **lowest-cost package** available that meets the shortfall.  
This is the **cheapest way** to unblock at least one more batch.

---

### Simulate Pantry Update
Add the purchased ingredient(s) into the pantry **(virtually)**.  
Recalculate the batch table again using the updated pantry.

---

### Post-Purchase Yield
Calculate how many **additional batches** can now be made.  
➕ **Record this as** `MinPurchaseYield`.

---

### Budget Evaluation
Compare total purchase cost to the defined budget.

- ➖ If `cost > budget` →  
  Store the gap as `BudgetDelta`.  
  Report that **0 additional batches** can be made within budget.  
  But show that **X batches** could be made if the user spends `$BudgetDelta` more.

- ✅ If `cost ≤ budget` →  
  Add `MinPurchaseYield` to `PantryOnlyYield` for the **total batch count**.
