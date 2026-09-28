# ⚡ The Process of EV Charging

> A technical presentation explaining what actually happens during EV charging — from individual lithium-ion cells and battery-pack configuration to BMS operation, AC/DC charging, DC fast-charging topology, losses, and thermal management.

---

## 📌 About This Project

Electric vehicle charging is often simplified as:

**"Connect the charger → supply current → battery gets charged."**

In reality, EV charging involves multiple stages of power conversion, battery-cell management, communication, thermal management, and protection.

This presentation explains the **process of EV charging** from the battery cells to the charging station and explores the engineering principles behind modern EV charging systems.

---

## 🎯 Topics Covered

* What people usually think about EV charging
* What EV charging actually is
* EV battery cell configuration
* Why EVs use multiple small cells
* Series and parallel battery-pack configurations
* Problems with different battery-pack topologies
* Battery Management System (BMS)
* AC vs DC charging
* Level 1 and Level 2 charging
* DC fast charging
* DC fast-charging topology
* Voltage, current and power losses
* Thermal management
* Why fast EV chargers are physically large

---

# 🔋 1. What Is EV Charging Actually?

An EV battery is not one giant battery cell.

It consists of **multiple small lithium-ion cells connected together** to achieve the required voltage and capacity.

EV battery packs operate at high voltages, with the presentation using approximately **600 V** as an example.

For DC charging, the main charging system is located outside the vehicle in the charging station.

---

# 🔬 2. Why Not Use One Giant Battery Cell?

A lithium-ion cell has a limited operating voltage because of the electrochemical properties of its electrode materials and electrolyte.

If we tried to deliver high power at a very low voltage, the required current would become extremely high.

The basic power equation is:

$$
P = VI
$$

Therefore:

$$
I = \frac{P}{V}
$$

For the same power, increasing the voltage reduces the required current.

High current also produces resistive losses:

$$
P_{loss}=I^2R
$$

Therefore, using a higher battery voltage helps reduce current and associated resistive losses.

---

# 🔋 3. EV Battery Pack Configuration

Battery cells can be connected using combinations of:

* **Series connection**
* **Parallel connection**

Two configurations discussed in the presentation are:

### 1. Series → Parallel

Cells are first connected in series and the resulting strings are then connected in parallel.

### 2. Parallel → Series

Cells are first connected in parallel and the resulting groups are then connected in series.

The presentation explains that both configurations can have the same overall voltage and current rating, while also discussing why battery-pack architecture matters for BMS design and fault behavior.

---

# ⚠️ 4. Problems With Series → Parallel Configuration

When multiple series strings are connected in parallel, differences in string voltage can result in **equalization currents** between the strings.

For example:

```text
String A → 402 V
String B → 398 V
String C → 400 V
String D → 397 V
```

If these strings are connected together, their voltage differences can cause current to flow between them.

A weak or aged cell can also limit the performance of an entire series string.

---

# 🧠 5. Battery Management System (BMS)

The **Battery Management System (BMS)** is an electronic system responsible for monitoring and controlling important battery parameters.

It monitors parameters such as:

* Cell voltage
* Current
* Temperature
* State of Charge (SOC)

The BMS helps maintain safe, efficient and reliable operation of the battery pack.

The presentation also describes monitoring the voltage of battery sections and bypassing charging current when required.

### Simplified BMS Concept

```text
              BATTERY PACK
                   │
                   ▼
             ┌───────────┐
             │    BMS    │
             └───────────┘
              │    │    │
              ▼    ▼    ▼
           Voltage Current Temperature
              │
              ▼
        Cell Monitoring
              │
              ▼
       Charging Protection
```

---

# 🔌 6. EV Charging System

The presentation divides EV charging into two main categories:

```text
                    EV CHARGING
                         │
              ┌──────────┴──────────┐
              │                     │
         AC CHARGING           DC CHARGING
              │                     │
        ┌─────┴─────┐               │
        │           │               ▼
     LEVEL 1      LEVEL 2       DC FAST CHARGING
```

---

# 🏠 7. AC Charging

## Level 1 Charging

* Single-phase charging
* Low power
* Long charging time

## Level 2 Charging

* Higher power than Level 1
* Uses a three-phase system in the presentation
* Suitable for higher-power charging

### AC Charging Architecture

```text
       GRID AC
          │
          ▼
┌─────────────────────┐
│  ONBOARD CHARGER    │
│      AC → DC        │
└─────────────────────┘
          │
          ▼
      DC OUTPUT
          │
          ▼
    EV BATTERY PACK
```

In AC charging, the AC supply is converted to DC by the **onboard charger** before being supplied to the battery.

---

# ⚡ 8. DC Fast Charging

DC fast charging uses an **external charging system**.

The main conversion stages are located inside the charging station rather than relying entirely on the vehicle's onboard charger.

```text
             GRID AC
                │
                ▼
        ┌────────────────┐
        │ AC → DC         │
        │ Rectifier       │
        └────────────────┘
                │
                ▼
          HIGH-VOLTAGE DC
                │
                ▼
        ┌────────────────┐
        │ High-Frequency │
        │ DC-DC Converter│
        └────────────────┘
                │
                ▼
        CONTROLLED DC
                │
                ▼
          EV BATTERY
```

The presentation describes first converting AC into DC and then using a high-frequency DC-DC converter to adjust the voltage.

---

# 🔄 9. Why Convert AC to DC First?

The charging system follows:

```text
AC
 ↓
AC → DC Conversion
 ↓
High-Voltage DC
 ↓
High-Frequency DC → DC Conversion
 ↓
Controlled DC
 ↓
EV Battery
```

The EV battery voltage can vary significantly during charging.

Therefore, the charging system needs controlled power conversion to provide the appropriate voltage and current to the battery.

The presentation also discusses high-frequency switching and the use of smaller ferrite-core transformers instead of large low-frequency iron-core transformers.

---

# 📉 10. Why Higher Voltage Reduces Power Loss

The basic relationship is:

$$
P=VI
$$

Therefore:

$$
I=\frac{P}{V}
$$

For a fixed power, increasing voltage decreases current.

The resistive loss is:

$$
P_{loss}=I^2R
$$

If the voltage is doubled:

$$
I_{new}=\frac{I}{2}
$$

Therefore:

$$
P_{loss,new}
=
\left(\frac{I}{2}\right)^2R
$$

$$
P_{loss,new}=\frac{I^2R}{4}
$$

So the resistive power loss becomes **one-fourth**.

This demonstrates why higher-voltage electrical systems can reduce current-related losses.

---

# 📊 11. Level 1 vs Level 2 vs DC Fast Charging

| Parameter           | Level 1  | Level 2              | DC Fast          |
| ------------------- | -------- | -------------------- | ---------------- |
| Supply              | AC       | AC                   | DC               |
| Conversion          | On-board | On-board             | Off-board        |
| Typical Application | Home     | Home / Work / Public | Highway / Public |
| Power               | Low      | Higher               | Very High        |
| Charging Current    | Low      | Moderate             | High             |
| Charging Time       | Long     | Moderate             | Short            |
| Grid Impact         | Lower    | Higher               | High             |
| Thermal Management  | Moderate | Moderate             | Critical         |

---

# 🌡️ 12. Why Are Fast EV Chargers So Large?

Fast chargers can handle **hundreds of kilowatts of electrical power**.

This creates several engineering challenges.

### 🔥 High Current

High current causes significant:

$$
I^2R
$$

losses.

These losses are converted into heat.

### ❄️ Thermal Management

Fast chargers may require:

* Large heat sinks
* Fans
* Liquid cooling systems

### ⚙️ Large Power Components

High-power chargers also require appropriately rated:

* Rectifiers
* Semiconductor switches
* Inductors
* Capacitors

Therefore, high power handling, power losses and thermal management contribute significantly to the physical size of fast EV chargers.

---

# 🧮 13. Important Engineering Equations

### Electrical Power

$$
P=VI
$$

### Current

$$
I=\frac{P}{V}
$$

### Resistive Power Loss

$$
P_{loss}=I^2R
$$

These equations help explain the relationship between:

**Voltage → Current → Power → Losses → Heat**

---

# 🧩 14. Complete EV Charging Process

A simplified view of the complete process is:

```text
             ELECTRICAL GRID
                    │
                    ▼
             AC POWER INPUT
                    │
          ┌─────────┴─────────┐
          │                   │
          ▼                   ▼
      AC CHARGING         DC CHARGING
          │                   │
          ▼                   ▼
   ONBOARD CHARGER      EXTERNAL CHARGER
          │                   │
          │             ┌─────┴─────┐
          │             ▼           ▼
          │         AC → DC      DC → DC
          │             │           │
          └─────────────┴───────────┘
                        │
                        ▼
                 CONTROLLED DC
                        │
                        ▼
                  BMS MONITORING
                        │
                        ▼
                  BATTERY CELLS
                        │
                        ▼
                 STORED ENERGY
```

---

# 🎥 Watch the Presentation

### ▶️ The Process of EV Charging

Click the thumbnail below to watch the video:

[![The Process of EV Charging](https://img.youtube.com/vi/IqDkF2qldaE/hqdefault.jpg)](https://youtu.be/IqDkF2qldaE)

**YouTube:** https://youtu.be/IqDkF2qldaE

---

# 📑 Presentation Details

**Title:** The Process of EV Charging
**Author:** Nikhil Kushwah
**Branch:** Electrical Engineering
**Semester:** 7th Semester
**Institution:** SATI Vidisha
**Date:** 26 September 2026

---

# 📚 Topics at a Glance

| Topic                           | Status |
| ------------------------------- | :----: |
| EV Battery Cells                |    ✅   |
| Series / Parallel Configuration |    ✅   |
| Battery Pack Topology           |    ✅   |
| BMS                             |    ✅   |
| AC Charging                     |    ✅   |
| Level 1 Charging                |    ✅   |
| Level 2 Charging                |    ✅   |
| DC Fast Charging                |    ✅   |
| DC-DC Converter                 |    ✅   |
| Power Losses                    |    ✅   |
| Thermal Management              |    ✅   |
| Fast Charger Architecture       |    ✅   |

---

# 👨‍💻 Author

### Nikhil Kushwah

**Electrical Engineering Student**
**SATI Vidisha**

Interested in:

* Electrical Engineering
* Power Electronics
* EV Technology
* Embedded Systems
* Hardware Development
* Engineering Research & Development

---

## ⭐ Support

If you found this project useful:

⭐ Star this repository
📺 Watch the presentation
🔗 Share it with other engineering students
💬 Feel free to discuss or suggest improvements

---

## 📜 License

This project is intended for **educational and academic purposes**.
