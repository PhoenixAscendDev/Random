## 🍽️ Substitution Module

This document defines the core business rules and structural model for the substitution system introduced after the MVP.

---

### 🧠 Business Rules

#### Food Group  
> A **Food Group** is a classification used to describe the dietary category or culinary role of a CulinaryItem or RawIngredient. These classifications support filtering, substitution, and ingredient reasoning throughout the system.

#### Nutritional Food Group  
> A **Nutritional Food Group** describes the broad dietary category of a RawIngredient based on its macronutrient content or traditional nutritional classification. These groups reflect conventional food groupings used in health and diet systems.

#### Culinary-Centric Food Group  
> A **Culinary-Centric Food Group** describes the functional or behavioral role of a RawIngredient in cooking. These groups support substitution logic, dietary restriction filtering, and culinary role reasoning.

#### Food Group Association  
> A **RawIngredient** must be associated with one or more **Food Groups** in order to support substitution logic, dietary filtering, and ingredient grouping within the system.

#### Diet  
> A **Diet** is a named set of one or more Food Groups that should not be included in a recipe.

---

### 🧩 UML Diagram

```mermaid
classDiagram
    class IFoodGroup {
        +ID : UUID
        +Name : TEXT
        +IsNutritional : BOOLEAN
        +IsCulinaryCentric : BOOLEAN
        +Source : TEXT
        +ParentFoodGroup : IFoodGroup
    }

    class IDiet {
        +ID : UUID
        +Name : TEXT
        +Owner : TEXT
        +Description : TEXT
        +FoodGroupRestrictions : IEnumerable~IFoodGroup~
    }

    class ICulinaryItem {
        +FoodGroups : IEnumerable~IFoodGroup~
    }



    IDiet --> "1..*" IFoodGroup : excludes
    ICulinaryItem --> "0..*" IFoodGroup : associated with
    IFoodGroup --> "0..1" IFoodGroup : parent
