# 🚗 Uber NCR Ride Analytics Dashboard

> A comprehensive ride-hailing analytics project analyzing **150,000 bookings** from the National Capital Region (NCR) — covering operational performance, revenue & pricing intelligence, and supply-demand efficiency through an interactive Power BI dashboard.

---

## 📌 Project Overview

This project analyzes Uber ride booking data across the NCR market to help operations and product teams monitor service health, identify demand hotspots, optimize driver supply, and track revenue performance. The dashboard is split into 3 focused analytical views — Overview, Revenue & Pricing, and Supply & ETA.

| | |
|---|---|
| **Market** | National Capital Region (NCR), India |
| **Period** | January 2024 – September 2024 (9 months) |
| **Total Bookings** | 150,000 |
| **Locations** | 176 unique pickup / drop zones |
| **Vehicle Types** | 7 (Auto, Go Mini, Go Sedan, Bike, Premier Sedan, eBike, Uber XL) |

---

## 🗂️ Dataset

**File:** `ncr_ride_bookings.csv` — 150,000 rows × 21 columns

| Category | Columns |
|---|---|
| Booking info | `Booking ID`, `Date`, `Time`, `Booking Status`, `Customer ID` |
| Trip details | `Vehicle Type`, `Pickup Location`, `Drop Location`, `Ride Distance` |
| Financials | `Booking Value`, `Payment Method` |
| Service quality | `Avg VTAT`, `Avg CTAT`, `Driver Ratings`, `Customer Rating` |
| Cancellations | `Cancelled Rides by Customer/Driver`, `Reason for cancelling by Customer/Driver` |
| Incomplete rides | `Incomplete Rides`, `Incomplete Rides Reason` |

### Booking Status Breakdown

| Status | Count | Share |
|---|---|---|
| ✅ Completed | 93,000 | 62.0% |
| ❌ Cancelled by Driver | 27,000 | 18.0% |
| 🔍 No Driver Found | 10,500 | 7.0% |
| 🙅 Cancelled by Customer | 10,500 | 7.0% |
| ⚠️ Incomplete | 9,000 | 6.0% |

### Vehicle Mix

| Vehicle | Bookings |
|---|---|
| Auto | 37,419 |
| Go Mini | 29,806 |
| Go Sedan | 27,141 |
| Bike | 22,517 |
| Premier Sedan | 18,111 |
| eBike | 10,557 |
| Uber XL | 4,449 |

### Key Statistics (Completed rides only)

| Metric | Value |
|---|---|
| Avg Booking Value | ₹508 (range: ₹50 – ₹4,277) |
| Avg Ride Distance | 24.6 km (range: 1 – 50 km) |
| Avg Driver Rating | 4.23 / 5.0 |
| Avg Customer Rating | 4.40 / 5.0 |
| Top Payment Method | UPI (45.0%), Cash (24.9%) |

---

## 📊 Power BI Dashboard

**3-page interactive report** with 6 cross-filtering slicers on every page:
`Date` · `Vehicle Type` · `Booking Status` · `Payment Method` · `Pickup Location` · `Drop Location`

---

### Page 1 — OVERVIEW
**Purpose:** Monitor booking volume, completion rate, and service quality KPIs at a glance.

**KPI Cards:**
`Total Bookings` · `Bookings (Completed)` · `Completion Rate %` · `Driver Cancel Rate %` · `No Driver Found Rate %` · `Avg VTAT (min)` · `VTAT SLA Hit %`

**Charts:**
- 📈 **Bookings by Hour** (area chart) — intraday demand pattern across 24h
- 🥧 **Vehicle Type** (pie chart) — fleet mix distribution
- 📊 **Payment Method** (clustered column) — digital vs. cash breakdown
- 📉 **Completion Rate and Avg VTAT** (line + column combo) — operational health over time
- ⭐ **Driver Rating** (clustered bar) — rating distribution by vehicle type
- 📋 Booking summary table and pivot for drill-down

---

### Page 2 — Revenue & Pricing
**Purpose:** Track GMV trends, pricing efficiency, and revenue contributions by segment.

**KPI Cards:**
`GMV (Completed)` · `Digital GMV (Completed)` · `Avg Booking Value (Completed)` · `Fare per km (Completed)` · `Revenue per min (Completed)` · `Cum GMV %`

**Charts:**
- 📈 **GMV Over Time** (line chart) — revenue trajectory Jan–Sep 2024
- 📊 **Completed Bookings and Avg Booking Value** (line + column combo) — volume vs. pricing trends
- 🍩 Payment method revenue split (donut chart)
- 📊 Revenue breakdown by vehicle type
- 📋 Pricing pivot by location / vehicle segment

---

### Page 3 — Supply & ETA
**Purpose:** Diagnose supply-demand gaps, ETA performance, and No Driver Found hotspots.

**KPI Cards:**
`No Driver Found Bookings` · `No Driver Found Rate %` · `Driver Cancel Bookings` · `Driver Cancel Rate %` · `VTAT P90` · `Hotspot Count (NDF ≥ 10, N ≥ 100)`

**Charts:**
- 📊 **No Driver Found Over/Under** — compares NDF rate vs. market baseline by zone
- 📋 Supply gap table — locations with highest unmet demand
- 📊 VTAT analysis by vehicle type and time window
- 📈 Driver cancellation trends and breakdown by reason

---

## 🔧 DAX Measures

| Measure | Description |
|---|---|
| `Completion Rate %` | Completed / Total Bookings |
| `Driver Cancel Rate %` | Driver-cancelled / Total Bookings |
| `No Driver Found Rate %` | NDF bookings / Total Bookings |
| `NDF Over/Under (pp)` | Location NDF rate vs. market average (percentage points) |
| `VTAT SLA Hit %` | % of completed rides where VTAT ≤ SLA threshold |
| `VTAT P90` | 90th percentile Vehicle Time Arrival Time — worst-case ETA |
| `GMV (Completed)` | Total revenue from completed rides |
| `Digital GMV (Completed)` | GMV from UPI + Wallet + Card payments |
| `Fare per km (Completed)` | GMV / Total distance for completed rides |
| `Hotspot Count (NDF≥10, N≥100)` | Zones with critical supply shortage signals |
| `Delta Driver Rating` | Change in driver rating vs. previous period |
| `Completion (pp)` | Period-over-period change in completion rate |

---

## 💡 Key Insights

1. **38% of bookings fail to complete** (driver cancellations 18% + NDF 7% + customer cancellations 7% + incomplete 6%) — a major operational gap with direct revenue impact.
2. **Driver cancellations outpace customer cancellations 2.6:1** — `Customer-related issues` and `sick passengers` are top driver reasons, suggesting demand-side friction.
3. **Auto dominates the fleet** (25% of bookings) but **Uber XL is severely undersupplied** (3% of bookings), indicating potential unmet premium demand.
4. **UPI leads payment adoption** (45%) but cash remains significant (25%) — digital incentive programs could accelerate cashless conversion.
5. **Intraday booking peaks** (visible in Bookings by Hour chart) can guide dynamic pricing and driver dispatch strategy during surge windows.
6. **NDF hotspots** identified via `Hotspot Count` measure — zones with NDF Rate ≥ 10% across ≥ 100 bookings are high-priority for supply reallocation.
7. **Wrong Address** is the #1 customer cancellation reason (22.5%) — a product fix (better address resolution UX) could recover a meaningful share of lost rides.

---

## 📁 File Structure

```
├── ncr_ride_bookings.csv   ← Raw dataset (150,000 rides × 21 columns)
└── Uber_Analysis.pbix      ← Power BI dashboard (3 pages, 30+ DAX measures)
```

---

## 🚀 How to Use

1. Download both files into the same folder
2. Open `Uber_Analysis.pbix` in **Power BI Desktop**
3. If prompted, update the data source path to point to `ncr_ride_bookings.csv`
4. Use the **6 slicers** on each page to filter by date range, vehicle type, location, or booking status
5. All visuals cross-filter — click any chart element to drill into that segment

---

## 🛠️ Tech Stack

| Tool | Usage |
|---|---|
| Power BI Desktop | Dashboard design, DAX measures, data modeling |
| DAX | 30+ custom measures for operational and revenue KPIs |
| Power Query | Data type handling, date/time column transformation |

---

## 👤 Author

**Vo Quang Khai**
Data Analyst | Finance & Data Science Background
[LinkedIn](https://www.linkedin.com/in/voquangkhaikg2003/) · [GitHub](https://github.com/voquangkhai2003)
