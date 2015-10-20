---
title       : A Simple Shiny Project
subtitle    : slidify practice
author      : mandyzzz
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
github:

user: mandyzzz
repo: SlidifyPractice

---

## What is BMI?

The body mass index (BMI) or Quetelet index is a value derived from the mass (weight) and height of an individual. The BMI is defined as the body mass divided by the square of the body height, and is universally expressed in units of kg/m2, resulting from mass in kilograms and height in metres.

(Source: wikipedia)

## Using shiny to build an application of BMI calcalation.

A shiny project should be consisted of two parts:

1. ui.R controls how it looks.
2. server.R controls what it does.

---

## ui.R

```r
library(shiny)
shinyUI(pageWithSidebar(
  headerPanel("Calculate Your BMI Value:"),
  sidebarPanel(
    numericInput('height', 'Your Height in Meter', 0, min = 0, max = 5, step = 0.001),
    numericInput('weight', 'Your Weight in Kilogram', 0, min = 0, max = 300, step = 0.001),
    submitButton('submit')
    # ask the user to enter his/her height and weight
  ),
  mainPanel(
    h4('Your Calculated BMI Value:'),
    verbatimTextOutput("BMI"),
    h6('Find Your Weight Category:Underweight = <18.5, Normal weight = 18.5-24.9, 
       Overweight = 25-29.9, Obesity = BMI of 30 or greater.')
    )
    # output information has both the value and the reference for BMI value
))
```

---

## server.R

```r
library(shiny)
shinyServer(
  function(input, output) {
    output$BMI <- renderPrint(round({input$weight/((input$height)^2)},3))
    # calculation of BMI value, which is devide weight by the sqaure of height
    }
)
```

---

## Where to find this shiny project and the code?

https://github.com/mandyzzz/develop-data-products_project-1
https://mandyzzz.shinyapps.io/Calculation_BMI
