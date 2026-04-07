# Stochastic Finance

A systematic series of theory documents and implementation notebooks covering the stochastic differential equations used in quantitative finance. Each entry is built from first principles: motivation, derivation, analytical solution, canonical pricing application, and limitations — before moving to the next.

The series is designed to be read in order. Each document builds on the mathematical foundations established in the previous one.

---

## Series Structure

| # | SDE | Theory | Notebook | Status |
|---|-----|--------|----------|--------|
| 01 | Geometric Brownian Motion | `01_gbm/gbm.pdf` | `01_gbm/gbm.ipynb` | ✅ Complete |
| 02 | Ornstein-Uhlenbeck Process | `02_ou/ou.pdf` | `02_ou/ou.ipynb` | 📄 Document complete |
| 03 | Cox-Ingersoll-Ross | — | — | 🔜 Upcoming |
| 04 | Heston Stochastic Volatility | — | — | 🔜 Upcoming |
| 05 | Jump-Diffusion (Merton) | — | — | 🔜 Upcoming |

---

## What Each Entry Contains

**Theory document (PDF)**
- Foundational concept the SDE is built on
- SDE construction term by term
- Full analytical derivation
- Canonical pricing application with complete derivation
- Limitations and pointer to the next SDE in the series

**Implementation notebook (Jupyter)**
- Each major theoretical result verified numerically
- Cells broken down by section, mirroring the PDF structure
- Brief explanatory notes before each code block
- No external dependencies beyond NumPy, SciPy, and Matplotlib

---

## 01 — Geometric Brownian Motion

**Foundation:** Log-price and the log-normal distribution. Linearization via logarithm.

**SDE:**
$$dS = \mu S \, dt + \sigma S \, dW$$

**Canonical pricing:** European option pricing via two routes — risk-neutral expectation (SDE route) and the Black-Scholes PDE (hedge portfolio route). Both produce the same formula:
$$V(S,t) = S\mathcal{N}(d_1) - Ke^{-r(T-t)}\mathcal{N}(d_2)$$

**Key result:** The log transformation linearizes GBM, enabling direct integration. The two-routes principle — expectation route and PDE route always agree — is established here as a general principle that carries through all subsequent SDEs.

---

## 02 — Ornstein-Uhlenbeck Process

**Foundation:** Stationarity and the Markov property. The stationary distribution and half-life.

**SDE:**
$$dX = \kappa(\theta - X)\,dt + \sigma\,dW$$

**Canonical pricing:** Zero-coupon bond pricing under the Vasicek model (OU applied to the short rate). Full derivation via both the expectation route and the Vasicek PDE. Bond option pricing as the derivative layer written on the bond price.

$$P(t,T) = A(t,T)\,e^{-B(t,T)\,r_t}$$

**Key result:** OU introduces the price process vs factor process distinction — unlike GBM where $S_t$ is directly traded, $r_t$ is an unobservable state variable that drives bond prices. The pricing chain $r_t \to P(r,t) \to V(P,t)$ is a three-layer structure absent in GBM.

---

## Dependencies

```bash
pip install numpy scipy matplotlib jupyter
```

All notebooks are self-contained and run with standard scientific Python. No financial data libraries required.

---

## Related

For applied SDE construction grounded in geoeconomic hypotheses — including case-specific derivations, numerical solvers, and calibration against real market data — refer to the [Geoeconomic SDE](https://github.com/aakashagarwal778/geoeconomic-sde) project, which applies these foundations across five cases.

---

*Aakash Agarwal*