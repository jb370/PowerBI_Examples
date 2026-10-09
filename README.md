# PowerBI_Examples

These are a few of examples of data visualizations I created in PowerBI that I learned through Coursera.


Adventure_Work_Product_Sales_Report - Analysis of the different products from company "Adventure Work"

Adventure_Work_Sales_Report - Analysis of the overall sales from company "Adventure Work"

WorldPopulation - Analysis of the World Population in 2021

# Power BI Portfolio

Interactive Power BI reports built to practice data modeling, dashboard design, and turning raw data into answers a business user can explore. Each project is a .pbix file you can open in Power BI Desktop.

| Project | Question it answers | Key techniques |

| [Adventure Works Sales Report](#1-adventure-works-sales-report) | How do sales trend over time, and what drives them by product and customer country? | Multi-table model, date hierarchy, waterfall and scatter analysis, Play Axis custom visual |

| [Adventure Works Product Sales Report](#2-adventure-works-product-sales-report) | Which product categories, colors, and sizes bring in the most revenue? | Multi-page report, custom accessible theme, category drill-down |

| [World Population Report](#3-world-population-report) | How is the world's population distributed by country and continent, and how has it changed over time? | Star-style model with a country dimension, DAX measure, ArcGIS map |

Tools: Power BI Desktop, DAX, Power Query
Data:  Microsoft's Adventure Works sample data; the World Population Data dataset
---
1. Adventure Works Sales Report

Adventure-Works-Sales-Report.pbix

Overview
An exploratory sales report on the Adventure Works dataset, built to analyze order totals over time and break them down by product category and customer country.

Data model
Three tables:

| Table | Role | Fields used in the report |

| `Order` | Order-level data | Order Date (with a Year / Quarter / Month / Day hierarchy), Order Total |

| `Sales` | Line-level product data | Product Name, Product Category, Product Price, Order Total |

| `Customer` | Customer attributes | Country (grouped) |

Relationships between the tables, their cardinality and filter direction  `Customer` 1 <-→ 1 `Order` on CustomerID, `Customer` 1 <-→ 1 `Sales`.

# Report page
One page with four visuals:

- **Line chart:** order total by day
- **Scatter chart:** product price vs. order total by product name, clustered to group similar products
- **Waterfall chart:** how daily order totals build up, broken down by **product category**
- **Waterfall chart:** the same view broken down by **customer country** (a grouped field)

# Techniques demonstrated
- Date hierarchy for drilling from year to day
- Grouping and clustering fields to simplify categories
- Custom visual integration
- Comparing product and geographic drivers of the same metric

# Insights
- Road Bikes made up the majority of the increase in Order Revenue between Day 2 and Day 3, however, Kids Bikes, Mountain Bikes, and E-Bikes all had losses.
- North America made up two thirds of the increase in Order Revenue between Day 2 and Day 3, Europe was the remaining third, while Other regions had losses.

---

# 2. Adventure Works Product Sales Report

Adventure-Works-Product-Sales-Report.pbix

# Overview
A three-page report titled **"Adventure Works Product Sales Report 2023"**, focused on product-level revenue.

# Data model
A single `Sales` table with product attributes (category, subcategory, color, size), an order date, and an order total.

# Report pages

| Page | Visual | What it shows |
| Product Sales Report | Stacked area chart | Order total by product color |
| Product Sales Report | Pie chart | Order total by product size |
| Top Product Categories| Clustered bar chart | Order total by product category and subcategory |
| Sales Monthly Summary | Clustered column chart | Order total by month |


# Design
- Custom accessible theme (*Accessible City Park*) applied across the report
- Consistent centered titles and fonts across visuals

### Insights
- Blue Bikes had the most Order Total values, while Silver had the least
- Order Totals more than doubled between February and March

---

# 3. World Population Report

WorldPopulation.pbix

# Overview
A single-page dashboard titled World Population Report 2021 showing the population by country and continent, plus how the total has changed over time.

# Data model
Two tables:

| Table | Role | Fields used in the report |

| `WorldPopulation` | Fact-style table of population figures | Year (date), Population, **CurrentPopulation** (DAX measure) |
| `DimCountry` | Country dimension | Country/Territory, Continent |

DAX Measure - CurrentPopulation = CALCULATE(SUM('WorldPopulation'[Population]), FILTER('WorldPopulation', YEAR('WorldPopulation'[Year]) = 2021))

### Report visuals
- Card: current world population
- Clustered column chart: current population by continent
- ArcGIS map: current population by country (bubble size and color by population)
- Line chart: world population by year (with Year / Quarter / Month / Day hierarchy)

A page-level filter removes records with no continent, so unmatched country rows don't distort the continent view.

# Techniques demonstrated
- Separating descriptive attributes (`DimCountry`) from measurements (`WorldPopulation`)
- A reusable DAX measure for the headline figure
- Geographic visualization with ArcGIS
- Data cleaning via a filter on unmatched records

# Insights
- Asia has the highest population with around 4.6 billion people with China, India, Pakistan, Indonesia contributing the most to this population
- The forecast of the World population will be 8.4 billion by 2031.


> **[ADD one screenshot per report, e.g., `/images/world-population.png`, and embed with `![World Population Report](images/world-population.png)`.]**

## About
Built by John (Jack) Burns, PhD. Connect on [LinkedIn](https://www.linkedin.com/in/jack-burns-ab9a47b6).
