# 🏨 Hotel Booking & Cancellation Analytics — Power BI Dashboard

An interactive Power BI dashboard that analyzes **119,390 hotel bookings** to show **when, where, and through which channels cancellations happen**, so hotel managers can plan pricing, deposit policies, and staffing around real demand.

![Hotel Booking Demand Analysis dashboard](images/dashboard.png)

---

## 📌 Business Problem

Hotels lose revenue when booked rooms are cancelled, and the loss is hard to recover close to the arrival date. Management needs answers to three questions:

1. **How big is the cancellation problem?**
2. **When and through which channels do cancellations happen?**
3. **Who are the loyal guests, and which rooms are in demand?**

---

## 🔍 Key Insights

| Metric | Value |
|---|---|
| Total bookings analyzed | 119,390 |
| Total cancellations | **44K** |
| Overall cancellation rate | **37.0%** |
| Repeat guests | 3,810 |

- **Cancellations peak in spring and early summer.** June has the highest cancellation rate (**41.5%**), followed by April (40.8%) and May (39.7%). January is the lowest (30.5%).
- **Online Travel Agents (OTAs) drive almost half of all cancellations (48.1%)**, followed by Groups (28.1%) and Offline TA/TO (19.3%). Direct bookings account for only 4.5%.
- **Demand is seasonal.** Weekday and weekend nights both climb through spring and peak in **August**, then drop sharply in the winter months.
- **Loyal guests are mostly domestic.** Portugal (PRT) accounts for about **3.3K of 3.8K repeat guests**, while international markets (GBR, ESP, FRA, ITA) rarely return.
- **Room type A dominates demand (69.1% of bookings)**, followed by D (23.6%) and E (7.3%).

### 💡 Recommendations

- **Tighten deposit or non-refundable rates for OTA bookings**, especially for arrivals in April–June.
- **Encourage direct bookings**, which have the lowest share of cancellations, through member rates or perks on the hotel's own website.
- **Build loyalty programs for international guests**, since almost all repeat business today is domestic.
- **Prioritize inventory and pricing for room type A**, which carries most of the demand.

---

## 📊 Dashboard Features

- **KPI cards:** Total Cancellations, Repeat Guests, Cancellation Rate
- **Cancellation Rate by Arrival Month:** months ranked by cancellation risk
- **Weekday vs Weekend Nights by Month:** seasonal demand pattern, sorted in calendar order
- **Repeat Guests by Country:** top 5 countries for returning guests
- **Share of Cancellations by Market Segment:** which channels generate cancellations
- **Bookings by Room Type:** room demand distribution
- **Slicers:** filter the whole page by **Hotel** (City Hotel / Resort Hotel) and **Country**

---

## 🧮 DAX Measures

```DAX
Total Bookings      = COUNTROWS('Hotel Bookings')
Total Cancellations = SUM('Hotel Bookings'[is_canceled])
Cancellation Rate   = DIVIDE([Total Cancellations], [Total Bookings])
Repeat Guests       = SUM('Hotel Bookings'[is_repeated_guest])
Weekday Nights      = SUM('Hotel Bookings'[stays_in_week_nights])
Weekend Nights      = SUM('Hotel Bookings'[stays_in_weekend_nights])
```

**Calendar month sorting.** The source stores months as text ("January", "February", …), which Power BI sorts alphabetically. A `Month Number` calculated column (1–12) and an `Arrival Month` column sorted by it keep every month-based visual in calendar order.

```DAX
Month Number =
SWITCH(
    'Hotel Bookings'[arrival_date_month],
    "January", 1, "February", 2, "March", 3, "April", 4,
    "May", 5, "June", 6, "July", 7, "August", 8,
    "September", 9, "October", 10, "November", 11, "December", 12
)

Arrival Month = 'Hotel Bookings'[arrival_date_month]   -- Sort by column: Month Number
```

---

## 🗂️ Dataset

- **Source:** [Hotel booking demand](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand) (public dataset on Kaggle), originally from Antonio, Almeida & Nunes (2019), *Hotel booking demand datasets*, Data in Brief.
- **Size:** 119,390 bookings × 32 columns
- **Scope:** a City Hotel and a Resort Hotel in Portugal, arrivals from July 2015 to August 2017
- **Main fields used:** `hotel`, `is_canceled`, `arrival_date_month`, `stays_in_week_nights`, `stays_in_weekend_nights`, `country`, `market_segment`, `is_repeated_guest`, room type

---

## 🛠️ Tools

- **Power BI Desktop:** data modeling, DAX measures, dashboard design
- **Power Query:** data import and type cleaning

---

## 📁 Repository Structure

```
hotel-booking-demand-analysis/
├── hotel-booking-demand-analysis.pbix   # Power BI report
├── data/
│   └── hotel_bookings.csv               # source data
├── images/
│   └── dashboard.png                    # dashboard screenshot
└── README.md
```

---

## ▶️ How to Open

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows).
2. Clone or download this repository.
3. Open `hotel-booking-demand-analysis.pbix`.
4. To refresh the data, go to **Home → Transform data → Data source settings → Change Source** and point it to `data/hotel_bookings.csv` on your machine.

---

## 👤 Author

**Yunido Baheramsyah**, Data Analyst & Data Scientist
GitHub: [@brmsyh](https://github.com/brmsyh)
