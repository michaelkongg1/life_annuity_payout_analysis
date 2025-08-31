# 💸 Life Annuity Payout Scenario Analysis (Excel)

A compact **Excel-only** model that estimates the **actuarial present value (APV)** of a **life annuity** using age- and gender-specific mortality. Includes a **Due / Immediate** timing toggle and an **interest-rate sensitivity** view for quick what-ifs. Built to be beginner-friendly and portfolio-ready.

---

## 🚀 Highlights
- **Timing toggle:** Life annuity-**due** by default; switch to **immediate**
- **Inputs:** Start Age, Gender, Interest Rate, Timing
- **Outputs:** Survival curve, discounting, **EPV by age**, **APV**
- **Sensitivity:** APV vs interest (e.g., 2–5%) with a clean chart
- Truncated at **age 100** for a lightweight, transparent demo

---

## 🗂️ Files & Sheets
**`Life_Annuity_Payout_Analysis.xlsx`**
- **`input table`** — user inputs & toggles (StartAge, Gender, Rate, Timing)
- **`calculator`** — core pipeline (Age grid, \(t\), survival, discounting, EPV, APV)
- **`moralitytable`** — mortality data (Age, qx_M, qx_F, M_lx, F_lx)  
  *(sheet name kept as in workbook)*
- **`sensitivity`** — APV vs rate table & chart

---

## 🔧 Inputs (on `input table`)
- **Timing:** `Due` / `Immediate`
- **StartAge:** e.g., 60, 65, 80
- **Gender:** `Male` / `Female`
- **Annual interest (i):** e.g., 3% (enter as 0.03 and format as %)

---

## 📊 Key Outputs
- **APV (Due/Immediate):** summary cell on `calculator`  
- **EPV by age:** on `calculator` (used to sum to APV)
- **Sensitivity chart:** APV vs interest on `sensitivity`

---

## 🧮 How It Works (conceptually)
1. Build an age grid from **StartAge → 100**.
2. Compute **survival from StartAge** using the selected gender’s cumulative survivors.
3. Apply **time-value of money** via annual discounting at the chosen interest rate.
4. Multiply survival × discount each year to get **EPV per $1**.
5. **Sum EPV** over ages to get **APV**.  
   - **Due** includes the certain \(t=0\) payment.  
   - **Immediate** excludes \(t=0\) (so it’s approximately **Due − 1** per \$1/yr).

---

## 📈 Sensitivity (APV vs Interest)
The `sensitivity` sheet shows how APV changes across a small set of interest rates (e.g., 2–5%). Use it to quickly illustrate the rate risk on annuity pricing and payout levels. A simple **Scatter with lines** chart is included.

---

## ✅ Sanity Checks (quick QA)
- Increasing **interest** → **APV decreases**
- Switching **Male → Female** (same StartAge, rate) → **APV(F) > APV(M)**
- Increasing **StartAge** → **APV decreases**
- **Due vs Immediate** → **APV_due ≈ APV_immediate + 1** (per \$1 annual payment)

---

## 🧩 Mortality Notes
- Mortality is provided in `moralitytable` as **qx** and **cumulative survivors (l_x)** for **Male** and **Female**.
- You can swap in public **Statistics Canada life tables** or keep the included mock/demo values for a self-contained portfolio file.

---

## 💡 Interpreting Results
- **APV** is **present value per \$1/year**.  
  To get a payout from a budgeted present value: **Annual Payment = PV / APV**.
- Comparing Male vs Female at the same PV and rate highlights how mortality drives payouts.


---

## 📝 Assumptions & Limits
- Annual payments; discrete-year model
- Truncation at **age 100** (small understatement vs full ultimate age)
- Deterministic interest rate; deterministic mortality basis

---


