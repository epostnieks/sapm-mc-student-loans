# Data Sources — Student Loan Securitization Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Student Loan Securitization: Guaranteed Demand Trap) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_tuition_extraction`

Tuition above at-cost baseline ($10K/yr cooperative). For-profit sector charges 2-4x public rates. β₁=72.4/46.8=1.55. Sources: IPEDS, NCES, Cellini & Turner 2019.

*Full citations: paper §4 (available SSRN).*

### `C2_debt_overhang`

Lifecycle economic distortion: delayed homeownership, reduced entrepreneurship, deferred family formation. 48% 12yr default rate at for-profits. Sources: Looney & Yannelis 2022, Fed NY CCP.

*Full citations: paper §4 (available SSRN).*

### `C3_servicing_rent`

Forbearance steering ($4B unnecessary interest from Navient alone 2010-2015), income-driven repayment obstruction, payment misapplication. Sources: CFPB, DOE IG, Navient settlement.

*Full citations: paper §4 (available SSRN).*

### `C4_securitization_moral_hazard`

SLABS investor constituency effects, origination moral hazard, political economy of non-discharge. $1.77T outstanding portfolio creates lobbying constituency against reform. Sources: SIFMA, Fitch SLABS reports.

*Full citations: paper §4 (available SSRN).*

### `C5_predatory_recruitment`

For-profit predatory recruitment, negative human capital returns, veteran targeting. 90/10 rule gaming. β₅=85.5/46.8=1.83, highest-weight channel. Sources: GAO, Senate HELP Committee, Deming et al. 2012.

*Full citations: paper §4 (available SSRN).*

### `C6_governance_failure`

Regulatory capture, revolving door (DeVos era), accreditation capture, lobbying ($100M+ cumulative). β₆=21.4/46.8=0.46. Sources: OpenSecrets, GAO, Senate investigations.

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $46.8B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Student Loan Securitization (Guaranteed Demand Trap)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
