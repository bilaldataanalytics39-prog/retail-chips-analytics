# retail-chips-analytics
Description: Descriptive analysis of 272 retail stores: store types, brands, pack size and customer life stage (Quantium virtual experience, Forage)
# Retail Chips Analytics

Descriptive analysis of one year of retail chip sales (Jul 2018 to Jun 2019, 272 stores,
about 265K transaction rows). Built as practice with the Quantium Data Analytics virtual
experience on Forage. This is my own exploratory work, not an official Quantium deliverable.

## Questions
1. How do the stores differ from each other?
2. Do brands, pack sizes or customer life stages explain those differences?
3. Do the three trial stores (77, 86, 88) look like each other, or like other stores?

## Dashboard
![Store Analysis](dashboard/page1_store_analysis.png)
![Customer Life Stage](dashboard/page2_customer_life_stage.png)

## Key findings
- 28% of stores (77 of 272) bring half of all sales. No single store brings more than 0.9%.
- Stores fall into 3 types by sales per customer: Low spend (82 stores), Mid spend (47)
  and High spend (131). High spend stores have fewer customers per store (256 vs 319) but
  each customer buys 5.8 times instead of 1.6, so sales per store are 4.6x higher.
- Pack size does not explain the difference: average pack size is 180 to 183g across store
  size groups, and its link with sales per customer is close to zero (Spearman -0.01).
- The trial stores are not one type: store 77 is Low spend, stores 86 and 88 are High spend.
- Life stage: Older Singles/Couples, Retirees and Older Families bring 58% of sales.
  Families spend the most per customer (36.04 and 34.45). Life stage has almost no link
  with brand or pack size (Cramer's V 0.03 and 0.02) and a weak link with store type (0.17).

## Project structure
code/
  common.py                      shared settings and helper functions
  01_store_overview.py           store spread and sales concentration
  02_store_types_pack_size.py    size groups, store types, pack size, charts
  03_life_stage.py               life stage analysis and links
dashboard/                       the two dashboard pages
outputs/                         tables and charts written by the scripts

## How to run
pip install -r requirements.txt
Put the merged data file QVI_data.csv in the project root (or set QVI_DATA=path/to/file.csv), then:
python code/01_store_overview.py
python code/02_store_types_pack_size.py
python code/03_life_stage.py

Column names and settings (trial stores, control stores, store-type cut-offs) are at the top
of code/common.py.

## Methods
- Python: pandas, matplotlib, scipy
- The 260 stores with all 12 months of data were split into 3 sales groups (Top, Medium, Low)
- Store types come from sales per customer, with cut-offs of 14 and 30 chosen by looking at
  the distribution
- Strength of links measured with Spearman correlation and Cramer's V

## Limitations
- The data covers the full year, so it includes the trial months. Trial dates were not
  confirmed in this exploration, so no trial effect (uplift) is claimed here.
- The store-type cut-offs were not tested for sensitivity.
- Results show what goes together, not what causes what.

## Next steps
Diagnostic analysis: why customers in some stores come back more often.

## Data
The raw data is not included. It comes from the Quantium virtual experience on Forage.

## Author
Bilal Ahmad, Data Analyst
LinkedIn: https://www.linkedin.com/in/bilal-ahmad-b0a1893b6
