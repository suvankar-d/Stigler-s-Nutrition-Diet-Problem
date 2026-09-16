# Stigler's Nutrition Diet Problem

## Overview

This project applies the classical Stigler Diet Problem to the case of a moderately active adult Indian woman weighing 55 kg. The objective is to determine the least-cost combination of commonly consumed Indian foods that satisfies specified Recommended Dietary Allowances (RDAs).

The optimization problem is formulated as a Linear Programming (LP) model and developed and implemented using the GAMS (General Algebraic Modeling System) language. The model minimizes daily food expenditure subject to nutritional requirements for calories, protein, calcium, iron, iodine, vitamin C, niacin, and vitamin B12.

## Research Objectives

The main objectives of the study are:

1. To formulate a least-cost diet model for a moderately active adult Indian woman.
2. To identify the combination of foods that satisfies the specified nutritional requirements at minimum cost.
3. To apply Linear Programming using GAMS for nutritional optimization.
4. To examine the practical implications of the optimized diet for nutrition planning and food-policy design.

## Theoretical Framework

The study is based on the classical Stigler Diet Problem introduced by George Stigler in 1945. The problem uses mathematical optimization to identify a combination of foods that satisfies nutritional requirements while minimizing expenditure.

The Linear Programming approach developed in the Stigler Diet Problem provides a framework for allocating expenditure across food items subject to nutritional constraints.

## Linear Programming Formulation

### Decision Variables

Let:

`x(f)`

represent the amount of money, in rupees per day, spent on food `f`.

The decision variables are non-negative:

`x(f) >= 0`

### Objective Function

The objective is to minimize total daily expenditure:

`min Cost = sum(f, x(f))`

### Nutritional Constraints

For each nutrient `n`, the total nutrient obtained from all foods must meet or exceed the required RDA:

`sum(f, a(f,n) * x(f)) =g= b(n)`

where:

- `a(f,n)` = amount of nutrient `n` obtained per ₹100 spent on food `f`
- `x(f)` = expenditure on food `f` in rupees per day
- `b(n)` = required RDA for nutrient `n`

The total expenditure is represented in GAMS as:

`cost =e= sum(f, x(f));`

## Food Set

The model considers the following food items:

- Milk
- Orange
- Apple
- Meat
- Green leafy vegetable / Spinach
- Eggs
- Millet / Bajra
- Ghee
- Butter
- Vegetable oil
- Common bean / Pulses
- Almond
- Mustard oilseeds
- Wheat
- Rice

## Nutrient Set

The nutritional requirements considered in the model are:

- Calories
- Calcium
- Protein
- Iron
- Iodine
- Vitamin C
- Niacin
- Vitamin B12

## Recommended Dietary Allowances

The RDA values used in the model are:

| Nutrient | Requirement |
|---|---:|
| Calories | 1660 kcal |
| Calcium | 1000 mg |
| Protein | 46 g |
| Iron | 29 mg |
| Iodine | 140 µg |
| Vitamin C | 65 mg |
| Niacin | 11 mg |
| Vitamin B12 | 2.2 µg |

## Construction of the Nutrient-Value Matrix

The nutrient-value matrix expresses the nutrient contribution of each food per ₹100 of expenditure.

The amount of a food that can be purchased for ₹100 is calculated as:

`Amount purchasable for ₹100 = (100 / Price of food) * 1000`

The nutrient contribution is then calculated using:

`Nutrient per ₹100 = (n / 100) * g`

where:

- `n/100` represents the nutrient content per gram
- `g` represents the quantity of the food that can be purchased for ₹100

This converts food composition and price information into coefficients that can be directly incorporated into the Linear Programming model.

## Data Sources

The study uses food price and nutrient information from the sources identified in the research material, including:

- Indian Food Composition Tables (IFCT), 2017
- National Institute of Nutrition (NIN) dietary guidance
- USDA FoodData Central
- Relevant millet and nutrition literature

The model combines food prices with nutrient composition to construct the nutrient-value matrix used in GAMS.

## GAMS Implementation

The optimization model is developed and implemented using the **GAMS (General Algebraic Modeling System) language**.

The main structure of the model includes:

1. Definition of food and nutrient sets.
2. Specification of RDA parameters.
3. Construction of the nutrient-value matrix.
4. Definition of decision variables.
5. Formulation of nutritional constraints.
6. Definition of the expenditure constraint.
7. Minimization of total food expenditure.
8. Solution of the Linear Programming model.

The central nutritional constraint is represented as:

`sum(f, a(f,n)*x(f)) =g= b(n);`

The expenditure balance is represented as:

`cost =e= sum(f, x(f));`

## Results

The model produces a reported minimum daily food cost of approximately:

**₹154.05 per day**

The reported optimized allocation is approximately:

| Food | Daily Expenditure |
|---|---:|
| Millet / Bajra | ₹153.67 |
| Milk | ₹0.33 |
| Spinach / Green leafy vegetable | ₹0.044 |
| Other foods | ₹0 |

The solution therefore concentrates expenditure on a small number of food items.

## Interpretation of Results

The optimized solution reflects the mathematical objective of minimizing expenditure while satisfying the specified nutrient constraints.

- **Millets** provide a major share of calories and contribute protein, calcium, and niacin.
- **Milk** contributes calcium and vitamin B12.
- **Spinach / green leafy vegetables** contribute vitamin C and iron.
- Several other foods, including meat and eggs, are excluded from the cost-minimizing solution because the model can satisfy the specified constraints without purchasing them.

The result demonstrates how Linear Programming can identify a mathematically least-cost food basket based on prices and nutrient requirements.

## Important Limitation: Corner Solution

A major limitation of the model is the possibility of a corner solution. Because the objective function minimizes expenditure subject only to nutritional constraints, the model can concentrate the diet on a small number of foods.

Although such a solution may satisfy the mathematical requirements, it may not represent a practical or desirable everyday diet because dietary variety, palatability, cultural preferences, sustainability, and other considerations are not fully incorporated into the basic cost-minimization framework.

## Policy Implications

The findings have potential applications in nutrition and food-policy planning.

### Food Subsidies and Food Distribution

Food-support programmes can consider a broader range of nutrient-dense foods, including:

- Pulses
- Millets
- Vegetables
- Other locally available nutrient-rich foods

This can help move beyond a narrow focus on staple cereals.

### Institutional Meal Planning

The optimization framework can be adapted for:

- Schools
- Hospitals
- Hostels
- ICDS-related nutrition programmes
- Other institutional food programmes

### Nutrition Planning

A cost-minimization model can help identify affordable combinations of foods capable of meeting specified nutritional requirements, particularly when food prices and nutrient composition are regularly updated.

## Future Extensions

The model can be extended by incorporating:

1. Minimum and maximum consumption limits for individual foods.
2. Dietary diversity requirements.
3. Palatability and cultural acceptability.
4. Sustainability considerations.
5. Regional differences in food prices.
6. Seasonal variation in food prices and availability.
7. Multi-objective optimization combining cost, nutrition, and dietary diversity.
8. Stochastic or interval programming to account for uncertainty.
9. Larger food databases containing additional Indian foods.

These extensions can reduce the likelihood of unrealistic corner solutions and make the optimized diet more applicable to real-world nutrition planning.

## Repository Structure

```text
Stigler-s-Nutrition-Diet-Problem/
│
├── Content/
│   └── [Research materials and project content]
│
└── README.md
```

## Key Takeaways

The project demonstrates the application of Linear Programming to a practical nutrition-planning problem.

The main findings are:

- The Stigler Diet Problem can be adapted to an Indian dietary context.
- GAMS can be used to solve the least-cost nutrition optimization model.
- The reported minimum daily cost is approximately ₹154.05.
- The mathematical solution relies heavily on millets, with small allocations to milk and green leafy vegetables.
- The model highlights the trade-off between minimum cost and practical dietary diversity.
- Additional constraints and objectives can make future versions of the model more realistic for household and institutional nutrition planning.
