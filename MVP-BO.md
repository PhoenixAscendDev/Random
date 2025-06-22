# 🍽️ MVP Business Objects

This document defines the core business rules and structural model for the foundational objects in the recipe system.

---

## 🧠 Business Rules

### CulinaryItem
> A **CulinaryItem** is any discrete food-related object—raw or prepared—that can appear in a recipe system.

### Ingredient
> A **CulinaryItem becomes an Ingredient** only when it is included in a Recipe with a **specific amount** and **modification to its natural form factor** if needed for the Recipe.

### FormModifier
> A **FormModifier** is a change applied to a `CulinaryItem` that **does not alter its modular identity level**, but instead adjusts its **physical form** for use in a Recipe. It excludes any modification that involves **heat, time-based transformation, or chemical change**.

### Recipe
> A **Recipe** is a transformation rule that takes one or more **CulinaryItems** as **Ingredients**, follows a **defined sequence** of **InstructionSteps**, and produces a **single new CulinaryItem** as the result.

### MeasuredQuantity
> A **MeasuredQuantity** is a structured expression that defines **how much** of a `CulinaryItem` is used, expressed through a **recognized unit of measure**, and may be either **quantitative or qualitative** in nature.

### InstructionStep
> An **InstructionStep** is a **discrete, actionable directive** that contributes to **producing a prepared CulinaryItem**.

---

## 🧩 UML Diagram

```mermaid
classDiagram
    %% Base Interface
    class ICulinaryItem {
        +IsRawIngredient : bool
        +IsIngredient : bool
        +IsRecipe : bool
    }

    %% Recipe-Centered Types
    class IRecipe {
        +Ingredients : IEnumerable~IIngredient~
        +PreparedCulinaryItem : ICulinaryItem
        +Instructions : IReadOnlyList~IInstructionStep~
    }

    class IIngredient {
        +CulinaryItem : ICulinaryItem
        +Amount : IMeasuredQuantity
        +FormModifier : FormModifier
    }

    class IMeasuredQuantity {
        +Amount : decimal
        +Unit : UnitOfMeasure
        +IsQuantitative : bool
    }

    class IInstructionStep {
        +Text : string
    }

    %% Enums with examples
    class UnitOfMeasure {
        <<enumeration>>
        - Gram
        - Milliliter
        - Teaspoon
        - Tablespoon
        - Cup
        - Ounce
        - ToTaste
    }

    class FormModifier {
        <<enumeration>>
        - Chopped
        - Sliced
        - Diced
        - Minced
        - Crushed
        - Whole
    }

    %% Inheritance
    ICulinaryItem <|-- IRecipe
    ICulinaryItem <|-- IIngredient

    %% Associations
    IRecipe --> "1..*" IIngredient : Ingredients
    IRecipe --> "0..*" IInstructionStep : Instructions
    IRecipe --> "1" ICulinaryItem : PreparedCulinaryItem

    IIngredient --> "1" ICulinaryItem : CulinaryItem
    IIngredient --> "1" IMeasuredQuantity : Amount
    IIngredient --> "0..1" FormModifier : FormModifier

    IMeasuredQuantity --> "1" UnitOfMeasure : Unit
```
