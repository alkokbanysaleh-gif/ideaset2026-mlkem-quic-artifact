# IDEASET-2026 Paper 183 Reproducibility Artifact

This repository provides the computational reproducibility artifact for IDEASET-2026 Paper 183:

**Archived Hybrid ML-KEM-Labelled QUIC Timings: Evidence-Gated Analysis and Reproducibility Limits**

The artifact contains the archived 1,080-row CSV, analysis scripts, generated results, robustness checks, evidence-gate validation, confirmatory-planning outputs, figures, and an anonymous Overleaf source package.

## Scope and evidence boundary

This artifact supports **computational reproducibility of the archived analysis**. It does **not** establish execution provenance for the original measurement campaign, verify the negotiated cryptographic group, certify realized RTT/loss, or provide packet-level evidence for a transport mechanism. Those limitations are intentional and are part of the paper's evidence-gating methodology.

## Repository files

- `IDEASET2026_MLKEM_QUIC_Code_Results_Anonymous_Final.zip`  
  Code, raw CSV, generated results, figures, manifests, and reproduction scripts.
- `IDEASET2026_MLKEM_QUIC_Overleaf_Anonymous_Final.zip`  
  Anonymous Overleaf/LaTeX source package used for reviewer-accessible paper-source reproduction.
- `SHA256SUMS_RELEASE.txt`  
  SHA-256 hashes for the released archives and the raw CSV.

## Reproduction

1. Download and extract `IDEASET2026_MLKEM_QUIC_Code_Results_Anonymous_Final.zip`.
2. From the extracted directory, install the pinned dependencies when needed:

```bash
python -m pip install -r analysis/requirements-lock.txt
```

3. Run:

```bash
python reproduce_results.py
```

Windows users may alternatively run `RUN_REPRODUCTION.ps1` or `RUN_REPRODUCTION.bat`.

Regenerated outputs are written to `results_regenerated/`.

## Expected verification summary

A successful reproduction checks the following archive properties:

- 1,080 rows
- 36 scenario cells
- 30 rows per cell
- 1,079 Success-labelled rows and 1 Failure-labelled row
- 0 exact duplicate records
- 216 cell-summary values regenerated, all within 0.01 ms of the archived displayed values
- 1,024 evidence-gate state vectors enumerated
- 5,120 claim decisions checked
- current evidence ceiling: `C3`
- H-768 exact within-loss RTT relabeling rank: `1 / 13,824`

The reproduction script also regenerates robustness and confirmatory-planning outputs. Confirmatory-planning calculations are archive-conditioned operational sensitivity analyses, **not** population-power guarantees.

## Integrity hashes

```text
c5b1380ee22022f2938648cf5fb00d2582b62d15fbaec26be7f09ff5a10d86fe  IDEASET2026_MLKEM_QUIC_Code_Results_Anonymous_Final.zip
6fc34b837ea496b9431e3cbe2f8a2f52451041f4baa6f7e83365eea073b83ecb  IDEASET2026_MLKEM_QUIC_Overleaf_Anonymous_Final.zip
29ece90f482bac1280bf28d7bb6919a133dd4e305ab3449e351617490003ee54  data/final_pqc_quic_raw_results.csv
```

## Reviewer entry point

Start with `README.md` inside the code/results archive and then run `python reproduce_results.py`. The release manifest and the scripts document which outputs are regenerated and which claims remain blocked by unavailable provenance or protocol evidence.

## Conference

1st International Conference on Intelligent, Dependable, Emerging, Autonomous, and Sustainable Engineering Technology (IDEASET-2026), Paper 183.
