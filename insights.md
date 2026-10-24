# Restaurant Orders Analysis Report

## Executive Summary

This report analyzes restaurant orders from three branches between January 1 and June 30, 2025. After removing fully duplicated rows and standardizing branch names in an analysis copy, the dataset contains **1,500 orders** and **$18,751.00 in revenue**.

Mall has the highest revenue. Dine-in is the largest revenue channel. The busiest hour is 8:00 PM, and the data shows lower average ratings for longer delivery times.

> The original `restaurant_orders.csv` file was not changed. Cleaning was applied to a separate analysis copy. Values below are calculated from the CSV using pandas.

## 1. About the Data

- **Period:** January 1 through June 30, 2025.
- **Original file:** 1,515 rows and 12 columns.
- **Record meaning:** Each row represents one order for one menu item.
- **Branches:** Downtown, Mall, and University.
- **Channels:** Dine-in, Takeaway, and Delivery.
- **Main fields:** Order ID and date, hour, branch, channel, item and category, quantity, unit price, row total, delivery time, and customer rating.
- **Revenue:** Sum of the `total` column.
- **Average order value:** Revenue divided by the number of distinct order IDs.

## 2. Data Quality and Cleaning

| Check | Result | Handling or meaning |
| --- | ---: | --- |
| Fully duplicated rows in the original file | 15 | Removed duplicate copies in the analysis dataset only. |
| Rows with inconsistent branch spelling | 24 | Trimmed extra spaces and standardized letter case in the analysis dataset. |
| Missing ratings in the original file | 136 | Rows were retained; missing ratings are excluded from rating averages. |
| Missing ratings after duplicate removal | 132 | Orders remain in the dataset; missing ratings are not included in averages. |
| Missing delivery times | 1,137 | Expected for non-delivery orders. All 374 delivery orders have a recorded duration. |
| Negative values in numeric columns | 0 | No negative values were found in the numeric fields checked. |

After cleaning, the analysis dataset has **1,500 rows** and **three branches**. Observed ranges:

| Field | Minimum | Maximum |
| --- | ---: | ---: |
| Order hour | 10 | 23 |
| Quantity | 1 | 7 |
| Unit price | $1.50 | $16.00 |
| Row total | $1.50 | $112.00 |
| Delivery time | 12 minutes | 74 minutes |
| Rating | 1 | 5 |

## 3. Overall Performance

| Metric | Result |
| --- | ---: |
| Total revenue | **$18,751.00** |
| Orders | **1,500** |
| Average order value | **$12.50** |
| Average rating | **4.07 / 5** |
| Orders with a rating | **1,368** |

## 4. Branch Comparison

| Branch | Orders | Revenue | Average order value | Average rating | Revenue share |
| --- | ---: | ---: | ---: | ---: | ---: |
| Mall | 590 | $7,933.00 | $13.45 | 4.12 | 42.31% |
| Downtown | 466 | $6,678.00 | $14.33 | 4.01 | 35.61% |
| University | 444 | $4,140.00 | $9.32 | 4.04 | 22.08% |
| **Total** | **1,500** | **$18,751.00** | **$12.50** | **4.07** | **100.00%** |

Branch revenue reconciles to total revenue: **$18,751.00**.

## 5. Channels and Menu Items

### Revenue by Channel

| Channel | Orders | Revenue | Average order value | Revenue share |
| --- | ---: | ---: | ---: | ---: |
| Dine-in | 661 | $8,122.00 | $12.29 | 43.32% |
| Takeaway | 465 | $5,459.00 | $11.74 | 29.11% |
| Delivery | 374 | $5,170.00 | $13.82 | 27.57% |
| **Total** | **1,500** | **$18,751.00** | **$12.50** | **100.00%** |

Channel revenue reconciles to total revenue: **$18,751.00**.

### Top Five Items by Revenue

| Rank | Menu item | Revenue |
| ---: | --- | ---: |
| 1 | Mixed Grill | $4,864.00 |
| 2 | Grilled Chicken Plate | $3,399.00 |
| 3 | Beef Burger | $2,464.00 |
| 4 | Chicken Shawarma | $1,878.50 |
| 5 | Falafel Wrap | $1,314.00 |

## 6. Order Timing

### Orders by Hour

| Hour | Orders | Hour | Orders |
| ---: | ---: | ---: | ---: |
| 10:00 | 17 | 17:00 | 67 |
| 11:00 | 47 | 18:00 | 94 |
| 12:00 | 110 | 19:00 | 178 |
| 13:00 | 216 | 20:00 | **220** |
| 14:00 | 153 | 21:00 | 139 |
| 15:00 | 75 | 22:00 | 86 |
| 16:00 | 49 | 23:00 | 49 |

The busiest hour is **8:00 PM**, with **220 orders**, followed by **1:00 PM**, with **216 orders**.

### Orders by Day of Week

| Day | Orders |
| --- | ---: |
| Monday | 204 |
| Tuesday | 179 |
| Wednesday | 180 |
| Thursday | 197 |
| Friday | 278 |
| Saturday | **280** |
| Sunday | 182 |

Saturday has the most orders (**280**), closely followed by Friday (**278**).

## 7. Delivery Time and Customer Ratings

This comparison includes delivery orders with both a recorded delivery time and a rating. Time bands are: under 30 minutes, 30–45 minutes inclusive, and over 45 minutes.

| Delivery time | Orders with ratings | Average rating |
| --- | ---: | ---: |
| Under 30 minutes | 61 | 4.11 |
| 30–45 minutes | 185 | 3.59 |
| Over 45 minutes | 94 | 2.47 |

Of the **374** delivery orders, **340** have both a delivery time and a rating. Average ratings decrease across the longer delivery-time bands. This is an association in the data; it does not prove that delivery time alone caused the lower ratings.

## 8. Key Insights

1. **Mall leads the branches in order count and revenue.** It recorded 590 orders and $7,933.00 in revenue, equal to 42.31% of total revenue. Source: **Branch Comparison** table.
2. **Orders peak at 8:00 PM and on Saturday.** The busiest hour had 220 orders, and the busiest day had 280 orders. Sources: **Orders by Hour** and **Orders by Day of Week** tables.
3. **Longer delivery-time bands have lower average ratings.** Orders taking over 45 minutes averaged 2.47, compared with 4.11 for orders under 30 minutes. Source: **Delivery Time and Customer Ratings** table. This does not establish causation.

## 9. Recommendations

1. **Review University branch performance and average order value.** It recorded $4,140.00 in revenue and a $9.32 average order value. Track branch revenue, order count, and average order value over subsequent periods to assess change.
2. **Plan staffing and operations around the evening and Saturday peaks.** These periods recorded 220 orders at 8:00 PM and 280 orders on Saturday. Monitor order volume, wait times, and delivery times during these periods.
3. **Monitor deliveries taking over 45 minutes.** This group averaged a 2.47 rating. Track the share of deliveries exceeding 45 minutes and their average ratings over time; check whether improvements in delivery time coincide with rating changes.

## 10. What We Do Not Know Yet

The dataset does not include operating or ingredient costs, so revenue cannot tell us net profit.
It also does not record the causes of delays or customer wait time, so the rating comparison cannot explain why customers gave lower ratings.
