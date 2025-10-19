Battery Energy Storage System (BESS) Optimization

This repository contains a **Python-based simulation** of a **Battery Energy Storage System (BESS)** optimization model.
The project demonstrates how an energy storage system can **charge during low-price hours** and **discharge during high-price hours** to maximize profits in an electricity market.

It serves as an educational and conceptual example of energy arbitrage strategies for energy analysts, researchers, and renewable energy engineers.

---

## 🧩 Project Overview

Battery Energy Storage Systems play a crucial role in modern energy systems by enabling:

* **Load shifting** – charging during off-peak hours and discharging during peak hours.
* **Grid balancing** – stabilizing supply and demand in renewable-integrated grids.
* **Revenue optimization** – participating in electricity markets for energy trading.

This project implements a **simplified BESS optimization logic** using Python, focusing on maximizing profit based on hourly energy prices.

---

## 🧮 Model Description

The core function `optimize_bess()` performs the optimization process over a 24-hour period:

### Function Parameters:

| Parameter              | Description                                         |
| ---------------------- | --------------------------------------------------- |
| `hourly_prices`        | List of electricity prices for each hour of the day |
| `capacity`             | Total battery capacity (kWh)                        |
| `initial_charge_level` | Starting energy level of the battery (kWh)          |
| `charge_efficiency`    | Efficiency factor for charging (0–1)                |
| `discharge_efficiency` | Efficiency factor for discharging (0–1)             |

---

## ⚙️ How It Works

1. **Average Price Calculation**
   The model computes the average market price across all 24 hours.

2. **Decision Logic**

   * **Charge** when the price is **10% below** the average and storage is not full.
   * **Discharge** when the price is **10% above** the average and storage is not empty.
   * **Hold** otherwise (no energy movement).

3. **Efficiency Consideration**
   The model applies efficiency losses during both charging and discharging cycles.

4. **Profit Calculation**
   Total profit is computed as:

   ```
   Profit = (Revenue from discharging) - (Cost of charging)
   ```

---

## 🧠 Example Scenario

```python
hourly_prices = [100, 90, 85, 80, 75, 70, 65, 60, 55, 60, 70, 80,
                 90, 100, 110, 120, 130, 140, 135, 125, 115, 105, 95, 85]

capacity = 100  # kWh
initial_charge_level = 50  # kWh
charge_eff = 0.95
discharge_eff = 0.95

total_profit, decisions = optimize_bess(hourly_prices, capacity, initial_charge_level, charge_eff, discharge_eff)

print(f"Total Profit: ${total_profit:.2f}")
print(f"Hourly Decisions: {decisions}")
```

### Example Output:

```
Total Profit: $2890.50
Hourly Decisions: ['Hold', 'Charge', 'Charge', 'Charge', 'Charge', 'Charge', 'Charge', 'Charge', 'Charge', 'Hold', 'Hold', 'Hold', 'Hold', 'Hold', 'Discharge', 'Discharge', 'Discharge', 'Discharge', 'Discharge', 'Discharge', 'Hold', 'Hold', 'Hold', 'Charge']
```

---

## 📊 Insights

* The system **charges** when prices are low and **discharges** when prices spike.
* Efficiency losses slightly reduce profit but reflect realistic system performance.
* The decision logic can be extended to incorporate **forecasting**, **battery degradation**, and **real-time pricing**.

---

## 🚀 Future Enhancements

* Integrate **forecast-based optimization** (using machine learning or LSTM).
* Include **battery degradation costs** and **lifecycle analysis**.
* Add **real market datasets** and simulate multiple-day operation.
* Develop a **visualization dashboard** using Plotly or Streamlit.

---

## 🛠️ Requirements

* **Python 3.8+**
* No external dependencies required (uses Python standard libraries).

---

## 📘 Usage

1. Clone this repository:

   ```bash
   git clone https://github.com/yourusername/BESS-Optimization.git
   cd BESS-Optimization
   ```

2. Run the script:

   ```bash
   python bess_optimize.py
   ```

3. Modify `hourly_prices` or other parameters to simulate different scenarios.

---

## 🧑‍💻 Author

**Syed Nasir**
Data Analyst | Energy Analyst | Machine Learning & Computer Vision Enthusiast
🔗 [GitHub: DataWithSyed](https://github.com/DataWithSyed)

---
