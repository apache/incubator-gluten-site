---
layout: page
title: velox backend generator function support
nav_order: 2
parent: Velox Backend
grand_parent: v1.5.0
---
# Generator Functions Support Status

**Out of 7 generator functions in Spark 3.5, Gluten currently fully supports 7 functions.**

## Generator Functions

| Spark Functions   | Spark Expressions        | Status   | Restrictions   |
|-------------------|--------------------------|----------|----------------|
| explode           | ExplodeExpressionBuilder | S        |                |
| explode_outer     | ExplodeExpressionBuilder | S        |                |
| inline            | Inline                   | S        |                |
| inline_outer      | Inline                   | S        |                |
| posexplode        | PosExplode               | S        |                |
| posexplode_outer  | PosExplode               | S        |                |
| stack             | Stack                    | S        |                |

