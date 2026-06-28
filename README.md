# 🚕 Uber Airport Supply-Demand Bottleneck: Root Cause Analysis (RCA)

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Libraries](https://img.shields.io/badge/Libraries-Pandas%20%7C%20Seaborn%20%7C%20Matplotlib-orange)
![Domain](https://img.shields.io/badge/Domain-Product%20Analytics%20%7C%20Supply%20Chain-brightgreen)
![Status](https://img.shields.io/badge/Status-Completed-success)

> *"Riders are furious! They book a cab, but either the driver cancels at the last minute OR the app says 'No Cars Available'. We are losing thousands of rides per week — especially to and from the airport."*  
> — **Hypothetical Monday Morning Briefing, Uber HQ**

---

## 📌 Executive Summary

This project is an end-to-end **Exploratory Data Analysis (EDA) & Root Cause Analysis** designed to diagnose severe trip failure rates at airport pickup points. 

Rather than treating unmet demand as a single blanket issue, data segmentation reveals **two mutually exclusive operational supply-chain failures** occurring at opposite times of the day.

| Peak Window | Route Direction | Primary Failure Mode | Core Operational Bottleneck |
| :--- | :--- | :--- | :--- |
| **Morning Rush** *(5 AM – 9 AM)* | City $\rightarrow$ Airport | **Driver Cancelled** | Unprofitable "Deadhead" *(Empty return leg)* |
| **Evening Rush** *(5 PM – 9 PM)* | Airport $\rightarrow$ City | **No Cars Available** | Absolute Supply Deficit *(Fleet trapped in urban rush hour)* |

---

## 📊 Key Visual Insights

### 1. The Macro View: A Strictly Bi-Modal Demand Curve
The 24-hour demand aggregation confirms two massive operational spikes separated by a midday lull. Interventions must be strictly time-separated.

<img width="1000" height="600" alt="lineChart_hrWise" src="https://github.com/user-attachments/assets/97a18780-a542-4a3d-a939-a57f093a1daa" />


***

### 2. The Morning Bottleneck: Driver Cancellations (5 AM – 9 AM)
During early morning hours, requests originating in the city heading to the airport experience an extreme cancellation rate. 

* **The Behavioral Driver Logic:** Drivers accept the request to secure the fare, see the Airport destination, and immediately cancel.
* **The Economic Root Cause:** At 6:00 AM, arriving flights are near zero. Dropping a passenger at the terminal guarantees the driver a **30km uncompensated return drive** back to the urban core. 

<img width="1000" height="600" alt="Picker_Point" src="https://github.com/user-attachments/assets/d5246995-7c2b-4dbe-b1f8-d08e4ea948e4" />


***

### 3. The Evening Bottleneck: Fleet Deficit (5 PM – 9 PM)
During evening hours, passengers landing at the airport face an overwhelming `No Cars Available` screen.

* **The Trigger:** Business flights land in synchronized waves, creating an instant, concentrated demand shock.
* **The Geographic Root Cause:** Evening flight arrivals coincide with peak city rush hour. Urban drivers are occupied capturing high-frequency, high-surge short trips inside the city; they refuse to travel 30km outward into highway traffic jams.

<img width="1400" height="600" alt="BarChart_Hour_Wise(Airport)" src="https://github.com/user-attachments/assets/1ec4ac1c-5a82-4513-bd96-63f205bfa6fb" />


---

## 💡 Strategic Product Roadmap 

To capture this lost revenue, Uber must deploy **mutually exclusive dispatch logic** for AM vs. PM operations:

### 🌅 Morning Strategy *(Fixing Behavioral Cancellations)*
1. **Queue-Jump Priority:** Guarantee morning drop-off drivers instant **#1 queue placement** at the airport terminal for incoming morning flights, eliminating the fear of an empty return drive.
2. **Deadhead Micro-Subsidization:** Introduce a slight ₹80 *Airport Return Surcharge* on morning trips to explicitly subsidize driver fuel for the deadhead leg.

### 🌃 Evening Strategy *(Solving Geographic Fleet Lockup)*
1. **Geofenced Pre-Surge:** Trigger an aggressive, isolated **1.8x Airport Surge Multiplier at 4:30 PM** *(30 minutes prior to landing waves)* to actively pull empty city cabs toward the terminals.
2. **Flight-Sync Pre-Booking:** Incentivize travelers booking flight tickets to reserve cabs 12 hours in advance, locking independent driver supply into guaranteed minimum payouts.

---

## 🛠️ Tech Stack & Repository Structure

* **Language:** Python 3.x
* **Data Manipulation:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib.pyplot`, `seaborn`

```text
├── Uber_Airport_RCA_AarishAnsari.pdf   # Executive 6-Slide Presentation Deck
├── [Notebook_Name].ipynb               # Full Python EDA & Visual script
├── BarChart_Hour_Wise(city).png        # Exported chart asset
├── BarChart_Hour_Wise(Airport).png     # Exported chart asset
├── lineChart_hrWise.png                # Exported chart asset
├── Days_Wise.png                       # Exported chart asset
├── pie_status.png                      # Exported chart asset
└── README.md                           # Project Documentation
