# Financial Module README

## Why This Module Exists
Orchard is both a trusted guide for daily kitchen life and a celebration of culinary craft. It meets people where they are, helps them choose and make meals with clarity, and treats everyday constraints as part of the art of cooking.

That is why financial context is a core part of Orchard and a central feature of the product experience.

Meal cost is one of the biggest factors that determines whether a recipe gets made. Ingredient pricing shapes real choices at the moment of commitment. If price is unclear, confidence drops, friction rises, and good cooking intentions often stop before the first step.

The Financial Module exists to reduce that friction with honest, practical visibility.

## What It Helps People Do
The module helps people understand the real cost of cooking at home before they commit. It supports better choices by showing how ingredient pricing and meal totals affect the path from idea to finished meal.

It also helps people see a broader truth in practical terms: home-cooked meals are often among the most affordable options, and ingredient choices can materially change total cost.

By making those differences visible, Orchard helps people:

- choose recipes they can actually execute tonight,
- understand tradeoffs clearly,
- build confidence through informed choices,
- and grow skill without losing budget control.

## Orchard Principle Behind Financial Focus
Orchard treats financial reality as part of culinary reality.

Cost, effort, and creativity belong to the same cooking experience. The Financial Module reflects that belief by keeping pricing transparent, grounded in real shopping conditions, and useful in everyday decisions.

## Respecting A Sensitive Topic
Financial conversation is often treated as private, stressful, or taboo. Orchard frames money as practical kitchen context that people can use with dignity, respect, and clarity.

Orchard’s primary goal is better everyday cooking decisions. A meaningful secondary effect is that respectful, useful cost visibility can help normalize healthy conversation about meal affordability.

This is the purpose of the Financial Module: to make cooking more possible, more confident, and more sustainable for real people in real life.

## What The Module Does
The Financial Module turns Orchard's financial purpose into practical decision support at recipe and grocery-list time.

It organizes decisions around two financial pillars:

- **Affordability**: what the user must spend now to cook the recipe.
- **Efficiency**: how effectively purchased ingredients are used by this recipe.

The module provides a strategy toggle that reshapes ranking and grocery-list recommendations:

- **Lowest Cost** (default): prioritize lower checkout spend.
- **Highest Utilization**: prioritize higher recipe-use efficiency and lower unused value.

Both strategies use the same pricing confidence framework; the ranking strategy changes, but data trust signals do not.

### Core Financial Signals
The Financial Module must produce these four metrics for every priced recipe estimate.

- **Checkout Cost (USD)**
  - Definition: total estimated out-of-pocket spend to buy the selected ingredient packages now.
  - Inputs: `packages_to_buy`, `package_price` for each selected ingredient offer.
  - Formula: `SUM(packages_to_buy_i * package_price_i)` across selected ingredients.
  - Output type: currency amount (`numeric`, USD).
  - Scope: package-purchase spend represented by the selected pricing records in this estimate.

- **Recipe Utilization % (0-100)**
  - Definition: percent of purchased quantity that is consumed by this recipe run.
  - Inputs: `used_qty`, `total_purchased_qty`.
  - Formula: `(used_qty / total_purchased_qty) * 100`.
  - Output type: percentage.
  - Example: `8 oz used / 16 oz purchased = 50%`.

- **Unused Value (USD)**
  - Definition: estimated dollar value remaining after this recipe run.
  - Inputs: `purchase_cost`, `used_cost`.
  - Formula: `purchase_cost - used_cost`.
  - Output type: currency amount (`numeric`, USD).
  - Example: `$1.78 purchase - $0.89 used = $0.89 unused value`.

- **Price Confidence (0.00-1.00 + label)**
  - Definition: reliability score for the estimate quality.
  - Inputs: data coverage and price-data freshness.
  - Data coverage definition: `% of recipe ingredients with usable price records`.
  - Data coverage example: `8 priced / 10 total ingredients = 80%`.
  - Freshness definition: recency of pricing records by `capturedAt` timestamps.
  - Freshness clarification: this is price-data age from captured timestamps.
  - Output type: numeric score plus label (`High`, `Medium`, `Low`).
  - Role: confidence expresses trust level; cost and efficiency metrics express financial outcome.

These metrics are separate on purpose:
- Checkout Cost = cash-out view.
- Utilization % and Unused Value = efficiency view.
- Price Confidence = data-trust view.
