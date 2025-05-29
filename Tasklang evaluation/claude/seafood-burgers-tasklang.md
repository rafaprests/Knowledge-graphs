# TaskLang: Seafood Burgers Recipe

## PROBLEM SeafoodBurgers
* **@RDFClass**: `tasklang:Problem`
* **@URI**: `<http://example.org/problems/SeafoodBurgers>`

**DESCRIPTION**: "Prepare quick and easy seafood burgers using canned fish"
**GOAL**: "Create 4 seafood patties that are golden brown and tasty"

**INPUTS**:
- resources: [
  * **@RDFClass**: `tasklang:Resource`
  * "Tuna/Salmon: Canned fish (170g/7½ oz), drained"
  * "Celery: Finely chopped (¼ cup/60mL)"
  * "Relish/Pickles: Chopped (2 Tbsp/30mL)"
  * "Eggs: Lightly beaten (2 units)"
  * "Bread Crumbs: (½ cup/125mL)"
  * "Green Onions: Chopped (2 units)"
  * "Salt and Pepper: To taste"
]
- context: {
  domain: "Home Cooking",
  constraints: "Quick preparation (10 minutes), Serves 4 people",
  parameters: [
    {
      name: "Cooking Temperature",
      value: "Medium-High",
      unit: "Stove Heat Level"
    },
    {
      name: "Cooking Time",
      value: 3,
      unit: "minutes per side"
    }
  ]
}

**QUALITY_CRITERIA**:
- "Golden Brown: Patties should be evenly browned on both sides"
- "Texture: Patties should hold together without falling apart"

**OUTPUTS**:
- finalProduct: "4 golden brown seafood burger patties"
- secondaryOutputs: [
  "Serving Suggestion: Serve on whole wheat toast, bannock, or bun"
]

## METHOD PrepareBurgers
* **@RDFClass**: `tasklang:Method`
* **@URI**: `<http://example.org/methods/PrepareBurgers>`

**DOMAIN**: "Home Cooking"
**DESCRIPTION**: "Method for creating seafood burger patties from canned fish"

**PREREQUISITES**:
- "Non-stick pan" [**@Importance**: "Critical"]
- "Mixing bowl" [**@Importance**: "Critical"]

**STEPS**:
1. **TASK** "CombineIngredients"
   * **@RDFClass**: `tasklang:Task`
   **ACTION**: "Mix all ingredients thoroughly in a large mixing bowl"
   **INPUTS**: ["Tuna/Salmon", "Celery", "Relish", "Eggs", "Bread Crumbs", "Green Onions", "Salt", "Pepper"]
   **DURATION**: "3-4 minutes"
   **OUTPUT**: "Mixed seafood burger mixture"

2. **TASK** "FormPatties"
   * **@RDFClass**: `tasklang:Task`
   **ACTION**: "Shape the mixed ingredients into 4 equal patties"
   **INPUTS**: ["Mixed seafood burger mixture"]
   **DURATION**: "2 minutes"
   **OUTPUT**: "4 formed seafood burger patties"

3. **TASK** "CookPatties"
   * **@RDFClass**: `tasklang:Task`
   **ACTION**: "Cook patties in a non-stick pan on medium-high heat, browning both sides"
   **DURATION**: "6 minutes (3 minutes per side)"
   **PARAMETERS**: [
     {
       name: "Heat Level",
       value: "Medium-High",
       measurement: "Stove dial setting"
     }
   ]
   **VALIDATION_RULES**: [
     "Patties must be golden brown on both sides",
     "Internal temperature should reach safe cooking temperature"
   ]

**RISKS**:
- "Patty Disintegration: Patties may fall apart" [**@Severity**: "Medium", **@Mitigation**: "Ensure thorough mixing and careful handling"]
- "Uneven Cooking: Patties may burn or remain undercooked" [**@Severity**: "Medium", **@Mitigation**: "Monitor heat and cooking time carefully"]

## STRATEGY SeafoodBurgerPreparation
* **@RDFClass**: `tasklang:Strategy`
* **@URI**: `<http://example.org/strategies/SeafoodBurgerPreparation>`

**PROBLEM**: SeafoodBurgers
**METHODS**:
- PrepareBurgers [**@Domain**: "Home Cooking", **@Context**: "Quick Meal Preparation"]

**STRATEGY_NOTES**:
- "Flexible Fish Choice: Recipe works with both tuna and salmon"
- "Serving Versatility: Can be served on toast, bannock, or bun"

**DOMAIN_CONTEXT**:
* **@RDFClass**: `tasklang:DomainContext`
* "Quick Meal Preparation: Suitable for fast, nutritious home cooking"
* **PROVENANCE**: {
  source: "Home Cooking Cookbook",
  confidence: "High",
  expert: "Home Cook"
}
