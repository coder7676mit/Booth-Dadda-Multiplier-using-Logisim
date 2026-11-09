# High-Speed 16x16 Signed Booth-Dadda Tree Multiplier

Welcome to the structural design and simulation repository for the **16x16 radix-4 Booth-Dadda Multiplier**. This project was developed as part of the Digital Computer Architecture (DCA) coursework at the Manipal Institute of Technology, MAHE.

### 📄 [Download the Full IEEE Project Report Here](./report.pdf)
*(Note: Ensure your compiled report is named `report.pdf` in your repository for this direct link to work, or update the filename accordingly).*

---

## 📌 Project Summary
This project implements a highly optimized, high-speed 16-bit signed multiplier built entirely from primitive logic gates in **Logisim**. The architecture tackles the three major bottlenecks of binary multiplication—generation, compression, and addition—by integrating three distinct arithmetic algorithms:

1. **Radix-4 Booth Encoding:** Scans the multiplier in 3-bit overlapping windows to halve the generated partial products, reducing the initial matrix depth from 16 rows to exactly 8 rows.
2. **Modified Sign Extension (MSE):** Eliminates the massive, resource-heavy triangle of redundant sign bits traditionally found in signed multiplication. By injecting a fixed pattern of inverted MSBs and rollover constants, it forces a continuous carry-chain that mathematically clears the redundant bits from the 32-bit window.
3. **Dadda Reduction Tree:** Employs exactly 119 combinational compressors (97 Full Adders and 22 Half Adders) to optimally flatten the partial product matrix. The tree strictly follows the Dadda threshold sequence (9 → 6 → 4 → 3 → 2), achieving final compression in just 4 parallel stages.

---

## 📂 Repository Structure

- `report.pdf` / `report.tex` — The complete, IEEE-formatted project report detailing the Boolean derivations, K-Maps, hardware utilization tables, and comparative analysis against standard array multipliers.
- `source/` — Contains the `.circ` Logisim circuit files.
  - `dadda_mul.circ`: The primary project file containing all modular components and the top-level schematic.

---

## 🚀 How to Run the Simulation

To interact with the multiplier and verify the test cases, you will need [Logisim-Evolution](https://github.com/logisim-evolution/logisim-evolution).

1. Clone or download this repository to your local machine.
2. Open **Logisim-Evolution**.
3. Go to `File > Open` and select `source/dadda_mul.circ`.
4. In the component hierarchy on the left pane, double-click the **`TEST2`** wrapper circuit.
5. Use the **Poke Tool** (the pointing finger icon) to input 16-bit hexadecimal values into the `X` and `Y` input pins.
6. The 32-bit output vector will immediately evaluate the signed two's-complement product. *(Refer to the Corner Cases table in the project report to test deep negative rollover boundaries).*

---
**Developers:** Nagendra Kudva, Suprit Shanbhag, Pramit Karmakar
