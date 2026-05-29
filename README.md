# HCL_MAIN_HACKATHON
#  Hospitality Management Analytics Dashboard

##  Project Title

**Hotel Occupancy & Revenue Management System using SQL, Informatica ETL, and Power BI**


##  Project Overview

The Hospitality Management Analytics Dashboard is a data-driven solution developed to help hotel management monitor daily operations, occupancy, guest activity, and revenue performance.

The project integrates **ETL processing, SQL database management, and interactive Power BI reporting** to transform raw hospitality data into meaningful business insights.

This system enables hotel management teams to make informed decisions through real-time analytical reporting.



##  Business Objective

Hotels need visibility into:

* Daily guest check-ins and check-outs
* Room occupancy status
* Revenue generation
* Room-type performance
* Guest stay behavior
* High-value customer identification

This solution helps management optimize hotel performance and operational efficiency.

##  Data Sources

The system processes data from **three hospitality datasets (CSV files)**.

### 1. Guest Master Dataset

Contains guest profile information.

**Business Purpose:**
Maintains customer information for guest tracking and customer analytics.

**Key Attributes:**

* Guest ID
* Guest Name
* Gender
* Contact Information
* Address Details
* Government ID Details
* Registration Date


### 2. Check-In / Check-Out Dataset

Contains transactional stay information.

**Business Purpose:**
Tracks hotel stays, occupancy, booking source, payments, and revenue.

**Key Attributes:**

* Stay ID
* Guest ID
* Room ID
* Check-in Date & Time
* Check-out Date & Time
* Booking Source
* Room Rate
* Extra Charges
* Discount Amount
* Payment Mode
* Total Revenue
* Stay Status


### 3. Room Master Dataset

Contains hotel room details.

**Business Purpose:**
Maintains room information and room availability.

**Key Attributes:**

* Room ID
* Room Type
* Floor Number
* Bed Type
* Base Rate
* Occupancy Capacity
* Room Status
* Amenities


## Solution Architecture

Raw CSV Files -> Informatica ETL Pipeline -> SQL Database (Data Warehouse Layer) -> Power BI Dashboard & Analytics


## ETL Implementation (Informatica)

The ETL pipeline was designed using Informatica to automate hospitality data processing.

### Data Extraction

* Read daily CSV files
* Incremental load using LastUpdated column
* Process only new or updated records

### Data Transformation

Performed business validations including:

#### Guest Lookup

Fetch guest details using GuestID.

#### Room Lookup

Fetch room information using RoomID.

#### Stay Validation

Validated stay records using:

VALID_STAY:
CheckoutDateTime is available

INVALID_STAY:
CheckoutDateTime is NULL

#### Revenue Calculation

Calculated hotel revenue using:

Revenue =
(Room Rate × Stay Duration)

* Extra Charges
  − Discount Amount

#### Error Handling

Handled:

* Missing check-out dates
* Invalid records
* Null values


## Database Design

The project follows a **Star Schema Data Model** for better analytical performance.

### Fact Table

#### FACT_GUEST_STAY

Stores transactional hospitality data.

**Contains:**

* Stay ID
* Guest ID
* Room ID
* Revenue
* Stay Duration
* Payment Details
* Occupancy Information

---

### Dimension Tables

#### DIM_GUEST

Stores guest profile details.

#### DIM_ROOM

Stores room-related information.

#### DIM_DATE

Stores date intelligence for time analysis.

---

##  Data Model (Star Schema)

DIM_GUEST
|
FACT_GUEST_STAY
|

DIM_ROOM

Benefits:

* Faster query performance
* Optimized Power BI reporting
* Better scalability
* Simplified business analytics


##  Power BI Dashboard

### Dashboard Objective

To provide hotel management with a centralized business intelligence view of hotel performance.

---

## KPI Metrics Implemented

### Revenue KPIs

* Total Revenue Generated
* Average Room Rate
* Revenue per Occupied Room

### Occupancy KPIs

* Total Guests
* Total Bookings
* Occupancy Rate %

### Operational KPIs

* Room-Type Performance
* Daily Revenue Trends
* Guest Revenue Analysis



## Dashboard Visualizations

### KPI Cards

Executive-level business summary.

### Revenue by Room Type

Analyze which room category generates maximum revenue.

### Occupancy Rate Gauge

Visual representation of occupancy performance.

### Revenue Trend Analysis

Daily revenue tracking over time.

### Guest Revenue Analysis

Identify high-value customers.

### Interactive Filters

* Check-in Date
* Room Type
* Guest Name

---

## 📈 Analytical Use Cases

### Use Case 1: Daily Occupancy & Revenue Summary

Business Goal:
Track hotel performance daily.

KPIs:

* Total Rooms Available
* Rooms Occupied Today
* Occupancy Rate
* Revenue Generated
* Revenue per Room


### Use Case 2: Room-Type Performance Analysis

Business Goal:
Identify best-performing room categories.

KPIs:

* Total Bookings by Room Type
* Occupancy Rate by Room Type
* Revenue by Room Type
* Average Daily Rate

### Use Case 3: Guest Stay Duration Analysis

Business Goal:
Understand customer stay patterns.

KPIs:

* Average Stay Duration
* Minimum Stay Duration
* Maximum Stay Duration
* Total Guest Nights


## Use Case 4: High-Value Guest Identification

Business Goal:
Identify premium customers.

KPIs:

* Total Revenue per Guest
* Visit Frequency
* Average Spend per Stay


##  Technology Stack

**ETL Tool:** Informatica IICS
**Database:** SQL Developer / Oracle SQL
**Visualization:** Power BI
**Programming Concepts:** SQL Window Functions, Triggers, Procedures
**Data Source:** CSV Files

##  Business Outcome

This solution enables hotel management to:

* Improve occupancy tracking
* Monitor hotel revenue
* Analyze customer behavior
* Optimize room utilization
* Support business decision-making through analytics
