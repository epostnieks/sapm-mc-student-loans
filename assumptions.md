# Monte Carlo Assumptions — Student Loan Securitization / Guaranteed Demand Trap

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $46.8B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 6.36 | Confirmed by N=100,000 draws |
| ΔW median (result) | $297.6B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_tuition_extraction` | lognormal | $55.0B | $72.4B | $95.0B | Tuition above at-cost baseline ($10K/yr cooperative). For-profit sector charges  |
| `C2_debt_overhang` | lognormal | $55.0B | $73.0B | $96.0B | Lifecycle economic distortion: delayed homeownership, reduced entrepreneurship,  |
| `C3_servicing_rent` | lognormal | $12.0B | $18.7B | $28.0B | Forbearance steering ($4B unnecessary interest from Navient alone 2010-2015), in |
| `C4_securitization_moral_hazard` | lognormal | $15.0B | $23.8B | $36.0B | SLABS investor constituency effects, origination moral hazard, political economy |
| `C5_predatory_recruitment` | lognormal | $65.0B | $85.5B | $112.0B | For-profit predatory recruitment, negative human capital returns, veteran target |
| `C6_governance_failure` | lognormal | $13.0B | $21.4B | $33.0B | Regulatory capture, revolving door (DeVos era), accreditation capture, lobbying  |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 2.6 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 2.6) = 0.0000%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 6.3 | 20% DC adj = 5.04 | 40% DC adj = 3.78

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $298B = 0.3% of world GDP ($106T) ✓
- **β_W range**: 6.36 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0000% ✓
