# 🔄 ConvertUnitAmount()

## 📌 Purpose
Convert an amount of a unit to another of the same or different type.

---

## 🧾 Inputs

- `IngredientId` — The ID of the ingredient being converted (used for density lookup if needed)
- `FromUnit` — The original unit (e.g., `"cup"`)
- `ToUnit` — The target unit (e.g., `"tbsp"` or `"lb"`)
- `Amount` — The numeric amount to convert (e.g., `1.5`)

---

## ⚙️ Behavior

- If both `FromUnit` and `ToUnit` are the **same type** (e.g., volume → volume like `tbsp` → `cup`),  
  → Use `UnitConversionVolume` lookup table
- If crossing **unit types** (e.g., `cup` → `lb`),  
  → Use `IngredientDensityBridge` (requires `IngredientId`)
- Return the converted amount as a **single numeric value**

---

## ✅ Example

Convert:
- IngredientId = `"CHEDDAR"`
- FromUnit = `"cup"`
- ToUnit = `"lb"`
- Amount = `1`

Result:
- Uses density bridge: `1 cup` of cheddar = `0.25 lb`  
- **Return**: `0.25`
