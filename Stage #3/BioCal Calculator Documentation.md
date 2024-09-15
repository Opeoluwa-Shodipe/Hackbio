# THE DOCUMENTATION OF FORMULAS AND LOGIC

The reasoning for each of the four calculators in R Shiny and the underlying mathematical formulas are explained below. The processes for configuring the reactive calculation, the underlying mathematical ideas, and the reasoning behind each calculator's implementation within the Shiny framework are all covered in the explanation.

## 1. Stock Solution Dilution Calculation

### Mathematical Formula
The following formula controls the dilution of the stock solution:
\[ C1 \times V1 = C2 \times V2 \]
Where: 
- C1 = Concentration of stock (known)
- V1 = Required (unknown) volume of stock solution
- C2 = Targeted ultimate concentration
- V2 = Final volume

The unknown volume can be solved by rearranging this as follows:
\[ V1 = \frac{C2 \times V2}{C1} \]

### R Shiny Implementation
**Inputs:**
- C1: Stock concentration (numeric input)
- C2: The desired amount (numeric input)
- V2: The final volume, entered as a number

**Reactive Calculation:**
Create a reactive function that applies the formula to compute V1:
```r
stock_volume <- reactive({
  C1 <- input$stock_concentration
  C2 <- input$final_concentration
  V2 <- input$final_volume
  V1 <- (C2 × V2) / C1
  return(V1)
})


**Text:** Show the stock solution's computed volume.

**Scene:** Make a bar graph that shows the ratio of the diluent (V2-V1) to the stock solution (V1):
