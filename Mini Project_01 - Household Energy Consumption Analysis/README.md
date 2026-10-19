# Mini Project_01 - Household Energy Consumption Analysis

## 📌 Overview
This project cleans, engineers features, and analyzes the **Individual Household Electric Power Consumption** dataset (spanning December 2006 to November 2010). The objective is to prepare minute-by-minute electrical measurements for time-series modeling and uncover meaningful patterns in household electricity usage across different time scales and appliance groups.

---

## 📂 Project Workflow & Notebooks

1. **[01_Data Cleaning](notebooks/01_cleaning.ipynb)**
   * Loads the raw dataset (`2,075,259` rows, `9` columns).
   * Merges `Date` and `Time` into a unified `Datetime` column and converts string-based power measurements into numeric (`float64`) types.
   * Identifies and removes `25,979` missing records and verifies zero duplicate entries.
   * Exports the cleaned dataset (`2,049,280` rows, `8` columns) to `data/data_cleaned.csv`.

2. **[02_Feature Engineering](notebooks/02_feature_engineering.ipynb)**
   * Expands the cleaned dataset from `8` to `39` columns to capture temporal and electrical dynamics.
   * **Temporal Features:** Extracts `Year`, `Quarter`, `Month`, `Day`, `Hour`, `WeekOfYear`, `DayOfWeek`, `IsWeekend`, `Day_Period` (Night, Morning, Afternoon, Evening), `Season`, and `IsPeakHour` (5 PM – 10 PM).
   * **Electrical & Consumption Metrics:** Computes `Sub_metering_total`, `Other_energy_consumption` (unmetered Watt-hours/min), `Apparent_Power`, `Power_Factor`, `Impedance`, `Active_Reactive_Difference`, `Reactive_Power_Ratio`, `Consumption_Level` (Low, Medium, High), and sub-meter ratios.

3. **[03_Normal Visualizations](notebooks/03_normal_visualizations.ipynb)**
   * Aggregates active power, reactive power, and sub-metering data across hourly, daily, monthly, yearly, and seasonal dimensions.
   * Visualizes consumption trends and compares home meter consumption rates using `matplotlib`.

4. **[04_Dashboard](notebooks/04_dashboard.ipynb)**
   * Builds an interactive **Energy Command Center** using `Plotly`.
   * Displays high-level KPIs: Average Active Power (`1.09 kW`), Peak Active Power (`11.12 kW`), Average Voltage (`240.84 V`), and Average Current (`4.63 A`).
   * Provides interactive multi-panel visualizations for time trends, consumption patterns (Weekday vs. Weekend, Seasonal, Day Period), and appliance group breakdowns.

---

## 📊 Dataset Description

| Column | Unit / Format | Description |
| :--- | :--- | :--- |
| **`Datetime`** | `YYYY-MM-DD HH:MM:SS` | Timestamp of the recording (sampled every minute). |
| **`Global_active_power`** | Kilowatts (kW) | Total active power consumed by the household. |
| **`Global_reactive_power`** | Kilowatts (kW) | Total reactive power consumed by inductive/capacitive loads. |
| **`Voltage`** | Volts (V) | Average minute-by-minute household AC voltage. |
| **`Global_intensity`** | Amperes (A) | Average current intensity drawn by the household. |
| **`Sub_metering_1`** | Watt-hours (Wh) | Energy consumed by the **kitchen** (dishwasher, oven, microwave). |
| **`Sub_metering_2`** | Watt-hours (Wh) | Energy consumed by the **laundry room** (washing machine, dryer, refrigerator, light). |
| **`Sub_metering_3`** | Watt-hours (Wh) | Energy consumed by **climate control** (electric water heater, air conditioner). |

---

## 🛠️ Technologies & Libraries
* **Python 3**
* **Data Manipulation:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib`, `plotly`, `missingno`

---

## 🚀 How to Run
1. Clone the repository and place the raw `household_power_consumption.txt` file inside the `data/` directory.
2. Install required dependencies:
   ```bash
   pip install numpy pandas matplotlib missingno plotly ipython