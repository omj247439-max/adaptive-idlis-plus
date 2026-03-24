```python
readme = open("/tmp/README.md").read() if False else """# I-DLIS+: Connectivity-Aware Branching for CDCL SAT Solvers on Random 3-SAT Phase Transition Instances

**Author:** Mayur Shrishrimal | Age 17 | Independent Researcher  
**Status:** Active Development | V20 Released  
March 2026 | [github.com/omj247439-max/adaptive-idlis-plus](https://github.com/omj247439-max/adaptive-idlis-plus)

---

## What is I-DLIS+?

I-DLIS+ augments VSIDS branching with Variable-Clause Graph (VCG) connectivity scoring:

```
score(v) = activity(v) + 1.5 × connectivity(v)
connectivity(v) = Σ(1/|c|) for all clauses c containing v
```

Integrated into MiniSAT's priority heap with O(log n) complexity.  
Connectivity cached lazily using clause-count invalidation — O(1) amortized per decision.

---

## Results (V20) — 50 Instances, ratio=4.26, seeds 0–49

### vs MiniSAT Baseline

| N | MiniSAT (mean ± std) | I-DLIS+ V20 (mean ± std) | Decision Reduction | Runtime Change |
|---|---------------------|--------------------------|-------------------|----------------|
| 50 | 49.3 ± 26.3 | 34.9 ± 14.5 | **29.2%** ↓ | 2.1% faster |
| 75 | 158.3 ± 98.7 | 116.6 ± 72.3 | **26.3%** ↓ | 10.1% faster |
| 100 | 412.1 ± 199.6 | 313.2 ± 226.3 | **24.0%** ↓ | 8.2% faster |
| 125 | 1250.9 ± 720.3 | 1022.5 ± 735.1 | **18.3%** ↓ | 8.7% faster |
| 150 | 3419.7 ± 2607.9 | 3419.7 ± 2607.9 | 0.0% (VSIDS mode) | — |

### vs Kissat 4.0.4

| N | Kissat 4.0.4 (mean ± std) | I-DLIS+ V20 | Decision Reduction |
|---|--------------------------|-------------|-------------------|
| 75 | 220.8 ± 162.2 | 116.6 ± 72.3 | **47.2%** fewer |
| 100 | 645.3 ± 457.1 | 313.2 ± 226.3 | **51.5%** fewer |
| 125 | 2074.3 ± 1083.1 | 1022.5 ± 735.1 | **50.7%** fewer |
| 150 | 5397.8 ± 3772.6 | 3419.7 ± 2607.9 | **36.6%** fewer |

> N=50 excluded from Kissat comparison — Kissat resolves small instances via preprocessing (≈0 decisions).  
> Kissat is optimized for industrial SAT; these results are specific to random 3-SAT phase transition instances.

---

## Key Findings

- **18–29% fewer decisions** than MiniSAT baseline with **up to 10% faster runtime** (N=50–125)
- **37–52% fewer decisions** than Kissat 4.0.4 on random 3-SAT phase transition (N=75–150)
- Adaptive switching to pure VSIDS at N>140 prevents regression at larger N
- Effective domain: random 3-SAT at phase transition ratio (4.26)

---

## Limitations

- Evaluated on random 3-SAT phase transition only
- 0% improvement on structured benchmarks (SATLIB Graph Coloring)
- N=140 switching threshold empirically determined
- 50 instances per N — larger validation needed

---

## Version History

| Version | Key Change |
|---------|-----------|
| V1–V3 | Python prototype |
| V4–V10 | MiniSAT C++ integration |
| V11 | Density-aware switching |
| V14 | Dirty-flag cache |
| V20 | Clause-count cache + optimized threshold |

---

## Experimental Setup

| Parameter | Value |
|-----------|-------|
| Platform | Google Colab, Ubuntu 22.04, x86_64 |
| Compiler | gcc -O3 -DNDEBUG |
| Benchmark | Random 3-SAT, ratio=4.26 |
| Instances | 50 per N, seeds 0–49 |
| Solvers | MiniSAT 2.2, Kissat 4.0.4 (default flags) |
| Metric | Decision count + runtime (ms) |

---

## Contact

GitHub: [@omj247439-max](https://github.com/omj247439-max)
"""

with open("/tmp/README_final.md", "w") as f:
    f.write(readme)
print("✅ README ready!")
```

```python
with open("/tmp/README_final.md") as f:
    print(f.read())
```
