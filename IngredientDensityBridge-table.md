## 🍽️ IngredientDensityBridge

This table supports **cross-unit conversions** (e.g., volume → weight) for specific ingredients by defining a fixed density ratio.

Used by: `ConvertUnitAmount()` when `FromUnit` and `ToUnit` are **different unit types** (e.g., converting `cup` → `lb`).

Once the conversion bridges to a **volume** or **weight base unit**, it continues using standard unit math — either:
- Simple arithmetic (e.g., `1 cup = 16 tbsp`)
- Or a lookup via the corresponding tables:
  - `UnitConversionVolume` (for volume → volume)
  - `UnitConversionWeight` (for weight → weight)

---

### 📄 Table: `IngredientDensityBridge`

| Column Name             | Data Type | Description                                                        |
|-------------------------|-----------|--------------------------------------------------------------------|
| `ingredient_id`         | TEXT      | Unique ID of the ingredient (e.g., `"FLOUR"`)                      |
| `volume_base_unit`      | TEXT      | Volume unit the ratio is based on (e.g., `"cup"`)                  |
| `weight_base_unit`      | TEXT      | Weight unit the ratio produces (e.g., `"lb"`)                      |
| `volume_to_weight_ratio`| DECIMAL   | How many weight units exist in one volume unit for this ingredient |

---

### ✅ Example Data: `IngredientDensityBridge`

| ingredient_id | volume_base_unit | weight_base_unit | volume_to_weight_ratio |
|---------------|------------------|------------------|-------------------------|
| FLOUR         | cup              | lb               | 0.30                    |
| SUGAR         | cup              | lb               | 0.44                    |
| HONEY         | cup              | lb               | 0.75                    |

---

### 📄 Table: `UnitConversionVolume`

| from_unit | to_unit | multiplier |
|-----------|---------|------------|
| cup       | tbsp    | 16         |
| tbsp      | tsp     | 3          |
| cup       | ml      | 240        |
| quart     | cup     | 4          |

---

### 📄 Table: `UnitConversionWeight`

| from_unit | to_unit | multiplier |
|-----------|---------|------------|
| lb        | oz      | 16         |
| oz        | gram    | 28.35      |
| kg        | lb      | 2.20462    |
| gram      | mg      | 1000       |

