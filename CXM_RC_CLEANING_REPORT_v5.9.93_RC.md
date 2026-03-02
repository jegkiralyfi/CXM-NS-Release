# CXM RC Cleaning Report — v5.9.93-RC
Date: 2026-03-02

## Inputs
- Source: `CXM_CANONICAL_NS_MASTER_v5.9.93.md`
- Output: `CXM_CANONICAL_NS_PUBLIC_v5.9.93_RC.md`

## Removals
- Lines removed by keyword filter: **23**
- Sections removed by heading filter: **1**


### RC hotfix (public packaging)
- Removed the incomplete public placeholder section `NFS.CA Computer-assisted certificates (executable)` (no CA artifacts are included in this public RC).

### Removed section headings (first 40)
- (H3) NFS.4 Mechanical check: χ-power normalization and reference integrity (tooling, non-submission)

### Keyword filter examples (first 30)
- > **Computer-verified.** A symbolic check in SymPy confirms the identity and fixes the prefactor:
- > \(u_\lambda(x,t)=\lambda u(\lambda x,\lambda^2 t)\). The exponent bookkeeping is certified in `CXM_CA_PROOF_NSScaling_LEI_Normalization_v1.ipynb` (PASS). \(\square\)
- > window normalization are certified in `CXM_CA_PROOF_TimeShift_Q1_Normalization_v1.ipynb` (PASS). \(\square\)
- > We use the test-function class from §NFS.SUIT and the chain-rule/Jacobian identities certified in `CXM_CA_PROOF_LEI_ChangeOfVariables_v2.ipynb`.
- > `CXM_CA_PROOF_LEI_ChangeOfVariables_v2.ipynb` (PASS):
- The similarity substitution is certified in the CA notebook `CXM_CA_PROOF_StationaryLRNS_SelfSimilar_v1.ipynb` (PASS). Moreover,
- - Manifest (coverage + roadmap): `CXM_CA_PROOF_MANIFEST_v21.md`
- - Runner (executes all notebooks, produces *_executed.ipynb outputs): `CXM_CA_PROOF_run_all_v21.py`
-  Notebook: `CXM_CA_PROOF_VI6_OUstar_v1.ipynb`.
-  Notebook: `CXM_CA_PROOF_NoTheft_Telescope_v1.ipynb`.
-  Notebook: `CXM_CA_PROOF_GatePacket_v1.ipynb`.
-  Notebook: `CXM_CA_PROOF_MovingCutoff_v1.ipynb`.
-  Notebook: `CXM_CA_PROOF_Lemma7_1H_v1.ipynb`.
-  Notebook: `CXM_CA_PROOF_PressureLocalization_7G2_v1.ipynb`.
-  Notebook: `CXM_CA_PROOF_LEI_ChangeOfVariables_v1.ipynb`.
-  Notebook: `CXM_CA_PROOF_NSScaling_LEI_Normalization_v1.ipynb`.
-  Notebook: `CXM_CA_PROOF_TimeShift_Q1_Normalization_v1.ipynb`.
-  Notebook: `CXM_CA_PROOF_WindowToStationary_v1.ipynb`.
-  Notebook: `CXM_CA_PROOF_RouteA_Recombination_Full_v1.ipynb`.
-  Notebook: `CXM_CA_PROOF_Tsai_InterfaceChecker_v2.ipynb`.
- ## Appendix DEV. Internal development changelog (omit in submission)
- ### v5.9.49 (computer-assisted calculus certificate)
- - Added a short “Computer-verified” note and produced an executable SymPy notebook certificate (see `CXM_CA_PROOF_VI6_OUstar_v2.ipynb`).
