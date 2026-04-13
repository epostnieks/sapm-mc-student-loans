# SAPM Monte Carlo — Student Loan Securitization / Guaranteed Demand Trap

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Student Loan Securitization (Guaranteed Demand Trap).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **6.36** |
| β_W mean | 6.41 |
| β_W std | 0.79 |
| **90% CI** | **[5.2, 7.8]** |
| 99% CI | [4.8, 8.5] |
| P(β_W < 1) | 0.0000% |
| **ΔW median** | **$297.6B/yr** |
| Π (revenue) | $46.8B/yr |

**β_W = 6.36** means the student loan securitization industry destroys **$6.36 in system
welfare for every $1.00 in revenue** — across 6 channels and 100,000 Monte Carlo draws.

**Classification**: Class 2 — Intractability

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-student-loans.git
cd sapm-mc-student-loans
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 6.36` and `ΔW median : $297.6B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_tuition_extraction | $72.3B | [$55.1B, $94.9B] | Lognormal |
| C2_debt_overhang | $73.0B | [$55.5B, $96.2B] | Lognormal |
| C3_servicing_rent | $18.7B | [$12.5B, $28.0B] | Lognormal |
| C4_securitization_moral_hazard | $23.8B | [$15.7B, $36.0B] | Lognormal |
| C5_predatory_recruitment | $85.4B | [$65.3B, $111.8B] | Lognormal |
| C6_governance_failure | $21.4B | [$13.9B, $33.0B] | Lognormal |
| **Total ΔW** | **$297.6B** | **[$243.6B, $364.2B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 2.6 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.0000%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Student Loan Securitization (Guaranteed Demand Trap)*.
> GitHub: epostnieks/sapm-mc-student-loans.
> https://github.com/epostnieks/sapm-mc-student-loans
