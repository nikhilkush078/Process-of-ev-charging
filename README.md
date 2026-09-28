# ⚡ The Process of EV Charging

> A technical presentation explaining what actually happens during EV charging — from individual lithium-ion cells and battery-pack configuration to BMS operation, AC/DC charging, and DC fast-charging topology.

---

## 📌 About This Project

Electric vehicle charging is often simplified as:

**"Connect the charger → supply current → battery gets charged."**

In reality, EV charging involves multiple stages of power conversion, battery-cell management, communication, thermal management, and protection.

This presentation explains the complete charging process and the engineering behind it.

### 🎯 Main Topics Covered

* What EV charging actually means
* EV battery cell configuration
* Why EVs use multiple small cells instead of one giant cell
* Series and parallel battery-pack configurations
* Battery Management System (BMS)
* AC vs DC charging
* Level 1, Level 2 and DC fast charging
* DC fast-charging topology
* Voltage, current and power losses
* Thermal management
* Why fast EV chargers are physically large

---

## 🔋 1. What Is EV Charging Actually?

An EV battery is not a single giant battery.

It consists of **multiple small lithium-ion cells connected together** to achieve the required voltage and capacity.

Typical EV battery packs operate at **high voltages**, with the presentation using approximately **600 V** as an example.

The main charging system for DC charging is located outside the vehicle in the charging station.

---

## 🔬 2. Why Not Use One Giant Battery Cell?

A lithium-ion cell has a limited operating voltage because of the electrochemical properties of its electrode materials and electrolyte.

If we tried to deliver high power at a very low voltage, the required current would become extremely high.

The basic relationship is:

$$
P = VI
$$

Therefore,

$$
I = \frac{P}{V}
$$

For the same power, increasing the voltage allows the required current to decrease.

High current also produces significant resistive losses:

$$
P_{loss}=I^2R
$$

Therefore, operating an EV battery at a higher voltage helps reduce current and associated losses.

---

## 🔋 3. EV Battery Pack Configuration

Battery cells can be arranged using combinations of:

* **Series connection**
* **Parallel connection**

Two common arrangements are:

1. First series → then parallel
2. First parallel → then series

The presentation discusses both configurations and their voltage/current characteristics.

### Why Cell Configuration Matters

The battery-pack architecture affects:

* Voltage
* Current capability
* BMS complexity
* Cell balancing
* Fault behavior
* Thermal management

---

## ⚙️ 4. Battery Management System (BMS)

The **Battery Management System (BMS)** is one of the most important systems in an EV battery pack.

It monitors and controls parameters such as:

* Cell voltage
* Current
* Temperature
* State of Charge (SOC)

The BMS helps ensure safe, efficient and reliable battery operation.

### Simplified BMS Function

```text
       Battery Pack
            │
            ▼
      ┌─────────────┐
      │     BMS     │
      └─────────────┘
       │    │    │
       ▼    ▼    ▼
    Voltage Current Temperature
       │
       ▼
 Cell Monitoring & Protection
```

The BMS can also control or bypass charging current for particular battery sections when required.

---

# 🔌 5. EV Charging Types

The presentation divides EV charging into:

```text
                 EV CHARGING
                      │
             ┌────────┴────────┐
             │                 │
          AC Charging      DC Charging
             │                 │
       ┌─────┴─────┐       DC Fast Charging
       │           │
    Level 1      Level 2
```

The major difference is where AC-to-DC conversion occurs.

---

## 🏠 6. AC Charging

### Level 1

* Single-phase charging
* Low power
* Long charging time
* Commonly associated with home charging

### Level 2

* Higher power than Level 1
* Uses a three-phase system in the presentation
* Suitable for home, workplace and public charging

The AC charging architecture sends grid AC to the vehicle's onboard charger, which converts it to DC for the battery.

```text
Grid AC
   │
   ▼
┌──────────────────┐
│ Onboard Charger  │
└──────────────────┘
   │
   ▼
   DC
   │
   ▼
Battery Pack
```

---

# ⚡ 7. DC Fast Charging

DC fast charging is different because the major power conversion system is located outside the vehicle.

```text
Grid AC
   │
   ▼
┌─────────────────┐
│ AC → DC         │
│ Rectifier       │
└─────────────────┘
   │
   ▼
 High Voltage DC
   │
   ▼
┌─────────────────┐
│ High-Frequency  │
│ DC-DC Converter │
└─────────────────┘
   │
   ▼
Controlled DC
   │
   ▼
EV Battery
```

The presentation describes first converting AC to DC and then using a high-frequency DC-DC converter to adjust the voltage.

---

## 🔄 8. Why AC Is Converted to DC First

The charging system first converts:

**AC → DC**

and then uses a high-frequency DC-DC conversion stage.

This allows the charger to provide controlled DC voltage suitable for the varying voltage of the EV battery.

The presentation also discusses the use of high-frequency switching and smaller ferrite-core magnetic components instead of large low-frequency iron-core transformers.

---

# 📉 9. Why Increasing Voltage Reduces Losses

Power:

$$
P=VI
$$

Therefore:

$$
I=\frac{P}{V}
$$

Copper/conductor loss:

$$
P_{loss}=I^2R
$$

If the voltage is doubled while delivering the same power:

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

So the resistive loss becomes **one-fourth** of the original value.

This is one of the important engineering reasons for using high-voltage systems in EVs and high-power charging.

---

# 🚗 10. Level 1 vs Level 2 vs DC Fast Charging

| Parameter          | Level 1  | Level 2              | DC Fast          |
| ------------------ | -------- | -------------------- | ---------------- |
| Supply             | AC       | AC                   | DC at vehicle    |
| Conversion         | On-board | On-board             | Off-board        |
| Application        | Home     | Home / Work / Public | Highway / Public |
| Power              | Low      | Higher               | Very High        |
| Charging Current   | Low      | Moderate             | High             |
| Charging Time      | Long     | Moderate             | Short            |
| Grid Impact        | Lower    | Higher               | High             |
| Thermal Management | Moderate | Moderate             | Critical         |

The comparison follows the charging characteristics presented in the presentation.

---

# 🌡️ 11. Why Are Fast EV Chargers So Large?

DC fast chargers can handle **hundreds of kilowatts of electrical power**.

This creates several engineering challenges:

### High Current

High current produces:

$$
P_{loss}=I^2R
$$

which creates heat.

### Thermal Management

Fast chargers require systems such as:

* Large heat sinks
* Fans
* Liquid cooling

### Power Electronics

Large power levels also require appropriately rated:

* Rectifiers
* Semiconductor switches
* Inductors
* Capacitors

The presentation identifies these components and thermal requirements as major reasons for the physical size of fast chargers.

---

# 🧠 Key Engineering Concepts

This presentation connects several electrical-engineering concepts:

```text
Battery Cells
      ↓
Series / Parallel Configuration
      ↓
High-Voltage Battery Pack
      ↓
BMS
      ↓
Charging System
      ↓
Power Conversion
      ↓
Controlled DC
      ↓
Battery Charging
      ↓
Thermal Management
```

### Important equations

**Electrical Power**

$$
P=VI
$$

**Current**

$$
I=\frac{P}{V}
$$

**Resistive Power Loss**

$$
P_{loss}=I^2R
$$

These equations help explain why EV charging systems use high voltages and why thermal management becomes increasingly important as charging power increases.

---

# 🎥 Presentation / Video

### ▶️ Watch the Explanation

Click the thumbnail below to watch the video:

[![The Process of EV Charging](https://img.youtube.com/vi/lBcdPCvLNJH5QvfJ/maxresdefault.jpg)](https://youtu.be/IqDkF2qldaE?si=lBcdPCvLNJH5QvfJ)

---

# 📊 Presentation

**Topic:** The Process of EV Charging
**Author:** Nikhil Kushwah
**Branch:** Electrical Engineering
**Semester:** 7th Semester
**Institution:** SATI Vidisha
**Date:** 26 September 2026

---

# 📚 Topics at a Glance

| Topic                           | Covered |
| ------------------------------- | :-----: |
| EV Battery Cells                |    ✅    |
| Series / Parallel Configuration |    ✅    |
| BMS                             |    ✅    |
| AC Charging                     |    ✅    |
| Level 1 Charging                |    ✅    |
| Level 2 Charging                |    ✅    |
| DC Fast Charging                |    ✅    |
| DC-DC Converter                 |    ✅    |
| Charging Losses                 |    ✅    |
| Thermal Management              |    ✅    |
| Fast Charger Architecture       |    ✅    |

---

## 👨‍💻 Author

**Nikhil Kushwah**

Electrical Engineering Student
SATI Vidisha

---

## ⭐ Support

If you found this project useful:

* ⭐ Star this repository
* 📺 Watch the presentation video
* 🔗 Share it with other engineering students
* 💬 Feel free to discuss or suggest improvements

---

## 📜 License

This project is intended for educational and academic purposes.
