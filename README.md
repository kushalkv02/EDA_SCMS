# **Project Summary -**

This dataset contains detailed information about shipment orders, shipment modes, weights, freight costs, managing teams, vendors, vendor INCO terms, scheduled delivery dates, delivered dates, and processing time information.

The initial step in data analysis begins with **data cleaning and preprocessing** to ensure consistency, accuracy, and usability of the dataset. The most critical steps include:

- Handling missing values  
- Converting date-time and numerical columns to appropriate data types  
- Creating derived features such as delivery status  
- Handling referenced values and outliers  

Outliers and referenced values can significantly distort visualizations and insights. For example:

- Null values are present in the **Shipment Mode** column  
- Referenced values are present in **Freight Cost** and **Weight** columns  

These values are referenced because freight cost and weight are calculated once per shipment rather than per line item.

---

## Exploratory Data Analysis (EDA)

EDA was performed to:

- Measure correlations between numerical variables  
- Identify cost-driving factors  
- Analyze delivery efficiency  
- Examine delivery timeliness patterns  

---

## Key Business Insights

### 1. Which numerical features depend heavily on each other?

The analysis revealed:

- **Weight, Line Item Value, and Insurance** are strongly correlated  
- Higher weight and higher item value lead to higher insurance costs  
- Freight cost has only a weak positive correlation with weight  

This indicates that additional factors beyond weight influence total freight cost.

---

### 2. Are shipments managed by specific teams more likely to be delivered on time?

- Most shipments are managed by the **PMO-US** team  
- On-time delivery rate: **88.5%**  
- Average delay: **-6.1 days**

A negative delay means shipments are delivered approximately **6 days earlier** than scheduled on average.

---

### 3. Does shipment mode influence meeting the scheduled delivery date?

Four shipment modes were analyzed (excluding null values).  

| Shipment Mode | On-time % | Average Delay |
|---------------|----------|--------------|
| Air           | 90%      | -3           |
| Air Charter   | 88%      | -19          |
| Truck         | 83%      | -9           |
| Ocean         | 82%      | 5            |

Key observations:

- **Air shipments** have the highest on-time rate (90%)
- **Air Charter** has the lowest average delay but higher freight cost
- **Ocean shipments** show the highest positive delay (late deliveries)

---

### 4. Do shipments from certain countries experience more delays?

Countries such as:

- Congo DRC  
- Kenya  

show greater delivery delays compared to others with significant shipment volume.  

However, countries with fewer orders may also show large delays due to limited sample size.

---

### 5. Does shipment mode impact the frequency of on-time deliveries?

- Overall on-time delivery rate: **88%**
- A small number of shipments experience severe delays (>90 days)
- Air shipments demonstrate the highest reliability in on-time performance

---

### 6. Does lead time (PO Sent → Scheduled Delivery) affect delivery performance?

Limitations:

- Many null values in **PO Sent to Vendor Date**
- Shipments originating from RDC do not follow standard PO flow

After excluding invalid entries and creating a **Lead Time** feature:

- Shorter lead times increase the risk of delivery delays  
- Adequate lead time improves the probability of on-time delivery  

---

### 7. Does INCO term impact vendor delivery performance?

Three major INCO terms were analyzed:

| INCO Term | On Time Rate | Average Delay |
|-----------|-------------|--------------|
| EXW       | 95%         | 0            |
| DDP       | 92%         | -12          |
| RDC       | 82%         | -8           |

Insights:

- **EXW** has the highest on-time rate  
- **DDP** shipments are frequently delivered early  
- **RDC** shipments show comparatively lower reliability  

---

### 8. Are higher weight shipments more likely to incur higher insurance costs?

Yes. There is a **moderately high positive correlation** between:

- Shipment weight  
- Line item insurance  

But factors other than weight, such as line item value and line item quantity, strongly influence the cost of insurance.

---

# Conclusion

The overall delivery performance is strong with an 88% on-time rate. Air shipments and EXW INCO terms show superior reliability, while shorter lead times and certain geographic regions contribute to increased delays. Cost drivers such as weight and item value significantly influence insurance expenses, but freight cost is impacted by multiple additional operational factors.
