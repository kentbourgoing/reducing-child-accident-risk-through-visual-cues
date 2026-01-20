# Reducing Child Accident Risk Through Visual Cues

A field experiment testing whether low-cost, child-themed roadside cues can reduce vehicle speeds on residential streets. Using dual-camera speed measurement and regression analysis, we found that toys + signage reduced speeds by 1.9 mph and increased 25-mph compliance by 18 percentage points, demonstrating measurable safety improvements without expensive infrastructure.

---

## Problem and Goal

- **Problem:** ~385 child pedestrian deaths and 9,300+ injuries occur annually in the U.S. Vehicle speed strongly affects injury severity (10% death risk at 23 mph vs. 50% at 42 mph). Physical traffic calming (speed humps) works but requires time, money, and city approval. "Children at Play" signs are cheap but prior research shows minimal impact (0.9-1.5 mph reductions).

- **Why It Matters:** Even small speed reductions save lives, especially during high-risk after-school hours (36% of deaths occur 3-7 PM). Communities need affordable, rapidly deployable interventions while permanent infrastructure is planned.

- **Goal:** Test whether child-themed visual cues produce statistically significant speed reductions. Compare four conditions (control, sign only, sign + toys, sign + toys + balloons) across 400+ vehicles. Measure both average speed and 25-mph compliance percentage.

---

## Research Question

**Can low-cost, child-themed visual cues meaningfully slow drivers and reduce child pedestrian injury risk?**

**Hypotheses:**
- H1: "Children at Play" sign reduces speeds vs. control (α = 0.05)
- H2: Sign + toys produces greater reduction than sign alone
- H3: Sign + toys + balloons produces greatest reduction
- H4: Any treatment increases 25-mph compliance percentage

---

## Experimental Design

**1×4 factorial field experiment** on Tracy Street, Silver Lake, Los Angeles (July 2025)

| Condition | Elements | Sample Size |
|:---------:|:---------|:-----------:|
| **C** | No intervention (control) | 108 |
| **T1** | Yellow "Slow, Kids at Play" sign | 178 |
| **T2** | Sign + ~300 toys scattered on roadside | 102 |
| **T3** | Sign + toys + 3 balloons | 109 |

**Speed Measurement:**
- Dual-camera system (18.6-23.6m apart, hidden from drivers)
- Frame-by-frame timestamp extraction → distance/time calculation
- 6 sessions, 3-6 PM, non-consecutive days

**Randomization:** Day-level assignment (visible treatments couldn't change mid-session). Validated assumptions: (1) single exposure per driver (low repeat probability in urban LA), (2) stable baseline across days (Kruskal-Wallis p > 0.05).

**Covariates:** Vehicle class, color, fuel type (for balance checks and precision).

---

## Approach

1. **Power Analysis:** Simulated 3 effect sizes (3, 5, 11 mph) based on prior research; determined ≥100 vehicles/condition needed for 80% power at α = 0.05

2. **Field Data Collection:** Hidden dual-camera setup; manual timestamp extraction; coded vehicle covariates via video review; 497 total observations

3. **Covariate Balance Verification:** Confirmed randomization quality—vehicle distributions balanced across groups (±8 percentage points)

4. **Nested Regression Models:** Estimated 4 models (treatment only → + class → + color → + fuel type); used HC1/HC3 robust standard errors

5. **F-Tests for Model Comparison:** Sequential tests showed covariates added no explanatory power (p > 0.05); treatment effects stable across specifications

6. **Compliance Analysis:** Secondary outcome (binary: ≤25 mph); estimated percentage-point changes with robust CIs

---

## Pictures and Videos

### Experimental Setup - Four Treatment Conditions

![Treatment Conditions](Pictures%20and%20Videos/Experimental%20Setup%20for%20Low-Cost%20Traffic-Calming%20Cues.png)

Four conditions on Tracy Street: Control (no intervention), T1 (yellow sign), T2 (sign + 300 toys), T3 (sign + toys + 3 balloons). Each tested on separate days with ~100 vehicles per group.

### Study Site Layout and Camera Placement

![Study Site Layout](Pictures%20and%20Videos/Study%20Site%20Layout%20and%20Camera%20Placement.png)

Aerial view showing hidden camera positions (behind tree and parked car), treatment placement location (yellow star), and traffic flow direction (orange arrows). Camera spacing: 18.6-23.6m.

### Dual-Camera Speed Measurement System

![Camera Setup](Pictures%20and%20Videos/Camera%20Setup.png)

Frame-by-frame timestamp extraction with virtual measurement lines (red dashed). Left: vehicle crosses end line; right: vehicle crosses start line. Speed = distance/time.

### Example Recording - Day 6 (Treatment T3)

**Video:** [Example Recording of Day 6 (T3)](Pictures%20and%20Videos/Example%20Recording%20of%20Day%206%20(T3).MOV)

Sample footage from T3 session showing sign, toys, and balloons in real-world free-flow traffic conditions.

---

## Results

### Key Findings

| Treatment | Speed Reduction | p-value | 95% CI | Compliance Increase |
|:---------:|:---------------:|:-------:|:------:|:-------------------:|
| **T1** (Sign) | -0.56 mph | 0.26 | [-1.53, 0.41] | +1.4 pp (ns) |
| **T2** (Sign + Toys) | **-1.92 mph** | **<0.001*** | [-2.91, -0.92] | **+18.0 pp*** |
| **T3** (Sign + Toys + Balloons) | **-1.56 mph** | **0.01** | [-2.76, -0.35] | **+16.9 pp** |

*pp = percentage points; ns = not significant*

### Technical Deliverables

- **497 vehicle observations** with precise speed measurements, treatment assignments, and covariates
- **Statistically significant effects** for T2 and T3 (toys-based interventions); T1 sign-only failed to achieve significance
- **Compliance shifts:** Baseline 56% → 73-75% under T2/T3 (potentially eliminating dangerous high-speed outliers)
- **Validated causal inference:** Covariate balance confirmed, day-to-day stability verified, robust standard errors for heteroskedasticity

### Key Outcomes

- **Low-cost scalability:** Setup cost <$100 (toys + sign) vs. thousands for speed humps; no city approval required
- **Consistent with prior research:** Sign-only ineffective (matches Minnesota DOT findings); visible child-related objects necessary
- **Rigorous methods:** Experimental design with validated assumptions, nested models, sequential F-tests, robust inference

---

## Tech/Methods

**Languages:** R (data.table, dplyr, ggplot2), R Markdown, LaTeX

**Statistical Packages:** sandwich (HC1/HC3 robust SE), lmtest (coeftest, coefci), AER, stargazer, knitr

**Methods:** Linear regression, heteroskedasticity-robust inference, nested model comparison (F-tests), power analysis (Monte Carlo), non-parametric tests (Kruskal-Wallis, Wilcoxon), time-over-distance speed calculation

**Design:** 1×4 factorial field experiment, day-level randomization, covariate balance checks, baseline stability validation

---

## Repo Structure

```
reducing-child-accident-risk/
├── Pictures and Videos/            # Visual documentation
│   ├── Experimental Setup for Low-Cost Traffic-Calming Cues.png
│   ├── Study Site Layout and Camera Placement.png
│   ├── Camera Setup.png
│   └── Example Recording of Day 6 (T3).MOV
│
├── Report/                         # Analysis and outputs
│   ├── Final_Project_Analysis.Rmd  # Code with regression models
│   └── Final_Project_Report.pdf    # Complete 22-page report
│
├── Rmd Files/                      # Reproducible source
│   └── Final_Project_Report.Rmd    # Full narrative + code
│
├── Slides/                         # Presentation
│   └── Evaluating Low-Cost Cues for Reducing Child Pedestrian Accident Risk.pdf
│
└── README.md
```

---

## Limitations and Next Steps

### Limitations

- **Repeated exposure:** Some drivers may have seen setup multiple times (underestimates effect)
- **Day-level randomization:** Unobserved day-of-week effects could confound (validated with stability tests)
- **No real pedestrians:** Drivers may have noticed absence and ignored cues
- **Single location:** Silver Lake, LA only—limited generalizability
- **Short-term:** 6 weeks; habituation effects unknown

### Next Steps

- **Automate collection:** Computer vision for speed/vehicle classification (YOLO, license plate recognition)
- **Multi-site replication:** Test across 10+ streets (urban/suburban/rural, different cities)
- **Real pedestrians:** Partner with families/schools (supervised, safety protocols)
- **Longitudinal study:** 6-12 months to measure habituation and persistence
- **Cost-benefit analysis:** Integrate with injury risk models (lives saved per dollar)

---

## Credits

**Institution:** UC Berkeley School of Information
**Course:** DATASCI 241 - Experiments and Causal Inference
**Timeline:** May 2025 - August 2025

**Data Sources:**
- Original field data (Tracy Street, Silver Lake, Los Angeles)
- Literature: AAA FTS, Children's Safety Network, IIHS, PubMed Central, Minnesota DOT

**License:** MIT License for academic/educational use.

**Citation:**
```
Brown, D., Bourgoing, K., & Thakur, S. (2025). Evaluating Low-Cost Cues for Reducing
Child Pedestrian Accident Risk. UC Berkeley School of Information, DATASCI 241.
```

---

## Team Members

| Name | Email | LinkedIn |
|------|-------|----------|
| Daniel Brown | daniel.brown@berkeley.edu | [LinkedIn](https://www.linkedin.com/in/daniel-s-brown/) |
| Kent Bourgoing | kent1bp@berkeley.edu | [LinkedIn](https://www.linkedin.com/in/kent-bourgoing/) |
| Sunil Thakur | sunil.thakur@berkeley.edu | [LinkedIn](https://www.linkedin.com/in/sktonline/) |
