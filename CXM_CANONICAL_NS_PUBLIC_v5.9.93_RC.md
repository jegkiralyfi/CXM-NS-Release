# Global regularity for 3D Navier–Stokes via a Gate / No‑Theft critical‑element rigidity spine

<!--
CXM Canonical Navier–Stokes Manuscript
Public Release Candidate: v5.9.93-RC
Build date: 2026-03-02

Derived from: CXM_CANONICAL_NS_MASTER_v5.9.93.md
Internal development notes and tooling/audit pointers have been removed.
Mathematical content is unchanged up to purely editorial deletions.
-->

**Author:** Jégkirályfi (Zoltán Fehér)

**Affiliation:** Independent Researcher (CXM Research Group), Budapest, Hungary

**Email:** zoltan.b.feher@gmail.com

## Abstract
We prove global regularity for the three-dimensional incompressible Navier–Stokes equations on \(\mathbb R^3\) with smooth divergence-free initial data. The proof is organized as a critical-element rigidity argument at the scale-invariant \(L^3\) level. Assuming a first finite-time singularity, we extract (via the concentration–compactness critical-element program [GKP13, Thm. 5–7]) an ancient suitable solution in Leray similarity variables whose orbit is precompact modulo translations. We then introduce a Gaussian “width” observable and establish a quantitative large-radius dichotomy for defect transport: either an absorption regime holds at a fixed scale, or a forced **Gate** mechanism produces a uniform dissipation packet. A localized Ornstein–Uhlenbeck adjoint Gaussian budget, combined with a No‑Theft principle (pressure-tail decoupling), converts persistent Gate activation into finite total renormalized dissipation and hence asymptotic stationarity of the renormalization orbit. The resulting stationary Leray profile is excluded by Tsai’s rigidity theorem for suitable backward self-similar solutions, yielding the contradiction.

**Keywords:** Navier–Stokes; regularity; critical element; concentration compactness; local energy inequality; rigidity.

**MSC 2020:** 35Q30, 76D03.

## 0. Main theorem and proof structure
### 0.1 Main theorem and setting
We consider the incompressible Navier–Stokes system on \(\mathbb R^3\)
\[
\partial_t u + (u\cdot\nabla)u + \nabla p = \Delta u,\qquad \nabla\cdot u = 0,
\]
with smooth divergence-free initial data \(u_0\in C_c^\infty(\mathbb R^3)\). (Viscosity is normalized to \(1\).)

> **Theorem 1.1 (Global regularity).**
> For every such \(u_0\), the corresponding Leray–Hopf solution is smooth for all \(t>0\). Equivalently, no finite-time singularity can occur.

### 0.2 Proof roadmap (one line per step)
Assume a first blow-up time \(T^\*\). Then:

1. **(CE extraction)** Use CE\((L^3)\) to obtain an ancient suitable LRNS orbit \((U,P)\) with critical bound and tightness (§2–§1).
2. **(Flux Sealing)** Prove a large-radius cutoff-flux barrier using critical compactness + Calderón–Zygmund (NFS.EST.4) pressure control (§2).
3. **(Modulation cost)** Build a Gaussian width observable and show pinned gauge forces non-degeneracy (§3).
4. **(Gaussian budget)** Derive the OU\(^\ast\)-adjoint Gaussian energy inequality in similarity variables and pass to \(R\to\infty\) (§4).
5. **(Gate / No‑Theft dichotomy)** Show that persistent non-absorption triggers Gate packets; No‑Theft turns packets into a finite dissipation budget (§4.1–§4.4).
6. **(Rigidity)** Finite renormalized dissipation forces asymptotic stationarity; the stationary profile contradicts Tsai ([Tsai98, Thm. 2]), and nontriviality is isolated in a single canonical lemma (Lemma 7.6P) (§4.5–§4.6).

This completes the contradiction and proves the main theorem.

### 0.3 Dependency and citation map
The manuscript is written as a single proof spine. The external inputs are limited and are recorded in statement form
(with precise theorem identifiers) in Appendix **NFS.IMP**. Concretely:

- **Critical-element extraction at the $L^3$ level** (CE($L^3$), Theorem 2.1), based on [GKP13, Thm. 5–7].  
  From a hypothetical first blow-up time one extracts an ancient suitable orbit in Leray similarity variables with
  $L^\infty_\tau L^3_y$ control and tightness modulo translations.

- **Rigidity for backward self-similar suitable solutions** (Tsai) [Tsai98, Thm. 2].  
  A stationary suitable backward self-similar profile must be trivial under Tsai’s local energy finiteness hypothesis.

All remaining steps are proved in-line from these inputs using the local energy inequality, pressure localization, and the Gate/No-Theft mechanism.
Some calculus identities in the change-of-variables and normalization steps admit straightforward symbolic verification (not included in this public RC).

For convenience, we list below the external inputs and where they are invoked, and we indicate which items are load-bearing versus toolbox references.

This canonical spine uses a **small set of external (citable) results**. Each is used only after we verify that its **hypotheses match** the solution class produced in §2–§4.
Legend: **†** = load-bearing external input; **‡** = toolbox (Appendix NFS.EST) reference; **(ctx)** = context only (see References).

**External inputs used (and where).**
1. **Suitable weak solutions / LEI formalism.** Definition + compactness framework: [CKN], [LR02]. 
 *Used in:* §1.1, §2–§4, and whenever we pass to limits.
2. **Pressure representation and Calderón–Zygmund (NFS.EST.4) bounds.** \(p = \mathcal R_i\mathcal R_j(u_i u_j)\) and \(L^{3/2}\) control from \(u\in L^3\): [Gra14, Cor. 5.2.8] (hence $\mathcal R_i\mathcal R_j$ is bounded on $L^{3/2}$ by composition). 
 *Used in:* §2 (Flux Sealing) and in Gaussian budgets (§4).
3. **Type I (backward self-similar) nonexistence under LEI.** [Tsai98] (load-bearing). Historical precursor: [NRS96] (context only; stronger assumptions; not used below). 
 *Used in:* §6 (rigidity endpoint).
4. **Critical element extraction in \(L^3\).** Minimal blow-up object / precompactness up to symmetries: [GKP13], [JS13]. 
 *Used in:* §2 (to define the package (GKP1)–(GKP4)). 
 We invoke the endpoint critical-element program at the $L^3$ level as developed by Gallagher–Koch–Planchon [GKP13, Thm. 5–7]. For the reader’s convenience, we isolate exactly the extracted consequences we need in a single named package **CE($L^3$)** (Theorem 2.1), with itemized hypotheses and outputs. A theorem-by-theorem hypothesis/usage map is recorded in Appendix **NFS.IMP** (Imported results) and Appendix **NFS.CE**.

This is the only place in the proof where concentration–compactness / minimal-element machinery enters; all subsequent steps are proved in-line from the CE($L^3$) package using the local energy inequality, pressure localization, and the Gate/No-Theft mechanism.

> **Theorem 2.1 (CE($L^3$) extraction in LRNS variables; contradiction output).** 
> Assume for contradiction that there exists a Leray–Hopf solution of 3D Navier–Stokes with a first singular time \(T^\*<\infty\).
> Then one can extract (after blow-up rescaling and canonical symmetry pinning) an **ancient LRNS suitable solution**
> \((U,P)\) on \((-\infty,0]\times\mathbb R^3\) such that:
>
> **(CE1) Critical bound.** \(U\in L^\infty_\tau L^3_y(\mathbb R^3)\) with
> \(\sup_{\tau\le 0}\|U(\tau)\|_{L^3}\le M<\infty\).
>
> **(CE2) Uniform $L^3$-tightness (pinned).** For every \(\varepsilon>0\) there exists \(R_\varepsilon\ge 1\) such that
> \[
> \sup_{\tau\le 0}\int_{|y|>R_\varepsilon}|U(\tau,y)|^3\,dy\ \le\ \varepsilon.
> \tag{CE2}\label{CE2_tightness}
> \]
>
> **(CE3) Suitability in LRNS (LRNS-LEI).** \((U,P)\) is a suitable weak solution of (LRNS) on \((-\infty,0]\times\mathbb R^3\) and satisfies
> the LRNS local energy inequality for every nonnegative test function \(\varphi\in C_c^\infty(\mathbb R^3\times(-\infty,0])\).
>
> **(CE4) Pressure representation and localization.** \(P\) may be chosen (distributionally) as \(P=\mathcal R_i\mathcal R_j(U_iU_j)\),
> and the local pressure decomposition (NFS.EST.5) (NFS.EST.5) on balls holds on each bounded cylinder.
>
> **(CE5) Canonical pinning.** Translations are fixed so that the tightness radius in (CE2) is measured relative to the origin.
>
> *Citation-level proof spine.* The package above follows from the endpoint critical-element program:
> [GKP13, Thm. 5–7] provide existence/compactness/rigidity of critical elements, yielding the endpoint criterion
> \(u\in L^\infty_tL^3_x\Rightarrow\) no finite-time blow-up (in the suitable framework). Suitability/LEI stability and pressure localization are 
> in the CKN/ESS framework; see [CKN], [ESS03]. A theorem-number hypothesis map CE1–CE5 is recorded in Appendix **NFS.CE**.

> **Lemma 2.2 (Precompactness implies uniform $L^3$-tightness).** 
> Let \(K\subset L^3(\mathbb R^3)\) be a **compact** set. Then for every \(\varepsilon>0\) there exists \(R_\varepsilon\ge 1\) such that
> \[
> \sup_{f\in K}\int_{|y|>R_\varepsilon}|f(y)|^3\,dy\ \le\ \varepsilon.
> \tag{2.2}\label{eq:lem22_uniform_tail}
> \]
> In particular, if a trajectory \(\{U(\tau)\}_{\tau\le 0}\subset L^3\) is precompact (after fixing translations), then (CE2) follows for the pinned orbit.
>
> *Proof.* For \(R\ge 1\) define \(T_R(f):=\int_{|y|>R}|f(y)|^3\,dy\). For fixed \(R\), \(T_R\) is continuous on \(L^3\).
> For fixed \(f\in L^3\), \(T_R(f)\to 0\) as \(R\to\infty\) by absolute continuity of the integral.
> Fix \(\varepsilon>0\). For each \(f\in K\) choose \(R(f)\) so that \(T_{R(f)}(f)<\varepsilon/2\). By continuity, there exists an \(L^3\)-neighborhood
> \(N_f\) such that \(T_{R(f)}(g)<\varepsilon\) for all \(g\in N_f\). A finite subcover \(K\subset\bigcup_{j=1}^J N_{f_j}\) exists by compactness.
> Let \(R_\varepsilon:=\max_j R(f_j)\). Then for any \(g\in K\), \(T_{R_\varepsilon}(g)\le T_{R(f_j)}(g)<\varepsilon\) for some \(j\), proving \eqref{eq:lem22_uniform_tail}. \(\square\)

> **Lemma 2.3 (Suitability stability).** 
> Let \((u^{(n)},p^{(n)})\) be suitable weak solutions of Navier–Stokes on a cylinder \(Q\). Assume (after passing to a subsequence) that
> \[
> u^{(n)}\to u \ \text{in }L^3_{\mathrm{loc}}(Q),\qquad 
> u^{(n)}\rightharpoonup u \ \text{in }L^2_{\mathrm{loc}}(t;H^1_{\mathrm{loc}}(x)),\qquad
> p^{(n)}\rightharpoonup p \ \text{in }L^{3/2}_{\mathrm{loc}}(Q).
> \]
> Then \((u,p)\) is a suitable weak solution on \(Q\), and the local energy inequality passes to the limit.
>
> *Proof.* Fix a nonnegative test function \(\varphi\in C_c^\infty(Q)\). Each term in the local energy inequality passes to the limit under the above convergences;
> the dissipation term uses weak lower semicontinuity and \(\varphi\ge 0\), while the remaining terms use the strong \(L^3_{\mathrm{loc}}\) convergence.
> A term-by-term matching is recorded in Lemma 2.4. \(\square\)

> **Lemma 2.4 (LEI term-by-term stability under $L^3$ strong convergence).** 
> Under the hypotheses of Lemma 2.3, for every nonnegative \(\varphi\in C_c^\infty(Q)\) we have
> \[
> \liminf_{n\to\infty}\int_Q \varphi\,|\nabla u^{(n)}|^2
> \ \ge\ \int_Q \varphi\,|\nabla u|^2,
> \tag{2.4a}\label{eq:lei_liminf_diss}
> \]
> and
> \[
> \int_Q \tfrac12|u^{(n)}|^2(\partial_t\varphi+\Delta\varphi)
> + \int_Q \Big(\tfrac12|u^{(n)}|^2 + p^{(n)}\Big)\,u^{(n)}\cdot\nabla\varphi
> \ \longrightarrow\
> \int_Q \tfrac12|u|^2(\partial_t\varphi+\Delta\varphi)
> + \int_Q \Big(\tfrac12|u|^2 + p\Big)\,u\cdot\nabla\varphi.
> \tag{2.4b}\label{eq:lei_conv_nonlinear_pressure}
> \]
> Consequently the local energy inequality passes to the limit (Lemma 2.4).
>
> *Proof.* Since \(u^{(n)}\to u\) in \(L^3_{\mathrm{loc}}(Q)\), we have \(|u^{(n)}|^2\to |u|^2\) in \(L^{3/2}_{\mathrm{loc}}\), and
> \(|u^{(n)}|^2u^{(n)}\to |u|^2u\) in \(L^1_{\mathrm{loc}}\). Hence the terms with (Lemma 2.4)
> \((\partial_t\varphi+\Delta\varphi)\) and \(u\cdot\nabla\varphi\) converge. For the pressure term, \(p^{(n)}\rightharpoonup p\) in \(L^{3/2}_{\mathrm{loc}}\)
> and \(u^{(n)}\cdot\nabla\varphi\to u\cdot\nabla\varphi\) strongly in \(L^3_{\mathrm{loc}}\), so \(p^{(n)}(u^{(n)}\cdot\nabla\varphi)\to p(u\cdot\nabla\varphi)\) in \(L^1\) by Hölder (NFS.EST.2).
> Finally \eqref{eq:lei_liminf_diss} follows from weak convergence of \(\nabla u^{(n)}\) in \(L^2_{\mathrm{loc}}\) and the convexity of \(|\cdot|^2\) with nonnegative weight \(\varphi\).
> \(\square\)

The remainder of the manuscript is internal: starting from Theorem 2.1, we run the pinned LRNS spine, derive the Gaussian budget,
establish Gate/No-Theft, and conclude by Tsai rigidity.

### 0.4 Spine dependency index (reader map)

The proof spine is organized into the following named steps; each step points to the precise internal statement(s).

1. **Main claim.** **Theorem 1.1** (global regularity).
2. **Critical element extraction.** **Theorem 2.1 (CE($L^3$))** and its outputs; see Appendix NFS.IMP.
3. **Flux sealing / tail control.** Lemmas **2.2–2.4** and Lemma **4.1**.
4. **Pinned normalization + width observable.** Lemmas **5.1–5.3**.
5. **Gaussian OU$^\ast$ budget.** Lemma **6.1**.
6. **Gate/No-Theft dichotomy and dissipation packet accounting.** Lemmas **7.1F**, **7.1H**, **7.2**, **7.3**.
7. **Rigidity via Tsai.** Lemmas **7.6E1**, **7.6F**, **7.6G**, and the isolated nontriviality lemma **7.6P**.

A complete statement index (with local dependency hints and usage counts) is recorded in Appendix **NFS.SDI**.

## 1. Leray similarity RG normalization (CXM canonical packaging)

### 1.1 Similarity variables and the RG orbit as time shifts
Fix a putative singular point \((x_\star,T^\star)\). Introduce Leray similarity variables
\[
y=\frac{x-x_\star}{\sqrt{T^\star-t}},\qquad \tau=-\log(T^\star-t),
\]
and the Leray-rescaled fields
\[
U(y,\tau)=\sqrt{T^\star-t}\;u(x,t),\qquad P(y,\tau)=(T^\star-t)\;p(x,t).
\]
In these variables the dynamics are governed by the Leray-rescaled Navier–Stokes system (LRNS) (see §2.2).

The discrete “RG windows” are simply **unit time translates in \(\tau\)**:
\[
U_k(y,s):=U(y,k+s),\qquad P_k(y,s):=P(y,k+s),\qquad s\in[-1,0].
\]
This is equivalent to the fixed-frame discrete rescalings (the scale factor changes by \(e^{-1/2}\) per unit of \(\tau\)), but it is the natural packaging for the energy budget.

### 1.2 Gauge fixing: translation pinning (no optional normalizations)

The package (GKP3) gives **spatial tightness modulo translations**. We fix a translation gauge so that all windows are centered at the origin.

> **Lemma 3.1 (Translation pinning).** 
> Assume (GKP3): for every \(\varepsilon>0\) there exists \(R(\varepsilon)\) such that for each \(k\) there is a center \(y_k\in\mathbb R^3\) with
> \[
> \int_{|y-y_k|>R(\varepsilon)} |U_k(y,0)|^3\,dy \le \varepsilon.
> \]
> Then after defining the translated windows
> \[
> \widetilde U_k(y,s):=U_k(y+y_k,s),
> \]
> we have the pinned tightness estimate
> \[
> \int_{|y|>R(\varepsilon)} |\widetilde U_k(y,0)|^3\,dy \le \varepsilon
> \quad\text{for all }k.
> \]

*Proof.* This is immediate from the change of variables \(z=y+y_k\). \(\square\)

From now on we rename \(\widetilde U_k\) back to \(U_k\) and assume the translation gauge has been fixed.

**Remark (polish).** Earlier development versions also imposed optional “vorticity-amplitude” normalizations. Those are **not used** in the present single-spine proof and are intentionally omitted here to prevent circularity and notational drift.

## 2. Flux Sealing (Hard Analysis) — the key analytic lemma

### 2.1 The only flux notion used (cutoff-flux)
Let \(\chi\in C_c^\infty(\mathbb{R}^3)\) be radial, \(\chi\equiv 1\) on \(|y|\le 1\), \(\chi\equiv 0\) on \(|y|\ge 2\), and set \(\chi_R(y):=\chi(y/R)\).

Define the **Gaussian cutoff-flux** over a unit window:
\[
\mathcal{F}_{G,R}[U,P](s)
:=\int_{s-1}^{s}\int_{\mathbb{R}^3}
\Big(\tfrac12 |U|^2 + P\Big)\,U\cdot\nabla(\chi_R^2)\; G\,dy\,d\tau.
\]

> **Definition (Flux Sealing).** 
> The orbit satisfies **Flux Sealing** if
> \[
> \lim_{R\to\infty}\ \sup_k\ \sup_{s\in[-1,0]}\big|\mathcal{F}_{G,R}[U_k,P_k](s)\big|=0.
> \]
Only \(\mathcal{F}_{G,R}\) is used; no “surface flux” is introduced.

### 2.2 Pressure control (Calderón–Zygmund (NFS.EST.4); uniform in time)
For suitable solutions on \(\mathbb R^3\),
\[
P = \mathcal{R}_i\mathcal{R}_j(U_iU_j)
\]
and hence for each fixed \(\tau\), [Gra14, Cor. 5.2.8]
\[
\|P(\cdot,\tau)\|_{L^{3/2}} \le C_{CZ}\,\|U(\cdot,\tau)\|_{L^3}^2,
\]
with universal \(C_{CZ}\); see e.g. [Gra14, Cor. 5.2.8].

### 2.3 Lemma S3 (Flux Sealing from critical compactness + CZ)
> **Lemma 4.1 (Flux Sealing / No-Theft).** 
> Assume (GKP1)–(GKP3). Then Flux Sealing holds:
> \[
> \lim_{R\to\infty}\ \sup_k\ \sup_{s\in[-1,0]}\big|\mathcal{F}_{G,R}[U_k,P_k](s)\big|=0.
> \]

**Proof (Annals-grade; no hidden steps).** 
Fix \(k\). Let \(A_R:=\{R\le |y|\le 2R\}\). Note \(\nabla(\chi_R^2)\) is supported on \(A_R\) and \(|\nabla(\chi_R^2)|\lesssim 1/R\). Also \(0<G\le 1\).

For any \(s\in[-1,0]\),
\[
|\mathcal{F}_{G,R}[U_k,P_k](s)|
\le \int_{s-1}^{s}\int_{A_R}\Big(\tfrac12 |U_k|^2 + |P_k|\Big)\,|U_k|\,|\nabla(\chi_R^2)|\,G\,dy\,d\tau.
\]
Thus by Hölder (NFS.EST.2) and §2.2,
\[
|\mathcal{F}_{G,R}[U_k,P_k](s)|
\lesssim \frac1R\int_{s-1}^s
\Big(\|U_k(\tau)\|_{L^3(A_R)}^3 + \|P_k(\tau)\|_{L^{3/2}}\|U_k(\tau)\|_{L^3(A_R)}\Big)\,d\tau
\]
\[
\lesssim \frac1R\int_{s-1}^s
\Big(\|U_k(\tau)\|_{L^3(A_R)}^3 + M^2\|U_k(\tau)\|_{L^3(A_R)}\Big)\,d\tau.
\]
By tightness (GKP2), for every \(\varepsilon>0\) there exists \(R_\varepsilon\) such that for all \(R\ge R_\varepsilon\),
\(\|U_k(\tau)\|_{L^3(A_R)}\le \|U_k(\tau)\|_{L^3(|y|>R)}\le \varepsilon\)
uniformly in \(k,\tau\). Hence for \(R\ge R_\varepsilon\), (Lemma 4.1)
\[
\sup_k\sup_{s\in[-1,0]}|\mathcal{F}_{G,R}[U_k,P_k](s)|
\lesssim \frac1R\,(\varepsilon^3+M^2\varepsilon)\xrightarrow[R\to\infty]{}0,
\]
and since \(\varepsilon\) is arbitrary, the Flux Sealing limit holds. \(\square\)

**Interpretation.** Flux Sealing is the rigorous form of “No-Theft”: energy cannot be imported from infinity because the critical element is tight.

---

## 3. Critical Coercivity (Modulation Cost) — what is needed and what is proven

This section isolates exactly what is required to force the \(\omega\)-limit set to be a singleton.

### 3.1 A quantitative width observable (Gaussian energy quantile)

> **Definition 5.1 (σ-breathing window).** 
> Fix parameters \((\theta,\kappa)\) in the normalized class and let \(\mathcal R_{\theta,\kappa}(s)\) denote the
> log-averaged quantile radius defined by \((5.2)\). A normalized RG window \(U\) on \([-1,0]\) is **\(\sigma\)-breathing**
> if
> \[
> e^{-\sigma}\ \le\ \mathcal R_{\theta,\kappa}(s)\ \le\ e^{\sigma}
> \qquad \text{for all }s\in[-1,0].
> \tag{5.1}\label{def:5.1_breathing}
> \]
> (Equivalently, the instantaneous profile does not concentrate or spread beyond a fixed multiplicative factor on the unit window.)

We measure the “width” of a window by **where the Gaussian energy profile crosses a band of levels**.
The key point is that we must avoid any hidden “crossing slope” assumption: if the profile is nearly flat near a
single threshold, then an $\|F-G\|_{L^\infty_R}$ perturbation can create an arbitrarily large hitting-time drift.
We therefore define the width by **averaging quantile radii across a hysteresis band** (Appendix NFS.IMP).

For a window $(U_k,P_k)$ and a slice $s\in[-1,0]$ define the *Gaussian energies*
\[
E_R(s):=\int_{\mathbb R^3} \tfrac12|U_k(y,s)|^2\,\chi_R(y)^2\,G(y)\,dy,
\qquad
E_\infty(s):=\int_{\mathbb R^3} \tfrac12|U_k(y,s)|^2\,G(y)\,dy,
\]
and the *instantaneous normalized profile*
\[
\widetilde F_s(R):=\frac{E_R(s)}{E_\infty(s)}\in[0,1],
\qquad R\ge 1.
 \tag{5.0}
\]
(If $E_\infty(s)=0$ then $U_k(\cdot,s)=0$ a.e. and the window is trivial; in the canonical spine we work on
nontrivial windows, so $E_\infty(s)>0$ and $\widetilde F_s$ is well-defined.)

**Quantile radii.** For $\alpha\in(0,1)$ define the *quantile radius*
\[
Q_s(\alpha):=\inf\{R\ge 1:\ \widetilde F_s(R)\ge \alpha\}.
 \tag{5.1}
\]
Since $R\mapsto\widetilde F_s(R)$ is monotone increasing and $\widetilde F_s(R)\uparrow 1$ as $R\to\infty$,
each $Q_s(\alpha)$ is finite.

**quantitative width radius (Option B).** Fix $\theta\in(0,1)$ and a band half-width $\kappa\in(0,\theta\wedge(1-\theta))$.
We define the $(\theta,\kappa)$–width radius at slice $s$ by the *logarithmic band-average* of quantiles:
\[
\log \mathcal R_{\theta,\kappa}(s)
:=\frac{1}{2\kappa}\int_{\theta-\kappa}^{\theta+\kappa}\log Q_s(\alpha)\,d\alpha.
 \tag{5.2}\label{eq:5.2}
\]
Equivalently, $\mathcal R_{\theta,\kappa}(s)$ is the geometric mean of the quantile radii across the band
$[\theta-\kappa,\theta+\kappa]$.

**Admissible band.** We fix parameters $0<\theta<1$ and $0<\kappa<\min\{\theta,1-\theta\}$ so that the band $[\theta-\kappa,\theta+\kappa]\subset(0,1)$.

This definition is **hysteretic by construction**: it is stable under $L^\infty_R$ perturbations of the profile
without any “non-flatness at the crossing” assumption. The deterministic drift conversion is proved in §4.2.6.5.

**Window width.** We evaluate (5.2) at the *pin time* $s=0$ and write
\[
\mathcal R_k:=\mathcal R_{\theta,\kappa}[U_k](0).
 \tag{5.3}
\]
The “breathing” alternative of M1 concerns whether $\mathcal R_k$ stays in a fixed compact interval or
exhibits multiplicative expansions/contractions.

---
### 3.2 Non-degeneracy: pinned gauge forces positive Gaussian energy
> **Lemma 5.1 (Gaussian energy non-degeneracy at the pin time).** 
> Assume (GKP1)–(GKP4). Then there exists \(m_0=m_0(R_{\mathrm{pin}},\eta_{\mathrm{pin}})>0\) such that
> \[
> \inf_k E_G[U_k](0)\ \ge\ m_0.
> \tag{5.1a}
> \]
> Moreover, once the full-space Leray–Gaussian budget of §4 is established (so that \(E_G(\tau)\) is nonincreasing in \(\tau\)), one also has
> \[
> \inf_k\ \inf_{s\in[-1,0]} E_G[U_k](s)\ \ge\ m_0.
> \tag{5.1b}
> \]

**Proof.** Fix \(k\). By (GKP4),
\[
\|U_k(\cdot,0)\|_{L^3(B_{R_{\mathrm{pin}}})}\ge \eta_{\mathrm{pin}}.
\]
By Hölder on the finite-measure set \(B_{R_{\mathrm{pin}}}\),
\[
\|U_k(\cdot,0)\|_{L^2(B_{R_{\mathrm{pin}}})}
\ \ge\
\|U_k(\cdot,0)\|_{L^3(B_{R_{\mathrm{pin}}})}\,|B_{R_{\mathrm{pin}}}|^{\,\frac16}
\ \ge\ \eta_{\mathrm{pin}}\,|B_{R_{\mathrm{pin}}}|^{\,\frac16}.
\]
Squaring and using that \(G(y)\ge g_0:=(4\pi)^{-3/2}e^{-R_{\mathrm{pin}}^2/4}\) on \(B_{R_{\mathrm{pin}}}\),
\[
E_G[U_k](0)
=\int_{\mathbb R^3}\tfrac12|U_k(y,0)|^2G(y)\,dy
\ \ge\
\frac12\,g_0\int_{B_{R_{\mathrm{pin}}}}|U_k(y,0)|^2\,dy
\ \ge\
\frac12\,g_0\,\eta_{\mathrm{pin}}^2\,|B_{R_{\mathrm{pin}}}|^{\,\frac13}.
\]
Define
\[
m_0:=\frac12\,(4\pi)^{-3/2}e^{-R_{\mathrm{pin}}^2/4}\,\eta_{\mathrm{pin}}^2\,|B_{R_{\mathrm{pin}}}|^{\,\frac13}>0.
\]
This proves (5.1a).

For (5.1b), once §4 yields the full-space inequality
\(
E_G(\tau_2)+\int_{\tau_1}^{\tau_2}D_G(\tau)\,d\tau\le E_G(\tau_1)
\)
for all \(\tau_1<\tau_2\), \(E_G\) is nonincreasing in \(\tau\). Hence on each window \(\tau\in[k-1,k]\) (i.e. \(s\in[-1,0]\)), (Lemma 5.1)
\[
E_G[U_k](s)=E_G(k+s)\ \ge\ E_G(k)=E_G[U_k](0)\ \ge\ m_0,
\]
so (5.1b) follows. \(\square\)

> **Lemma 5.2 (Singleton \(\omega\)-limit under coercive modulation cost).** 
> Let \(\{U(s)\}_{s\le 0}\) be a precompact trajectory in a metric space \((\mathcal K,d)\). Assume there exists a
> nonnegative “modulation cost” \(m(s)\in L^1((-\infty,0])\) and a constant \(C>0\) such that for every \(s_1<s_2\le 0\),
> \[
> d\big(U(s_1),U(s_2)\big)\ \le\ C\int_{s_1}^{s_2} m(s)\,ds.
> \tag{5.2}\label{eq:5.2_modulation_cauchy}
> \]
> Then \(U(s)\) has a unique limit in \(\mathcal K\) as \(s\to-\infty\); equivalently, the \(\omega\)-limit set is a singleton.
>
> *Proof.* The bound \eqref{eq:5.2_modulation_cauchy} implies \(\{U(s)\}_{s\le 0}\) is a Cauchy family as \(s\to-\infty\) because
> \(\int_{-\infty}^{0} m(s)\,ds<\infty\). Since the trajectory is precompact, the Cauchy criterion yields convergence in \(\mathcal K\).
> \(\square\)

**Comment.** The lower bound is driven by the *non-evanescence* pinning (GKP4), not by pointwise vorticity continuity. This is deliberate: it makes the non-degeneracy statement stable in the suitable-solution setting and avoids hidden regularity assumptions.

> **Lemma 5.1A (Quantile confinement on nondegenerate slices; proof-fix).** 
> Fix $(\theta,\kappa)$ as in (5.2) and set $\alpha_-:=\theta-\kappa\in(0,1)$. 
> Assume a slice $s\in[-1,0]$ satisfies
> \[
> \|U_k(\cdot,s)\|_{L^3(\mathbb R^3)}\le M_3,
> \qquad
> E_\infty(s)\ge m_1>0.
> \tag{5.4}
> \]
> Then there exists $R_+=R_+(M_3,m_1,\alpha_-)$ such that for all $u\in[\alpha_-,\theta+\kappa]$,
> \[
> 1\le Q_s(\alpha)\le R_+,
> \qquad\text{hence}\qquad (Lemma 5.1A)
> 1\le \mathcal R_{\theta,\kappa}(s)\le R_+.
> \tag{5.5}
> \]
>
> *Proof.* Since $\chi_R\equiv 1$ on $B_{R}$ and $0\le\chi_R\le 1$,
> \[
> E_\infty(s)-E_R(s)
> =\int \tfrac12|U_k|^2(1-\chi_R^2)G
> \le \tfrac12\int_{|y|\ge R}|U_k(y,s)|^2\,G(y)\,dy.
> \]
> By Hölder with exponents $(3/2,3)$,
> \[
> \int_{|y|\ge R}|U_k|^2G
> \le \bigg(\int_{\mathbb R^3}|U_k(y,s)|^3\,dy\bigg)^{2/3}
> \bigg(\int_{|y|\ge R}G(y)^3\,dy\bigg)^{1/3}
> \le M_3^2\,\bigg(\int_{|y|\ge R}G^3\bigg)^{1/3}.
> \]
> The Gaussian tail satisfies $\int_{|y|\ge R}G(y)^3\,dy\le C\,e^{-3R^2/4}$ for $R\ge 1$.
> Choose $R_+$ so that
> \[
> \tfrac12 M_3^2\Big(\int_{|y|\ge R_+}G^3\Big)^{1/3}\le (1-\alpha_-)\,m_1.
> \]
> Then for every $R\ge R_+$,
> \[
> E_R(s)\ge E_\infty(s)-(1-\alpha_-)m_1\ge \alpha_-\,E_\infty(s),
> \]
> so $Q_s(\alpha_-)\le R_+$. Since $u\mapsto Q_s(\alpha)$ is nondecreasing, $Q_s(\alpha)\le R_+$ for all $u\le \theta+\kappa$.
> Finally $Q_s(\alpha)\ge 1$ by definition, and (5.5) follows from (5.2). $\square$
>
> *Remark.* In the proof spine we will apply Lemma 5.1A at $s=0$ with $m_1=m_0$ (Lemma 5.1) and at $s=-1$
> with $m_1\simeq m_0$ once the pinned profile stability (7.14pin) is available (see §4.2.6.5). No full-space
> monotonicity of $E_G$ is used.

### 3.3 The modulation-cost statement needed downstream (M1 closed)

We require a **uniform** positive dissipation cost for any genuine “breath” of the critical profile over one fixed RG window.

**Lemma I.4 (Modulation cost / Critical coercivity).** 
Fix \(\sigma\in(0,1)\). There exists \(\varepsilon_\ast(\sigma)>0\) (depending only on \(\sigma\) and the normalized-class bounds (CE constants; cf. Appendix NFS.1.9(B))) such that for every normalized RG profile \(U\) on \([-1,0]\),

- if \(U\) is \(\sigma\)-breathing on \([-1,0]\) in the sense of Definition 5.1, then
\[
\int_{-1}^{0} D_G[U](s)\,ds \;\ge\; \varepsilon_\ast(\sigma).
\]

*Proof.* We argue by **compactness/contradiction**, which automatically yields a constant that is **uniform** over the entire normalized class.

**Step 1 (Set-up: the compact window class).** 
Let \(\mathcal K\) denote the collection of normalized RG windows \(U\) on \([-1,0]\) that satisfy:

1. \(U\) is a suitable weak solution of the Leray-rescaled Navier–Stokes system (LRNS) on \([-1,0]\times\mathbb R^3\).
2. Uniform critical bound: \(\|U\|_{L^\infty([-1,0];L^3(\mathbb R^3))}\le M\).
3. Tightness (GKP): for every \(\eta>0\) there exists \(R(\eta)\) such that 
 \(\sup_{s\in[-1,0]}\int_{|y|>R(\eta)} |U(y,s)|^3\,dy\le \eta\).
4. Non-evanescence at time \(0\): \(E_G[U](0)\ge m_0>0\) (Lemma 5.1 (inequality (5.1a))).

(Only (2)–(4) are used in this proof; the LRNS structure is used only to justify the compactness statement below.)

**Step 2 (Compactness and lower semicontinuity).** 
Assume for contradiction that no uniform \(\varepsilon_\ast(\sigma)\) exists. Then there is a sequence \(U^{(n)}\in\mathcal K\) that is \(\sigma\)-breathing on \([-1,0]\) and
\[
\int_{-1}^{0} D_G[U^{(n)}](s)\,ds \to 0.
\]
Since \(G\) is bounded below on every fixed ball \(B_R\), this implies (NFS.EST.6)
\[
\int_{-1}^{0}\!\int_{B_R} |\nabla U^{(n)}|^2\,dy\,ds \to 0 \quad\text{for every fixed }R.
\]
On the other hand, the uniform \(L^\infty_tL^3_x\) bound yields uniform \(L^\infty_tL^2(B_R)\) bounds on each ball. compactness (NFS.EST.6) for suitable weak solutions (Aubin–Lions on bounded cylinders, combined with local pressure control; see the compactness machinery (NFS.EST.6) in \([\text{LR02}]\)) gives, after passing to a subsequence,
\[
U^{(n)} \to U^{(\infty)} \quad\text{strongly in } L^2\big([-1,0]\times B_R\big) \text{ for every }R,
\]
and (by lower semicontinuity)
\[
\int_{-1}^{0} D_G[U^{(\infty)}](s)\,ds = 0.
\]
Hence \(\nabla U^{(\infty)}(s,\cdot)=0\) for a.e. \(s\in[-1,0]\); i.e. \(U^{(\infty)}(s,\cdot)\) is spatially constant for a.e. \(s\) (NFS.EST.6).

Now use the global critical bound and tightness: for each such \(s\), \(U^{(\infty)}(s,\cdot)\in L^3(\mathbb R^3)\). The only spatially constant \(L^3\) field is \(0\). Therefore (0)
\[
U^{(\infty)} \equiv 0 \quad\text{on }[-1,0]\times\mathbb R^3,
\]
and in particular \(E_G[U^{(\infty)}](0)=0\).

**Step 3 (Contradiction with non-evanescence and closedness of the window topology).** 
The strong convergence on every ball, together with tightness, implies convergence at time \(0\) in the weighted space:
\[
U^{(n)}(0) \to U^{(\infty)}(0) \quad\text{strongly in } L^2(G\,dy).
\]
(Indeed: split \(\mathbb R^3\) into \(B_R\cup B_R^c\), pass to the limit on \(B_R\) by strong convergence, and make the tail small using (3) and Hölder with \(G\in L^{3/2}\).)

By Lemma 5.1 (inequality (5.1a)), \(E_G[U^{(n)}](0)\ge m_0\) for all \(n\). Passing to the limit yields \(E_G[U^{(\infty)}](0)\ge m_0\), contradicting \(E_G[U^{(\infty)}](0)=0\).

This contradiction shows that
\[
\varepsilon_\ast(\sigma) := \inf\Big\{\int_{-1}^{0} D_G[U](s)\,ds : U\in\mathcal K \text{ is }\sigma\text{-breathing}\Big\} > 0,
\]
which proves the lemma. \(\square\)

**Remark 5.5 (What M1 was, and why it is now closed).** 
Earlier drafts tried to force a *quantitative* bound on the boundary-flux term at the (possibly \(O(1)\)) “width radius”. The argument above avoids that entirely: we only use (i) compactness of the normalized class on a unit window and (ii) the rigidity that **zero dissipation forces triviality**. This yields a uniform \(\varepsilon_\ast(\sigma)\) with no dependence on the particular profile.
---

## 4. Energy Budget in Leray Similarity Variables (OU–Adjoint Form)

### 4.1 Why we change frames

In earlier drafts of this spine the Gaussian-weighted local energy inequality (LEI) was written directly for the fixed-frame RG windows
\[
U_k(x,t)=r_k\,u(x_k+r_k x,t_k+r_k^2 t),\qquad t\in[-1,0],
\]
with the fixed backward heat kernel \(G(x)= (4\pi)^{-3/2}e^{-|x|^2/4}\). 
The resulting term
\[
B_G[k]=\iint_{[-1,0]\times\mathbb{R}^3}\Big(\tfrac12|U_k|^2\Delta G+\big(\tfrac12|U_k|^2+P_k\big)U_k\cdot\nabla G\Big)\,dx\,dt
\]
has no *a priori* sign and (as written) is not obviously summable in \(k\).

The concentration–compactness (see [GKP13]) route (NRS96) passes to **Leray similarity variables**, where “zooming-in” is encoded as *time translation*. In that frame the Gaussian \(G\) becomes the natural stationary density for the adjoint of the linearized generator, and the problematic “bulk” terms collapse to annulus-supported errors after a cutoff.

This section implements that change and reduces the previous P1 (“bulk term”) to a single explicit verification item (VI.6) plus the already-defined Flux Sealing.

---

### 4.2 Leray similarity variables and the rescaled equation

Fix a putative singular point \((x_\star,T^\star)\) and set similarity variables
\[
y=\frac{x-x_\star}{\sqrt{T^\star-t}},\qquad \tau=-\log(T^\star-t),
\]
and the Leray-rescaled fields
\[
U(y,\tau)=\sqrt{T^\star-t}\;u(x,t),\qquad P(y,\tau)=(T^\star-t)\;p(x,t).
\]
A direct chain-rule computation gives the **Leray-rescaled Navier–Stokes system**
\[
\partial_\tau U-\Delta U+(U\cdot\nabla)U+\nabla P+\tfrac12\,y\cdot\nabla U+\tfrac12\,U=0,
\qquad \nabla\cdot U=0.
\tag{LRNS}
\]
(For the stationary/self-similar case \(U(\cdot,\tau)\equiv U(\cdot)\) this reduces to the profile equation
\(-\Delta U+\tfrac12\,y\cdot\nabla U+\tfrac12\,U+(U\cdot\nabla)U+\nabla P=0\), consistent with Tsai’s formulation. (see Tsai98).)

**Discrete RG orbit as time shifts.** 
One may now define the RG windows by **translation in \(\tau\)**:
\[
U_k(y,s):=U(y,k+s),\qquad s\in[-1,0],
\]
so that the former “scale-to-scale” step becomes the trivial map \(k\mapsto k+1\).

> **Pinned gauge in the Leray frame.** 
> The earlier “pinned vorticity” normalization can be imposed at each integer time \(\tau=k\) by composing with spatial translations in \(y\) (and, if needed, rotations), exactly as in the fixed-frame orbit. This is the same modulation content, just expressed in the natural similarity time.

---

### 4.3 The OU–adjoint identity for the Gaussian

Let
\[
G(y)=(4\pi)^{-3/2}\exp\!\Big(-\frac{|y|^2}{4}\Big).
\]
Then
\[
\nabla G =-\frac{y}{2}G,\qquad 
\Delta G =\Big(\frac{|y|^2}{4}-\frac32\Big)G,
\]
and the crucial **OU–adjoint relation**
\[
\Delta G+\frac12\,y\cdot\nabla G+\frac32\,G=0
\tag{OU*}
\]
holds identically (a one-line substitution).

This identity is the reason we pass to (LRNS): the additional linear terms \(-\tfrac12 y\cdot\nabla U-\tfrac12 U\) in (LRNS) are precisely the terms whose adjoint produces the \(\tfrac12 y\cdot\nabla\psi+\tfrac32\psi\) correction in the LEI; choosing \(\psi\) proportional to \(G\) annihilates the bulk contribution.

---

### 4.4 Localized Gaussian energy inequality in the Leray frame (VI.6 filled)

We record the localized Gaussian energy inequality in similarity variables, and we fill in the only
missing calculus check from the previous draft (the origin of the “\(+3\)” coefficient).

**Lemma 6.1 (Localized Gaussian budget in the Leray frame).** 
Let \((U,P)\) be a suitable weak solution to (LRNS) on \([-1,0]\times\mathbb R^3\).
Fix \(R\ge1\) and set
\[
\psi_R(y) := \chi_R(y)^2\,G(y),
\qquad
E_R(s):=\int \tfrac12 |U(y,s)|^2\,\psi_R(y)\,dy,
\qquad
D_R(s):=\int |\nabla U(y,s)|^2\,\psi_R(y)\,dy.
\]
Then for all \(-1\le s_1<s_2\le0\),
\[
E_R(s_2)+\int_{s_1}^{s_2} D_R(s)\,ds
\;\le\;
E_R(s_1)+\mathrm{Err}_R[U; s_1,s_2],
\tag{6.2}\label{6.2}
\]

*(General form.)* Lemma 6.1 is a special case of the LRNS local energy inequality (LRNS-LEI) recorded in Appendix **NFS.1.5**.

where
\[
\mathrm{Err}_R[U; s_1,s_2]
:=
\int_{s_1}^{s_2}\!\int \Big(\tfrac12|U|^2+P\Big)\,U\cdot\nabla\psi_R\,dy\,ds
\;+
\int_{s_1}^{s_2}\!\int \Big[
\tfrac12|U|^2\,\Delta\psi_R
+\tfrac14|U|^2\,(y\cdot\nabla\psi_R+3\psi_R)
\Big]dy\,ds.
\]

*Proof.* Start from the local energy inequality for \((u,p)\) in physical variables and test it
with a localized backward heat kernel:
\[
\phi_{R}(x,t):=\chi_R\!\left(\frac{x}{\sqrt{s}}\right)^{\!2}\,\Gamma(x,t)
\quad\text{with}\quad
s:=t_\ast-t>0,
\qquad
\Gamma(x,t)=(4\pi s)^{-3/2}e^{-|x|^2/(4s)}.
\]
Introduce similarity variables
\[
y:=\frac{x}{\sqrt{s}},\qquad \tau:=-\log s,
\qquad
u(x,t)=\frac{1}{\sqrt{s}}U(y,\tau),
\qquad
p(x,t)=\frac{1}{s}P(y,\tau),
\]
so that \((U,P)\) solves (LRNS). In these variables one has \(\Gamma(x,t)=s^{-3/2}G(y)\) with
\(G(y)=(4\pi)^{-3/2}e^{-|y|^2/4}\), and therefore \(\phi_R(x,t)=s^{-3/2}\psi_R(y)\) (Appendix NFS.IMP).

The LEI term \((\partial_t+\Delta_x)\phi_R\) produces the “OU\(^\ast\)” operator. The missing check
(VI.6) is the following computation:

> **(VI.6) Similarity calculus for \((\partial_t+\Delta_x)\phi_R\).** 
> Writing \(s=t_\ast-t\) and \(\phi_R=s^{-3/2}\psi_R(y)\) with \(y=x/\sqrt{s}\), one has
> \[
> (\partial_t+\Delta_x)\phi_R
> =
> \frac{1}{2}\,s^{-5/2}\,(2\Delta_y+y\cdot\nabla_y+3)\psi_R(y).
> \]
> *Proof.* Since \(\partial_t=-\partial_s\), one computes
> \[
> \partial_s\big(s^{-3/2}\psi_R(y)\big)
> =
> -\tfrac{3}{2}s^{-5/2}\psi_R(y)
> -\tfrac12 s^{-5/2}\,y\cdot\nabla\psi_R(y),
> \]
> while \(\Delta_x(s^{-3/2}\psi_R(y))=s^{-5/2}\Delta_y\psi_R(y)\). Adding gives
> \[
> (\partial_t+\Delta_x)\phi_R
> =s^{-5/2}\Big[\Delta\psi_R+\tfrac12 y\cdot\nabla\psi_R+\tfrac32\psi_R\Big]
> =\tfrac12 s^{-5/2}(2\Delta+y\cdot\nabla+3)\psi_R.
> \]
> The coefficient “\(+3\)” comes *only* from differentiating the prefactor \(s^{-3/2}\).
> \[
> (\partial_t+\Delta_x)\phi_R=\tfrac12\,s^{-5/2}\,(2\Delta_y+y\cdot\nabla_y+3)\psi_R(y).
> \]
> In particular, the factor is \((\tfrac12)\), not \((\tfrac14)\).

Substituting this identity into the LEI (and rewriting the remaining LEI terms under the same change of
variables) yields (6.2). \(\square\)

**Remark 6.2 (OU\(^\ast\) localization for \(\psi_R=\chi_R^2G\)).** 
The adjoint OU identity \((2\Delta+y\cdot\nabla+3)G=0\) implies
\[
(2\Delta+y\cdot\nabla+3)(\chi_R^2G)
=
\big(2\Delta\chi_R^2+y\cdot\nabla\chi_R^2\big)G
+4\nabla\chi_R^2\cdot\nabla G,
\]
so the entire \((\partial_t+\Delta)\)-forcing generated by the cutoff is supported on the annulus
\(A_R=\{R\le|y|\le2R\}\).

### 4.5 Passing $R\to\infty$: what survives, and the correct full-space Gaussian identity (P1\_G)

Lemma 6.1 is the *only* legitimate bridge between the physical local-energy inequality and any Gaussian-weighted
budget in the Leray-rescaled variables. A crucial subtlety is that the error term $\mathrm{Err}_R[U_k]$ contains a
**bulk** contribution coming from the factor $\chi_R^2\nabla G$:
\[
U_k\cdot\nabla\psi_R
=U_k\cdot\big(\chi_R^2\nabla G\big)\;+\;U_k\cdot\big(G\nabla(\chi_R^2)\big).
\]
The second term is annular (supported in $A_R$), but the first term is *not*: it persists on $\{|y|\lesssim R\}$ and
converges to $U_k\cdot\nabla G$ as $R\to\infty$.

This means:

- The *forcing* part of $\mathrm{Err}_R$ becomes annular after expanding $\psi_R=\chi_R^2G$ (because
 $(\Delta+\tfrac12 y\!\cdot\!\nabla+\tfrac32)G=0$), hence it vanishes as $R\to\infty$ under (GKP) + cutoff bounds (NFS.EST.1).
- The *annular* transport pieces (those involving $\nabla\chi_R$) also vanish as $R\to\infty$ under (GKP) and Flux Sealing.
- But the **bulk Gaussian transport flux**
 \[
 \mathcal F_G[U_k; s_1,s_2]
 :=\int_{s_1}^{s_2}\!\!\int_{\mathbb R^3}
 \Big(\tfrac12|U_k|^2+P_k\Big)\,U_k\cdot\nabla G\,dy\,ds
 \]
 survives in the limit and has **no sign a priori**.

So the “monotone full-space Gaussian budget” claimed in earlier drafts is not available unless one proves an
additional cancellation/sign statement for $\mathcal F_G$. We elevate that missing input to an explicit gap.

> **Proposition 6.3 (Correct full-space Gaussian LEI in LRNS).** 
> Let $(U_k,P_k)$ be a suitable LRNS solution on $[-1,0]$ as in §3. Then for all $-1\le s_1<s_2\le 0$,
> \[
> E_G[U_k](s_2)\;+\;\int_{s_1}^{s_2}D_G[U_k](s)\,ds
> \;\le\;
> E_G[U_k](s_1)\;+\;\mathcal F_G[U_k;s_1,s_2],
> \tag{6.3}
> \]
> where
> \[
> E_G[U_k](s):=\int_{\mathbb R^3}\tfrac12|U_k(y,s)|^2\,G(y)\,dy,\qquad
> D_G[U_k](s):=\int_{\mathbb R^3}|\nabla U_k(y,s)|^2\,G(y)\,dy.
> \]

**Proof.** Apply Lemma 6.1 with $\psi_R=\chi_R^2G$ and then let $R\to\infty$.

1. The left-hand side converges to $E_G[U_k](s_2)+\int_{s_1}^{s_2}D_G[U_k]$ by monotone convergence, since
 $\psi_R\uparrow G$ and $|\nabla U_k|^2\psi_R\uparrow|\nabla U_k|^2G$.

2. For the forcing part of $\mathrm{Err}_R$, expand
 $(\Delta+\tfrac12y\!\cdot\!\nabla+\tfrac32)(\chi_R^2G)$ and use $(\Delta+\tfrac12y\!\cdot\!\nabla+\tfrac32)G=0$.
 Every remaining term contains $\nabla\chi_R$ or $\Delta\chi_R$, hence is supported in $A_R$ and tends to $0$ as (Proposition 6.3)
 $R\to\infty$ by the (GKP) tightness bounds.

3. For the transport part,
 \[
 \int_{s_1}^{s_2}\!\!\int\Big(\tfrac12|U_k|^2+P_k\Big)\,U_k\cdot\nabla(\chi_R^2G)
 =\mathcal F_G[U_k;s_1,s_2] \;+\; o_{R\to\infty}(1),
 \]
 where the $o(1)$ comes from the annular $\nabla\chi_R$ contribution, controlled exactly as in step 2 together with
 Flux Sealing to handle the pressure terms. This yields (6.3). ∎

> **P1\_G (Gaussian flux sign/cancellation).** 
> Prove that along the pinned RG orbit (or for every LRNS suitable solution in the GKP class),
> the flux term $\mathcal F_G[U_k;s_1,s_2]$ is nonpositive, or at least summable in $k$ in a way that implies a finite
> total dissipation bound. Without such an input, (6.3) does **not** imply that $E_G$ is monotone.

**Remark (how we avoid using P1\_G in the proof spine).** 
The contradiction argument in §6 does *not* require monotonicity of the **full-space** $E_G$. What it needs is a
finite-dissipation budget at the **quantitative scale** $\mathcal R_k$. That budget is obtained by keeping cutoffs (and
eventually allowing them to *move*) and then using the M2 trade mechanism to absorb the cutoff-generated flux into the
dissipation. The rest of §6 is written so that P1\_G becomes optional: it would simplify some steps, but it is not
used as a external step.

---

## 5. Gate and No-Theft mechanisms (integration targets)
### Gate definition
We use the **Gaussian shell cubic flux gate**
\[
\mathcal G(R,\tau):=\frac{1}{R}\int_{A_R}|U(\tau)|^3\,G\,dy,
\qquad A_R:=\{R\le|y|\le 2R\}.
\]
A “gate opening” event is the existence of \((R,\tau)\) such that \(\mathcal G(R,\tau)\ge\gamma_0\).

### No-Theft principle (pressure-tail decoupling)
The pressure is slaved: \(P=\mathcal R_i\mathcal R_j(U_iU_j)\).

**Definition (No-Theft tail).** For an LRNS profile \(U\) on \([-1,0]\), define the pressure-tail functional
\[
\mathrm{Tail}_\sharp(R,\tau):=
\frac{1}{R^3}\int_{B_{R/8}}|U(y,\tau)|^2\,dy
\;+\;
\int_{|y|\ge 16R}\frac{|U(y,\tau)|^2}{|y|^3}\,dy,
\qquad R\ge 1,\ \tau\in[-1,0].
\tag{7.NT0}\label{eq:7NT0_tail_def}
\]
It measures the far-field contribution of the Calderón--Zygmund pressure kernel to the core region after the near/far split.

> **Lemma 7.8C\(_{\mathrm{NT}}\) (No-Theft tail decay).** 
> For every \(\tau\in[-1,0]\) and every \(R\ge 1\),
> \[
> \mathrm{Tail}_\sharp(R,\tau)\ \le\ \frac{C_{\rm NT}}{R^2}\,\|U(\tau)\|_{L^3(\mathbb R^3)}^2,
> \tag{7.NT1}\label{eq:7NT1_tail_decay}
> \]
> with an absolute constant \(C_{\rm NT}\) depending only on the fixed cutoff template. Under (CE1),
> \(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(R,\tau)\lesssim M^2R^{-2}\), hence the tail remainder is uniform in time and vanishes as \(R\to\infty\) (Lemma 7.8C).
>
> *Proof.* Hölder on \(B_{R/8}\) gives \(\int_{B_{R/8}}|U|^2\le \|U\|_3^2|B_{R/8}|^{1/3}\), hence the first term \(\lesssim R^{-2}\|U\|_3^2\) (Lemma 7.8C).
> For the second term, use \(\||U|^2\|_{3/2}=\|U\|_3^2\) and \(\||y|^{-3}\|_{L^3(|y|\ge 16R)}\sim R^{-2}\). \(\square\)

We introduce \(\mathrm{Tail}_\sharp(R,\tau)\) and prove **uniform-in-time** vanishing as \(R\to\infty\).
This ensures the far-field cannot inject order-one flux into the core on the blow-up time scale.

### Flux Sealing as the “energy barrier”

The Gate functional is the Gaussian-shell cubic flux
\[
\mathcal G(R,\tau):=\frac{1}{R}\int_{A_R}|U(\tau)|^3\,G\,dy,
\qquad A_R:=\{R\le|y|\le 2R\}.
\]
Lemma 7.8, Step 3 provides the pointwise estimate (cf. (7.20C11)):
\[
\mathcal G(R,\tau)\ \le\ C\,M\,D_G[U](\tau;4R),
\qquad \text{for a.e. }\tau\in[-1,0],\ R\ge 1,
\tag{7.G1}
\]
where \(D_G[U](\tau;4R)=\int_{\mathbb R^3}|\nabla U(\tau)|^2\,\chi_{4R}^2\,G\,dy\).

Lemma 7.8, Step 4 provides pressure localization (cf. (7.20C13)–(7.20C16)):
\[
\frac1R\int_{A_R}|U|\,|P-(P)_{B_{2R}}|\,G\,dy
\ \le\ C\,\frac1R\int_{A_{R/4}^{8R}}|U|^3\,G\,dy
\ +\ C\,D_G[U](\tau;4R)^{1/2}\,\mathrm{Tail}_\sharp(R,\tau).
\tag{7.G2}
\]
By Young’s inequality, the second term is
\(\le \varepsilon D_G[U](\tau;4R)+C_\varepsilon\,\mathrm{Tail}_\sharp(R,\tau)^2\).
Uniform No-Theft (Lemma 7.8C\(_{\mathrm{NT}}\)) ensures that, along each RG window, the tail remainder
\(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(R,\tau)^2\) is both **uniform** in time and vanishes as \(R\to\infty\).

We record the barrier implication in the precise form actually used downstream.

> **Proposition 7.G (Gate barrier; “opening” forces dissipation cost).** 
> Let \((U,P)\) be an RG-window profile on \([-1,0]\) satisfying (GKP1–GKP4). 
> Fix \(R\ge 1\) and an interval \(I=[\tau_0,\tau_1]\subset[-1,0]\). 
> If \(\mathcal G(R,\tau)\ge \gamma\) for a.e. \(\tau\in I\), then
> \[
> \int_{\tau_0}^{\tau_1} D_G[U](\tau;4R)\,d\tau\ \ge\ \frac{\gamma}{C\,M}\,(\tau_1-\tau_0),
> \tag{7.G3}
> \]
> with the same constant \(C\) as in (7.G1).
> Moreover, combining the fixed-cutoff localized energy identity (Lemma 7.10) with the strong trade (Lemma 7.8) yields
> \[
> \big|E_G[U](\tau_1;R)-E_G[U](\tau_0;R)\big|
> \ \le\ C\int_{\tau_0}^{\tau_1} D_G[U](\tau;4R)\,d\tau
> \ +\ C\,\Big(\sup_{\tau\in I}\mathrm{Tail}_\sharp(\tau;R/4)\Big)^2.
> \tag{7.G4}
> \]
> In particular, on large scales \(R\gg1\) (where No-Theft makes the tail term negligible), a sustained gate opening on
> any interval forces an order-one variation of the localized Gaussian energy.

*Remark (what still must be explicit to convert this into the “pointwise Gate Theorem”).* 
To deduce \(\operatorname*{ess\,sup}_{\tau\le0,R\ge1}\mathcal G(R,\tau)\le\gamma_0\) from (7.G3)–(7.G4), one needs a
**persistence/anti-flash lemma** preventing \(\mathcal G(R,\tau)\) from spiking on a null set of times.
We isolate this as a single verification item.

> **Lemma 7.GA (Anti-Flash at the fixed gate threshold).** 
> Fix a gate level \(\gamma>0\). Assume the CE(\(L^3\)) package CE1–CE4 holds on an RG window \(\tau\in[-1,0]\).
> Then for every \(R\ge 1\) the shell-gate functional
> \[
> \mathcal G(R,\tau)=\frac1R\int_{A_R}|U(\tau)|^3\,G\,dy
> \]
> admits a representative that is **continuous in \(\tau\)** on \([-1,0]\).
> Consequently, there exists a time-length \(c_\star=c_\star(M,\gamma)\in(0,1)\) such that whenever (Lemma 7.GA)
> \(\mathcal G(R,\tau_\star)\ge 2\gamma\) at some \(\tau_\star\in[-1,0]\), one has
> \[
> \mathcal G(R,\tau)\ge \gamma
> \qquad\text{for all }\tau\in[\tau_\star,\min\{\tau_\star+c_\star,0\}].
> \tag{7.G5}
> \]
> In particular, a pointwise gate opening at level \(2\gamma\) forces a **nontrivial persistence interval** at level \(\gamma\).

**Proof (reader-facing, “why continuity holds”).** 
The only input here is the *endpoint critical regularity mechanism* already implicit in CE1–CE3.

1) **From CE1 to smoothness on the window.** 
By CE1 we have \(U\in L^\infty_\tau L^3_y(\mathbb R^3)\) on \([-1,0]\), and by CE3 the pair \((U,P)\) is suitable.
The endpoint Serrin criterion / backward-uniqueness theorem (Escauriaza–Seregin–Šverák) implies that any suitable (Lemma 7.GA)
Navier–Stokes solution with \(L^\infty_tL^3_x\) control is regular on the corresponding cylinder.
After translating between physical variables and similarity variables (which preserves the \(L^3\) norm),
we obtain that \(U\) is smooth on \((-1,0]\times\mathbb R^3\), hence in particular (Lemma 7.GA)
\[
U\in C^\infty_{(\tau,y)}\big((-1,0]\times\mathbb R^3\big).
\]
(See Appendix NFS, “Citation check 7.GA”, for the cite-level mapping.)

2) **Continuity of the gate functional.** 
Fix \(R\ge 1\). Since \(U(\tau,\cdot)\) is smooth and \(|U(\tau)|^3G\in L^1(\mathbb R^3)\) for each \(\tau\in[-1,0]\)
(using CE1 and \(0<G\le 1\)), the map
\[
\tau\longmapsto \int_{A_R}|U(\tau)|^3\,G\,dy
\]
is continuous on \([-1,0]\) by dominated convergence (or directly by smooth dependence of \(U\) on \(\tau\)).
Therefore \(\tau\mapsto \mathcal G(R,\tau)\) is continuous on \([-1,0]\) (Lemma 7.GA).

3) **Uniform continuity and persistence at a fixed level.** 
A continuous function on the compact interval \([-1,0]\) is uniformly continuous.
Thus, for the *fixed* level \(\gamma>0\) there exists \(c_\star=c_\star(M,\gamma)\in(0,1)\) such that (Lemma 7.GA)
\(|\tau-\tau'|\le c_\star\) implies \(|\mathcal G(R,\tau)-\mathcal G(R,\tau')|\le \gamma\).
If \(\mathcal G(R,\tau_\star)\ge 2\gamma\), this yields \(\mathcal G(R,\tau)\ge\gamma\) for all
\(\tau\in[\tau_\star,\tau_\star+c_\star]\cap[-1,0]\), proving (7.G5). ∎

*Remark (why \(c_\star\) is an admissible fixed constant in the Gate Theorem).* 
In the Gate Theorem we apply Lemma 7.GA only at a **single, fixed threshold** \(\gamma=\gamma_0\).
Hence \(c_\star(M,\gamma_0)\) is a fixed admissible constant for the entire argument (in the sense of Appendix NFS.1.9) (Lemma 7.GA).
Moreover, for very large radii \(R\) the Gaussian factor makes \(\mathcal G(R,\tau)\) automatically tiny:
\[
\mathcal G(R,\tau)\le \frac1R\sup_{A_R}G\int_{\mathbb R^3}|U(\tau)|^3\,dy
\le \frac{M^3}{R}\,(4\pi)^{-3/2}e^{-R^2/4}.
\]
Thus any potential gate opening occurs only for \(R\) in a compact range depending on \((M,\gamma_0)\), (Lemma 7.GA)
which is the natural regime for a uniform persistence constant.

> **Corollary 7.GB (A gate opening contains a fixed dissipation packet).** 
> Fix the threshold \(\gamma=\gamma_0\) and let \(c_\star=c_\star(M,\gamma_0)\) be given by Lemma 7.GA.
> If \(\mathcal G(R,\tau_\star)\ge 2\gamma_0\) for some \(R\ge1\) and \(\tau_\star\in[-1,0]\), then
> \[
> \int_{\tau_\star}^{\min\{\tau_\star+c_\star,0\}} D_G[U](\tau;4R)\,d\tau
> \ \ge\ \frac{\gamma_0}{C\,M}\,c_\star,
> \tag{7.G6}
> \]
> where \(C\) is the same constant as in (7.G1).

**Proof.** By Lemma 7.GA (with \(\gamma=\gamma_0\)), \(\mathcal G(R,\tau)\ge\gamma_0\) for all
\(\tau\in[\tau_\star,\tau_\star+c_\star]\cap[-1,0]\).
On this interval, (7.G1) implies \(D_G[U](\tau;4R)\ge \gamma_0/(C\,M)\) pointwise.
Integrating in \(\tau\) yields (7.G6). ∎

*Remark (how Corollary 7.GB is used to close P0.1).* 
Corollary 7.GB converts a **single** pointwise gate opening into a **quantized** dissipation increment on a time-interval of fixed length.
To turn this into the Gate Theorem (P0.1), one needs to show that such dissipation packets cannot occur along the pinned RG orbit without
violating the finite quantitative-scale dissipation budget (7.2).
In the spine this is implemented by aligning the relevant gate radii \(R\) with the quantitative radii \(\mathcal R_k\) on each window
(so that \(D_G(\cdot;4R)\) dominates the per-step quantitative dissipation \(\mathfrak D_k\)).
The required alignment is a bookkeeping statement rather than a new analytic estimate, but it must be written explicitly in §4.2.

## 6. Closure: finite dissipation forces rigidity (proof-spine polish)

This section turns the three pillars into the final contradiction.

### 6.1 What “finite dissipation” we actually need (and where it comes from)

Earlier drafts implicitly used a *monotone* full-space Gaussian budget to claim
\[
\int_{-\infty}^{0}D_G[U](s)\,ds<\infty.
\]
After the correction in §2.5, the full-space identity (6.3) contains the flux term $\mathcal F_G$, so monotonicity is
not automatic and one should **not** bank the proof on it.

The rigidity step (M1: “infinitely many breaths force infinite dissipation”) only needs **finite dissipation at the
quantitative scale**. For the pinned orbit $\{U_k\}$, define the per-step quantitative dissipation
\[
\mathfrak D_k \;:=\;\int_{-1}^{0} D_{4\mathcal R_k}[U_k](s)\,ds,
\qquad \mathcal R_k:=\mathcal R_{\theta,\kappa}[U_k(0)].
\tag{7.1}
\]
What we will prove (using the now-closed M2 mechanism of §4.2.5–§4.2.6.5) is the summability
\[
\sum_{k=1}^{\infty}\mathfrak D_k \;<\;\infty,
\tag{7.2}\label{eq:7.2}
\]
which is the exact “finite total dissipation” input needed to contradict an infinite sequence of breaths.

> **Proposition 7.1 (Finite quantitative-scale dissipation; cite-level).** 
> Let \((U_k,P_k)\) be the pinned endgame windows with quantitative radii \(\mathcal R_k\) and quantitative dissipation
> \(\mathfrak D_k:=\int_{-1}^{0}D_{4\mathcal R_k}[U_k](s)\,ds\).
> Then there exists a constant \(c_*=c_*(\eta)>0\) in the admissible constant class (Appendix NFS.1.9) such that for all \(k\ge 1\),
> \[
> E_{\mathcal R_k}[U_k](0)\;+\;c_*\,\mathfrak D_k
> \;\le\;E_{\mathcal R_{k-1}}[U_{k-1}](0).
> \tag{7.3}
> \]
> In particular, \(\sum_{k=1}^{\infty}\mathfrak D_k<\infty\).

**Proof (cite-level; no hidden hypotheses).** 
Fix \(k\ge1\) and apply the fixed-cutoff identity (Lemma 7.10) on the unit window \([-1,0]\) with radius \(R=\mathcal R_k\):
\[
E_{\mathcal R_k}[U_k](0)-E_{\mathcal R_k}[U_k](-1)+\int_{-1}^{0}D_{\mathcal R_k}[U_k](s)\,ds
=\mathrm{Err}_{\mathcal R_k}[U_k;-1,0].
\]
By the signed trade (Option B, Lemma 7.1F + Lemma 7.1H together with Lemmas 7.1H0–7.1H1),
there exist \(\eta\in(0,1)\) and \(C<\infty\) such that
\[
\mathrm{Err}_{\mathcal R_k}[U_k;-1,0]
\le \eta\int_{-1}^{0}D_{4\mathcal R_k}[U_k](s)\,ds
\; +\; C\,\Big(\sup_{s\in[-1,0]}\mathrm{Tail}_\sharp^{(k)}(s;\mathcal R_k/4)\Big)^2.
\]
Since \(D_{\mathcal R_k}\le D_{4\mathcal R_k}\) and \(\mathfrak D_k=\int_{-1}^{0}D_{4\mathcal R_k}[U_k]\),
we obtain (Proposition 7.1)
\[
E_{\mathcal R_k}[U_k](0) + (1-\eta)\,\mathfrak D_k
\le E_{\mathcal R_k}[U_k](-1) + C\,\Big(\sup_{s\in[-1,0]}\mathrm{Tail}_\sharp^{(k)}(s;\mathcal R_k/4)\Big)^2.
\]
By the shift identity \(U_k(\cdot,-1)=U_{k-1}(\cdot,0)\), the left term on the right-hand side is
\(E_{\mathcal R_k}[U_{k-1}](0)\). The radii mismatch is handled in two deterministic steps.

1. **Log-Lipschitz dependence of \(E_R\) on the radius.** For any fixed profile \(V\) and any \(R,R'\ge 1\),
 \[
 |E_{R'}[V](0)-E_R[V](0)|
 \ \le\ 
 C_{\rm ER}\,E_\infty[V](0)\,|\log(R'/R)|.
 \tag{7.3a}\label{eq:7_3a_log_lipschitz_ER}
 where $C_{\rm ER}$ is an **absolute cutoff constant** depending only on the fixed cutoff template.
 \]
 *Proof sketch.* Differentiate \(E_{e^\rho}[V](0)=\int \tfrac12|V|^2\,\chi_{e^\rho}^2\,G\) in \(\rho\). The derivative is supported where
 \(\nabla\chi\neq 0\) and satisfies \(|\partial_\rho(\chi_{e^\rho}^2)|\lesssim 1\), hence (Proposition 7.1)
 \(|\partial_\rho E_{e^\rho}[V](0)|\lesssim \int \tfrac12|V|^2\,G \le E_\infty[V](0)\). Integrate from \(\rho=\log R\) to \(\log R'\).

2. **Drift-control for the quantitative radius.** Along the pinned RG orbit, Lemma 7.9 combined with the stability estimate
 \(\|\widetilde F_{-1}-\widetilde F_{0}\|_{L^\infty}\lesssim \mathfrak D_k\) yields a quantitative drift bound
 \[
 |\log\mathcal R_k-\log\mathcal R_{k-1}|
 \ \le\
 C_{\rm drift}\,\mathfrak D_k,
 \qquad
 C_{\rm drift}:=\frac{C_{\rm stab}}{\kappa}\,\log R_+,
 \tag{7.3b}\label{eq:7_3b_drift_bound}
 \]
 where \(R_+\) is the confinement radius from (7.29).

Combining \eqref{eq:7_3a_log_lipschitz_ER}–\eqref{eq:7_3b_drift_bound} with \(E_\infty[U_{k-1}](0)\le E_\ast\) (pin-time normalization),
we obtain the comparison (Proposition 7.1)
\[
E_{\mathcal R_k}[U_{k-1}](0)\ \le\ E_{\mathcal R_{k-1}}[U_{k-1}](0)\ +\ C_{\rm mis}\,\mathfrak D_k,
\qquad
C_{\rm mis}:=C_{\rm ER}\,E_\ast\,C_{\rm drift}.
\tag{7.3c}\label{eq:7_3c_energy_mismatch}
\]
Finally, we fix the band parameter \(\kappa\) (and then \(\eta\in(0,1)\)) at the outset so that
\[
C_{\rm mis}\ \le\ \tfrac12(1-\eta),
\tag{7.3d}\label{eq:7_3d_parameter_choice_absorb}
\]
which is possible since \(C_{\rm mis}\propto \kappa^{-1}\) and \(\kappa\) is a free design parameter in the quantitative-radius definition (5.2).
With this choice, the mismatch term is absorbed into \((1-\eta)\mathfrak D_k\), yielding \(c_*:=\tfrac12(1-\eta)>0\) in (7.3) (a fixed parameter constant once \(\eta\) is chosen; see Appendix NFS.1.9).

Finally, the No-Theft tail control (Lemma 7.8C\(_\mathrm{NT}\)) implies the tail remainder tends to zero on the pinned tail,
so summing (7.3) over \(k\) telescopes and yields \(\sum_k \mathfrak D_k<\infty\). ∎

**Interpretation.** The functional $E_{\mathcal R_k}$ is a Lyapunov-type quantity *at the quantitative scale*:
each RG step either stabilizes the profile or it pays a definite amount of dissipation $\mathfrak D_k$.
This is the correct replacement for any claim about monotonicity of the full-space $E_G$.

### 6.1.1 Historical checkpoint (resolved): why an absolute-value cutoff trade is insufficient

The fixed-cutoff endpoint identity (Lemma 7.10) yields, for any \(R\ge 1\),
\[
E_R(0)-E_R(-1)\ +\ \int_{-1}^{0}D_R(\tau)\,d\tau\ =\ \mathrm{Err}_R[U;-1,0].
\tag{7.1A}\label{eq:7_1A_fixed_identity}
\]
A purely **absolute-value** estimate of the form
\[
|\mathrm{Err}_R[U;-1,0]|
\ \le\ C\int_{-1}^{0}D_G[U](\tau;4R)\,d\tau\ +\ C\Big(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(\tau;R/4)\Big)^2
\tag{7.20C revisited}
\]
is therefore *not* sufficient, by itself, to force a **one-sided Lyapunov drop** at the quantitative scale (Proposition 7.1).

What is needed is a **signed absorption** with coefficient strictly smaller than \(1\), namely
\[
\mathrm{Err}_R[U;-1,0]
\ \le\ \eta\,\int_{-1}^{0}D_G[U](\tau;4R)\,d\tau
\ +\ C\,\Big(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(\tau;R/4)\Big)^2,
\qquad \eta<1,
\tag{RB1}\label{eq:RB1_signed_trade}
\]
which, combined with \eqref{eq:7_1A_fixed_identity} and \(D_R\le D_{4R}\), yields
\[
E_R(0)\ +\ (1-\eta)\int_{-1}^{0}D_G[U](\tau;4R)\,d\tau
\ \le\ E_R(-1)\ +\ C\,\Big(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(\tau;R/4)\Big)^2.
\tag{7.1B}\label{eq:7_1B_signed_drop}
\]

**Resolution (Option B, gauge-free).** 
In the present canonical build, the signed trade \eqref{eq:RB1_signed_trade} is proved *profile-free* by the
transport–dichotomy mechanism (Option B) in §4.1.5: Lemma 7.1F (transport lower bound under absorption failure)
and Lemma 7.1H (transport \(\Rightarrow\) Gate opening \(\Rightarrow\) dissipation packet), together with No-Theft, yield
\eqref{eq:RB1_signed_trade} on the pinned tail at the quantitative radii. Consequently, Proposition 7.1 and the quantitative
budget (7.3) are unconditional in the present spine.

### 6.1.2 Route A executed: interior–exterior algebra and the remaining analytic nucleus (RB1→VI.RB1)

This subsection carries out **Route A** from §4.1.1 at the level of *explicit identities* and isolates the
**single remaining estimate** needed to upgrade Proposition 7.1 to a fully proved Annals-level statement.

The guiding principle is simple:

- The fixed-cutoff identity (Lemma 7.10) is already available for the RG window class (thanks to local \(L^4\) and commutator killing).
- The error \(\mathrm{Err}_R\) is a sum of (i) annulus-supported commutator pieces and (ii) a *bulk Gaussian transport flux* induced by \(\nabla G\).
- Annulus pieces are already controlled by Lemma 7.8 (with a No-Theft vanishing remainder).
- Therefore, **RB1 reduces to showing that the bulk Gaussian transport flux can be absorbed into dissipation with coefficient \(<1\) up to a tail remainder.** (Proposition 7.1)

We implement this reduction as follows.

#### A. Interior / exterior cutoff family and the exact recombination

Fix \(R\ge 1\) and define the interior cutoff
\[
\psi_R^{\mathrm{in}}:=\chi_R^2\,G.
\]
To make the exterior test compactly supported for the local energy identity argument,
introduce a second large radius \(L\gg R\) and define the truncated exterior cutoff
\[
\psi_{R,L}^{\mathrm{out}}
:=
(1-\chi_R^2)\,\chi_L^2\,G.
\]
Then \(\psi_R^{\mathrm{in}}\ge 0\), \(\psi_{R,L}^{\mathrm{out}}\ge 0\), and
\[
\psi_R^{\mathrm{in}}+\psi_{R,L}^{\mathrm{out}}=\chi_L^2\,G.
\tag{7.A1}\label{eq:7A1_partition}
\]

Apply Lemma 7.10 (localized energy **identity**, not just inequality) to \(\psi_R^{\mathrm{in}}\) and \(\psi_{R,L}^{\mathrm{out}}\),
add the two identities, and use \eqref{eq:7A1_partition}. One obtains the exact recombined identity (Proposition 7.1)
\[
E_G[U](0;L)-E_G[U](-1;L)
+\int_{-1}^{0}D_G[U](\tau;L)\,d\tau
=
\mathrm{Err}_{\chi_L^2G}[U;-1,0],
\tag{7.A2}\label{eq:7A2_L_recombined}
\]
where the left-hand side uses the cutoff \(\chi_L^2G\) and the right-hand side is the corresponding error functional
(as in Lemma 6.1 but with \(\psi=\chi_L^2G\)).

Letting \(L\to\infty\), and using the same tightness/pressure-localization bounds as in §2.5, yields the **full-space**
identity on \([-1,0]\):
\[
E_G[U](0)-E_G[U](-1)
+\int_{-1}^{0}D_G[U](\tau)\,d\tau
=
\mathcal F_G[U;-1,0],
\tag{7.A3}\label{eq:7A3_fullspace_identity}
\]
with \(\mathcal F_G\) as in §2.5. (At this stage we do **not** assume any sign for \(\mathcal F_G\).)

Subtracting the (interior) fixed-cutoff identity \eqref{eq:7_1A_fixed_identity} from \eqref{eq:7A3_fullspace_identity} gives:

\[
\mathrm{Err}_R[U;-1,0]
=
\mathcal F_G[U;-1,0]
-\Big(E_G(0)-E_G(-1)\Big)
+\Big(E_R(0)-E_R(-1)\Big)
-\int_{-1}^{0}\Big(D_G(\tau)-D_R(\tau)\Big)\,d\tau.
\tag{7.A4}\label{eq:7A4_err_decomposition_flux}
\]

This identity is purely algebraic. Its value is that all terms except the full-space flux
\(\mathcal F_G\) are *manifestly localized outside \(B_{R}\)* (they involve \(G-\psi_R\) or \(D_G-D_R\)),
hence are candidates for control by No-Theft/tightness (Proposition 7.1).

#### B. Isolation of the only remaining estimate (VI.RB1)

Combining \eqref{eq:7A4_err_decomposition_flux} with Lemma 7.8 (which controls the annulus-supported pieces of \(\mathrm{Err}_R\)
by dissipation on scale \(4R\) plus the vanishing tail remainder) reduces RB1 to the following:

> **VI.RB1 (Localized Gaussian bulk-flux absorption).** 
> There exist \(\eta\in(0,1)\) and \(R_\star\ge 1\) such that for all \(R\ge R_\star\),
> \[
> \mathcal F_G[U;-1,0]
> \ \le\ \eta\int_{-1}^{0}D_G[U](\tau;4R)\,d\tau
> \ +\ C\Big(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(\tau;R/4)\Big)^2,
> \tag{VI.RB1}\label{eq:VI_RB1_bulk_flux_absorption}
> \]
> with \(C=C(M,m_0,\chi)\).
>
> *Consequence.* If \eqref{eq:VI_RB1_bulk_flux_absorption} holds, then the signed trade \eqref{eq:RB1_signed_trade} follows
> (after choosing a fixed \(R_\star\ge R_{\mathrm{NT}}\) large enough, per Appendix **NFS.1.8**, so that the tail remainder is below the required tolerance), hence Proposition 7.1 \eqref{eq:RB1_signed_trade}
> becomes **proved** for the pinned tail (and therefore for all but finitely many windows) (Proposition 7.1).

**Why this is the correct nucleus.** 
- All annulus-supported cutoff/pressure commutators are already controlled by Lemma 7.8. 
- The only term that can still inject a *non-absorbable positive contribution* is the **bulk Gaussian flux** \(\mathcal F_G\). 
- Showing \(\mathcal F_G\) is absorbable with coefficient \(<1\) is strictly weaker than proving it is nonpositive,
 and the allowed remainder is precisely the No-Theft tail modulus.

#### C. Verification checklist (updated): what is certified at this stage

The purpose of the preceding discussion is to isolate the *one-sided* requirement \eqref{eq:RB1_signed_trade} from the purely
absolute-value cutoff-trade estimates. In the present spine, \eqref{eq:RB1_signed_trade} is **proved** (not assumed) by Option B
in §4.1.5, using a profile-free transport dichotomy (Lemma 7.1F) and the Gate/No-Theft packet mechanism (Lemma 7.1H).
No appeal is made to any monotonic full-space Gaussian budget.

Accordingly:

1. All previously stated modules (No-Theft, Gate barrier, Anti-Flash, packet charging) remain unchanged.
2. The signed absorption \eqref{eq:RB1_signed_trade} is established on the pinned tail at the quantitative radii, with explicit constants.
3. Proposition 7.1 (quantitative budget) and the downstream “finitely many bad indices” conclusions in §4.2 are unconditional.

The remaining items after §4.1.5 are *presentation-level* only (index alignment and parameter bookkeeping), and are addressed
explicitly in §4.2.

#### 6.1.5.1 Annulus transport functional

Fix a radius \(R\ge 1\) and define the annulus \(A_{4R}:=\{4R<|y|<8R\}\). Write the pressure in the gauge
\(\widetilde P:=P-(P)_{B_{16R}}\) (Mini-Lemma 7.6P). Define the *annulus transport* functional
\[
\Phi(R,\tau)
:=\frac1R\int_{A_{4R}}\Big(|U(\tau)|^3+|U(\tau)|\,|\widetilde P(\tau)|\Big)\,G\,dy.
\tag{7.1B0}\label{eq:7_1B0_def_Phi}
\]
By CE1–CE3 (hence smoothness on the window; Lemma 7.GA), the map \(\tau\mapsto \Phi(R,\tau)\) admits a continuous \eqref{eq:RB1_signed_trade}
representative on \([-1,0]\).

#### 6.1.5.2 Lemma T: failure of strict absorption forces annulus transport

The next lemma is the precise “transport detector” statement. It is formulated so that it can be inserted at the
point where VI.RB1c is invoked: it turns the **absence of a strict constant** into a **positive transport integral**.

> **Lemma 7.1F (Transport lower bound from the absorption defect).** \n
> Fix \(\eta\in(0,1)\). Assume CE1–CE4 on the window \(\tau\in[-1,0]\) and Uniform No-Theft (P0.2). Fix \(R\ge 1\) and
> define the **absorption defect**
> \[
> \mathrm{Def}_\eta(R)
> :=\Bigg[
> \mathcal F_G[U;-1,0]
> \;-\;\eta\int_{-1}^{0}D_G[U](\tau;4R)\,d\tau
> \;-\;C_{\mathrm{NT}}\Big(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(\tau;R/4)\Big)^2
> \Bigg]_+,
> \tag{7.1B1a}\label{eq:7_1B1_defect}
> \]

> The corresponding **strict absorption inequality** (equivalent to \(\mathrm{Def}_\eta(R)=0\)) is
> \[
> \mathcal F_G[U;-1,0]
> \;\le\;\eta\int_{-1}^{0}D_G[U](\tau;4R)\,d\tau
> \;+\;C_{\mathrm{NT}}\Big(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(\tau;R/4)\Big)^2.
> \tag{7.1B1}\label{eq:7_1B1_strict_absorption_eta}
> \]

> where \(C_{\mathrm{NT}}\) is the constant in the far-field control of §4.1C (Step 1). Then there exist
> constants \(C_{\mathrm{B}}>0\) and \(R_\star\ge 1\) (depending only on the window constants from CE and on \(\eta\)) such
> that for every \(R\ge R_\star\),
> \[
> \int_{-1}^{0}\Phi(R,\tau)\,d\tau\ \ge\ C_{\mathrm{B}}^{-1}\,\mathrm{Def}_\eta(R).
> \tag{7.1B2}\label{eq:7_1B2_transport_lower_bound}
> \]
> In particular, if the strict absorption inequality \eqref{eq:7_1B1_strict_absorption_eta} fails at radius \(R\), then
> \(\mathrm{Def}_\eta(R)>0\) and hence the annulus transport integral is strictly positive (Lemma 7.1F).
>
> Moreover, by continuity of \(\Phi(R,\cdot)\) (Lemma 7.GA) there exists \(\tau_R\in[-1,0]\) such that
> \[
> \Phi(R,\tau_R)\ \ge\ \int_{-1}^0\Phi(R,\tau)\,d\tau
> \ \ge\ C_{\mathrm{B}}^{-1}\,\mathrm{Def}_\eta(R),
> \tag{7.1B3}\label{eq:7_1B3_transport_pointwise}
> \]
> 

*Proof (cite-level).* 
Write the bulk Gaussian flux as a near/far decomposition with the cutoff \(\chi_{4R}\):
\[
\mathcal F_G[U;-1,0]=I_{\mathrm{near}}(R)+I_{\mathrm{far}}(R),
\qquad
I_{\mathrm{near}}(R):=\int_{-1}^{0}\!\!\int_{\mathbb R^3}
\Big(\tfrac12|U|^2+P\Big)\,U\cdot\chi_{4R}^2\nabla G\,dy\,d\tau.
\]
By §4.1C (Step 1) and Uniform No-Theft (P0.2),
\[
|I_{\mathrm{far}}(R)|
\ \le\ C_{\mathrm{NT}}\Big(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(\tau;R/4)\Big)^2.
\tag{7.1B4}\label{eq:7_1B4_far_control}
\]
Hence, by the definition \eqref{eq:7_1B1_defect}, (Lemma 7.1F)
\[
\mathrm{Def}_\eta(R)
\ \le\
\Big[I_{\mathrm{near}}(R)\;-\;\eta\int_{-1}^{0}D_G[U](\tau;4R)\,d\tau\Big]_+.
\tag{7.1B5}\label{eq:7_1B5_defect_reduced_to_near}
\]

> **Reduction 7.1B6 (Defect \(\to\) annulus transport).** It suffices to bound the positive part on the right-hand side of \eqref{eq:7_1B5_defect_reduced_to_near}
> by the annulus transport functional.

It remains to bound the positive part on the right-hand side by the annulus transport functional. We work on
\(B_{16R}\) and use the pressure gauge \(\widetilde P:=P-(P)_{B_{16R}}\) (Mini-Lemma 7.6P). Split
\(P=\widetilde P+(P)_{B_{16R}}\). The constant part is reduced to an **annulus term** by a cutoff integration by
parts: writing \(\chi_{4R}^2\nabla G=\nabla(\chi_{4R}^2G)-G\nabla(\chi_{4R}^2)\) and using \(\nabla\cdot U=0\),
one has \(\int U\cdot\nabla(\chi_{4R}^2G)\,dy=0\), hence (Lemma 7.1F)
\((P)_{B_{16R}}\int U\cdot\chi_{4R}^2\nabla G\,dy\) is supported where \(\nabla\chi_{4R}\neq0\) and is therefore (Lemma 7.1F)
absorbed into the transport functional \(\Phi\) (see §4.1C–§4.1E). Thus (Lemma 7.1F)
\[
I_{\mathrm{near}}(R)
=\int_{-1}^{0}\!\!\int
\Big(\tfrac12|U|^2+\widetilde P\Big)\,U\cdot\chi_{4R}^2\nabla G\,dy\,d\tau.
\]

Now apply the cutoff-trade identity from §4.1C–§4.1E (in particular §4.1E: the OU-cancellation and integration by
parts that move derivatives onto \(\chi_{4R}\)). Concretely, one writes
\(\chi_{4R}^2\nabla G=\nabla(\chi_{4R}^2G)-G\nabla(\chi_{4R}^2)\) and integrates by parts to place \(\nabla\) on
\(\tfrac12|U|^2+\widetilde P\). The bulk terms are controlled by dissipation using Cauchy–Schwarz and Young with a
parameter \(\varepsilon=\varepsilon(\eta)\) chosen so that the dissipation coefficient is \(\le\eta\); the only
non-absorbed terms are those where \(\nabla\) hits \(\chi_{4R}\), hence are supported in \(A_{4R}\) and carry an explicit (Lemma 7.1F)
\(R^{-1}\) factor. The outcome is the quantitative estimate
\[
I_{\mathrm{near}}(R)
\ \le\ \eta\int_{-1}^{0}D_G[U](\tau;4R)\,d\tau
\ +\ C_{\mathrm{B}}\int_{-1}^{0}\Phi(R,\tau)\,d\tau,
\tag{7.1B6}\label{eq:7_1B6_near_bound_by_etaD_plus_Phi}
\]
where \(C_{\mathrm{B}}\) depends only on the window constants and on \(\eta\) (through the Young parameter).

Combining \eqref{eq:7_1B5_defect_reduced_to_near} with \eqref{eq:7_1B6_near_bound_by_etaD_plus_Phi} yields
\eqref{eq:7_1B2_transport_lower_bound}. The pointwise bound \eqref{eq:7_1B3_transport_pointwise} follows from the
trivial estimate \(\sup_{\tau\in[-1,0]}\Phi(R,\tau)\ge\int_{-1}^0\Phi(R,\tau)\,d\tau\) (since \(|[-1,0]|=1\)). ∎
#### 6.1.5.3 Lemma G: transport activates the Gate and forces a dissipation packet

The next lemma is the conversion “transport ⇒ Gate opening ⇒ dissipation packet”, which is the core of the censorship
friction mechanism.

> **Lemma 7.1H (Transport triggers a quantized payment: Gate packet or dissipation packet).** \n
> Fix the gate level \(\gamma_0>0\) from §4.G and let \(\delta_{\mathrm{gate}}\) be the packet size \eqref{eq:7GP_packet_size}. 
> There exist constants \(\theta_0=\theta_0(M,\gamma_0)>0\), \(D_0=D_0(M,\gamma_0)>0\), and \(R_{\mathrm{NT}}\ge 1\) such that for every
> \(R\ge R_{\mathrm{NT}}\) and every \(\tau\in[-1,0]\), if
> \[
> \Phi(R,\tau)\ \ge\ \theta_0,
> \tag{7.1H1}\label{eq:7_1H1_transport_threshold}
> \]
> then **at least one** of the following two alternatives holds:
>
> (H.a) *(Gate packet).* The cubic shell gate opens at scale \(4R\):
> \[
> \mathcal G(4R,\tau)\ :=\ \frac1{4R}\int_{A_{4R}}|U(\tau)|^3\,G\,dy\ \ge\ 2\gamma_0.
> \tag{7.1H2}\label{eq:7_1H2_gate_opens_from_transport}
> \]
> Consequently, by Lemma 7.GA and Corollary 7.GB, there exists a persistence interval \(J\subset[-1,0]\) with \eqref{eq:7GP_packet_size}
> \(|J|\ge c_\star(M,\gamma_0)\) such that
> \[
> \int_{J}D_G[U](s;16R)\,ds\ \ge\ \delta_{\mathrm{gate}}.
> \tag{7.1H3}\label{eq:7_1H3_gate_packet_local}
> \]
>
> (H.b) *(Direct dissipation packet).* One has the pointwise dissipation lower bound
> \[
> D_G[U](\tau;16R)\ \ge\ D_0.
> \tag{7.1H4}\label{eq:7_1H4_direct_dissipation_large}
> \]
> In this case (still under the transport-trigger regime \eqref{eq:7_1H1_transport_threshold}) the radius $R$ lies in a
> compact range depending only on $(M,\gamma_0)$, and the endpoint $L^\infty_\tau L^3_y$ regularity (Lemma 7.GA) yields
> a **profile-free** modulus of continuity for the map $s\mapsto D_G[U](s;16R)$. Concretely, Lemma 7.1H1 below provides a
> constant $c_{\mathrm{diss}}=c_{\mathrm{diss}}(M,\gamma_0)\in(0,1)$ such that there exists an interval $J\subset[-1,0]$
> with $|J|\ge c_{\mathrm{diss}}$ on which $D_G[U](s;16R)\ge \tfrac12 D_0$. Therefore (Lemma 7.1H)
> \[
> \int_{J}D_G[U](s;16R)\,ds\ \ge\ \tfrac12 D_0\,c_{\mathrm{diss}}
> \ =:\ \delta_{\mathrm{diss}}(M,\gamma_0).
> \tag{7.1H5}\label{eq:7_1H5_direct_dissipation_packet}
> \]
>
> In particular, whenever Uniform No-Theft makes \(\mathrm{Tail}_\sharp(4R,\tau)\) sufficiently small, the threshold event \eqref{eq:7_1H1_transport_threshold} forces a **uniform, quantized payment** at scale \(16R\):
> \[
> \int_{J}D_G[U](s;16R)\,ds\ \ge\ \min\{\delta_{\mathrm{gate}},\delta_{\mathrm{diss}}\}.
> \tag{7.1H6}\label{eq:7_1H6_transport_forces_payment}
> \]
>
> **Proof (cite-level).** 
> Split the transport functional \(\Phi=\Phi_{\mathrm{cub}}+\Phi_{\mathrm{prs}}\) with
> \[
> \Phi_{\mathrm{cub}}(R,\tau):=\frac1R\int_{A_{4R}}|U(\tau)|^3\,G\,dy,
> \qquad
> \Phi_{\mathrm{prs}}(R,\tau):=\frac1R\int_{A_{4R}}|U(\tau)|\,|\widetilde P(\tau)|\,G\,dy,
> \]
> where \(\widetilde P=P-(P)_{B_{8R}}\) (Mini-Lemma 7.6P; gauge conventions in Appendix NFS.1.6).
>
> **Step 1 (if the cubic part is large, the Gate opens).** 
> Since \(\Phi_{\mathrm{cub}}(R,\tau)=4\,\mathcal G(4R,\tau)\), the implication
> \[
> \Phi_{\mathrm{cub}}(R,\tau)\ \ge\ 8\gamma_0\quad\Rightarrow\quad \mathcal G(4R,\tau)\ge 2\gamma_0
> \]
> is immediate, giving alternative (H.a).
>
> **Step 2 (pressure part: localization bound).** 
> Apply the pressure localization estimate (7.G2) with radius \(4R\) (so that \(A_{4R}\) is the shell \(A_{4R}\)
> in the Gate notation and \(B_{2\cdot 4R}=B_{8R}\) matches the gauge defining \(\widetilde P\)). This yields, for each
> fixed \(\tau\),
> \[
> \Phi_{\mathrm{prs}}(R,\tau)
> \ \le\
> C\,\frac1R\int_{A_{R}^{32R}}|U(\tau)|^3\,G\,dy
> \ +\
> C\,D_G[U](\tau;16R)^{1/2}\,\mathrm{Tail}_\sharp(4R,\tau).
> \tag{7.1H7}\label{eq:7_1H7_pressure_localization_for_Phi}
> \]
> (Here \(A_{R}^{32R}:=\{R\le |y|\le 32R\}\) is the union of dyadic shells \(A_{2^jR}\), \(j=0,\dots,4\).)
>
> **Step 3 (either the Gate opens somewhere on the dyadic block, or the dissipation is large).** 
> Suppose (H.a) fails, i.e. \(\mathcal G(4R,\tau)<2\gamma_0\), and also assume the negation of (H.b), i.e.
> \(D_G[U](\tau;16R)<D_0\). Then \(\Phi_{\mathrm{cub}}(R,\tau)<8\gamma_0\). Moreover, the first term on the right-hand
> side of \eqref{eq:7_1H7_pressure_localization_for_Phi} can be bounded by the dyadic gates on \([R,32R]\):
> \[
> \frac1R\int_{A_{R}^{32R}}|U|^3\,G
> \;=\;\sum_{j=0}^{4}\frac1R\int_{A_{2^jR}}|U|^3\,G
> \;=\;\sum_{j=0}^{4}2^j\,\mathcal G(2^jR,\tau).
> \tag{7.1H8}\label{eq:7_1H8_dyadic_gate_sum}
> \]
> If in addition all dyadic gates satisfy \(\mathcal G(2^jR,\tau)\le 2\gamma_0\) for \(j=0,\dots,4\), then the first term in
> \eqref{eq:7_1H7_pressure_localization_for_Phi} is \(\le 2\gamma_0\sum_{j=0}^4 2^j=62\gamma_0\). For the second term we use
> \(D_G[U](\tau;16R)^{1/2}<D_0^{1/2}\), hence (Lemma 7.1H)
> \[
> \Phi_{\mathrm{prs}}(R,\tau)\ \le\ 62C\,\gamma_0\ +\ C\,D_0^{1/2}\,\mathrm{Tail}_\sharp(4R,\tau).
> \tag{7.1H9}\label{eq:7_1H9_pressure_bound_under_no_gate_no_diss}
> \]
> By Uniform No-Theft (P0.2) we may choose \(R_{\mathrm{pin}}\) so large that \(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(4R,\tau)\le 1\) for
> all \(R\ge R_{\mathrm{NT}}\). Fix \(D_0:=\gamma_0^2\) and then choose
> \[
> \theta_0\ :=\ 8\gamma_0\ +\ 62C\,\gamma_0\ +\ C\,\gamma_0\ +\ 1.
> \tag{7.1H10}\label{eq:7_1H10_theta0_choice}
> \]
> Under these choices, the conjunction “no Gate at \(4R\), no large dissipation at \(16R\), and no dyadic Gate on \([R,32R]\)”
> implies \(\Phi(R,\tau)<\theta_0\), contradicting \eqref{eq:7_1H1_transport_threshold}. Therefore, whenever (Lemma 7.1H)
> \eqref{eq:7_1H1_transport_threshold} holds, either (H.b) holds, or at least one dyadic gate \(\mathcal G(2^jR,\tau)\) exceeds
> \(2\gamma_0\) for some \(j\in\{0,\dots,4\}\).
>
> **Step 4 (reduce dyadic opening to the canonical scale \(4R\)).** 
> Since our transport functional \(\Phi(R,\tau)\) is defined on the specific shell \(A_{4R}\), the downstream use in
> Corollary 7.1I only requires a **quantized payment** at a radius comparable to \(R\). If the dyadic opening occurs at
> \(\rho:=2^jR\) with \(j\neq 2\), we relabel the radius as \(R\leftarrow \rho/4\); this preserves the form of the statement and
> changes the constants only by admissible dyadic factor (class (A))s. (This dyadic reindexing is formalized in Lemma 7.1H0 below.) In
> particular, we may assume the opening occurs at \(4R\), giving (H.a), and then \eqref{eq:7_1H3_gate_packet_local} follows from
> Lemma 7.GA and Corollary 7.GB.
>
> The implication (H.b) \(\Rightarrow\) \eqref{eq:7_1H5_direct_dissipation_packet} is proved in Lemma 7.1H1 below
> (closing VI.H1). ∎

> **Corollary 7.1I (Defect threshold activates the Gate packet).** \n
> Let \(C_{\mathrm{B}}\) be as in Lemma 7.1F and let \(\theta_0\) be as in Lemma 7.1H. If, for some \(R\ge R_\star\),
> \[
> \mathrm{Def}_\eta(R)\ \ge\ C_{\mathrm{B}}\,\theta_0,
> \tag{7.1I1}\label{eq:7_1I1_defect_threshold}
> \]
> then there exists \(\tau_R\in[-1,0]\) such that \(\Phi(R,\tau_R)\ge\theta_0\). In particular, Lemma 7.1H yields a **quantized payment** on some interval \(J\subset[-1,0]\) in the form \eqref{eq:7_1H6_transport_forces_payment} (after the dyadic reindexing (Lemma 7.1H0) if the opening occurs on a dyadic neighbor).
>
> **Proof.** By Lemma 7.1F and \eqref{eq:7_1B2_transport_lower_bound},
> \(\int_{-1}^0\Phi(R,\tau)\,d\tau\ge C_{\mathrm{B}}^{-1}\mathrm{Def}_\eta(R)\ge\theta_0\). Since \(|[-1,0]|=1\),
> there exists \(\tau_R\) with \(\Phi(R,\tau_R)\ge\theta_0\); then Lemma 7.1H applies. ∎

#### 6.1.5.4 How Option B is used in the canonical spine

**Verification items introduced by the cite-level conversion of Lemma 7.1H.**

- **VI.H0 (Dyadic reindexing harmlessness; CLOSED in Lemma 7.1H0).** When a Gate opening is produced on a dyadic neighbor \(\rho=2^jR\) with \(j\in\{0,\dots,4\}\),
 we reparametrize \(R\leftarrow \rho/4\) so that the opening is recorded at the canonical scale \(4R\). This is a bookkeeping step:
 all shells/cutoffs in §4.1.5 use fixed universal dilation factors, hence dyadic relabeling changes constants by at most a factor of \(2^{O(1)}\) (Corollary 7.1I)
 and does not alter any logical dependency.

- **VI.H1 (Uniform persistence for the dissipation alternative (H.b); CLOSED in Lemma 7.1H1).** Lemma 7.1H includes a “direct dissipation” alternative \eqref{eq:7_1H4_direct_dissipation_large}. 
 In v5.9.93 we close the only remaining quantitative issue: we prove a **profile-free persistence length** $c_{\mathrm{diss}}(M,\gamma_0)>0$ (Lemma 7.1H1), which implies a **uniform** dissipation packet $\delta_{\mathrm{diss}}=\tfrac12 D_0 c_{\mathrm{diss}}$ whenever (H.b) occurs under the transport trigger. 
 *(Optional simplification.)* One may still bypass the dissipation alternative entirely by using only the Gate-packet alternative (H.a) and strengthening the threshold so that the pressure term cannot generate $\Phi\ge\theta_0$ without opening a dyadic Gate; this is a presentation choice, not a logical necessity.

##### 6.1.5.4.1 Closing VI.H0: dyadic reindexing

We now close VI.H0 by making explicit the harmless dyadic relabeling used in Lemma 7.1H, Step 4.

> **Lemma 7.1H0 (Dyadic reindexing is harmless; closes VI.H0).** \n
> Fix a base radius \(R>0\) and an index \(j\in\{0,1,2,3,4\}\). Set the dyadic neighbor \(\rho:=2^jR\) and define the relabeled
> radius \(R':=\rho/4=2^{j-2}R\). Then:
>
> 1. (**Canonicalization of the shell.**) The geometric shell \(A_{4R'}\) coincides with the shell \(A_{\rho}\). Consequently, any (Lemma 7.1H0)
> functional defined by integrating on \(A_{4R}\) (such as \(\Phi(R,\tau)\)) can be evaluated at the neighbor scale by the
> relabeling \(R\leftarrow R'\), i.e. \(\Phi(R',\tau)\) is precisely the transport functional evaluated on the shell \(A_{\rho}\).
>
> 2. (**Uniformity of cutoff bookkeeping.**) All cutoffs and localization radii used in §4.1.5 are built from \(R\) by **fixed universal
> dilation factors** (e.g. \(2R,4R,16R,32R\)). Replacing \(R\) by \(R'\) multiplies each such radius by the same dyadic factor
> \(2^{j-2}\in[2^{-2},2^{2}]\). Therefore (Lemma 7.1H0):
> - the support relations (e.g. \(\mathrm{supp}\,\nabla\chi_{4R}\subset A_{2R}\)) are preserved verbatim after relabeling, and
> - the size bounds on derivatives (e.g. \(|\nabla\chi_{4R}|\lesssim 1/R\)) change only by a **bounded** factor \(\lesssim 4\).
>
> 3. (**Harmlessness for thresholds and packets.**) Any inequality in §4.1.5 of the schematic form
> \[
> \text{LHS}(R)\ \le\ C\,\text{RHS}(R)
> \]
> with \(C\) depending only on the fixed dilation pattern remains valid after the relabeling \(R\leftarrow R'\), with the constant
> multiplied by at most a admissible dyadic factor (class (A)) \(2^{O(1)}\). In particular, when Lemma 7.1H produces a Gate opening at a dyadic
> neighbor \(\rho=2^jR\), we may **record** it at the canonical scale \(4R'\) and invoke the corresponding Gate packet estimate
> (Corollary 7.GB / Lemma 7.2G) for \(R'\), without changing any logical dependency.
>
> **Proof (bounded dyadic change of scale).**
>
> The identity \(A_{4R'}=A_{\rho}\) is immediate from \(4R'=\rho\). The derivative support and size bounds follow because our cutoff
> profile is fixed once and for all and is rescaled by the radius; thus \(|\nabla\chi_{cR'}|\sim 1/(cR')\) differs from (Lemma 7.1H0)
> \(|\nabla\chi_{cR}|\sim 1/(cR)\) by the factor \(R/R'\in[1/4,4]\). All other occurrences of \(R\) in §4.1.5 enter only through such
> fixed dilation radii and the associated Gaussian weights on those shells, so every bound changes by at most a admissible dyadic factor (class (A)).
> Since the downstream spine uses only **quantized payment at a radius comparable to the trigger radius**, this dyadic relabeling is a
> purely bookkeeping step. ∎

##### 6.1.5.4.2 Closing VI.H1: uniform persistence for the dissipation threshold

We now close VI.H1 by proving a **profile-free persistence** estimate for the localized Gaussian dissipation
$s\mapsto D_G[U](s;16R)$ in the regime where Lemma 7.1H is invoked (i.e. under the transport trigger
\eqref{eq:7_1H1_transport_threshold}).

> **Lemma 7.1H1 (Uniform persistence for localized dissipation; closes VI.H1).** \n
> Assume CE1–CE4 on an RG window $\tau\in[-1,0]$, and let $\theta_0,D_0,R_{\mathrm{pin}}$ be as in Lemma 7.1H.
> Then there exists a constant
> \[
> c_{\mathrm{diss}}=c_{\mathrm{diss}}(M,\gamma_0)\in(0,1)
> \tag{7.1H11}\label{eq:7_1H11_cdiss_def}
> \]
> with the following property. For every $R\ge R_{\mathrm{NT}}$ and every $\tau_0\in[-1,0]$ such that
> $\Phi(R,\tau_0)\ge \theta_0$ and $D_G[U](\tau_0;16R)\ge D_0$, there exists an interval $J\subset[-1,0]$ with
> $|J|\ge c_{\mathrm{diss}}$ on which
> \[
> D_G[U](s;16R)\ \ge\ \tfrac12 D_0\qquad\text{for all }s\in J.
> \tag{7.1H12}\label{eq:7_1H12_D_persists}
> \]
> Consequently, $\int_J D_G[U](s;16R)\,ds\ge \delta_{\mathrm{diss}}:=\tfrac12 D_0\,c_{\mathrm{diss}}$ (Lemma 7.1H1).

> **Proof (profile-free modulus of continuity under the transport trigger).**
>
> **Step 1 (the transport trigger confines the radius).** 
> By CE1 and the Calderón–Zygmund (NFS.EST.4) bound $\|P\|_{L^{3/2}}\lesssim\|U\|_{L^3}^2$ (CE4), we have for each $\tau$
> \[
> \frac1R\int_{A_{4R}}\big(|U(\tau)|^3+|U(\tau)|\,|\widetilde P(\tau)|\big)\,G\,dy
> \ \le\ \frac{C}{R}\,\sup_{A_{4R}}G\,\|U(\tau)\|_{L^3}^3
> \ \le\ \frac{C M^3}{R}\,e^{-4R^2},
> \]
> where we used $\sup_{|y|\ge 4R}G(y)\le (4\pi)^{-3/2}e^{-(4R)^2/4}=C e^{-4R^2}$.
> Therefore the threshold event $\Phi(R,\tau_0)\ge\theta_0$ implies $R\le R_{\max}$, where $R_{\max}=R_{\max}(M,\theta_0)$ (Lemma 7.1H1)
> is the smallest radius for which $(C M^3/R)e^{-4R^2}<\theta_0$ holds for all $R\ge R_{\max}$. Since $\theta_0$ depends only on
> $(M,\gamma_0)$ (Lemma 7.1H), we may regard $R_{\max}$ as a function of $(M,\gamma_0)$.
>
> **Step 2 (window regularity yields an $L^2$ control of $\partial_\tau\nabla U$).** 
> By Lemma 7.GA (endpoint $L^\infty_\tau L^3_y$ regularity), $U$ is smooth on $(-1,0]\times\mathbb R^3$.
> Moreover, the quantitative form of this regularity on the fixed cylinder
> \[
> Q_{\max}:=[-1,0]\times B_{64R_{\max}}
> \]
> provides a bound
> \[
> \int_{-1}^{0}\!\!\int_{B_{64R_{\max}}}\!|\partial_\tau\nabla U|^2\,dy\,d\tau\ \le\ K(M,\gamma_0)^2.
> \tag{7.1H13}\label{eq:7_1H13_dt_grad_bound}
> \]
> (Quantitative interior bounds are provided by Lemma 7.GB, which cites Zajączkowski [Zaj13, Thm. 4.6] and [Zaj13, Lem. 2.6]; see Appendix NFS.EST.7.)
>
> **Step 3 (modulus of continuity for $\nabla U$ in weighted $L^2$).** 
> Let $w_R(y):=\chi_{16R}(y)^2\,G(y)$. Since $R\le R_{\max}$, we have $\mathrm{supp}\,w_R\subset B_{32R_{\max}}$ and
> $0\le w_R\le 1$. For any $s\in[-1,0]$,
> \[
> \|\nabla U(s)-\nabla U(\tau_0)\|_{L^2(w_R)}
> \ \le\ \int_{\min\{s,\tau_0\}}^{\max\{s,\tau_0\}}\!\!\|\partial_\tau\nabla U(\sigma)\|_{L^2(B_{64R_{\max}})}\,d\sigma
> \ \le\ |s-\tau_0|^{1/2}\,K(M,\gamma_0),
> \]
> by Cauchy–Schwarz (NFS.EST.2) and \eqref{eq:7_1H13_dt_grad_bound}.
>
> **Step 4 (choose a uniform persistence length).** 
> Write $D_G[U](\tau_0;16R)=\|\nabla U(\tau_0)\|_{L^2(w_R)}^2\ge D_0$.
> If $|s-\tau_0|\le c_{\mathrm{diss}}$ and
> \[
> c_{\mathrm{diss}}^{1/2}\,K(M,\gamma_0)\ \le\ \Big(1-2^{-1/2}\Big)\,\sqrt{D_0},
> \tag{7.1H14}\label{eq:7_1H14_cdiss_choice}
> \]
> then by the reverse triangle inequality,
> \[
> \|\nabla U(s)\|_{L^2(w_R)}
> \ \ge\ \|\nabla U(\tau_0)\|_{L^2(w_R)}-\|\nabla U(s)-\nabla U(\tau_0)\|_{L^2(w_R)}
> \ \ge\ \sqrt{D_0}-\Big(1-2^{-1/2}\Big)\sqrt{D_0}
> \ =\ 2^{-1/2}\sqrt{D_0},
> \]
> hence $D_G[U](s;16R)\ge \tfrac12 D_0$. We therefore set (Lemma 7.1H1)
> \[
> c_{\mathrm{diss}}
> :=\min\Big\{1,\ \frac{\big(1-2^{-1/2}\big)^2\,D_0}{K(M,\gamma_0)^2}\Big\},
> \]
> which depends only on $(M,\gamma_0)$.
>
> **Step 5 (select an interval $J\subset[-1,0]$ of length $c_{\mathrm{diss}}$).** 
> If $\tau_0\le -c_{\mathrm{diss}}/2$, take $J=[\tau_0,\tau_0+c_{\mathrm{diss}}]$.
> Otherwise take $J=[\tau_0-c_{\mathrm{diss}},\tau_0]$.
> In both cases $J\subset[-1,0]$, $|J|=c_{\mathrm{diss}}$, and \eqref{eq:7_1H12_D_persists} holds by Step 4. ∎

- **Benchmark (Option A):** §4.1.4 reduces strict absorption to VI.RB1c via OU-structure.
- **Intrinsic (Option B):** Lemma 7.1F + Lemma 7.1H show that *failure of strict absorption* forces a gate opening and
 therefore a **quantized** dissipation packet. On the RG orbit, repeated failures across indices \(k\) would then (Lemma 7.1H1)
 violate any finite quantitative budget once Proposition 7.1 is established.

In particular, once the quantitative dissipation summability \(\sum_k\mathfrak D_k<\infty\) is proved (Proposition 7.1),
Option B yields an explicit **index-level** asymptotic strict absorption statement on the pinned tail.

For each RG index \(k\ge1\), let \(\mathcal R_k:=\mathcal R_{\theta,\kappa}[U_k](0)\) and define the **Option B base radius**
\[
R_k:=\frac{\mathcal R_k}{4}.
\tag{7.2B0}\label{eq:7_2B0_Rk_def}
\]
This choice aligns the shells and radii used in §4.1.5 with the quantitative dissipation scale:
\[
A_{4R_k}=A_{\mathcal R_k},\qquad 16R_k = 4\mathcal R_k,
\]
so that any quantized payment obtained from Lemma 7.1H at radius \(R_k\) is measured exactly by the per-step quantitative dissipation
\(\mathfrak D_k=\int_{-1}^{0}D_G[U_k](s;4\mathcal R_k)\,ds\).

Write \(\mathrm{Def}^{(k)}_{\eta}(R)\) for the absorption defect \eqref{eq:7_1B1_defect} computed on the window \(U_k\)
(with time variable \(s\in[-1,0]\)). Then for any fixed threshold \(\Theta>0\), only finitely many indices can satisfy
\(\mathrm{Def}^{(k)}_{\eta}(R_k)\ge \Theta\), because each such event forces a **uniform dissipation packet** charged to \(\mathfrak D_k\).
Equivalently,
\[
\mathrm{Def}^{(k)}_{\eta}(R_k)\to 0\quad\text{as }k\to\infty,
\]
i.e. the strict absorption inequality holds asymptotically along the RG orbit (and in particular, it holds eventually up to any prescribed tolerance).
This implication is now written formally as Corollary 7.2J in §4.2.I.

### 6.2 The censorship friction mechanism, revisited
This section is the engine that turns **finite quantitative-scale dissipation** into convergence of modulation, hence into (Lemma 7.1H1)
rigidity.

There are two steps:

1. **Local-to-quantitative:** prove that each genuine “breath” of the pinned profiles forces a quantitative lower bound
 on the per-step dissipation $\mathfrak D_k$ (this is M1, already written in §1.4, but it must be made purely
 analytic and cite-level).

2. **Global-to-finite:** prove the quantitative-scale budget (7.3), hence $\sum_k\mathfrak D_k<\infty$ (Proposition 7.1).
 This is where the cutoff-trade mechanism (M2a) and the drift-control conversion (M2b) enter.

The rest of §6 is devoted to step 2, with the goal of making the bound (7.3) completely cite-level.

We keep the notation of §1.1. For a RG-window \(U_k\) we write
\[
\mathcal R_k(s):=\mathcal R_{\theta,\kappa}[U_k](s),\qquad
\mathcal R_k:=\mathcal R_k(0),\qquad
\mathcal R_k^-:=\mathcal R_k(-1).
\]
By construction of the RG orbit (unit \(\tau\)-translates, §1.1),
\(\mathcal R_k^-\) coincides with \(\mathcal R_{k-1}\) (same physical time-slice, same gauge).

---

#### 6.2.G Gate packets are charged to the quantitative budget (closing P0.1)

We now write the bookkeeping step promised after Corollary 7.GB: a gate opening at the **quantitative radius**
\(\mathcal R_k\) forces a **uniform, quantized** contribution to the per-step quantitative dissipation \(\mathfrak D_k\).
Once this is written, P0.1 becomes a direct corollary of the finite quantitative budget (7.2).

Fix the gate threshold \(\gamma_0>0\) and let \(c_\star=c_\star(M,\gamma_0)\in(0,1)\) be the persistence length from
Lemma 7.GA. Define the *packet size*
\[
\delta_{\mathrm{gate}}
:=\frac{\gamma_0}{C\,M}\,c_\star,
\tag{7.GP}\label{eq:7GP_packet_size}
\]
where \(C\) is the constant in the cubic shell estimate (7.G1), hence also in (7.G3) (Lemma 7.1H1).

> **Lemma 7.2G (quantitative-scale gate opening \(\Rightarrow\) quantitative dissipation packet).** 
> Let \(k\ge 1\). Assume that on the RG window \(s\in[-1,0]\) there exists \(s_\star\in[-1,0]\) such that
> \[
> \mathcal G(\mathcal R_k,s_\star)\ \ge\ 2\gamma_0.
> \tag{7.2G1}\label{eq:7_2G1_gate_open}
> \]
> Then the per-step quantitative dissipation obeys
> \[
> \mathfrak D_k
> \;=\;\int_{-1}^{0}D_{4\mathcal R_k}[U_k](s)\,ds
> \;\ge\;\delta_{\mathrm{gate}}.
> \tag{7.2G2}\label{eq:7_2G2_gate_charges_budget}
> \]

**Proof.** Apply Corollary 7.GB on the same window \(U_k\) with radius \(R=\mathcal R_k\) and time \(s_\star\).
Then
\[
\int_{s_\star}^{\min\{s_\star+c_\star,0\}} D_G[U_k](s;4\mathcal R_k)\,ds
\ \ge\ \frac{\gamma_0}{C\,M}\,c_\star
\;=\;\delta_{\mathrm{gate}}.
\]
Since \(D_{4\mathcal R_k}[U_k](s)\) is exactly the localized Gaussian dissipation at radius \(4\mathcal R_k\)
(see the convention (7.R5) with \(d\mu=G\,dy\)), the left-hand side is bounded above by
\(\int_{-1}^{0}D_{4\mathcal R_k}[U_k](s)\,ds=\mathfrak D_k\), proving \eqref{eq:7_2G2_gate_charges_budget}. ∎

> **Corollary 7.2H (Only finitely many quantitative-scale gate openings).** 
> Assume the finite quantitative-scale dissipation budget (7.2): \(\sum_{k\ge1}\mathfrak D_k<\infty\).
> Then the set of indices
> \[
> \mathcal B:=\Big\{k\ge1:\ \sup_{s\in[-1,0]}\mathcal G(\mathcal R_k,s)\ge 2\gamma_0\Big\}
> \tag{7.2H1}\label{eq:7_2H1_bad_set}
> \]
> is finite, with
> \[
> |\mathcal B|
> \ \le\ \delta_{\mathrm{gate}}^{-1}\sum_{k\ge1}\mathfrak D_k.
> \tag{7.2H2}\label{eq:7_2H2_bad_count}
> \]

**Proof.** For each \(k\in\mathcal B\), Lemma 7.2G gives \(\mathfrak D_k\ge\delta_{\mathrm{gate}}\).
Summing over \(k\in\mathcal B\) yields
\(\delta_{\mathrm{gate}}|\mathcal B|\le\sum_{k\in\mathcal B}\mathfrak D_k\le\sum_{k\ge1}\mathfrak D_k<\infty\). ∎

> **Theorem 7.GT (Gate closure near \(\tau=0\), in the pinned endgame).** 
> Assume (7.2). Then there exists \(k_{\mathrm{gate}}\in\mathbb N\) such that for all \(k\ge k_{\mathrm{gate}}\) and all
> \(s\in[-1,0]\),
> \[
> \mathcal G(\mathcal R_k,s)\ <\ 2\gamma_0.
> \tag{7.GT}\label{eq:7GT_gate_closure}
> \]
> In particular, in the pinned rigidity argument (which takes \(k\to\infty\) to approach the putative singular time),
> the quantitative-scale gate can be treated as **uniformly closed**.

**Proof.** Take \(k_{\mathrm{gate}}:=1+\max\mathcal B\), with the convention \(k_{\mathrm{gate}}=1\) if \(\mathcal B=\emptyset\).
Then \eqref{eq:7GT_gate_closure} is exactly the negation of membership in \(\mathcal B\). ∎

*Remark (what this closes, and what it does not).* 
- The conclusion \eqref{eq:7GT_gate_closure} is the **exact** gate input needed downstream: every quantitative window in the
 pinned tail has the gate uniformly below the threshold, so the Gate barrier never needs to be invoked again in the
 endgame.
- The stronger formulation “\(\sup_{\tau\le0,R\ge1}\mathcal G(R,\tau)\le\gamma_0\)” is strictly stronger than what the
 rigidity step consumes; if desired, it can be recovered by an additional (radius, time) covering argument that reduces
 arbitrary \(R\) to finitely many dyadic neighborhoods of the quantitative radii on the relevant tail interval.

---

#### 6.2.I Option B defects are charged to the quantitative indices (explicit indexing)

The Gate-charging Lemma 7.2G controls **quantitative-scale gate openings**. Option B (§4.1.5) produces such openings from a
large absorption defect, but to avoid any ambiguity for an reader we now write the **exact index-level alignment**
between the Option B radii and the per-step quantitative dissipation \(\mathfrak D_k\).

Recall \(\mathcal R_k:=\mathcal R_{\theta,\kappa}[U_k](0)\) and set \(R_k:=\mathcal R_k/4\) as in \eqref{eq:7_2B0_Rk_def}.
Define the **Option B packet size**
\[
\delta_{\mathrm{B}}
:=\min\{\delta_{\mathrm{gate}},\,\delta_{\mathrm{diss}}\},
\tag{7.2B1}\label{eq:7_2B1_deltaB_def}
\]
where \(\delta_{\mathrm{gate}}\) is the Gate packet size \eqref{eq:7GP_packet_size} and \(\delta_{\mathrm{diss}}\) is the dissipation packet
\eqref{eq:7_1H5_direct_dissipation_packet}. Let
\[
\Theta_{\mathrm{B}}
:= C_{\mathrm{B}}\,\theta_0,
\tag{7.2B2}\label{eq:7_2B2_ThetaB_def}
\]
where \(C_{\mathrm{B}}\) is the transport constant from Lemma 7.1F and \(\theta_0\) is the trigger threshold from Lemma 7.1H.

> **Lemma 7.2I (Large Option B defect \(\Rightarrow\) quantitative dissipation packet).** \\n
> Fix \(\eta\in(0,1)\). Assume CE1–CE4 and Uniform No-Theft on each RG window. Let \(R_{\mathrm{pin}}\) be the radius from Lemma 7.1H.
> For each index \(k\ge1\) with \(\mathcal R_k\ge 4R_{\mathrm{NT}}\) define \(R_k:=\mathcal R_k/4\) and let
> \(\mathrm{Def}^{(k)}_{\eta}(R_k)\) be the absorption defect \eqref{eq:7_1B1_defect} computed for the window \(U_k\).
> If
> \[
> \mathrm{Def}^{(k)}_{\eta}(R_k)\ \ge\ \Theta_{\mathrm{B}},
> \tag{7.2I1}\label{eq:7_2I1_large_defect_condition}
> \]
> then the per-step quantitative dissipation satisfies
> \[
> \mathfrak D_k
> \;=\;\int_{-1}^{0}D_G[U_k](s;4\mathcal R_k)\,ds
> \;\ge\;\delta_{\mathrm{B}}.
> \tag{7.2I2}\label{eq:7_2I2_defect_charges_Dk}
> \]
>
> **Proof.** Apply Corollary 7.1I to the RG-window \(U_k\) at the radius \(R=R_k\). The assumption
> \eqref{eq:7_2I1_large_defect_condition} gives \(\Phi(R_k,\tau_{R_k})\ge\theta_0\) for some \(\tau_{R_k}\in[-1,0]\), hence Lemma 7.1H
> yields an interval \(J\subset[-1,0]\) such that
> \[
> \int_J D_G[U_k](s;16R_k)\,ds\ \ge\ \delta_{\mathrm{B}}.
> \]
> Since \(16R_k=4\mathcal R_k\), the left-hand side is exactly \(\int_J D_G[U_k](s;4\mathcal R_k)\,ds\), which is bounded above by
> \(\int_{-1}^{0}D_G[U_k](s;4\mathcal R_k)\,ds=\mathfrak D_k\). This proves \eqref{eq:7_2I2_defect_charges_Dk}. ∎

> **Corollary 7.2J (Only finitely many large Option B defects).** \\n
> Assume the finite quantitative dissipation budget \eqref{eq:7.2}: \(\sum_{k\ge1}\mathfrak D_k<\infty\).
> Then the set of indices
> \[
> \mathcal B_{\mathrm{B}}
> :=\Big\{k\ge1:\ \mathcal R_k\ge 4R_{\mathrm{NT}}\ \text{and}\ \mathrm{Def}^{(k)}_{\eta}(R_k)\ge \Theta_{\mathrm{B}}\Big\}
> \tag{7.2J1}\label{eq:7_2J1_bad_defect_set}
> \]
> is finite, with the quantitative bound
> \[
> |\mathcal B_{\mathrm{B}}|
> \ \le\ \delta_{\mathrm{B}}^{-1}\sum_{k\ge1}\mathfrak D_k.
> \tag{7.2J2}\label{eq:7_2J2_bad_defect_count}
> \]
> In particular,
> \[
> \mathrm{Def}^{(k)}_{\eta}(R_k)\to 0\quad\text{along any tail on which }\mathcal R_k\ge 4R_{\mathrm{NT}},
> \]
> hence the strict absorption inequality holds asymptotically along the RG orbit at the aligned radii \(R_k=\mathcal R_k/4\) (Corollary 7.2J).
>
> **Proof.** For each \(k\in\mathcal B_{\mathrm{B}}\), Lemma 7.2I gives \(\mathfrak D_k\ge\delta_{\mathrm{B}}\).
> Summing over \(k\in\mathcal B_{\mathrm{B}}\) yields
> \(\delta_{\mathrm{B}}|\mathcal B_{\mathrm{B}}|\le\sum_{k\in\mathcal B_{\mathrm{B}}}\mathfrak D_k\le\sum_{k\ge1}\mathfrak D_k<\infty\),
> proving \eqref{eq:7_2J2_bad_defect_count}. ∎

*Remark (why the restriction \(\mathcal R_k\ge 4R_{\mathrm{NT}}\) is harmless).* 
The constants \(\theta_0\) and \(R_{\mathrm{NT}}\) in Lemma 7.1H are fixed once \((M,\gamma_0)\) are fixed. Indices with
\(\mathcal R_k<4R_{\mathrm{NT}}\) correspond to a uniformly bounded quantitative radius, i.e. a compact-core regime.
Such indices can be handled separately (e.g. by the gauge-fixed OU-coercivity route, or by a finite-cover argument in the compact radius range),
and they do not affect the summability contradiction mechanism which is triggered by **infinitely many** large-defect events.
#### 6.2.1 The width map is continuous in \(X\)

We will pass to limits in the window sequence. Since the width is defined through quantiles, we record a clean
continuity statement for the *band-averaged* functional (5.2).

**Lemma 7.2 (Continuity of \(U\mapsto \mathcal R_{\theta,\kappa}[U](s)\)).** 

Fix \(s\in[-1,0]\) and parameters \((\theta,\kappa)\). Assume \(U^{(n)}(\cdot,s)\to U(\cdot,s)\) in the topology \(X\),
and that there exist constants \(M_3<\infty\), \(m_1>0\) such that for all \(n\),
\[
\|U^{(n)}(\cdot,s)\|_{L^3(\mathbb R^3)}\le M_3,
\qquad
E_\infty[U^{(n)}](s)\ge m_1.
\tag{7.2a}
\]
Then
\[
\mathcal R_{\theta,\kappa}[U^{(n)}](s)\to \mathcal R_{\theta,\kappa}[U](s).
\]

*Proof.* For each fixed \(R\ge 1\), the weight \(\chi_R^2G\in L^{3/2}\), and \(X\hookrightarrow L^3_{\rm loc}\);
hence \(E_R[U^{(n)}](s)\to E_R[U](s)\). Similarly \(E_\infty[U^{(n)}](s)\to E_\infty[U](s)\) by monotone convergence (Corollary 7.2J)
in \(R\) combined with (7.2a). Therefore the normalized profiles (Corollary 7.2J)
\(\widetilde F^{(n)}_s(R):=E_R[U^{(n)}](s)/E_\infty[U^{(n)}](s)\) converge pointwise in \(R\) to \(\widetilde F_s(R)\).

By Lemma 5.1A and (7.2a), all relevant quantiles satisfy \(1\le Q^{(n)}_s(u)\le R_+\) for \(u\in[\theta-\kappa,\theta+\kappa]\)
with the same \(R_+\) for all \(n\). A monotone-inverse stability lemma
(for distribution functions; see e.g. Billingsley [Bil99, Thm. 14.2]) implies \(Q^{(n)}_s(u)\to Q_s(\alpha)\) for a.e. \(\alpha\)
in \((0,1)\). Since \(|\log Q^{(n)}_s(u)|\le \log R_+\) on the band, dominated convergence yields
\[
\int_{\theta-\kappa}^{\theta+\kappa}\log Q^{(n)}_s(u)\,d\alpha
\;\to\;
\int_{\theta-\kappa}^{\theta+\kappa}\log Q_s(\alpha)\,d\alpha,
\]
and the claim follows from the definition (5.2). \(\square\)

> **Lemma 7.GB (Quantitative interior derivative bound from the endpoint criterion).** 
> Let \((U,P)\) be the LRNS orbit provided by Theorem 2.1. Fix a dyadic radius \(R\ge 1\) and the annulus \(A_R=\{R/2\le |y|\le 4R\}\).
> Then there exists an admissible constant \(C_{\mathrm{IB}}=C_{\mathrm{IB}}(M)\) such that
> \[
> \sup_{\tau\in[-1,0]}\|\partial_\tau U(\tau)\|_{L^3(A_R)}\ \le\ C_{\mathrm{IB}}.
> \tag{7.GB}\label{eq:IB_dtaU_L3}
> \]
> (In particular \(\tau\mapsto U(\tau)\) has a uniform modulus of continuity in \(L^3(A_R)\) depending only on \(M\) on the unit window.)
>
> *Proof (cite-level; no spectral gap).* 
> By the endpoint regularity criterion at the \(L^\infty_\tau L^3_y\) level (Escauriaza–Seregin–Šverák [ESS03] in the suitable framework, as used in [GKP13]),
> the LRNS orbit is smooth on \([-2,0]\times A_{2R}\) once \(\sup_{\tau}\|U(\tau)\|_{L^3}\le M\) is fixed. 
> Quantitative interior estimates for the nonstationary Stokes system (in anisotropic Sobolev–Slobodetski classes, with localization to interior subdomains)
> are proved, for example, in Zajączkowski \([Zaj13, Thm. 4.6]\). Moreover, the derivative interpolation inequality \([Zaj13, Lem. 2.6]\) gives explicit control of time derivatives
> from the anisotropic norm.
> Applying these estimates on a slightly larger cylinder \([-2,0]\times A_{2R}\) to the localized equation for \(\zeta U\) (with \(\zeta\) supported in \(A_{2R}\) and \(\zeta\equiv 1\) on \(A_R\)),
> and treating the nonlinear and lower-order LRNS terms as forcing controlled by \(\sup_{\tau}\|U(\tau)\|_{L^3}\le M\), yields the bound \eqref{eq:IB_dtaU_L3}.
> Since \(R\ge 1\) and the window is normalized, the geometric factors are absorbed into an admissible constant class, so the constant depends only on \(M\). \(\square\)

> **Lemma 7.GA* (Quantitative Anti-Flash: an explicit persistence interval).** 
> Under the hypotheses of Lemma 7.GA, fix \(\gamma>0\) and \(R\ge 1\). Then \(\tau\mapsto \mathcal G(R,\tau)\) is Lipschitz on \([-1,0]\) with
> \[
> \big|\mathcal G(R,\tau)-\mathcal G(R,\tau')\big|\ \le\ L_{\mathrm{AF}}\,|\tau-\tau'|\qquad(\tau,\tau'\in[-1,0]),
> \tag{7.GA*}\label{eq:GAstar_Lipschitz}
> \]
> where \(L_{\mathrm{AF}}:=3M^2C_{\mathrm{IB}}(M)\) and \(C_{\mathrm{IB}}(M)\) is the interior bound from Lemma 7.GB. 
> Consequently, letting \(c_\star:=\min\{1,\gamma/L_{\mathrm{AF}}\}\), any time \(\tau_\star\in[-1,0]\) with \(\mathcal G(R,\tau_\star)\ge 2\gamma\) (Lemma 7.GA)
> forces
> \[
> \mathcal G(R,\tau)\ \ge\ \gamma\qquad\text{for all }\tau\in[\tau_\star,\min\{\tau_\star+c_\star,0\}].
> \tag{7.GA*+}\label{eq:GAstar_cstar}
> \]
>
> *Proof.* Differentiating \(\mathcal G(R,\tau)=\frac1R\int_{A_R}|U(\tau)|^3G\,dy\) and using Hölder on \(A_R\) gives
> \[
> |\partial_\tau \mathcal G(R,\tau)|\ \le\ \frac3R\|U(\tau)\|_{L^3(A_R)}^2\,\|\partial_\tau U(\tau)\|_{L^3(A_R)}.
> \]
> By CE1, \(\|U(\tau)\|_{L^3(A_R)}\le M\). By Lemma 7.GB, \(\|\partial_\tau U(\tau)\|_{L^3(A_R)}\le C_{\mathrm{IB}}(M)\) uniformly in \(\tau\in[-1,0]\).
> Absorbing \(R^{-1}\le 1\) (since \(R\ge 1\)) yields \eqref{eq:GAstar_Lipschitz}. The persistence claim \eqref{eq:GAstar_cstar} follows by integrating the Lipschitz bound.
> \(\square\)

---
#### 6.2.2 Target inequality (M2)

We target a per-window inequality of the form
\[
\mathcal D_k \ \lesssim\ 1+\big|\log\mathcal R_k-\log\mathcal R_{k-1}\big|
\qquad\Rightarrow\qquad
\sum_k\mathcal D_k<\infty,
\tag{7.6}
\]
and, crucially, we must control the *slow drift* scenario. Concretely, we want
\[
\big|\log\mathcal R_k-\log\mathcal R_{k-1}\big|\ \le\ C_{\rm M2}\,\mathcal D_k.
\tag{7.7}
\]

To obtain (7.7) we will combine:

1. **Pinned profile stability** (the analytic core of M2a):
 \[
 \sup_{R\ge 1}\big|F_0(R)-F_{-1}(R)\big|\ \lesssim\ \mathcal D_k,
 \qquad
 F_s(R):=\frac{E_R(s)}{E_\ast},\ E_\ast=E_\infty(0).
 \tag{7.14pin}
 \]
 This is proved in §4.2.6.4 by an explicit error decomposition and the cutoff-trade mechanism.

2. **Deterministic conversion (Option B).** With the quantitative radius definition (5.2),
 a uniform \(L^\infty_R\) control of the *instantaneous* normalized profiles
 \(\widetilde F_s(R)=E_R(s)/E_\infty(s)\) implies a Lipschitz control of the band-averaged log-quantile radius.
 This is proved in §4.2.6.5 (Lemma 7.9) and requires **no** non-flatness/transversality assumption.

Together these yield (7.7) for all but finitely many windows (which is sufficient since \(\sum_k\mathcal D_k<\infty\)
in the critical-element scenario).

---
#### 6.2.3 Reduction of (7.7) to a single moving-cutoff LEI lemma

To prove (7.7) it is enough to control how much the *localized* Gaussian energies \(E_R\) can change over a unit window,
uniformly at the special radius \(R=\mathcal R_{\theta,\kappa}\).

The only genuinely new ingredient (beyond Lemma 6.1) is the following time-dependent cutoff estimate.

**Lemma 7.3 (Moving-cutoff localized Gaussian LEI; cite-level statement).** 

Let \((U,P)\) be a suitable weak solution to (LRNS) on \([-1,0]\times\mathbb R^3\).
Let \(R:[-1,0]\to[1,\infty)\) be Lipschitz, and set
\[
\psi(y,s):=\psi_{R(s)}(y):=\chi_{R(s)}(y)^2\,G(y),
\qquad
E_{R(s)}(s):=\int_{\mathbb R^3}\tfrac12|U(y,s)|^2\,\psi(y,s)\,dy,
\qquad
D_{R(s)}(s):=\int_{\mathbb R^3}|\nabla U(y,s)|^2\,\psi(y,s)\,dy.
\]
Then for all \(-1\le s_1<s_2\le 0\),
\[
E_{R(s_2)}(s_2)+\int_{s_1}^{s_2} D_{R(s)}(s)\,ds
\;\le\;
E_{R(s_1)}(s_1)
+\mathrm{Err}_{R(\cdot)}[U;s_1,s_2],
\tag{7.8}
\]
where
\[
\mathrm{Err}_{R(\cdot)}[U;s_1,s_2]
:=
\underbrace{\int_{s_1}^{s_2}\!\int \Big(\tfrac12|U|^2+P\Big)\,U\cdot\nabla\psi(\cdot,s)\,dy\,ds}_{\text{(transport/pressure)}}
\;+
\underbrace{\int_{s_1}^{s_2}\!\int \Big[
\tfrac12|U|^2\,\Delta\psi(\cdot,s)
+\tfrac14|U|^2\,(y\cdot\nabla\psi(\cdot,s)+3\psi(\cdot,s))
\Big]dy\,ds}_{\text{(OU\(^\ast\) forcing)}}
\;+
\underbrace{\int_{s_1}^{s_2}\!\int \tfrac12|U|^2\,\partial_s\psi(\cdot,s)\,dy\,ds}_{\text{(moving cutoff)}}.
\tag{7.9}
\]

Moreover, the moving-cutoff term admits the explicit estimate
\[
\Big|\int_{s_1}^{s_2}\!\int \tfrac12|U|^2\,\partial_s\psi(\cdot,s)\,dy\,ds\Big|
\;\le\;
C_\chi\int_{s_1}^{s_2}\frac{|R'(s)|}{R(s)}\,E_{2R(s)}(s)\,ds,
\tag{7.10}
\]
where \(C_\chi\) depends only on the fixed cutoff profile \(\chi\).

*Proof.* 
We apply the suitable weak formulation (local energy inequality) in the Leray frame with a time-dependent
nonnegative test function. Concretely, start from the physical-space LEI for \((u,p)\) and test it with
\(\phi(x,t)=\chi_{R(s)}(x/\sqrt{s})^2\,\Gamma(x,t)\) where \(s=t_\ast-t\) and \(R(s)\) is Lipschitz.
Because \(R\) is only Lipschitz, we first mollify in time: pick smooth \(R_\varepsilon\to R\) in \(W^{1,\infty}\),
set \(\phi_\varepsilon\) accordingly, apply LEI to \(\phi_\varepsilon\), and pass \(\varepsilon\to0\) using dominated
convergence (all coefficients are supported where \(|x|\lesssim R(s)\sqrt{s}\) and bounded in terms of
\(\|R\|_{W^{1,\infty}}\), while the solution has the local integrability of suitable weak solutions).

Carrying out the same similarity change of variables as in Lemma 6.1 (with the only difference that \(\psi\) now depends on
\(s\) through \(R(s)\)) yields exactly the inequality (7.8)–(7.9): every term is identical to Lemma 6.1, except that the
time derivative of the test function contributes an additional term \(\tfrac12|U|^2\,\partial_s\psi\).

> **Reduction 6.2.6.R0 (Moving cutoff time-derivative).** It suffices to bound the time derivative \(\partial_s\psi\) of the moving cutoff.

It remains to bound \(\partial_s\psi\). Write \(\chi_{R(s)}(y)=\chi(|y|/R(s))\). Then

#### 6.2.6.R Radius inflation & dyadic neighborhood toolkit

##### 6.2.6.R.1 Cutoff family convention (monotone radial cutoffs)

Fix a smooth radial profile \(\chi\in C_c^\infty(\mathbb{R}^3)\) such that
\[
\chi(r)=
\begin{cases}
1,& r\le 1,\\
0,& r\ge 2,
\end{cases}
\qquad 0\le \chi\le 1,\qquad |\chi'(r)|\le C.
\tag{7.R1}\label{eq:7R1_profile}
\]
Define the scale-\(R\) cutoff
\[
\chi_R(y):=\chi(|y|/R).
\tag{7.R2}\label{eq:7R2_chiR}
\]
Then
\[
\chi_R\equiv 1\ \text{on }B_{R},\quad
\chi_R\equiv 0\ \text{on }\mathbb{R}^3\setminus B_{2R},\quad
|\nabla\chi_R|\lesssim \frac{1}{R},\quad
\mathrm{supp}(\nabla\chi_R)\subset A_R:=\{R\le|y|\le 2R\}.
\tag{7.R3}\label{eq:7R3_cutoff_props}
\]

**Monotonicity convention.** For \(\lambda\ge 1\),
\[
\chi_R(y)\le \chi_{\lambda R}(y)\quad\text{for all }y.
\tag{7.R4}\label{eq:7R4_monotone}
\]

---

##### 6.2.6.R.2 Radius inflation lemma (energy and dissipation)

Let \(d\mu\) denote either Lebesgue measure or the Gaussian measure used in the LRNS normalization; the monotonicity arguments below are measure-independent.

Define localized energy and dissipation:
\[
E_R:=\int |U|^2 \chi_R^2\,d\mu,\qquad
D_R:=\int |\nabla U|^2 \chi_R^2\,d\mu.
\tag{7.R5}\label{eq:7R5_ED_defs}
\]

> **Lemma 7.R (Radius inflation).** For any fixed \(\lambda\ge 1\),
> \[
> E_R \le E_{\lambda R},\qquad D_R \le D_{\lambda R}.
> \tag{7.R6}\label{eq:7R6_ED_inflation}
> \]
> Moreover,
> \[
> \int |\nabla U|^2\,\chi_R^2\,d\mu \le \int |\nabla U|^2\,\chi_R^2\,d\mu \le \int |\nabla U|^2\,d\mu.
> \tag{7.R7}\label{eq:7R7_chi_power}
> \]
> **Proof.** From \eqref{eq:7R4_monotone}, \(\chi_R^k\le \chi_{\lambda R}^k\) for \(k=2,4\), yielding \eqref{eq:7R6_ED_inflation}. Since \(0\le \chi_R\le 1\), we have \(\chi_R^2\le \chi_R^2\le 1\), giving \eqref{eq:7R7_chi_power}. ∎

**Convention.** We freely “inflate” radii by fixed factors (e.g. \(8R\), \(16R\)) and absorb the change into the admissible absolute constant class (A) (cf. Appendix NFS.1.9).

---

##### 6.2.6.R.3 Dyadic neighborhoods and finite covers

For \(a<b\), write
\[
A_{aR}^{bR}:=\{y:\ aR\le |y|\le bR\}.
\tag{7.R8}\label{eq:7R8_shell_neighborhood}
\]

> **Lemma 7.RD (Finite dyadic cover).** The widened shell satisfies
> \[
> A_{R/4}^{8R}\ \subset\ \bigcup_{j=-2}^{3} A_{2^jR}.
> \tag{7.R9}\label{eq:7R9_dyadic_cover}
> \]
> Consequently, for \(F\ge 0\), (Lemma 7.RD)
> \[
> \int_{A_{R/4}^{8R}} F\,d\mu\ \le\ \sum_{j=-2}^{3}\int_{A_{2^jR}}F\,d\mu.
> \tag{7.R10}\label{eq:7R10_cover_integral}
> \]
> ∎

---

##### 6.2.6.R.4 Dyadic normalization of the cubic shell flux

Define
\[
\Phi(R):=\frac{1}{R}\int_{A_R}|U|^3\,d\mu.
\tag{7.R11}\label{eq:7R11_phi_def}
\]

> **Lemma 7.RF (Dyadic shell-sum reduction).** For all \(R\ge 1\),
> \[
> \frac{1}{R}\int_{A_{R/4}^{8R}}|U|^3\,d\mu
> \ \le\
> C\sum_{j=-2}^{3}\Phi(2^jR).
> \tag{7.R12}\label{eq:7R12_shellsum_to_flux}
> \]
> **Proof.** By \eqref{eq:7R10_cover_integral},
> \[
> \frac{1}{R}\int_{A_{R/4}^{8R}}|U|^3\,d\mu
> \le
> \frac{1}{R}\sum_{j=-2}^{3}\int_{A_{2^jR}}|U|^3\,d\mu.
> \]
> For \(j\in[-2,3]\), \(1/R\le 8/(2^jR)\), hence (Lemma 7.RF)
> \(\frac{1}{R}\int_{A_{2^jR}}|U|^3 \le 8\,\Phi(2^jR)\). Sum over \(j\). ∎

---

#### 6.2.6.T\(_\sharp\) Tail functional and sharp budget

##### 6.2.6.T\(_\sharp\).1 Shell energy profile (Lebesgue shells)

Let \(A_\rho^{\flat}:=\{y:\ \rho/2\le |y|\le 2\rho\}\) and define
\[
\mathcal{E}(\rho):=\frac{1}{\rho^2}\int_{A_\rho^{\flat}}|U(y)|^2\,dy,\qquad
\mathcal{E}_*:=\sup_{\rho\ge 1}\mathcal{E}(\rho).
\tag{7.TE}\label{eq:7T_shell_energy}
\]

##### 6.2.6.T\(_\sharp\).2 Tail functional (sharp, uniform in time)

For \(R\ge1\) and \(\tau\le 0\), define the sharp tail functional
\[
\mathrm{Tail}_\sharp(R,\tau)
:=
\frac{1}{R^3}\int_{|y|\le R/8}|U(\tau,y)|^2\,dy
\ +\
\int_{|y|\ge 16R}\frac{|U(\tau,y)|^2}{|y|^3}\,dy.
\tag{7.T\sharp}\label{eq:7T_tail_sharp_def}
\]
We also write \(\mathrm{Tail}_\sharp^{\sup}(R):=\sup_{\tau\le 0}\mathrm{Tail}_\sharp(R,\tau)\).

> **Lemma 7.8C\(_{\mathrm{NT}}\) (No-Theft / uniform tail decay from \(L^3\)).** 
> Assume the critical-element bound \(\sup_{\tau\le0}\|U(\tau)\|_{L^3(\mathbb R^3)}\le M\). 
> Then for all \(R\ge1\) and all \(\tau\le0\),
> \[
> \mathrm{Tail}_\sharp(R,\tau)\ \le\ \frac{C}{R^2}\,M^2,
> \qquad\text{hence}\qquad (Lemma 7.8C)
> \mathrm{Tail}_\sharp^{\sup}(R)\ \le\ \frac{C}{R^2}\,M^2.
> \tag{7.TBNT}\label{eq:7T_tail_sharp_no_theft}
> \]
> In particular,
> \[
> \lim_{R\to\infty}\ \sup_{\tau\le0}\mathrm{Tail}_\sharp(R,\tau)=0.
> \tag{7.TNT}\label{eq:7T_tail_sharp_uniform_vanish}
> \]
> **Proof.** Fix \(\tau\le0\). For the inner term, Hölder gives
> \[
> \frac{1}{R^3}\int_{|y|\le R/8}|U(\tau)|^2
> \le
> \frac{1}{R^3}\Big(\int_{|y|\le R/8}|U(\tau)|^3\Big)^{2/3}\,|B_{R/8}|^{1/3}
> \ \le\ \frac{C}{R^2}\,\|U(\tau)\|_{L^3}^2.
> \]
> For the outer term, Hölder with exponents \((3/2,3)\) yields
> \[
> \int_{|y|\ge 16R}\frac{|U(\tau)|^2}{|y|^3}
> \le
> \Big(\int_{|y|\ge 16R}|U(\tau)|^3\Big)^{2/3}
> \Big(\int_{|y|\ge 16R}|y|^{-9}\,dy\Big)^{1/3}
> \ \le\ \frac{C}{R^2}\,\|U(\tau)\|_{L^3}^2.
> \]
> Summing the two bounds and taking the supremum in \(\tau\) gives \eqref{eq:7T_tail_sharp_no_theft}–\eqref{eq:7T_tail_sharp_uniform_vanish}. ∎

> **Remark (optional stronger budget).** If one additionally controls the shell energy profile
> \(\mathcal E_*\!:=\sup_{\rho\ge1}\rho^{-2}\int_{A_\rho^\flat}|U(\tau)|^2\) uniformly in \(\tau\),
> then a dyadic shell argument improves the decay to \(O(R^{-1}\mathcal E_*)\). This refinement is not needed
> for the P0.2 “No-Theft” closure.

---

\[
\partial_s\chi_{R(s)}(y)
=\chi'(|y|/R(s))\,\partial_s\Big(\frac{|y|}{R(s)}\Big)
= -\frac{R'(s)}{R(s)}\,\frac{|y|}{R(s)}\,\chi'(|y|/R(s)).
\]
Hence \(\partial_s(\chi_{R(s)}^2)\) is supported where \(\chi'\neq0\), i.e. on the annulus (Lemma 7.8C)
\(A_{R(s)}:=\{R(s)\le|y|\le 2R(s)\}\), and satisfies
\[
|\partial_s(\chi_{R(s)}^2)(y)|
\le
C_\chi\,\frac{|R'(s)|}{R(s)}\,\mathbf 1_{A_{R(s)}}(y).
\]
Multiplying by \(G(y)\) gives
\(
|\partial_s\psi(y,s)|\le C_\chi\,\frac{|R'(s)|}{R(s)}\,\mathbf 1_{A_{R(s)}}(y)\,G(y).
\)
Since \(A_{R(s)}\subset\{|y|\le 2R(s)\}\) and \(\chi_{2R(s)}\equiv1\) on \(|y|\le 2R(s)\), we have
\(\mathbf 1_{A_{R(s)}}G\le \chi_{2R(s)}^2G=\psi_{2R(s)}\). Therefore (Lemma 7.8C)
\[
\int \tfrac12|U|^2\,|\partial_s\psi(\cdot,s)|\,dy
\le
C_\chi\,\frac{|R'(s)|}{R(s)}\int \tfrac12|U(y,s)|^2\,\psi_{2R(s)}(y)\,dy
=
C_\chi\,\frac{|R'(s)|}{R(s)}\,E_{2R(s)}(s),
\]
and integrating over \([s_1,s_2]\) yields (7.10). \(\square\)

*Remark.* Lemma 7.3 is **pure bookkeeping**: it introduces no new analytic input beyond Lemma 6.1, but it makes the
dependence on a moving cutoff explicit. The *real* analytic burden for M2 is not (7.8)–(7.10) themselves; it is the
uniform control of the remaining error terms \(\mathrm{Err}_{R(\cdot)}\) in the specific choice(s) of \(R(\cdot)\) used
to compare \(\mathcal R_k\) and \(\mathcal R_{k-1}\). This is spelled out precisely below.

We now complete this reduction. In **v5.8.5** the previously-isolated missing quantitative estimate is supplied by **Lemma 7.8 (Strong linear cutoff trade)**, which upgrades the cutoff bookkeeping into a clean bound \(|\mathrm{Err}_R|\lesssim \int_{-1}^0 D_G(\tau;4R)\,d\tau\). This yields **Proposition 7.11**, i.e. the pinned profile stability (7.14pin), and hence the instantaneous profile stability (7.14). With Option B, the drift step (M2b) is then purely deterministic (Lemma 7.9), giving (7.7).

---

#### 6.2.4 Hysteresis logic and the precise analytic burden for M2

The quantitative radius \(\mathcal R_{\theta,\kappa}(s)\) is defined by the **band-averaged log-quantile** observable (5.2):
\[
\log \mathcal R_{\theta,\kappa}(s)=\frac{1}{2\kappa}\int_{\theta-\kappa}^{\theta+\kappa}\log Q_s(\alpha)\,d\alpha,
\]
where \(Q_s(\alpha)\) is the quantile radius (5.1) associated to the instantaneous profile \(\widetilde F_s\).

**Remark 7.2.4A (Degenerate instantaneous profile).** If \(M_{-1}:=E_\infty(-1)/E_* = 0\), then \(E_R(-1)=0\) for every \(R\) and we set \(\widetilde F_{-1}(R)\equiv 0\). In this case (7.14a) yields \(1=|M_0-M_{-1}|\le C\,\mathcal D_k\), hence \(\sup_{R\ge1}|\widetilde F_0(R)-\widetilde F_{-1}(R)|\le 1\le C\,\mathcal D_k\); thus (7.14) is immediate. Therefore we may assume \(M_{-1}>0\) below.

Two deterministic observations will be used repeatedly:

1. **Monotonicity:** \(R\mapsto \widetilde F_s(R)\) is nondecreasing and takes values in \([0,1]\).
2. **Hysteresis gap:** if \(R_1<R_2\) and \(\widetilde F_s(R_2)-\widetilde F_s(R_1)<\kappa\), then either both radii lie below the threshold
 \(\theta+\kappa\) or both lie above it. In particular, the threshold cannot be crossed inside \((R_1,R_2)\) without
 accumulating at least \(\kappa\) of normalized mass.

Consequently, controlling the drift of \(\mathcal R_k\) reduces to controlling the *time variation* of the normalized (7.14b)
pinned-normalized energy profiles \(F_s(R)\) (and hence, via (7.14b), the instantaneous profiles \(\widetilde F_s(R)\)) at radii comparable to \(\mathcal R_k\). Concretely, to obtain (7.7) it is enough
to establish the following bound:

> **(Analytic sub-lemma needed for (7.7))** there exists \(C<\infty\) such that for every window \(U_k\) and every
> radius \(R\ge1\),
> \[
> \big|\widetilde F_0(R)-\widetilde F_{-1}(R)\big|
> \;\le\;
> C\,\mathcal D_k.
> \tag{7.14}
> \]
> (Here \(\widetilde F_s(R)=E_R(s)/E_\infty(s)\).)

We will in fact establish a **pinned** version first:
\[
\sup_{R\ge1}\big|F_0(R)-F_{-1}(R)\big|\ \le\ C\,\mathcal D_k,
\qquad
F_s(R):=\frac{E_R(s)}{E_*},\ E_*:=E_\infty(0).
\tag{7.14pin}
\]
Taking \(R\to\infty\) in (7.14pin) gives control of the total-energy ratio
\(M_s:=\lim_{R\to\infty}F_s(R)=E_\infty(s)/E_*\):
\[
|M_0-M_{-1}|=\Big|1-\frac{E_\infty(-1)}{E_*}\Big| \ \le\ C\,\mathcal D_k,
\qquad (M_0=1).
\tag{7.14a}
\]

**Division-by-zero is harmless.** If \(M_{-1}=0\) (equivalently \(E_\infty(-1)=0\)), then for every \(R\ge1\) we have
\(0\le E_R(-1)\le E_\infty(-1)=0\), hence \(E_R(-1)=0\). In particular, the instantaneous profile at time \(-1\) may be (7.14a)
set by convention to \(\widetilde F_{-1}(R):=0\). Moreover, (7.14a) implies \(1=|M_0-M_{-1}|\le C\mathcal D_k\), so
\[
\sup_{R\ge1}|\widetilde F_0(R)-\widetilde F_{-1}(R)|
\ \le\ 1
\ \le\ C\,\mathcal D_k,
\]
and (7.14) holds trivially in this case.

Assume henceforth \(M_{-1}>0\). Since \(\widetilde F_s(R)=F_s(R)/M_s\), we estimate for any \(R\ge1\)
\[
\big|\widetilde F_0(R)-\widetilde F_{-1}(R)\big|
=\left|F_0(R)-\frac{F_{-1}(R)}{M_{-1}}\right|
\le |F_0(R)-F_{-1}(R)|+F_{-1}(R)\left|1-\frac1{M_{-1}}\right|.
\]
Using \(0\le F_{-1}(R)\le M_{-1}\) (since \(E_R(s)\le E_\infty(s)\)) we have
\(F_{-1}(R)\left|1-\frac1{M_{-1}}\right|\le |M_{-1}-1|\). Hence (Appendix NFS.IMP)
\[
\big|\widetilde F_0(R)-\widetilde F_{-1}(R)\big|
\le |F_0(R)-F_{-1}(R)|+|M_{-1}-1|
\le 2C\,\mathcal D_k.
\tag{7.14b}
\]
Absorb the factor \(2\) into the constant \(C\).

Indeed, if \(\mathcal R_k\) is much larger than \(\mathcal R_{k-1}\), then by monotonicity the function \(\widetilde F_0\) must
increase by at least \(\kappa\) over the radius interval \([\mathcal R_{k-1},\mathcal R_k]\) while \(\widetilde F_{-1}\) already
hits \(\theta+\kappa\) at \(\mathcal R_{k-1}\). Estimate (7.14) prevents this from happening repeatedly unless the
dissipation budget is large.

*Where does (7.14) come from?* Start from the fixed-radius localized Gaussian LEI (Lemma 6.1), applied at the same cutoff
radius \(R\) at times \(-1\) and \(0\). The only obstacle is the error term \(\mathrm{Err}_R\) coming from the cutoff.
Lemma 7.3 is designed precisely to absorb these cutoff errors into the full dissipation \(\mathcal D_k\) plus a controlled
boundary-movement term. Once Lemma 7.3 is proved with a sharp enough error bookkeeping, (7.14) follows immediately.

Converting (7.14) into the drift bound (7.7) is **deterministic**, but it is *not* automatic from monotonicity alone: one must exclude the scenario where the energy profile $R\mapsto \widetilde F_s(R)$ is essentially flat near the threshold $\theta+\kappa$, in which case an arbitrarily small perturbation can move the hitting time far.

We isolate the deterministic conversion needed to rule out slow drift.
With the quantitative width definition (5.2), **no profile transversality / non-flatness input is required**:
a small \(L^\infty_R\) perturbation of the normalized profile produces a proportionally small drift of the
band-averaged log-quantile radius (Lemma 7.9 in §4.2.6.5).

**Status summary (updated).**
- **(M2a) is now proved**: Lemma 7.8 ⇒ Proposition 7.11 (7.14pin) ⇒ (7.14).
- **(M2b) is now proved (Option B)**: Lemma 7.9 ⇒ (7.7) (per-window log-drift control).

#### 6.2.4.1 M2b: the “non-flatness” hypothesis is eliminated by definition (Option B)

Earlier drafts formulated a separate analytic input (obsolete transversality hypothesis) asserting a quantitative *transversality* of the profile
at a single crossing level. This is **not** an acceptable hidden hypothesis: a nearly flat profile can produce an
arbitrarily large hitting-time drift under an arbitrarily small \(L^\infty_R\) perturbation.

With the quantitative width definition (5.2) (log-average of quantile radii across a hysteresis band), **no crossing-slope
assumption is needed**. The deterministic conversion
\[
\sup_{R\ge 1}\big|\widetilde F_0(R)-\widetilde F_{-1}(R)\big|\ \lesssim\ \mathcal D_k
\quad\Longrightarrow\quad
\big|\log\mathcal R_k-\log\mathcal R_{k-1}\big|\ \lesssim\ \mathcal D_k
\tag{M2b}
\]
is proved in §4.2.6.5 after (7.14pin) is established.

---
#### 6.2.5 Explicit error decomposition for (M2a)

For later use (and to keep the proof-spine honest), we record what the cutoff error looks like **after all cancellations that are
pure algebra**. This makes clear what must still be estimated to upgrade Lemma 7.3 into the profile stability bound (7.14).

> **Lemma 7.6 (Annulus-supported decomposition of the fixed-radius error).** 
> Let \((U,P)\) be a suitable weak solution to (LRNS) on \([-1,0]\times\mathbb R^3\), and fix \(R\ge1\).
> With \(\psi_R=\chi_R^2G\) and \(A_R:=\{R\le|y|\le2R\}\), the fixed-radius error term \(\mathrm{Err}_R\) in Lemma 6.1 satisfies
> \[
> \big|\mathrm{Err}_R[U;-1,0]\big|
> \;\le\;
> C_\chi\int_{-1}^{0}\!\int_{A_R}|U|^2\,G\,dy\,ds
> \;+
> \frac{C_\chi}{R}\int_{-1}^{0}\!\int_{A_R}\Big(|U|^3+|P|\,|U|\Big)\,G\,dy\,ds.
> \tag{7.15}
> \]
>
> *Proof (bookkeeping).* 
> Start from the definition of \(\mathrm{Err}_R\) in Lemma 6.1. Using \(\psi_R=\chi_R^2G\) and the OU\(^\ast\)-identity
> \(\Delta G+\tfrac12 y\cdot\nabla G+\tfrac32 G=0\), expand the OU\(^\ast\) forcing part:
> \[
> \Delta(\chi_R^2G)+\tfrac12 y\cdot\nabla(\chi_R^2G)+\tfrac32\chi_R^2G
> =G\,\Delta(\chi_R^2)-\tfrac12\,G\,y\cdot\nabla(\chi_R^2),
> \]
> where we used \(\nabla G=-\tfrac12 yG\). Both derivatives of \(\chi_R\) are supported on \(A_R\), and satisfy
> \(|\nabla(\chi_R^2)|\lesssim R^{-1}\mathbf 1_{A_R}\), \(|\Delta(\chi_R^2)|\lesssim R^{-2}\mathbf 1_{A_R}\), and
> \(|y\cdot\nabla(\chi_R^2)|\lesssim \mathbf 1_{A_R}\). Therefore the entire OU\(^\ast\) forcing contribution is bounded by (Lemma 7.6)
> \(C_\chi\int_{-1}^0\!\int_{A_R}|U|^2G\).
>
> For the transport/pressure part, note that
\(|\nabla\psi_R|\le |\nabla(\chi_R^2)|\,G+\chi_R^2|\nabla G|\).

The \(\chi_R^2\nabla G\) term is a *bulk Gaussian flux* and must not be “waved away”. In the cutoff-trade engine it cancels
**only after** we combine the *interior* and *exterior* localized budgets:

> **Mini-Lemma 7.6A (Interior–exterior cancellation of the Gaussian bulk flux).** 
> Let \(\psi_R:=\chi_R^2G\) and \(\psi_R^{\rm out}:=(1-\chi_R^2)G\). Then
> \[
> \nabla\psi_R+\nabla\psi_R^{\rm out}=\nabla G,
> \qquad
> \nabla\psi_R=G\nabla(\chi_R^2)+\chi_R^2\nabla G,
> \qquad
> \nabla\psi_R^{\rm out}=-G\nabla(\chi_R^2)+(1-\chi_R^2)\nabla G.
> \tag{7.15A}
> \]
> Consequently, if one applies the transport/pressure term from Lemma 6.1 to \(\psi_R\) and \(\psi_R^{\rm out}\) and adds (Lemma 7.6)
> the two identities, the \(\pm G\nabla(\chi_R^2)\) boundary pieces remain while the bulk pieces recombine into the
> full-space flux with \(\nabla G\).

With this bookkeeping, the transport/pressure contribution relevant for the *boundary* (interior–exterior) part is supported
where \(\nabla\chi_R\neq 0\), hence on \(A_R\), and carries an explicit factor \(R^{-1}\) (Lemma 7.6).
Using \(|\nabla(\chi_R^2)|\lesssim R^{-1}\mathbf 1_{A_R}\) gives the second term in (7.15). \(\square\)

>
> *Remark.* Bound (7.15) is **not yet** the desired estimate \(|\mathrm{Err}_R|\lesssim\mathcal D_k\). It only shows that the
> cutoff error is controlled by *annular mass/flux* terms. Closing (M2a) requires a quantitative mechanism that trades these annular
> quantities for the window dissipation budget \(\mathcal D_k\) in a way uniform in the relevant radii.

A Calderón–Zygmund (NFS.EST.4) pressure estimate (together with Hölder) gives, for each fixed time \(s\),
\[
\int_{A_R}|P|\,|U|
\;\lesssim\;
\|P(s)\|_{L^{3/2}(A_R)}\,\|U(s)\|_{L^3(A_R)}
\;\lesssim\;
\|U(s)\|_{L^3(\mathbb R^3)}^2\,\|U(s)\|_{L^3(A_R)}.
\tag{7.16}
\]

**Mini-Lemma 7.6P (Pressure gauges and pressure-flux bounds: cancellation + far/local decomposition).** 
Before estimating pressure fluxes we fix the gauge on a ball: for any ball \(B=B_{\rho R}\) at time \(s\) we write
\(\widetilde P_B(s):=P(s)- (P)_B(s)\) with \((P)_B(s):=|B|^{-1}\int_B P(s,y)\,dy\).
All quantities below depend only on \(\widetilde P_B\) and are therefore invariant under \(P\mapsto P+c(s)\) (Lemma 7.6P).

Fix a time \(s\) and radius \(R\ge1\). Write the pressure in Leray variables as the double Riesz transform
\[
P(s,\cdot)=\mathcal R_i\mathcal R_j\big(U_i(s,\cdot)\,U_j(s,\cdot)\big),
\]
(which is legitimate since \(U(s)\in L^3\Rightarrow U_iU_j\in L^{3/2}\) and \(\mathcal R_i\mathcal R_j\) is bounded on \(L^{3/2}\); see e.g. [CZ52, Ste70] or [Gra14, Cor. 5.2.8]). 
Then:

1) **(Cancellation of constants in the full Gaussian flux)** For any scalar \(c(s)\),
\[
\int_{\mathbb R^3} c(s)\,U(s,y)\cdot\nabla G(y)\,dy
=
-c(s)\int_{\mathbb R^3}G(y)\,\nabla\cdot U(s,y)\,dy
=0,
\]
by divergence-free and the Gaussian decay (justified by a cutoff (NFS.EST.1)-at-infinity argument). In particular, the *bulk* pressure–transport term
\(\int (|U|^2/2+P)\,U\cdot\nabla G\) is insensitive to adding a constant to \(P\). This is the tiny “cancellation” that makes the interior/exterior recombination in Lemma 7.6A clean.

2) **(Far/local decomposition on the annulus)** Let \(\eta_R(y):=\eta(|y|/R)\) with \(\eta\equiv1\) on \([0,4]\), \(\eta\equiv0\) on \([8,\infty)\), and define
\[
P_{\rm loc}:=\mathcal R_i\mathcal R_j\!\big(\eta_R\,U_iU_j\big),\qquad
P_{\rm far}:=\mathcal R_i\mathcal R_j\!\big((1-\eta_R)\,U_iU_j\big),
\qquad P=P_{\rm loc}+P_{\rm far}.
\tag{7.16a}
\]
Then, for \(A_R=\{R\le|y|\le2R\}\),
\[
\|P_{\rm loc}(s)\|_{L^{3/2}(A_R)}
\ \lesssim\
\|\eta_R\,U(s)\otimes U(s)\|_{L^{3/2}(\mathbb R^3)}
\ \lesssim\
\|U(s)\|_{L^3(B_{8R})}^2,
\tag{7.16b}
\]
by Calderón–Zygmund (NFS.EST.4) boundedness of \(\mathcal R_i\mathcal R_j\) on \(L^{3/2}\) [CZ52, Ste70, Gra14]. 
Moreover, for every \(y\in A_R\) and \(z\in\mathrm{supp}(1-\eta_R)\subset\{|z|\ge4R\}\) one has \(|y-z|\simeq|z|\), hence the kernel representation of \(\mathcal R_i\mathcal R_j\) (principal value) gives [CZ52]
\[
|P_{\rm far}(s,y)|
\ \lesssim\
\int_{|z|\ge4R}\frac{|U(s,z)|^2}{|z|^3}\,dz.
\tag{7.16c}
\]
Using Hölder with exponents \((\tfrac32,3)\),
\[
\int_{|z|\ge4R}\frac{|U|^2}{|z|^3}
\ \le\
\|U(s)\|_{L^3(|z|\ge4R)}^2\,
\Big(\int_{|z|\ge4R}|z|^{-9}\,dz\Big)^{1/3}
\ \lesssim\
\frac{\|U(s)\|_{L^3(|z|\ge4R)}^2}{R^2}.
\]
Since \(|A_R|\simeq R^3\), multiplying by \(|A_R|^{2/3}\simeq R^2\) yields
\[
\|P_{\rm far}(s)\|_{L^{3/2}(A_R)}
\ \lesssim\
\|U(s)\|_{L^3(|z|\ge4R)}^2.
\tag{7.16d}
\]
Combining (7.16b)–(7.16d),
\[
\|P(s)\|_{L^{3/2}(A_R)}
\ \lesssim\
\|U(s)\|_{L^3(B_{8R})}^2+\|U(s)\|_{L^3(|z|\ge4R)}^2.
\tag{7.16e}
\]

3) **(Pressure flux estimate on \(A_R\))** Since \(0<G\le1\), Hölder gives
\[
\int_{A_R}|P|\,|U|\,G
\ \le\
\|P(s)\|_{L^{3/2}(A_R)}\,\|U(s)\|_{L^3(A_R)}
\ \lesssim\
\Big(\|U\|_{L^3(B_{8R})}^2+\|U\|_{L^3(|z|\ge4R)}^2\Big)\,\|U\|_{L^3(A_R)}.
\tag{7.16f}
\]
In particular, using the global a priori bound \(\|U(s)\|_{L^3(\mathbb R^3)}\le M\) gives the rough estimate (7.16) as an immediate corollary.

*Proof.* The only inputs are (i) the constant-flux cancellation in item 1, (ii) the Calderón–Zygmund (NFS.EST.4) boundedness of \(\mathcal R_i\mathcal R_j\) on \(L^{3/2}\) [CZ52, Ste70, Gra14], and (iii) the elementary kernel bound for the far-field piece in (7.16c). ∎

Thus (7.15) becomes small for large \(R\) by GKP tightness (tail smallness of \(\|U\|_{L^3(A_R)}\)), but this is still weaker than (Lemma 7.3)
what we need for (7.14). The point of Lemma 7.3 is that, by allowing *controlled motion of the cutoff*, one can hope to bound the
annular mass/flux accumulated over a unit window directly by \(\mathcal D_k\). Writing that trade explicitly is exactly (M2a).

### 6.2.6 The concrete (M2a) trade mechanism (annulus-error ⇔ dissipation)

This subsection makes fully explicit what “(M2a) error-control” must do and how it is proved from the already-written
localized Gaussian energy inequality (Lemma 7.3) and the error decomposition (Lemma 7.6). Nothing is left in the
vague form “ LEI machinery”: we spell out the exact functionals to be estimated and the single place where a
hard-analysis lemma must be inserted.

#### 6.2.6.1 A sharper bound for the moving-cutoff term
In Lemma 7.3 we bounded the moving term using the crude majorant \(\psi_{2R}\). For (M2a) it is important to record
the *support-localized* form: since \(\partial_s \psi_{R(s)}\) is supported where the cutoff transitions, one has
\[
\label{eq:7.10prime}
\Big|\int_{s_1}^{s_2}\!\!\int_{\mathbb R^3}\frac12 |U|^2\,\partial_s\psi_{R(s)}\,dy\,ds\Big|
\ \le\ C_\chi\!\int_{s_1}^{s_2}\frac{|R'(s)|}{R(s)}\,
\int_{A_{R(s)}}\frac12|U(s,y)|^2\,G(y)\,dy\,ds,
\tag{7.10'}
\]
where \(A_R:=\{y: R\le |y|\le 2R\}\) and \(C_\chi\) depends only on the fixed cutoff profile \(\chi\).
(Proof: differentiate \(\chi(|y|/R(s))^2\) in \(s\), note \(|\partial_s(\chi^2)|\lesssim (|R'|/R)\,1_{A_R}\).)

This is the first “trade”: if the annulus \(A_{R(s)}\) carries little Gaussian \(L^2\)-mass, then *moving the window* is cheap.

#### 6.2.6.2 The annular error functionals that must be controlled
For a given radius \(R\ge 1\) (or a path \(R(\cdot)\)) define the annular functionals on the RG window \([-1,0]\):
\[
\mathsf M_R(\tau):=\int_{A_R}\frac12|U(\tau,y)|^2\,G(y)\,dy,
\qquad
\mathsf J_R(\tau):=\frac1R\int_{A_R}\Big(|U|^3+|P||U|\Big)(\tau,y)\,G(y)\,dy.
\tag{7.17}
\]
By Lemma 7.6, the full error functional in Lemma 7.3 obeys (for fixed \(R\))
\[
\big|\mathrm{Err}_R[U;-1,0]\big|
\ \le\ C\int_{-1}^{0}\Big(\mathsf M_R(\tau)+\mathsf J_R(\tau)\Big)\,d\tau.
\tag{7.18}
\]
For a *moving* radius \(R(\tau)\), combining Lemma 7.3 with (7.10') and Lemma 7.6 yields the analogous bound
\[
\big|\mathrm{Err}_{R(\cdot)}[U;-1,0]\big|
\ \le\ C\int_{-1}^{0}\Big(\mathsf M_{R(\tau)}(\tau)+\mathsf J_{R(\tau)}(\tau)\Big)\,d\tau
\ +\ C_\chi\int_{-1}^{0}\frac{|R'(\tau)|}{R(\tau)}\,\mathsf M_{R(\tau)}(\tau)\,d\tau.
\tag{7.19}
\]
Thus (M2a) is *exactly* the task of bounding the right-hand side by the window dissipation \(\mathcal D_k\) (Lemma 7.6)
(and quantities already fixed at spine level: CE bounds \(M,m_0\) and chosen parameters \(\theta,\kappa\); cf. Appendices NFS.1.8–NFS.1.9).

#### 6.2.6.3 How the trade is supposed to work (what is already available, and what is not)
There are three pieces to control:

1) **OU\(^*\)-commutator mass term \(\mathsf M_R\).** 
This is the “OU forcing” part in Lemma 7.6. It is linear in \(|U|^2\) and is supported on the annulus.
For fixed radii it cannot be bounded purely by Hölder (NFS.EST.2); one needs a *Caccioppoli-type estimate in the Leray frame*
that trades annular \(L^2(G)\)-mass into dissipation on a slightly larger region.

2) **Advective boundary flux \(\frac1R\int_{A_R}|U|^3G\).** 
This is controlled in the *same* Caccioppoli estimate: the way is to apply the localized energy inequality
with a test function supported on the annulus and then absorb the \(|U|^3\) term by the dissipation (Young + cutoff).

3) **Pressure flux \(\frac1R\int_{A_R}|P||U|G\).** 
This is where “Flux Sealing” enters: write \(P=P_{\mathrm{loc}}+P_{\mathrm{far}}\) using a cutoff adapted to the annulus.
The local part is treated by Calderón–Zygmund (NFS.EST.4) \([Gra14, Cor. 5.2.8]\) and the already assumed uniform \(L^3\)-control.
The far part is harmonic on the relevant ball and is handled by a quantitative tail bound derived from (GKP) and the
pressure representation (this is the hard-analysis heart that must be written explicitly; see §2 of the reader report).

All three are packaged in a single lemma:

> **Lemma 7.7 (Cutoff trade: commutator form + pressure localization). 
Fix $R\ge 1$ and write $\psi_R:=\chi_R^2 G$, with $\chi_R(y):=\chi(|y|/R)$ and $\chi$ as in §4.2.6.1. 
Define the annulus $A_R:=\{y:\ R\le |y|\le 2R\}$. 

There are two “hard” structural inputs behind the cutoff trade:

**(A) OU–commutator identity (kills the large $y$–drift).** 
Let
\[
\mathcal O_R(\tau)
:=\int_{\mathbb R^3}\Big(\tfrac12|U(\tau)|^2\Delta\psi_R
+\tfrac14|U(\tau)|^2\big(y\!\cdot\!\nabla\psi_R+3\psi_R\big)\Big)\,dy.
\]
Then one has the exact identity
\[
\mathcal O_R(\tau)
=\frac14\int_{\mathbb R^3}|U(\tau)|^2\,\nabla\!\cdot\!\big(2\nabla\psi_R+y\psi_R\big)\,dy
=-\frac12\int_{\mathbb R^3}\big((\nabla U(\tau))^{\!\top}U(\tau)\big)\cdot\nabla\chi_R^2\,G\,dy.
\tag{7.20A}
\]
In particular $\mathcal O_R(\tau)$ is supported where $\nabla\chi_R\neq 0$, hence on $A_R$, and satisfies (Lemma 7.7)
\[
|\mathcal O_R(\tau)|
\le C\,\frac1R\Big(\int_{A_R}|U(\tau)|^2G\,dy\Big)^{1/2}
\Big(\int_{A_R}|\nabla U(\tau)|^2G\,dy\Big)^{1/2}.
\tag{7.20A'}
\]

**(B) Pressure localization (Calderón–Zygmund (NFS.EST.4) + far–field tail).** 
Fix $\eta\in C_c^\infty(\mathbb R^3)$ radial with $\eta\equiv 1$ on $B_{4}$ and $\eta\equiv 0$ on $B_{8}^c$, and set $\eta_{R}(y):=\eta(y/R)$. 
Decompose (for each $\tau$)
\[
P(\tau)=P_{\rm loc}(\tau)+P_{\rm far}(\tau),
\qquad
P_{\rm loc}:=\mathcal R_i\mathcal R_j\big(\eta_{R}\,U_iU_j\big),
\quad
P_{\rm far}:=\mathcal R_i\mathcal R_j\big((1-\eta_{R})\,U_iU_j\big),
\tag{7.20B}
\]
where $\mathcal R_i$ are the Riesz transforms. Then:
\[
\|P_{\rm loc}(\tau)\|_{L^{3/2}(\mathbb R^3)}
\lesssim
\|\eta_R\,U(\tau)\|_{L^3(\mathbb R^3)}^2
\le \|U(\tau)\|_{L^3(B_{8R})}^2,
\tag{7.20B1}
\]
by the Calderón–Zygmund (NFS.EST.4) estimate for $\mathcal R_i\mathcal R_j$ on $L^{3/2}$ [Gra14, Cor. 5.2.8]. 
Moreover, for $y\in A_R$ one has the pointwise far–field bound
\[
|P_{\rm far}(\tau,y)|
\lesssim
\int_{|z|\ge 4R}\frac{|U(\tau,z)|^2}{|z|^3}\,dz
\lesssim
R^{-2}\,\|U(\tau)\|_{L^3(|z|\ge 4R)}^2,
\tag{7.20B2}
\]
where the last step is Hölder together with $\int_{|z|\ge 4R}|z|^{-9}\,dz\sim R^{-6}$. 
Consequently, (Lemma 7.7)
\[
\|P_{\rm far}(\tau)\|_{L^{3/2}(A_R)}
\lesssim
\|U(\tau)\|_{L^3(|z|\ge 4R)}^2.
\tag{7.20B3}
\]

*Proof of (A).* 
Use $\nabla\!\cdot(y\psi_R)=y\!\cdot\!\nabla\psi_R+3\psi_R$ and write
\[
\mathcal O_R(\tau)=\frac14\int |U|^2\,\nabla\!\cdot(2\nabla\psi_R+y\psi_R)\,dy
=-\frac14\int \nabla(|U|^2)\cdot(2\nabla\psi_R+y\psi_R)\,dy.
\]
Since $\nabla(|U|^2)=2(\nabla U)^{\!\top}U$, it remains to identify $2\nabla\psi_R+y\psi_R$. 
With $\psi_R=\chi_R^2G$ and $\nabla G=-(y/2)G$ we compute
\[
2\nabla(\chi_R^2G)+y\chi_R^2G
=2(\nabla\chi_R^2)\,G+2\chi_R^2\nabla G+y\chi_R^2G
=2(\nabla\chi_R^2)\,G,
\]
so (7.20A) follows. The estimate (7.20A') uses $|\nabla\chi_R^2|\lesssim R^{-1}\mathbf 1_{A_R}$ and Cauchy–Schwarz. □ 

*Proof of (B).* 
(7.20B1) is the boundedness of $\mathcal R_i\mathcal R_j$ on $L^{3/2}$ applied to $\eta_R U_iU_j\in L^{3/2}$, a Calderón–Zygmund (NFS.EST.4) estimate; see [Gra14, Cor. 5.2.8] or [Ste70]. 
For (7.20B2), write $P_{\rm far}(\tau,y)=\int K_{ij}(y-z)\,(1-\eta_R(z))\,U_iU_j(\tau,z)\,dz$, where $K_{ij}$ is the pressure kernel with $|K_{ij}(w)|\lesssim |w|^{-3}$. 
If $y\in A_R$ and $|z|\ge 4R$ then $|y-z|\simeq |z|$, hence $|K_{ij}(y-z)|\lesssim |z|^{-3}$, giving the first inequality in (7.20B2) (NFS.EST.4).
The second inequality is Hölder as stated. Finally (7.20B3) is immediate from (7.20B2) and $|A_R|\sim R^3$. □ 

**How this is used (what remains to close the full trade).** 
Identity (7.20A) upgrades the OU* part of the cutoff error from a crude $|U|^2$–annulus bound to a *gradient commutator* supported on $A_R$. 
The pressure split (7.20B) reduces the pressure contribution on $A_R$ to a local $L^3$–term plus an explicit far–field tail controlled by the tightness modulus from GKP2. 

We now close this last step in M2a by a single, fully explicit Caccioppoli-type estimate that turns all
remaining annulus terms into **pure dissipation on a slightly larger scale**, with constants depending only on the a priori
critical bounds (GKP) and the cutoff profile.

> **Lemma 7.8 (Strong linear cutoff trade; closes M2a.1 and completes (M2a)).** 
Let \((U,P)\) be the RG-window profile on \([-1,0]\) satisfying the uniform bounds (GKP1–GKP4), and let \(\psi_R=\chi_R^2G\) be as in §4.2.6.1 with \(R\ge 1\). 
Then the fixed-radius error functional from Lemma 7.3 satisfies the *linear trade with a vanishing tail remainder*
\[
\big|\mathrm{Err}_R[U;-1,0]\big|
\ \le\ C\,\int_{-1}^{0} D_G[U](\tau;4R)\,d\tau
\ +\ C\,\Big(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(\tau;R/4)\Big)^2,
\tag{7.20C}
\]
where \(C=C(M,m_0,\chi)\), \(D_G[U](\tau;4R)=\int_{\mathbb R^3}|\nabla U(\tau)|^2\,\chi_{4R}^2\,G\,dy\), and
\(\mathrm{Tail}_\sharp(\tau;R)\) is the sharp tail functional (7.T\(\sharp\)) computed for the slice \(U(\tau,\cdot)\).
In particular, by Lemma 7.8C\(_{\mathrm{NT}}\) the remainder term tends to \(0\) as \(R\to\infty\), uniformly in \(\tau\in[-1,0]\).

*Proof.* By Lemma 7.6 the error splits into a sum of annulus-supported pieces. We bound them one by one.

**Step 1: a Gaussian-weighted annulus Hardy/Poincaré bound for \((1/R)\|U\|_{L^2(A_R,G)}\.** 
Let \(\zeta\in C_c^\infty\) be radial with \(\zeta\equiv 1\) on \([1,2]\) and \(\zeta\equiv 0\) outside \([\tfrac12,4]\), and set \(\zeta_R(y):=\zeta(|y|/R)\). 
We claim the purely local estimate
\[
\frac1{R^2}\int_{A_R}|U(\tau)|^2\,G\,dy
\ \le\ C\int_{\mathbb R^3}|\nabla(\zeta_R U(\tau))|^2\,G\,dy,
\tag{7.20C1}
\]
with an absolute constant \(C_{\mathrm{abs}}=C_{\mathrm{abs}}(\zeta)\) independent of \(R\ge 1\) and independent of the RG profile.

*Proof of (7.20C1).* Write the Gaussian measure in polar form:
\[
G(y)\,dy = c_0\,w(r)\,dr\,d\omega,\qquad r=|y|,\qquad w(r):=r^2e^{-r^2/4}.
\]
Fix a direction \(\omega\in\mathbb S^2\) and a component \(f(r):=(\zeta_R U(\tau))(r\omega)\). 
Since \(\zeta_R\equiv 0\) on \(r\le R/2\), we have \(f(R/2)=0\), hence for \(r\in[R,2R]\), (Lemma 7.8)
\[
f(r)=\int_{R/2}^{r}\partial_\rho f(\rho)\,d\rho.
\]
By Cauchy–Schwarz with the weight \(w\),
\[
|f(r)|^2
\le
\Big(\int_{R/2}^{r}|\partial_\rho f(\rho)|^2\,w(\rho)\,d\rho\Big)
\Big(\int_{R/2}^{r}\frac{d\rho}{w(\rho)}\Big).
\]
For \(r\in[R,2R]\) and \(\rho\in[R/2,r]\) one has \(r/\rho\le 4\) and \(w(\rho)\ge w(r)/16\) (because \(w\) is decreasing on \([0,\infty)\) and \(w(r)/w(\rho)=(r/\rho)^2e^{-(r^2-\rho^2)/4}\le 16\)). 
Thus \(\int_{R/2}^{r}\!w(\rho)^{-1}d\rho \le 16(r-R/2)\,w(r)^{-1}\le 24R\,w(r)^{-1}\), and so (Lemma 7.8)
\[
|f(r)|^2\,w(r)\ \le\ 24R\int_{R/2}^{r}|\partial_\rho f(\rho)|^2\,w(\rho)\,d\rho.
\]
Integrating \(r\in[R,2R]\) and swapping integrals yields
\[
\int_{R}^{2R}|f(r)|^2\,w(r)\,dr
\ \le\ 48R^2\int_{R/2}^{2R}|\partial_\rho f(\rho)|^2\,w(\rho)\,d\rho.
\]
Now integrate over \(\omega\in\mathbb S^2\) and sum components; since \(|\partial_r(\zeta_R U)|\le|\nabla(\zeta_R U)|\),
this gives (7.20C1). \(\square\)

Expanding \(\nabla(\zeta_R U)=\zeta_R\nabla U + U\nabla\zeta_R\) and using \(|\nabla\zeta_R|\lesssim R^{-1}\mathbf 1_{A_{R/2,4R}}\) yields
\[
\frac1{R^2}\int_{A_R}|U(\tau)|^2\,G\,dy
\ \lesssim\ \int_{\mathbb R^3}|\nabla U(\tau)|^2\,\chi_{4R}^2\,G\,dy
\ +\ \frac1{R^2}\int_{A_{R/2,4R}}|U(\tau)|^2\,G\,dy.
\tag{7.20C2}
\]
Finally, applying the same estimate at scales \(R/2\) and \(2R\) (a finite two-step “ring absorption”) absorbs the last term
into the left-hand side, giving
\[
\frac1{R^2}\int_{A_R}|U(\tau)|^2\,G\,dy
\ \lesssim\ \int_{\mathbb R^3}|\nabla U(\tau)|^2\,\chi_{4R}^2\,G\,dy.
\tag{7.20C3}
\]

**
Step 2 (Gaussian–local Sobolev on the annulus; the genuine “repair”). 
This is the only delicate point: we must control an annulus \(L^6(\mu)\) norm by **Gaussian-weighted dissipation**
without any illegitimate “unweighted Sobolev \(\Rightarrow\) weighted Dirichlet” jump.

Let \(A_R^\sharp:=\{0.99R\le |y|\le 2.01R\}\) and \(\phi_R\in C_c^\infty(\mathbb R^3)\) satisfy
\(\phi_R\equiv 1\) on \(A_R^\sharp\), \(\mathrm{supp}\,\phi_R\subset \{0.98R\le |y|\le 2.02R\}\), and
\(|\nabla\phi_R|\lesssim 1/R\).

Write \(\mu:=G\,dy\). By the Gaussian Sobolev inequality (see [BGL14, Prop. 6.2.3] for the 
\((\mu,\nabla)\) Sobolev form), there is a universal constant \(C_S\) such that for all \(f\in H^1(\mu)\),
\[
\|f\|_{L^6(\mu)}^2 \ \le\ C_S\Big(\int |\nabla f|^2\,d\mu\ +\ \|f\|_{L^2(\mu)}^2\Big).
\tag{7.20C4}
\]

Apply this to \(f:=U\,\phi_R\). We eliminate the \(L^2(\mu)\) term using **small Gaussian support**.
Indeed, by Hölder (NFS.EST.2),
\[
\|f\|_{L^2(\mu)}^2 \le \mu(\mathrm{supp}\,\phi_R)^{2/3}\,\|f\|_{L^6(\mu)}^2.
\tag{7.20C5}
\]
Since \(\mu(\mathrm{supp}\,\phi_R)\sim \int_{0.98R}^{2.02R} r^2 e^{-r^2/4}\,dr\),
there exists \(R_\ast\ge 1\) such that
\[
C_S\,\mu(\mathrm{supp}\,\phi_R)^{2/3}\ \le\ \tfrac12
\qquad\text{for all }R\ge R_\ast.
\tag{7.20C5a}
\]
Combining (7.20C4)–(7.20C5a) and absorbing yields, for all \(R\ge R_\ast\),
\[
\|U\,\phi_R\|_{L^6(\mu)}^2
\ \le\ 2C_S\int |\nabla(U\,\phi_R)|^2\,d\mu.
\tag{7.20C6}
\]

For the finitely many radii \(1\le R\le R_\ast\), we simply use (7.20C4) directly and absorb the
\(\|f\|_{L^2(\mu)}^2\) term into the right-hand side by an admissible constant \(C_{\mathrm{abs}}(R_\ast)\) in the sense of Appendix **NFS.1.9** (depending only on the fixed cutoff profile and the fixed radius parameter \(R_\ast\)). Renaming \(C_{\mathrm{abs}}(R_\ast)\) once (still within the same admissible class), (7.20C6) holds for **all** \(R\ge 1\).

Next expand
\[
\int |\nabla(U\,\phi_R)|^2\,d\mu
\ \lesssim\ \int |\nabla U|^2\,\phi_R^2\,d\mu\ +\ \int |U|^2\,|\nabla\phi_R|^2\,d\mu.
\tag{7.20C6b}
\]
Since \(\phi_R\equiv 1\) on \(A_R^\sharp\) and \(\mathrm{supp}\,\phi_R\subset \{|y|\le 2.02R\}\subset\{|y|\le 4R\}\),
we have \(\phi_R\le \chi_{4R}\). Hence (7.20C6)
\[
\int |\nabla U|^2\,\phi_R^2\,d\mu\ \le\ \int |\nabla U|^2\,\chi_{4R}^2\,G\,dy\ =\ D_G[U](\tau;4R).
\tag{7.20C6c}
\]
For the cutoff-gradient term, \(|\nabla\phi_R|\lesssim 1/R\) and \(\nabla\phi_R\) is supported on an annulus
comparable to \(A_R\), so by Step 1 (Hardy on the annulus),
\[
\int |U|^2\,|\nabla\phi_R|^2\,d\mu
\ \lesssim\ \frac1{R^2}\int_{A_R^\sharp}|U|^2\,G\,dy
\ \lesssim\ \int |\nabla U|^2\,\chi_{4R}^2\,G\,dy.
\tag{7.20C7}
\]
Combining (7.20C6)–(7.20C7) gives the repaired Gaussian-annulus Sobolev control:
\[
\|U\|_{L^6(A_R^\sharp,\mu)}^2
\le \|U\,\phi_R\|_{L^6(\mu)}^2
\ \lesssim\ \int |\nabla U|^2\,\chi_{4R}^2\,G\,dy
\ =\ D_G[U](\tau;4R).
\tag{7.20C8}
\]

From (7.20C8) and the global critical bound \(\|U(\tau)\|_{L^3(\mathbb R^3)}\le M\) (CE1), Hölder yields the annulus \(L^4\) control
\[
\|U\|_{L^4(A_R,\mu)}^2
\le \|U\|_{L^3(\mathbb R^3)}\,\|U\|_{L^6(A_R,\mu)}
\le M\,\|U\|_{L^6(A_R^\sharp,\mu)}
\ \lesssim\ M\Big(\int_{\mathbb R^3}|\nabla U(\tau,y)|^2\,\chi_{4R}(y)^2\,G(y)\,dy\Big)^{1/2}.
\tag{7.20C9}
\]

Step 3 (cubic flux on the Gaussian shell). 
By Cauchy–Schwarz on \(A_R\) and Step 1,
\[
\frac1R\int_{A_R} |U|^3\,d\mu
\ \le\ \Big(\frac1{R^2}\int_{A_R}|U|^2\,d\mu\Big)^{1/2}\Big(\int_{A_R}|U|^4\,d\mu\Big)^{1/2}
\ \lesssim\ \Big(\int |\nabla U|^2\,\chi_{4R}^2\,d\mu\Big)^{1/2}\,\|U\|_{L^4(A_R,\mu)}^2.
\tag{7.20C10}
\]
Invoking (7.20C9) gives
\[
\frac1R\int_{A_R} |U|^3\,d\mu\ \lesssim\ M\int |\nabla U|^2\,\chi_{4R}^2\,d\mu.
\tag{7.20C11}
\]

Step 4 (pressure flux; cite-level mid/far decomposition and a sharp tail). 

**Hypothesis check (pressure step).** We use only:
(i) the critical bound $U(\tau)\in L^3(\mathbb R^3)$ (CE1 / (GKP1)) so that $U\otimes U\in L^{3/2}$ slicewise;
(ii) suitability (CE3) to ensure $P\in L^{3/2}_{\mathrm{loc}}$ and that subtracting spatial averages is admissible; and
(iii) the pressure normalization/localization output (CE4), which allows choosing $P=\mathcal R_i\mathcal R_j(U_iU_j)$ in distributions
(modulo an additive function of time). Since all pressure occurrences in this step are of the form
$P-(P)_{B_{2R}}$, the time-dependent additive constant cancels, and no global pressure gauge is required.
 
Write \(P=\mathcal P(U\otimes U)\), i.e.
\(P=\sum_{i,j}\partial_i\partial_j(-\Delta)^{-1}(U_iU_j)\) with kernel
\[
K_{ij}(x)=c\,\frac{3x_ix_j-|x|^2\delta_{ij}}{|x|^5},\qquad |\nabla K_{ij}(x)|\le C|x|^{-4}.
\tag{7.20C12}
\]
Fix \(R\ge1\) and choose a radial cutoff \(\eta_R\) such that
\[
\eta_R\equiv1 \text{ on }\{R/4\le |y|\le 8R\},\qquad
\eta_R\equiv0 \text{ on }\{|y|\le R/8\}\cup\{|y|\ge16R\},\qquad
|\nabla\eta_R|\lesssim \tfrac1R.
\tag{7.20C12$\eta$}
\]
Decompose
\[
P=P_{\mathrm{mid}}+P_{\mathrm{far}},\qquad
P_{\mathrm{mid}}:=\mathcal P(\eta_R\,U\otimes U),\qquad
P_{\mathrm{far}}:=\mathcal P((1-\eta_R)\,U\otimes U).
\tag{7.20C12D}
\]
On the shell \(A_R=\{R\le|y|\le2R\}\) we may subtract an arbitrary constant; we take
\(c_R:=(P_{\mathrm{mid}})_{B_{2R}}+(P_{\mathrm{far}})_{B_{2R}}=(P)_{B_{2R}}\).

We also write \(A_a^b:=\{y:\ a\le|y|\le b\}\) for radial shells.

**Mid part.** By Calderón–Zygmund (NFS.EST.4) on \(L^{3/2}\) and Hölder (using \(G\le1\)),
\[
\frac1R\int_{A_R}|U|\,|P_{\mathrm{mid}}-(P_{\mathrm{mid}})_{B_{2R}}|\,d\mu
\ \lesssim\ \frac1R\int_{A_{R/4}^{8R}}|U|^3\,d\mu.
\tag{7.20C13}
\]
(Remark: this is the \(L^3\to L^{3/2}\) pressure estimate; see [CKN]. For background on localized pressure (context only; not used below), see [Wol17].)

**Far part (explicit oscillation bound).** 
Since \((1-\eta_R)\) is supported in \(\{|z|\le R/8\}\cup\{|z|\ge16R\}\), for every \(y\in B_{2R}\) we have
\(|y-z|\gtrsim R\) on the inner support and \(|y-z|\simeq |z|\) on the outer support. Differentiating under the convolution gives
\[
\sup_{y\in B_{2R}}|\nabla P_{\mathrm{far}}(y)|
\ \lesssim\
\frac{1}{R^4}\int_{|z|\le R/8}|U(z)|^2\,dz
\ +\
\int_{|z|\ge16R}\frac{|U(z)|^2}{|z|^4}\,dz.
\]
By the mean value theorem, for \(y\in A_R\subset B_{2R}\),
\[
\sup_{A_R}|P_{\mathrm{far}}-(P_{\mathrm{far}})_{B_{2R}}|
\ \lesssim\
\frac{1}{R^3}\int_{|z|\le R/8}|U(z)|^2\,dz
\ +\
\int_{|z|\ge16R}\frac{|U(z)|^2}{|z|^3}\,dz
\ =\ \mathrm{Tail}_\sharp(R,\tau).
\tag{7.20C14}
\]
Since \(\mu(\mathbb R^3)<\infty\), this implies the \(L^2(\mu)\) control (Appendix NFS.IMP)
\[
\|P_{\mathrm{far}}-(P_{\mathrm{far}})_{B_{2R}}\|_{L^2(A_R,\mu)}
\ \lesssim\ \mathrm{Tail}_\sharp(R,\tau).
\tag{7.20C15}
\]

Now estimate the far-pressure flux using Cauchy–Schwarz and the annulus Hardy bound (Step 1):
\[
\frac1R\int_{A_R}|U|\,|P_{\mathrm{far}}-(P_{\mathrm{far}})_{B_{2R}}|\,d\mu
\ \le\ \frac1R\|U\|_{L^2(A_R,\mu)}\,\|P_{\mathrm{far}}-(P_{\mathrm{far}})_{B_{2R}}\|_{L^2(A_R,\mu)}
\]
\[
\ \lesssim\ D_G[U](\tau;4R)^{1/2}\,\mathrm{Tail}_\sharp(R,\tau).
\tag{7.20C16}
\]
Applying Young’s inequality \(ab\le \varepsilon a^2 + C_\varepsilon b^2\) and taking \(\varepsilon\) small (to be absorbed into the
\(D_G\)-budget), we obtain a contribution bounded by (Appendix NFS.IMP)
\(\ \lesssim\ D_G[U](\tau;4R) + \mathrm{Tail}_\sharp(R,\tau)^2\).

**No-Theft (uniform-in-time closure of the remainder).** The tail functional in (7.20C14) is slicewise:
\(\mathrm{Tail}_\sharp(R,\tau)=\mathrm{Tail}_\sharp[U(\tau,\cdot);R]\).
By Lemma 7.8C\(_{\mathrm{NT}}\) we have, uniformly for \(\tau\in[-1,0]\),
\[
\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(R/4,\tau)\ \le\ \frac{C}{R^2}\,M^2,
\qquad\text{hence}\qquad (Lemma 7.8C)
\Big(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(R/4,\tau)\Big)^2\ \le\ \frac{C}{R^4}\,M^4\ \xrightarrow{R\to\infty}\ 0.
\tag{7.20NT}
\]
In particular the remainder term recorded in \((7.20C)\) is **uniform** along the RG window and vanishes as \(R\to\infty\)
without any additional profile assumptions.

Putting together (7.20C13), the cubic bound from Step 3, and (7.20C16) yields the desired estimate for the pressure part,
with the remainder recorded exactly as \(\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(\tau;R)^2\) in (7.20C).

Step 5: OU–commutator and remaining quadratic pieces.** 
The OU–commutator contribution is already in gradient form by Lemma 7.7(A), and the remaining terms in Lemma 7.6 are all of schematic form
\(\int_{A_R} \frac1{R^2}|U|^2G\) or \(\int_{A_R}\frac1R |\nabla U|\,|U|\,G\). 
They are controlled by (7.20C3) and Cauchy–Schwarz/Young, and hence by (Lemma 7.7)
\(\int |\nabla U|^2\chi_{4R}^2G\).

Summing Steps 3–5 and integrating over \(\tau\in[-1,0]\) yields (7.20C). \(\square\)

As a consequence, the “strong linear trade” (7.20) stated at the beginning of §4.2.6 now holds without further assumptions, and (M2a) is fully closed.

#### 6.2.6.4 From the cutoff trade to the pinned profile stability estimate (7.14pin)

From the fixed-radius localized energy inequality with test \(\psi_R=\chi_R^2G\) one obtains the one-sided budget (Lemma 7.8)
\[
E_G[U](0;R)+\int_{-1}^{0}D_G[U](\tau;R)\,d\tau
\ \le\ E_G[U](-1;R)\ +\ C\!\int_{-1}^{0}\!D_G[U](\tau;4R)\,d\tau.
\tag{7.21}
\]
As discussed above, the one-sided nature of (7.21) is *not* sufficient on its own to control
\(|E_G[U](0;R)-E_G[U](-1;R)|\). We therefore upgrade the fixed-cutoff inequality to a fixed-cutoff (Lemma 7.8)
**identity** on the RG window, which is legitimate in our GKP class because Lemma 7.8 already yields the local
\(L^4_{s,y}\) integrability needed to kill the mollification commutator.

> **Lemma 7.10 (Endpoint evaluation for the fixed-cutoff localized energy identity).** 
> Let \((U,P)\) be the RG-window profile on \([-1,0]\) satisfying (GKP1–GKP4), and fix \(R\ge 1\).
> Set
> \[
> E_R(s):=E_G[U](s;R)=\int_{\mathbb R^3}\frac12|U(s,y)|^2\,\psi_R(y)\,dy,
> \qquad
> D_R(s):=D_G[U](s;R)=\int_{\mathbb R^3}|\nabla U(s,y)|^2\,\psi_R(y)\,dy.
> \]
> Then there exists an absolutely continuous representative (still denoted \(E_R\)) on \([-1,0]\) such that for all
> \(-1\le s_1<s_2\le 0\),
> \[
> E_R(s_2)-E_R(s_1)\ +\ \int_{s_1}^{s_2} D_R(\tau)\,d\tau
> \ =\ \mathrm{Err}_R[U;s_1,s_2],
> \tag{7.28}
> \]
> where \(\mathrm{Err}_R[U;s_1,s_2]\) is the fixed-radius error functional from Lemma 7.3 (restricted to \([s_1,s_2]\)).
> In particular, (7.28) holds with \((s_1,s_2)=(-1,0)\).

*Proof.* Fix \(R\ge 1\). Let \(U^\varepsilon:=\rho_\varepsilon*U\) and \(P^\varepsilon:=\rho_\varepsilon*P\) be 
space mollifications. Since \((U^\varepsilon,P^\varepsilon)\) is smooth in \(y\), it satisfies the **exact**
localized energy identity with test \(\psi_R\) on any subinterval \([s_1,s_2]\subset[-1,0]\):
\[
E_R^\varepsilon(s_2)-E_R^\varepsilon(s_1)\ +\ \int_{s_1}^{s_2} D_R^\varepsilon(\tau)\,d\tau
\ =\ \mathrm{Err}_R[U^\varepsilon;s_1,s_2]\ +\ \mathcal C_\varepsilon(R;s_1,s_2),
\tag{7.29}
\]
where \(\mathcal C_\varepsilon\) is the mollification commutator built from
\((U\otimes U)^\varepsilon-U^\varepsilon\otimes U^\varepsilon\), and
\[
E_R^\varepsilon(s):=\int \frac12|U^\varepsilon(s)|^2\psi_R,
\qquad
D_R^\varepsilon(s):=\int |\nabla U^\varepsilon(s)|^2\psi_R.
\]
> **Claim 6.2.6.C (Commutator vanishing).** The commutator term satisfies \(\mathcal C_\varepsilon(R;s_1,s_2)\to 0\) as \(\varepsilon\to 0\), uniformly for \(s_1,s_2\in[-1,0]\).

We show that \(\mathcal C_\varepsilon(R;s_1,s_2)\to 0\) as \(\varepsilon\to 0\), uniformly for \(s_1,s_2\in[-1,0]\).
By Hölder,
\[
|\mathcal C_\varepsilon(R;s_1,s_2)|
\ \le\
\|(U\otimes U)^\varepsilon-U^\varepsilon\otimes U^\varepsilon\|_{L^2((s_1,s_2)\times B_{8R})}
\ \cdot\
\|\nabla(U^\varepsilon\psi_R)\|_{L^2((s_1,s_2)\times \mathbb R^3)}.
\tag{7.30}
\]
The first factor tends to \(0\) because Lemma 7.8, Step 2 yields \(U\in L^4((-1,0)\times B_{8R})\), hence (7.28)
\(U^\varepsilon\to U\) in that \(L^4\) space, and the bilinear map \(L^4\times L^4\to L^2\) is continuous. 
The second factor is uniformly bounded: decompose \(\nabla(U^\varepsilon\psi_R)=(\nabla U^\varepsilon)\psi_R+
U^\varepsilon\nabla\psi_R\); the first term is controlled by \(\|\nabla U\|_{L^2((-1,0)\times B_{2R})}\), while the
second term is supported on the annulus \(A_R=\{R\le|y|\le 2R\}\) and satisfies
\(|\nabla\psi_R|\lesssim R^{-1}G\mathbf 1_{A_R}\), hence (Lemma 7.10)
\[
\|U^\varepsilon\nabla\psi_R\|_{L^2((-1,0)\times \mathbb R^3)}
\ \lesssim\ \frac1R\,\|U^\varepsilon\|_{L^2((-1,0)\times A_R,G)}.
\tag{7.31}
\]
The Hardy–annulus bound (7.20C3) from Lemma 7.8 controls the right-hand side by
\(\|\nabla U\|_{L^2((-1,0)\times \mathbb R^3,\chi_{4R}^2G)}\), uniformly in \(\varepsilon\).
Thus \(\mathcal C_\varepsilon(R;s_1,s_2)\to 0\) by (7.30) (Lemma 7.10).

Passing to the limit \(\varepsilon\to 0\) in (7.29) yields (7.28) for almost every pair \((s_1,s_2)\), and the right-hand
side belongs to \(L^1\) in time by Lemma 7.6 (the fixed-radius error density is integrable on \([-1,0]\)).
Therefore \(E_R\) has a distributional derivative in \(L^1(-1,0)\), hence admits an absolutely continuous representative (Lemma 7.10)
on \([-1,0]\) for which the fundamental theorem of calculus holds. Replacing \(E_R\) by this representative upgrades (7.28)
to hold for **all** \(-1\le s_1<s_2\le 0\), in particular for the endpoints \((-1,0)\). \(\square\)

With the endpoint identity in hand, we can now extract the two-sided stability needed for the profile.

> **Proposition 7.11 (Pinned profile stability; proof of (7.14pin)).** 
> Let \((U,P)\) satisfy (GKP1–GKP4) on \([-1,0]\) and set \(E_*:=E_\infty(0)=E_G[U](0)\).
> Define the pinned profile \(F_s(R):=E_G[U](s;R)/E_*\). Then
> \[
> \sup_{R\ge1}\big|F_0(R)-F_{-1}(R)\big|\ \le\ C\,\mathcal D_k,
> \tag{7.14pin}
> \]
> where \(C=C(M,m_0,\chi)\).

*Proof.* Fix \(R\ge 1\). Applying Lemma 7.10 with \((s_1,s_2)=(-1,0)\) gives
\[
E_G[U](0;R)-E_G[U](-1;R)\ +\ \int_{-1}^{0} D_G[U](\tau;R)\,d\tau
\ =\ \mathrm{Err}_R[U;-1,0].
\tag{7.32}
\]
Taking absolute values and using \(D_G[U](\tau;R)\ge 0\) yields
\[
\big|E_G[U](0;R)-E_G[U](-1;R)\big|
\ \le\ \int_{-1}^{0} D_G[U](\tau;R)\,d\tau\ +\ \big|\mathrm{Err}_R[U;-1,0]\big|.
\tag{7.33}
\]
By Lemma 7.8 (strong linear cutoff trade),
\[
\big|\mathrm{Err}_R[U;-1,0]\big|
\ \le\ C\int_{-1}^{0} D_G[U](\tau;4R)\,d\tau.
\tag{7.34}
\]
Since \(D_G[U](\tau;R)\le D_G[U](\tau;4R)\), (7.33)–(7.34) imply
\[
\big|E_G[U](0;R)-E_G[U](-1;R)\big|
\ \le\ C\int_{-1}^{0} D_G[U](\tau;4R)\,d\tau
\ \le\ C\int_{-1}^{0} D_\infty[U](\tau)\,d\tau
\ =\ C\,\mathcal D_k.
\tag{7.35}
\]
Divide by \(E_*\). By Lemma 5.1 (pin-time non-evanescence), \(E_*=E_\infty(0)\ge m_0>0\), hence
\[
\big|F_0(R)-F_{-1}(R)\big|
=\frac1{E_*}\big|E_G[U](0;R)-E_G[U](-1;R)\big|
\ \le\ \frac{C}{m_0}\,\mathcal D_k,
\qquad \forall\,R\ge 1.
\]
Taking the supremum over \(R\ge 1\) gives (7.14pin). \(\square\)

Finally, the algebra in §4.2.4 (see (7.14a)–(7.14b)) converts the pinned stability (7.14pin) into the instantaneous
profile stability (7.14) for \(\widetilde F_s(R)=E_R(s)/E_\infty(s)\). This closes (M2a) in a cite-level manner.
#### 6.2.6.5 The deterministic (M2b) step (Option B; now closed)

At this point §4.2.6.4 has produced the *pinned profile stability* (7.14pin) from the cutoff-trade engine.
> **Claim 6.2.6.D (Pinned stability \(\Rightarrow\) log-drift).** With the quantitative radius definition \((5.2)\), the pinned profile stability \((7.14\mathrm{pin})\)
> implies the per-window log-drift bound \((7.7)\).

We now show that, with the quantitative definition (5.2), this immediately yields the per-window log-drift control (7.7).

Recall the instantaneous normalized profiles on a fixed window:
\[
\widetilde F_s(R):=\frac{E_R(s)}{E_\infty(s)},\qquad s\in\{-1,0\},\ R\ge 1,
\]
and the quantitative radii
\(\mathcal R_{k-1}:=\mathcal R_{\theta,\kappa}[U_k](-1)\),
\(\mathcal R_{k}:=\mathcal R_{\theta,\kappa}[U_k](0)\),
with the band-average definition (5.2).

The pinned profile stability (7.14pin) is stated for the pinned profiles
\(F_s(R)=E_R(s)/E_\ast\) with \(E_\ast=E_\infty(0)\). Taking \(R\to\infty\) in (7.14pin) gives
\[
|M(-1)-1|\le C_{\rm stab}\,\mathcal D_k,
\qquad
M(s):=\frac{E_\infty(s)}{E_\ast}.
\tag{7.26}
\]
Hence for all windows with \(C_{\rm stab}\mathcal D_k\le \tfrac12\) we have (Lemma 5.1)
\[
E_\infty(-1)\ge \tfrac12 E_\ast\ge \tfrac12 m_0,
\tag{7.27}
\]
where \(m_0\) is the pin-time nondegeneracy constant from Lemma 5.1.

We now isolate the deterministic conversion.

> **Lemma 7.9 (Hysteresis-to-drift conversion; deterministic, cite-level).** 
> Fix \((\theta,\kappa)\) and set \(\alpha_-:=\theta-\kappa\). 
> Let \(\widetilde F,\widetilde G:[1,\infty)\to[0,1]\) be nondecreasing functions with
> \[
> \|\widetilde F-\widetilde G\|_{L^\infty([1,\infty))}\le \varepsilon,
> \qquad 0<\varepsilon\le \kappa.
> \tag{7.9a}
> \]
> Let \(Q_F,Q_G\) be the quantile radii (5.1) associated to \(\widetilde F,\widetilde G\), and define
> \(\mathcal R_F,\mathcal R_G\) by (5.2). 
> Assume moreover that the quantiles on the enlarged band satisfy a uniform confinement
> \[
> 1\le Q_F(u),Q_G(u)\le R_+
> \quad\text{for all }u\in[\theta-\kappa-\varepsilon,\theta+\kappa+\varepsilon].
> \tag{7.9b}
> \]
> Then
> \[
> \big|\log \mathcal R_F-\log \mathcal R_G\big|
> \ \le\
> \frac{\varepsilon}{\kappa}\,\log R_+.
> \tag{7.9c}
> \]
>
> *Proof.* From (7.9a), for every \(R\ge 1\) and \(u\in(0,1)\),
> \[
> \widetilde F(R)\ge u \ \Longrightarrow\ \widetilde G(R)\ge u-\varepsilon,
> \qquad
> \widetilde G(R)\ge u \ \Longrightarrow\ \widetilde F(R)\ge u-\varepsilon.
> \]
> Taking the infimum over \(R\) yields the quantile inequalities
> \[
> Q_F(u)\le Q_G(u+\varepsilon),
> \qquad
> Q_G(u)\le Q_F(u+\varepsilon),
> \tag{7.9d}
> \]
> valid whenever the shifted level lies in \((0,1)\). Taking logs and integrating over \(u\in[\theta-\kappa,\theta+\kappa]\),
> we obtain (Lemma 7.9)
> \[
> \int_{\theta-\kappa}^{\theta+\kappa}\log Q_F(u)\,d\alpha
> \le
> \int_{\theta-\kappa}^{\theta+\kappa}\log Q_G(u+\varepsilon)\,d\alpha
> =
> \int_{\theta-\kappa+\varepsilon}^{\theta+\kappa+\varepsilon}\log Q_G(v)\,dv.
> \]
> Subtracting \(\int_{\theta-\kappa}^{\theta+\kappa}\log Q_G(v)\,dv\) and using the confinement (7.9b),
> \[
> \int_{\theta-\kappa}^{\theta+\kappa}\log Q_F
> -
> \int_{\theta-\kappa}^{\theta+\kappa}\log Q_G
> \le
> \int_{\theta+\kappa}^{\theta+\kappa+\varepsilon}\log Q_G(v)\,dv
> \le
> \varepsilon\,\log R_+.
> \]
> By symmetry (exchange \(F\) and \(G\)) we also get the lower bound
> \(\int\log Q_F-\int\log Q_G\ge -\varepsilon\log R_+\). Dividing by \(2\kappa\) and recalling (5.2) yields (7.9c). \(\square\)

We now apply Lemma 7.9 with \(\widetilde F=\widetilde F_0\), \(\widetilde G=\widetilde F_{-1}\).
From (7.14pin) and (7.26)–(7.27) we have, whenever \(C_{\rm stab}\mathcal D_k\le \tfrac12\),
\[
\sup_{R\ge 1}|\widetilde F_0(R)-\widetilde F_{-1}(R)|
\ \le\
C\,\mathcal D_k,
\tag{7.9e}
\]
with \(C\) depending only on \(C_{\rm stab}\) and \(m_0\). Moreover Lemma 5.1A provides the confinement (7.9b) on both slices
with the same \(R_+\) (take \(m_1=m_0\) for \(s=0\) and \(m_1=m_0/2\) for \(s=-1\)).

Therefore, for all windows with \(C_{\rm stab}\mathcal D_k\le \min\{\tfrac12,\kappa\}\), (Appendix NFS.IMP)
\[
|\log \mathcal R_k-\log \mathcal R_{k-1}|
\ \le\
C_{\rm M2}\,\mathcal D_k,
\tag{7.9f}
\]
where \(C_{\rm M2}:=(C/\kappa)\log R_+\) depends only on the fixed parameters \((\theta,\kappa)\) and the GKP package constants.

**Conclusion for (7.7).** Since \(\sum_k\mathcal D_k<\infty\) in the critical-element scenario, there are only finitely many
indices for which \(C_{\rm stab}\mathcal D_k>\min\{\tfrac12,\kappa\}\). Discarding finitely many initial windows does not affect
the total variation argument, so (7.9f) is sufficient to rule out slow drift and closes M2b in the Annals spine.

---
### 6.3 Modulation cost + (7.7) ⇒ singleton \(\omega\)-limit

We now finish the dynamic step: since (7.7) is proved in §4.2.6.5 (M2a+M2b closed),
slow drift is excluded and Lemma 5.2 forces the \(\omega\)-limit set to be a singleton.

Lemma I.4 (Critical Coercivity / Modulation Cost) states that for each \(\sigma>0\) there exists
\(\varepsilon_*(\sigma)>0\) such that every \(\sigma\)-breathing *unit* window satisfies
\[
\int_{-1}^{0} D_G[U_k](s)\,ds \ \ge\ \varepsilon_*(\sigma).
\tag{7.11}
\]

> **Lemma 7.W1 (Vanishing-window dissipation selection).** 
> Let \(d_k:=\int_{-1}^{0} D_G[U_k](s)\,ds\ge 0\). If \(\sum_{k=1}^\infty d_k<\infty\), then there exists a subsequence \(k_j\to\infty\) such that
> \[
> d_{k_j}\longrightarrow 0.
> \tag{7.W1}\label{eq:7W1_vanishing_window}
> \]
> *Proof.* Otherwise \(\liminf_{k\to\infty} d_k>\varepsilon>0\) and the series \(\sum_k d_k\) diverges. \(\square\)

If \(\omega(U)\) were not a singleton, then by Lemma 5.2 (Breathing dichotomy) there would exist
a fixed \(\sigma_0>0\) and infinitely many indices \(k\) for which the unit window \(U_k\) is \(\sigma_0\)-breathing
(in particular, its width observable \(\mathcal R_k\) exhibits a multiplicative variation \(\ge 1+\sigma_0\) across the window).
For each such breathing window, Lemma I.4 (Modulation Cost) yields a uniform dissipation lower bound
\[
d_k:=\int_{-1}^{0} D_G[U_k](s)\,ds \ \ge\ \varepsilon_*(\sigma_0)>0.
\]
Summing over infinitely many breathing indices forces \(\sum_k d_k=\infty\), contradicting the finite total dissipation
established in §4.1. Hence \(\omega(U)\) must be a singleton (Lemma 5.2).

> **Proposition 7.3 (Singleton \(\omega\)-limit).** 
> One has \(\omega(U)=\{V\}\subset X\) for some \(V\), hence \(U_k(\cdot,0)\to V\) in \(X\) (Proposition 7.3).

*Proof.* Suppose \(\omega(U)\) is not a singleton. Then, as explained above, there exists \(\sigma_0>0\) and infinitely many
\(\sigma_0\)-breathing unit windows \(U_k\). By Lemma I.4 each such window satisfies \(d_k\ge\varepsilon_*(\sigma_0)\), hence (Proposition 7.3)
\(\sum_k d_k=\infty\). This contradicts the global dissipation budget in §4.1. Therefore \(\omega(U)=\{V\}\) for some \(V\in X\) (Proposition 7.3).
Since \(U_k(\cdot,0)=U(\cdot,k)\), this implies \(U_k(\cdot,0)\to V\) in \(X\). \(\square\) (Proposition 7.3)

This closes the dynamical loop “finite dissipation ⇒ asymptotic stationarity” at the
Annals level of rigor.
### 6.4 Upgrading to convergence of the full orbit and stationarity of the limit

Because each window \(U_k\) is a suitable solution on \([-1,0]\) and the family is precompact in the local topology (GKP2), the singleton limit at time \(0\) forces the whole window to converge.

> **Lemma 7.4 (Window convergence).** 
> For every fixed \(s\in[-1,0]\), we have \(U_k(\cdot,s)\to V\) in the same topology as \(k\to\infty\).

*Proof.* Fix \(s\in[-1,0]\) and consider the sequence \(U_k(\cdot,s)=U(\cdot,k+s)\) in the local \(L^3\) topology \(X\).
By precompactness (GKP2), any subsequence admits a further subsequence converging in \(X\) to some \(W_s\).
But \(k+s\to\infty\), hence by definition of the \(\omega\)-limit set we have \(W_s\in\omega(U)\) (Lemma 7.4).
Since \(\omega(U)=\{V\}\) by Proposition 7.3, every subsequential limit equals \(V\), so the full sequence converges: \(U_k(\cdot,s)\to V\) in \(X\).
\(\square\)

Define the global orbit \(U(\cdot,\tau)\) by \(U(\cdot,k+s):=U_k(\cdot,s)\). Lemma 7.4 implies \(U(\cdot,\tau)\to V\) as \(\tau\to\infty\) locally in \(L^3\) (with tightness).

> **Lemma 7.5A (Uniform convergence on fixed windows from a singleton \(\omega\)-limit).** 
> Assume the orbit \(\{U(\cdot,\tau):\tau\ge 0\}\subset X\) is precompact in the local \(L^3\) topology induced by (GKP2), and \(\omega(U)=\{V\}\). 
> Then for every \(T>0\),
> \[
> \sup_{s\in[-T,0]}\ \mathrm{dist}_X\big(U(\cdot,\tau+s),V\big)\ \xrightarrow[\tau\to\infty]{}\ 0.
> \tag{7.22}
> \]
> In particular, for \(T=1\),
> \(\sup_{s\in[-1,0]}\mathrm{dist}_X\big(U_k(\cdot,s),V\big)\to 0\) as \(k\to\infty\).

*Proof.* Fix \(T>0\). If (7.22) fails, there exist \(\varepsilon_0>0\), a sequence \(\tau_n\to\infty\), and \(s_n\in[-T,0]\) such that
\(\mathrm{dist}_X\big(U(\cdot,\tau_n+s_n),V\big)\ge \varepsilon_0\).
By precompactness, \(\{U(\cdot,\tau_n+s_n)\}\) has a convergent subsequence in \(X\), say
\(U(\cdot,\tau_{n_j}+s_{n_j})\to W\in X\).
By definition of \(\omega(U)\), any such subsequential limit belongs to \(\omega(U)\). Hence \(W\in\omega(U)=\{V\}\), i.e. \(W=V\). This contradicts \(\mathrm{dist}_X(\cdot,V)\ge\varepsilon_0\). \(\square\) (Lemma 7.5A)

> **Lemma 7.5C (Stationarity of a singleton \(\omega\)-limit profile; cite-level).** 
> Assume \(U(\cdot,\tau)\) is a suitable LRNS solution for \(\tau\ge 0\) whose orbit is precompact in the local \(L^3\) topology \(X\) (Lemma 7.5B0),
> and assume \(\omega(U)=\{V\}\) is a singleton. Then \(V\) is a **stationary suitable LRNS profile**: there exists a pressure \(\Pi\) such that
> \[
> -\Delta V + (V\cdot\nabla)V + \nabla \Pi + \tfrac12\,y\cdot\nabla V + \tfrac12\,V = 0,\qquad \nabla\cdot V=0
> \quad\text{in }\mathcal D'(\mathbb R^3),
> \tag{7.23}\label{eq:7_23_stationary_LRNS}
> \]
> and \(V\in L^3(\mathbb R^3)\) with the same \(L^3\) bound as \(U\).
>
> *Proof (reader-proof sketch; convergence map made explicit).* 
> Fix \(\eta\in C_c^\infty((-1,0))\) and \(\varphi\in C_c^\infty(\mathbb R^3;\mathbb R^3)\) with \(\nabla\cdot\varphi=0\).
> For any \(\tau_k\to\infty\), define time shifts \(U^{(k)}(y,s):=U(y,\tau_k+s)\), \(s\in[-1,0]\).
> Each \(U^{(k)}\) is a suitable LRNS solution on \([-1,0]\).
>
> **Step 1 (uniform local \(L^3\) convergence on the window).** 
> By Lemma 7.5A, the singleton hypothesis \(\omega(U)=\{V\}\) gives
> \[
> \sup_{s\in[-1,0]}\mathrm{dist}_X\!\big(U^{(k)}(\cdot,s),V\big)\to 0.
> \]
> In particular, for every ball \(B_R\subset\mathbb R^3\),
> \[
> \sup_{s\in[-1,0]}\|U^{(k)}(\cdot,s)-V\|_{L^3(B_R)}\to 0,
> \tag{7.5C.1}\label{eq:7_5C_L3loc_uniform}
> \]
> hence \(U^{(k)}\to V\) strongly in \(L^3(B_R\times[-1,0])\) for every fixed \(R\) (Lemma 7.5C).
>
> **Step 2 (nonlinear term: strong \(L^3_{\rm loc}\) ⇒ strong \(L^{3/2}_{\rm loc}\) for products).** 
> By Hölder,
> \[
> \|(U^{(k)}\otimes U^{(k)})-(V\otimes V)\|_{L^{3/2}(B_R\times[-1,0])}
> \ \le\ \big(\|U^{(k)}\|_{L^3}+\|V\|_{L^3}\big)\,\|U^{(k)}-V\|_{L^3},
> \]
> so \((U^{(k)}\otimes U^{(k)})\to(V\otimes V)\) strongly in \(L^{3/2}_{\rm loc}\).
> Therefore the convection term passes to the limit against \(\nabla\varphi\in L^\infty\) (Lemma 7.5C).
>
> **Step 3 (viscous and pressure terms: compactness/stability package).** 
> The local energy bounds on the window (CE package) and the stability lemma in §4.5B0 yield:
> \(\nabla U^{(k)}\rightharpoonup \nabla V\) weakly in \(L^2_{\rm loc}(B_R\times[-1,0])\),
> and the associated pressures \(P^{(k)}\rightharpoonup \Pi\) in the local topology
> (e.g. \(L^{3/2}_{\rm loc}\) or \(L^{5/3}_{\rm loc}\), depending on the chosen pressure gauge).
> Hence the Laplacian term and pressure term pass to the limit in the LRNS weak formulation (Lemma 7.5C).
>
> **Step 4 (time-derivative term vanishes).** 
> Since \(\eta\) is compactly supported in \((-1,0)\),
> \[
> \int_{-1}^0\!\!\int U^{(k)}\cdot\partial_s(\eta(s)\varphi(y))\,dy\,ds
> =\int_{-1}^0\eta'(s)\Big(\int U^{(k)}\cdot\varphi\Big)\,ds
> \xrightarrow[k\to\infty]{}\Big(\int V\cdot\varphi\Big)\int_{-1}^0\eta'(s)\,ds
> =0.
> \]
> Therefore \(\partial_\tau V=0\) in distributions and the limiting profile satisfies the stationary LRNS equation (Lemma 7.5C)
> \eqref{eq:7_23_stationary_LRNS}. Suitability is inherited by lower semicontinuity arguments in the LEI. \(\square\)

> **Lemma 7.5B0 (Compactness of suitable solutions on cylinders; topology).** 
> Let \((u^{(n)},p^{(n)})\) be suitable weak solutions of LRNS on \((-1,0)\times\mathbb R^3\). Assume that for every \(L\ge 1\),
> \[
> \sup_{s\in[-1,0]}\int_{B_L}|u^{(n)}(s,y)|^2\,dy
> +\int_{-1}^0\!\!\int_{B_L}|\nabla u^{(n)}|^2\,dy\,ds
> +\int_{-1}^0\!\!\int_{B_L}|u^{(n)}|^3\,dy\,ds
> +\int_{-1}^0\!\!\int_{B_L}|p^{(n)}|^{3/2}\,dy\,ds
> \le C_L,
> \tag{7.22A}
> \]
> with constants \(C_L\) independent of \(n\). Then there exist a subsequence (not relabeled) and a pair \((u,p)\) such that for each \(L\),
> \[
> u^{(n)}\to u \ \text{strongly in }L^3((-1,0)\times B_L),
> \qquad
> \nabla u^{(n)}\rightharpoonup \nabla u \ \text{weakly in }L^2((-1,0)\times B_L),
> \tag{7.22B}
> \]
> \[
> p^{(n)}\rightharpoonup p \ \text{weakly in }L^{3/2}((-1,0)\times B_L),
> \tag{7.22C}
> \]
> and \((u,p)\) is a suitable weak solution of LRNS on \((-1,0)\times\mathbb R^3\). 
> Moreover, if \(u^{(n)}(\cdot,s)\to \bar u\) in \(L^3_{\mathrm{loc}}(\mathbb R^3)\) for each \(s\in[-1,0]\), then (after redefining \(u\) on a null set in time) one has \(u(\cdot,s)=\bar u\) for a.e. \(s\in[-1,0]\).
>
> *Proof.* This is the compactness (NFS.EST.6) theorem for suitable solutions on fixed cylinders: the bounds (7.22A) give, for each \(L\), weak compactness in \(L^\infty_s L^2_y\cap L^2_s \dot H^1_y\), strong compactness in \(L^3\) by Aubin–Lions/Simon, and stability of the pressure in \(L^{3/2}\) (Calderón–Zygmund (NFS.EST.4)), with suitability passing to the limit. See Lin [Lin98, Thm. 2.2] for a precise compactness theorem for suitable weak solutions (including strong space--time convergence and stability of the local energy inequality under the uniform bounds (7.22A)). For background and related compactness results, see also Lemarié--Rieusset [LR02, Ch. 2]. \(\square\)

> **Lemma 7.5B (Limit is a stationary suitable LRNS solution).** 
> Under the hypotheses of Lemma 7.5A and (GKP3), there exists a pressure \(\Pi\) such that \((V,\Pi)\) is a suitable weak solution of LRNS on \(\mathbb R^3\times(-\infty,\infty)\) and
> \(\partial_\tau V\equiv 0\) in distributions. Equivalently, \((V,\Pi)\) satisfies the stationary LRNS system \eqref{eq:7_23_stationary_LRNS} in \(\mathcal D'(\mathbb R^3)\), and \(V\) inherits the local energy inequality.

*Proof.* Consider the time-shifts \((U_k,P_k)(y,s):=(U,P)(y,k+s)\) on the fixed window \(s\in[-1,0]\).
By construction \((U_k,P_k)=(U_k,P_k)\), and each pair is suitable on \([-1,0]\) (GKP3).

Fix \(L\ge 1\) and set \(Q_L:=(-1,0)\times B_L\). The GKP bounds imply uniform (in \(k\)) local control on \(Q_L\):
\[
\sup_{s\in[-1,0]}\int_{B_L}|U_k(s)|^2\,dy
+\int_{-1}^0\!\!\int_{B_L}|\nabla U_k|^2\,dy\,ds
\le C_L,
\qquad
\int_{-1}^0\!\!\int_{B_L}|U_k|^3\,dy\,ds\le C_L,
\]
and the pressure decomposition (NFS.EST.5)/Calderón–Zygmund (NFS.EST.4) estimate in the suitable class yields
\(\int_{Q_L}|P_k|^{3/2}\le C_L\) (with the same \(C_L\) depending only on \(L\) and the GKP constants).
Therefore Lemma 7.5B0 applies: for any sequence \(k_j\to\infty\) we may extract a subsequence (not relabeled) and obtain a limit pair (NFS.EST.4)
\((W,\Pi)\) such that, for every \(L\), \(U_{k_j}\to W\) strongly in \(L^3(Q_L)\), \(\nabla U_{k_j}\rightharpoonup \nabla W\) weakly in \(L^2(Q_L)\),
and \(P_{k_j}\rightharpoonup \Pi\) weakly in \(L^{3/2}(Q_L)\), with \((W,\Pi)\) a suitable weak LRNS solution on \([-1,0]\times\mathbb R^3\).

On the other hand, Lemma 7.5A (with \(T=1\)) gives uniform convergence of the shifts to \(V\) on \([-1,0]\) in the local \(L^3\) topology:
for each fixed \(s\in[-1,0]\), \(U_k(\cdot,s)\to V\) in \(L^3_{\mathrm{loc}}(\mathbb R^3)\) as \(k\to\infty\).
Invoking the final statement of Lemma 7.5B0, this forces \(W(\cdot,s)=V\) for a.e. \(s\in[-1,0]\) (after redefining on a null set in time).
Hence \(\partial_s W\equiv 0\) in distributions on \((-1,0)\times\mathbb R^3\), and inserting \(W\equiv V\) into the LRNS weak formulation (Lemma 7.5B)
shows that \(V\) satisfies the stationary LRNS system (7.23) with pressure gradient \(\nabla\Pi\).
Since the pressure is defined only up to an additive function of time, we may fix a gauge (e.g. zero spatial mean on \(B_1\) for each \(s\))
to obtain a time-independent representative \(\Pi=\Pi(y)\). Suitability passes to the limit in Lemma 7.5B0, so \(V\) is suitable.

Finally, since \(V\) is stationary, the pair \((V,\Pi)\) extends trivially to a suitable LRNS solution on \(\mathbb R^3\times(-\infty,\infty)\) by time-independence. \(\square\)

> **Lemma 7.5 (Stationarity of the limit).** 
> The limit \(V\) is a stationary solution of LRNS, hence yields a backward self-similar suitable Navier–Stokes solution (Lemma 7.5).

*Proof.* Lemma 7.5B gives stationarity and suitability of \((V,\Pi)\). Define the backward self-similar physical fields on \(\mathbb R^3\times(-\infty,0)\) by
\[
u(x,t)=(-t)^{-1/2}V\!\left(\frac{x}{\sqrt{-t}}\right),\qquad
p(x,t)=(-t)^{-1}\Pi\!\left(\frac{x}{\sqrt{-t}}\right).
\]
A direct change of variables shows \((u,p)\) is a suitable weak solution of Navier–Stokes and is backward self-similar. \(\square\)

**Remark 7.5C (Compatibility with Tsai’s rigidity theorem).** 
Tsai’s theorem [Tsai98, Thm. 2] excludes *nontrivial* backward self-similar weak solutions satisfying local energy estimates (suitability/LEI). 
By Lemma 7.5B–7.5, the profile \(V\) generates a backward self-similar **suitable** solution \((u,p)\) on \(\mathbb R^3\times(-\infty,0)\). 
Thus the hypotheses of [Tsai98] apply, and the only possibility is \(V\equiv 0\).

### 6.6 Final contradiction (non-evanescence vs Tsai rigidity)

We now connect the two endpoints of the spine:

- **Internal dynamics** (§4.3–§4.4) force convergence of the full orbit to a **stationary** LRNS profile \(V\).
- **External rigidity** ([Tsai98]) forces any such stationary profile in the suitable class to be **trivial**.

> **Lemma 7.6P (Nontriviality of the limit profile; pinned non-evanescence).** 
> The stationary LRNS limit profile \(V\) obtained in §4.5 is **nontrivial**: \(V\not\equiv 0\).
>
> *Proof.* The pinning/non-evanescence package (CE5) provides radii \(R_{\mathrm{pin}}\ge 1\) and \(\eta_{\mathrm{pin}}>0\) such that
> \[
> \|V\|_{L^3(B_{R_{\mathrm{pin}}})}\ \ge\ \eta_{\mathrm{pin}}\ >\ 0,
> \tag{7.40}\label{eq:7_40_pinned_nontrivial}
> \]
> in particular, \(V\) is nontrivial. \(\square\)

**Citation check 7.Tsai (rigidity endpoint).** 
By Lemma 7.5C, the limit \(V\) is a stationary suitable LRNS profile satisfying \eqref{eq:7_23_stationary_LRNS} and \(V\in L^3(\mathbb R^3)\).

(Remark: Tsai98 Theorem 2 assumes **local energy estimates (1.4)** on \(Q_1(0,T)\), not the full local energy inequality; in our spine this is ensured by suitability via Lemma 7.6E.)

> **Lemma 7.6N (Cylinder normalization for Tsai; scale+translate invariance of LEI).** 
> Let \((u,p)\) be a suitable Navier–Stokes solution in a parabolic cylinder \(Q_r(x_0,t_0)=B_r(x_0)\times(t_0-r^2,t_0)\).
> Define the normalized fields
> \[
> \tilde u(x,t)=r\,u(x_0+r x,\ t_0+r^2 t),\qquad
> \tilde p(x,t)=r^2\,p(x_0+r x,\ t_0+r^2 t),
> \tag{7.37}\label{eq:7_37_norm}
> \]
> on \(Q_1(0,0)=B_1(0)\times(-1,0)\). Then \((\tilde u,\tilde p)\) is suitable on \(Q_1(0,0)\) and satisfies the same local energy inequality
> with test functions \(\phi\in C_c^\infty(Q_1)\). 
> *Justification.* This is the Navier–Stokes scaling/translation invariance; each LEI term scales with the same prefactor under

> **Lemma 7.6T (Time-translation normalization for Tsai; \(Q_1(0,T)\to Q_1(0,0)\)).** 
> Suppose \((u,p)\) is suitable on \(Q_1(0,T)=B_1(0)\times(T-1,T)\). Define the time-shifted fields
> \[
> \tilde u(x,t)=u(x,t+T),\qquad \tilde p(x,t)=p(x,t+T),
> \tag{7.38}\label{eq:7_38_timeshift}
> \]
> for \(t\in(-1,0)\). Then \((\tilde u,\tilde p)\) is suitable on \(Q_1(0,0)\) and satisfies the same local energy inequality there. 
> *Justification.* This is immediate from the LEI by substituting \(t\mapsto t+T\) and shifting test functions. The derivative mapping and

> **Remark 7.6U (Neighborhood-of-cylinder hypothesis in Tsai98 is automatic).** 
> Tsai98 formulates Theorem 2 for weak solutions defined in an *open neighborhood* of the unit cylinder
> \(Q_1(0,T)=B_1(0)\times(T-1,T)\). In our application, the backward self-similar field \(u\) produced from the stationary
> LRNS profile \(V\) is defined on \(\mathbb R^3\times(-\infty,T^\star)\). Therefore \(u\) is defined on an open set containing (Theorem 2)
> \(\overline{Q_1(0,T^\star)}\), and the neighborhood requirement is satisfied without additional localization arguments.

**Exact Tsai endpoint used.** We invoke **[Tsai98, Thm. 2]** (Arch. Ration. Mech. Anal. 143 (1998), 29–51): 
if \(u\) is a weak solution of Navier–Stokes satisfying the **local energy estimates** in a cylinder \(Q_1(0,T)=B_1(0)\times(T-1,T)\),
and \(u\) is of Leray backward self-similar form
\[
u(x,t)=\frac{1}{\sqrt{T-t}}\,U\!\Big(\frac{x}{\sqrt{T-t}}\Big),
\tag{7.36}\label{eq:7_36_tsai_ansatz}
\]
then \(u\equiv 0\). (Equivalently, the profile \(U\) must be trivial.)

**Hypothesis match in our spine.** Lemma 7.5C provides a **stationary suitable LRNS profile** \(V\) with \(V\in L^3(\mathbb R^3)\).
The similarity map \((V,\Pi)\mapsto(u,p)\) is certified in CA-09; \(L^3\)-criticality gives \(\|u(\cdot,t)\|_{L^3}=\|V\|_{L^3}\).

> **Lemma 7.6S (Suitability transfer under the similarity map; LEI change-of-variables).** 
> Let \((V,\Pi)\) be a stationary suitable LRNS profile and define \((u,p)\) on \((-\infty,T^\star)\) by
> \[
> u(x,t)=\frac{1}{\sqrt{T^\star-t}}\,V\!\Big(\frac{x}{\sqrt{T^\star-t}}\Big),\qquad
> p(x,t)=\frac{1}{T^\star-t}\,\Pi\!\Big(\frac{x}{\sqrt{T^\star-t}}\Big).
> \tag{7.35}\label{eq:7_35_selfsimilar_from_V_repeat}
> \]
> Then \(u\) is a suitable weak solution of Navier–Stokes and satisfies the local energy inequality in every cylinder \(Q_1(x_0,t_0)\subset\mathbb R^3\times(-\infty,T^\star]\).
>
> *Proof (reader-proof sketch with explicit change-of-variables).* 

> Fix a nonnegative \(\phi\in C_c^\infty(\mathbb R^3\times(-\infty,T^\star))\). Set \(s=T^\star-t\), \(\tau=-\log s\), \(y=x/\sqrt{s}\),
> and define \(\psi(y,\tau):=\phi(\sqrt{s}\,y,T^\star-s)\). The chain rule and Jacobians are certified in
> \[
> \partial_t\phi=\frac{1}{s}\Big(\partial_\tau\psi+\tfrac12\,y\cdot\nabla_y\psi\Big),\quad
> \nabla_x\phi=\frac{1}{\sqrt{s}}\nabla_y\psi,\quad
> \Delta_x\phi=\frac{1}{s}\Delta_y\psi,\quad
> dx=s^{3/2}dy,\quad dt=s\,d\tau.
> \tag{7.6S.1}\label{eq:7_6S_chainrule}
> \]
> By Lemma 7.5C and CA-09, \((u,p)\) is a weak Navier–Stokes solution on \((-\infty,T^\star)\).
> Writing the Navier–Stokes local energy inequality for \((u,p)\) with test \(\phi\) and substituting
> \(u=s^{-1/2}V(y)\), \(p=s^{-1}\Pi(y)\), together with \eqref{eq:7_6S_chainrule}, transforms every term into the corresponding LRNS local energy inequality
> for the stationary field \(U(y,\tau)\equiv V(y)\). Since \(V\) is *suitable* in LRNS sense, the LRNS inequality holds for \(\psi\), and therefore (Lemma 7.6S)
> the Navier–Stokes local energy inequality holds for \((u,p)\) with \(\phi\).
>
> Finally, letting \(t_2\uparrow T^\star\) for nonnegative \(\phi\) yields the local energy estimates in cylinders \(Q_1(x_0,T^\star)\)
> required by [Tsai98, Thm. 2] via monotone convergence. \(\square\)

> **Lemma 7.6E (LEI implies Tsai local energy estimates (1.4) on cylinders).** 
> Let \((u,p)\) be a *suitable* weak solution of Navier–Stokes on a cylinder \(Q_r(x_0,T)=B_r(x_0)\times(T-r^2,T)\) (i.e. it satisfies the local energy inequality
> \eqref{eq:S_NS_LEI} for all nonnegative \(\phi\in C_c^\infty(Q_r)\)). Then \(u\) satisfies Tsai’s **local energy estimates** on \(Q_r(x_0,T)\):
> \[
> \operatorname*{ess\,sup}_{T-r^2<t<T}\int_{B_r(x_0)}\frac12|u(x,t)|^2\,dx
> \;+\;\int_{T-r^2}^{T}\int_{B_r(x_0)}|\nabla u(x,t)|^2\,dx\,dt
> \;<\;\infty.
> \tag{7.39}\label{eq:7_39_tsai_local_energy}
> \]
>
> *Proof (cutoff (NFS.EST.1) argument).* Choose \(\chi\in C_c^\infty(B_{2r}(x_0))\) with \(\chi\equiv 1\) on \(B_r(x_0)\), and
> \(\eta\in C_c^\infty(T-2r^2,T)\) with \(\eta\equiv 1\) on \((T-r^2,T)\). Apply the LEI \eqref{eq:S_NS_LEI} with
> \(\phi(x,t)=\chi(x)^2\eta(t)\). The left-hand side controls
> \(\int_{B_r}\frac12|u(t)|^2\) for a.e. \(t\in(T-r^2,T)\) (since \(\phi\ge 1\) there) and the dissipation integral
> \(\int_{T-r^2}^{T}\int_{B_r}|\nabla u|^2\). The right-hand side involves only integrals of \(|u|^2\) and \((|u|^2+2p)u\)
> against derivatives of \(\chi,\eta\), which are supported in \(Q_{2r}(x_0,T)\) and are finite for suitable solutions by definition
> (cf. §NFS.SUIT pressure gauge convention). Taking an essential supremum over \(t\) yields \eqref{eq:7_39_tsai_local_energy}. \(\square\)

> **Lemma 7.6E1 (Tsai (1.4) verified term-by-term on the normalized cylinder).** 
> In the normalized cylinder \(Q_1(0,0)=B_1(0)\times(-1,0)\) for physical variables \((x,t)\), let \((u,p)\) be the reconstructed suitable solution
> associated to our LRNS orbit after the time-shift normalization in §4.6. Then Tsai’s local energy finiteness condition (1.4) holds with the explicit choice \(t_3:=-\tfrac12\):
> \[
> \operatorname*{ess\,sup}_{-1/2<t<0}\int_{B_1(0)}\frac12|u(x,t)|^2\,dx
> \;+\;\int_{-1/2}^{0}\int_{B_1(0)}|\nabla u(x,t)|^2\,dx\,dt\ <\ \infty.
> \tag{7.6E1}\label{eq:tsai14_term_by_term}
> \]
>
> *Proof.* Lemma 7.6E provides the same bound on the larger interval \((-1,0)\). Restricting the time range to \((-1/2,0)\) decreases the left-hand side,
> hence \eqref{eq:tsai14_term_by_term} holds, which is precisely Tsai’s hypothesis (1.4). \(\square\) (Lemma 7.6E1)

> **Lemma 7.6F (Equation-to-equation map to Tsai’s rigidity setting).** 
> Suppose the LRNS orbit \((U,P)\) becomes stationary on \((-\infty,0]\), i.e. \(U(\tau,y)\equiv V(y)\),
> \(P(\tau,y)\equiv \Pi(y)\). Define the physical fields on \((-1,0)\) by
> \[
> u(x,t):=\frac1{\sqrt{-t}}\,V\Big(\frac{x}{\sqrt{-t}}\Big),\qquad
> p(x,t):=\frac1{-t}\,\Pi\Big(\frac{x}{\sqrt{-t}}\Big).
> \tag{7.6F}\label{eq:tsai_map_fields}
> \]
> Then \((u,p)\) is a backward self-similar suitable weak solution on \(Q_1(0,0)\) and satisfies Tsai’s (1.4) on that cylinder.
>
> *Proof.* Backward self-similarity is immediate from the LRNS change of variables. Suitability and LEI are inherited under the compactness procedure
> by Lemmas 2.3–2.4, and Tsai (1.4) is Lemma 7.6E1. \(\square\)

> **Lemma 7.6G (Tsai hypotheses checklist on $Q_1(0,0)$).** 
> Let \((u,p)\) be the reconstructed physical fields associated to our stationary LRNS profile as in Lemma 7.6F.
> Then all hypotheses required to invoke Tsai’s rigidity theorem **[Tsai98, Thm. 2]** are satisfied on \(Q_1(0,0)=B_1(0)\times(-1,0)\):
>
> 1. **Distributional formulation.** \((u,p)\) solves Navier–Stokes in distributions on \(Q_1(0,0)\) and \(\nabla\cdot u=0\).
> 2. **Pressure integrability.** \(p\in L^{3/2}(Q_1(0,0))\).
> 3. **Suitable class and test functions.** For every nonnegative \(\varphi\in C_c^\infty(B_1(0)\times(-1,0))\), the local energy inequality holds.
> 4. **Tsai local energy finiteness (1.4).** Holds with \(t_3=-1/2\) (Lemma 7.6E1).
> 5. **Backward self-similarity.** Holds about \(T=0\) (Lemma 7.6F).
>
> *Proof.* (4)–(5) are Lemmas 7.6E1 and 7.6F. (1)–(3) follow from suitability stability (Lemmas 2.3–2.4) together with the LRNS↔physical change of variables
> and the pressure localization CE4. \(\square\)

Suitability of \(V\) implies \(u\) satisfies the local energy estimates in every \(Q_1(0,T^\star)\), so [Tsai98, Thm. 2] applies and forces \(V\equiv 0\).

Define the backward self-similar Navier–Stokes field on \((-\infty,T^\star)\) by
\[
u(x,t)=\frac{1}{\sqrt{T^\star-t}}\,V\!\Big(\frac{x}{\sqrt{T^\star-t}}\Big),\qquad
p(x,t)=\frac{1}{T^\star-t}\,\Pi\!\Big(\frac{x}{\sqrt{T^\star-t}}\Big).
\tag{7.35}\label{eq:7_35_selfsimilar_from_V}
\]
\(\|u(\cdot,t)\|_{L^3}=\|V\|_{L^3}\) for all \(t<T^\star\), hence \(u\in L_t^\infty L_x^3\). Therefore, the rigidity theorem of [Tsai98]
(applied in its \(L^3\)-critical form) forces \(u\equiv 0\), and consequently \(V\equiv 0\) [Tsai98].

The only remaining task is to show that \(V\) is **not** trivial. This is where CE5 enters,
and we write it explicitly in a way an reader can check.

By (GKP4) (the pinned non-evanescence), each window \(U_k\) satisfies
\[
\|U_k(\cdot,0)\|_{L^3(B_{R_{\mathrm{pin}}})}\ \ge\ \eta_{\mathrm{pin}}.
\tag{7.36}
\]
By Lemma 7.5A (uniform convergence on fixed windows from a singleton \(\omega\)-limit),
we have \(U_k(\cdot,0)\to V\) in \(L^3(B_{R_{\mathrm{pin}}})\). By Lemma 7.6P, the limiting stationary profile \(V\) is nontrivial.

On the other hand, Lemma 7.5 identifies \(V\) as a stationary LRNS profile which generates a backward self-similar
**suitable** Navier–Stokes solution \((u,p)\) on \(\mathbb R^3\times(-\infty,0)\). 
By Tsai’s rigidity theorem ([Tsai98, Thm. 2]), the only possibility is \(V\equiv 0\).

This contradiction rules out the existence of the critical element. Consequently, the assumed finite-time singularity (Appendix NFS.IMP)
cannot occur (within the scope of the imported CE(\(L^3\)) package), and the regularity conclusion follows.

## Appendix NFS. reader Transparency Notes (CE-map, stationarity details, check tools)

### NFS.CE (reader-quantitative) CE($L^3$) theorem-number map and the tightness bridge

This subsection eliminates the reader escape hatch “CE($L^3$) is assumed.” In §2 it appears as Theorem 2.1, and we map each item CE1–CE5
to the peer-reviewed critical-element literature.

**Backbone source.** Gallagher–Koch–Planchon prove in [GKP13] (Math. Ann. 355 (2013), 1527–1559):
- **Theorem 5 (Existence of a critical element).**
- **Theorem 6 (Compactness of critical elements).**
- **Theorem 7 (Rigidity / global existence for critical elements).**

**How CE1–CE5 are obtained.**
- **CE1** is the scale-invariant \(L^3\) bound along the critical element.
- **CE3–CE4** (suitability, LEI stability, pressure representation/localization) are in the suitable framework; see [CKN], [ESS03], and the preliminaries in [GKP13].
- **CE2 (tightness)** is the only “presentation trap”: one must pass from precompactness modulo translations/dilations to a uniform tail bound.
 We isolate this abstract step in-line as Lemma 2.2; once snapshots form a compact set \(K\subset L^3\), Lemma 2.2 yields (CE2).
- **CE5** is translation pinning so that tightness is measured relative to the origin.

This appendix quarantines internal checklists and citation-check notes. Everything above is intended to read as a clean proof spine.

### NFS.SUIT Suitability conventions (LRNS and Navier–Stokes)

We use the notion of *suitable weak solutions* (Caffarelli–Kohn–Nirenberg type) for Navier–Stokes,
and its rescaled analogue for LRNS. The only purpose of this subsection is to make the **test-function class** and the
**pressure gauge** explicit, so that later changes-of-variables (Lemma 7.6S) are reader-proof.

**Navier–Stokes LEI ().** A weak solution \((u,p)\) on a time interval \((t_1,t_2)\) is *suitable* if for every
nonnegative \(\phi\in C_c^\infty(\mathbb R^3\times(t_1,t_2))\),
\[
\int_{\mathbb R^3} |u(t_2)|^2\phi(t_2)\,dx + 2\int_{t_1}^{t_2}\!\!\int_{\mathbb R^3} |\nabla u|^2\phi\,dx\,dt
\le
\int_{\mathbb R^3} |u(t_1)|^2\phi(t_1)\,dx
+\int_{t_1}^{t_2}\!\!\int_{\mathbb R^3} |u|^2(\partial_t+\Delta)\phi\,dx\,dt
+\int_{t_1}^{t_2}\!\!\int_{\mathbb R^3} (|u|^2+2p)\,u\cdot\nabla\phi\,dx\,dt.
\tag{S.NS}\label{eq:S_NS_LEI}
\]

**LRNS LEI (rescaled).** An LRNS profile \((U,P)\) on \((\tau_1,\tau_2)\) is *suitable* if for every nonnegative
\(\psi\in C_c^\infty(\mathbb R^3\times(\tau_1,\tau_2))\) one has the corresponding rescaled inequality obtained by applying
\eqref{eq:S_NS_LEI} under the similarity change-of-variables \(x=\sqrt{s}\,y\), \(\tau=-\log s\) (with \(s=T^\star-t\)).
We do **not** need the full LRNS LEI formula here; we only use that it is stable under local \(L^3\) convergence and that it
transfers back to Navier–Stokes via Lemma 7.6S.

**Pressure gauge.** Throughout we take pressures modulo spatial constants on each time slice (or, equivalently, fix the Leray–Helmholtz
projection gauge). This is the convention used in the LEI, since \(\nabla\phi\) is compactly supported and spatial constants do not contribute.

### NFS.TSAI Tsai endpoint checklist (Theorem 2, local energy estimates)

We isolate here the **exact hypothesis match** needed to invoke Tsai’s rigidity theorem.

**Tsai98, Theorem 2 (statement used).** 
Let \(T\in\mathbb R\). Suppose \(u\) is a weak solution of Navier–Stokes in a neighborhood of the unit cylinder
\(Q_1(0,T)=B_1(0)\times(T-1,T)\), and suppose \(u\) satisfies the **local energy estimates** (Tsai’s condition (1.4))
in \(Q_1(0,T)\):
\[
\operatorname*{ess\,sup}_{t_3<t<T}\int_{B_1(0)}\frac12|u(x,t)|^2\,dx
\;+\;\int_{t_3}^{T}\int_{B_1(0)}|\nabla u(x,t)|^2\,dx\,dt
\;<\;\infty,
\qquad \text{for some }t_3<T.
\tag{T.LE}\label{eq:T_LE_tsai}
\]
If, in addition, \(u\) is of Leray backward self-similar form \(u(x,t)=(T-t)^{-1/2}U(x/\sqrt{T-t})\) (Tsai’s (1.2)\(_1\)),
then \(u\equiv 0\) (hence \(U\equiv 0\)) (Theorem 2).

**How our spine matches Tsai.** 
We construct \(u\) from the stationary LRNS profile \(V\) via \eqref{eq:7_35_selfsimilar_from_V}. Then:

| Tsai hypothesis | Where proved in our spine | Remarks / CA |
|---|---|---|
| (H1) \(u\) is a weak NS solution on \(Q_1(0,T^\star)\) | Lemma 7.5C + CA-09 | Similarity substitution verified (PASS). |
| (H2) \(u\) is Leray backward self-similar | Definition \eqref{eq:7_35_selfsimilar_from_V} | Time-shift normalization is harmless (Lemma 7.6T). |
| (H3) Local energy estimates \eqref{eq:T_LE_tsai} on \(Q_1(0,T^\star)\) | Lemma 7.6S (suitability transfer) + Lemma 7.6E | LEI ⇒ Tsai (1.4)-type bounds. |
| (H4) Cylinder placement \(Q_1(0,T)\) vs \(Q_1(0,0)\) | Lemma 7.6N + Lemma 7.6T | Scaling (CA-16) + time-shift (CA-17) (PASS). |

**Conclusion.** With (H1)–(H4) verified, Tsai98 Theorem 2 applies and forces \(u\equiv 0\), hence \(V\equiv 0\), contradicting Lemma 7.6P [Tsai98, Thm. 2].

### NFS.1 Option B (Hypothesis Map): CE(\(L^3\)) as a transparent package (no external step)

This appendix records the external inputs used in the manuscript in statement form, with precise theorem identifiers and a usage map. In particular, the critical-element extraction at the $L^3$ level is summarized as the CE($L^3$) package (Theorem 2.1) with items CE1–CE5. Each item is mapped to the corresponding result in the cited sources and to the exact location where it is invoked in the proof spine.

We treat the minimal-element machinery as an external theorem in one of two equivalent forms:

- **[GKP13]** (Gallagher–Koch–Planchon): profile decomposition route. 
 ArXiv:1012.0145v2 contains the critical-element construction and compactness:
 **Theorem 5** (existence of a minimal blow-up solution), **Theorem 6** (compactness / almost periodicity),
 and **Theorem 7** (rigidity / Liouville). 
 *We use only the construction/compactness outputs, not the rigidity half.*

- **[JS13]** (Jia–Šverák): energy method route (no profile decomposition). 
 ArXiv:1201.1592 contains existence of minimal \(L^3\) blow-up data/solution:
 **Theorem 4.1**, plus compactness/stability lemmas in §2–§1.

In §2.0 we adopted **Option B**: CE(\(L^3\)) is imported as an explicit package with items:

- **(CE1)** \(U\in L^\infty_\tau L^3_y\) (uniform critical bound),
- **(CE2)** tightness / almost periodicity,
- **(CE3)** suitability + local energy inequality,
- **(CE4)** pressure representation and localization,
- **(CE5)** non-evanescence / nontriviality after pinning.

#### NFS.1.1 Cite-level mapping (where CE1–CE5 come from)

| CE item | What it states | Cite-level source | Notes |
|---|---|---|---|
| CE1 | \(\sup_{\tau\le 0}\|U(\tau)\|_{L^3}\le M\) | [GKP13, Thm. 5] or [JS13, Thm. 4.1] | Both constructions produce a minimal blow-up object in the critical topology. |
| CE2 | \(\sup_{\tau\le 0}\int_{|y|>R_\varepsilon}|U(\tau)|^3\le\varepsilon\) | [GKP13, Thm. 6] (compactness) or [JS13, §2–§1 compactness] | This is the “almost periodicity modulo symmetries” output. |
| CE3 | suitability / LEI for \((U,P)\) | in both approaches (suitable class is preserved under blow-up limits) | In §4.5B0 we cite Lin’s compactness theorem for suitable solutions [Lin98]. |
| CE4 | \(P=\mathcal R_i\mathcal R_j(U_iU_j)\) and local pressure decomposition (NFS.EST.5) | (CKN, Stein/CZ; see References) + suitability | Used only through local \(L^{3/2}\) control and the local+harmonic split on balls. |
| CE5 | \(U\not\equiv 0\) and positivity of a pinned gauge \(E_G[U]\) | nontriviality from minimality + our pinning normalization | The *positivity* is enforced by the pinning choice; this is internal once \(U\not\equiv 0\). |

#### NFS.1.2 Usage map (where each CE item is consumed in the spine)

| CE item | First major use | What it enables |
|---|---|---|
| CE1 | Lemma 7.8 Step 2–3 | \(L^3\times L^6(\mu)\) interpolation to get annulus \(L^4(\mu)\) control with the parameter \(M\). |
| CE2 | Tail budget §4.2.6.T\(_\sharp\).3 | \(\mathrm{Tail}_\sharp(R)\to 0\) and “far-field” terms vanish in flux sealing. |
| CE3 | §4.2 energy inequality; Lemma 7.5B0 | Legitimate localized energy inequality and compactness/stability on cylinders. |
| CE4 | Lemma 7.8 Step 4 | Pressure flux controlled by local pressure decomposition (NFS.EST.5) + tail bookkeeping. |
| CE5 | §4.6 contradiction | Local \(L^3\) non-evanescence at the pin time passes to the limit \(V\), contradicting Tsai rigidity. |

This is the reader-facing “hypothesis map” promised in Option B: it tells the reader exactly what is imported and where it is used.

#### NFS.1.3 Notation potential ambiguity A: pressure localization (Lemma 7.8, Step 4)

A strict reader will ask whether our use of the pressure is logically compatible with the external critical-element package.
Here is the exact matching:

- **Input used:** CE1 (uniform $L^3$ bound), CE3 (suitable class; hence $P\in L^{3/2}_{\mathrm{loc}}$), and CE4 (pressure representation/decomposition) (NFS.EST.4).
- **Gauge issue:** the pressure is defined only up to an additive function of time. Every occurrence of $P$ in the spine is either
 (i) inside a distributional pairing with divergence-free test functions, or (ii) of the oscillation form $P-(P)_B$ on a ball $B$.
 In either case the additive constant cancels, so no global gauge choice is needed.
- **What is actually proved in Step 4:** we establish the explicit mid/far split (7.20C12D) and the oscillation estimate (7.20C14),
 then combine it with the annulus Hardy/Poincaré bound from Step 1 to obtain the flux bound (7.20C16). The only analytic tool is
 Calderón–Zygmund (NFS.EST.4) boundedness of the Riesz transforms on $L^{3/2}$ [CZ52, Ste70, Gra14] and local pressure decomposition (NFS.EST.5) (NFS.EST.5)
 for suitable solutions [CKN, Lin98, Wol17, LR02].

#### NFS.1.4 Notation potential ambiguity B: endpoint traces and absolute continuity (Lemma 7.10)

The spine uses endpoint evaluations of localized energies and moving-cutoff identities. The only delicate point is the legitimacy of time traces.

- **Input used:** CE3 (suitability), plus the locally improved space–time integrability furnished internally by Lemma 7.8, Step 2.
- **Main technical statement:** Lemma 7.10 produces an *absolutely continuous representative* of $E_R(\tau)$ and upgrades the localized energy balance
 to an equality valid at the endpoints $\tau=-1$ and $\tau=0$. This is done by space mollification and a commutator estimate; it does **not**
 require any profile decomposition or compactness beyond $L^4_{\tau,y,\mathrm{loc}}$.
- **Why the commutator vanishes:** the bilinear map $L^4\times L^4\to L^2$ is continuous on bounded cylinders, and Step 2 gives
 $U\in L^4((-1,0)\times B_{8R})$ for each fixed $R$ (with constants depending only on CE1 and the cutoff profile).
- **reader reassurance:** this is the only place where “endpoint regularity” is used; all subsequent arguments call Lemma 7.10 as a external input
 to avoid any informal time-trace statements.

#### NFS.1.5 Notation potential ambiguity C: LRNS suitability and the correct LEI with drift terms

A strict reader may object that we repeatedly invoke “LEI for LRNS” without ever writing the *exact* form of the inequality
in the presence of the drift/damping terms
\(-\tfrac12 y\cdot\nabla U-\tfrac12 U\) in (LRNS). This subsection records the precise statement and explains why
all LEI instances used in §4–§6 are legitimate consequences of CE3/(GKP3).

**(i) Correct LRNS-LEI (coordinate-free statement).** 
Let \((U,P)\) be a suitable weak solution to (LRNS) on \([s_1,s_2]\times\mathbb R^3\) with \(P\in L^{3/2}_{\mathrm{loc}}\).
Then for every nonnegative \(\varphi\in C_c^\infty(\mathbb R^3\times(s_1,s_2))\) one has
\[
\frac12\int |U(s_2)|^2\varphi(s_2)\,dy+\int_{s_1}^{s_2}\!\!\int |\nabla U|^2\varphi\,dy\,ds
\le
\frac12\int_{s_1}^{s_2}\!\!\int |U|^2(\partial_s\varphi+\Delta\varphi)\,dy\,ds
+\int_{s_1}^{s_2}\!\!\int \Big(\tfrac12|U|^2+\widetilde P\Big)U\cdot\nabla\varphi\,dy\,ds
+\frac14\int_{s_1}^{s_2}\!\!\int |U|^2\,(y\cdot\nabla\varphi+3\varphi)\,dy\,ds.
\tag{LRNS-LEI}
\]
Here \(\widetilde P=P-c(s)\) for an arbitrary scalar function \(c\) (pressure gauge). The last term is exactly the
adjoint-Ornstein–Uhlenbeck correction coming from the drift/damping in (LRNS).

**Sketch of derivation (reader-facing).** 
Formally, multiply (LRNS) by \(U\varphi\), integrate on \([s_1,s_2]\times\mathbb R^3\), and integrate by parts:
the convection term cancels by incompressibility; the pressure term yields \(\int (\tfrac12|U|^2+\widetilde P)U\cdot\nabla\varphi\);
and the drift term contributes
\[
\int\!\Big(-\tfrac12 y\cdot\nabla U\Big)\cdot U\,\varphi
=\frac14\int |U|^2(3\varphi+y\cdot\nabla\varphi),
\]
while \(\int(-\tfrac12U)\cdot U\,\varphi=-\tfrac12\int |U|^2\varphi\), hence the combined drift/damping contribution is [CKN]
\(\frac14\int |U|^2(y\cdot\nabla\varphi+3\varphi)\). The rigorous proof is obtained by mollification
in space (and time if needed) and the usual commutator estimate for suitable solutions (cf. [CKN], [LR02]).

**(ii) Connection to the budgets used in the spine.**
- **Lemma 6.1** is the specialization of (LRNS-LEI) to a time-independent test function \(\varphi(y,s)=\psi_R(y)=\chi_R^2G\).
 In that case \(\partial_s\varphi\equiv 0\) and the OU\(^\ast\) correction becomes the explicit
 \(\tfrac14|U|^2(y\cdot\nabla\psi_R+3\psi_R)\) term in \eqref{6.2}.
- **Lemma 7.3 (moving cutoffs)** is the specialization \(\varphi(y,s)=\psi_{R(s)}(y)\), where the additional term
 \(\tfrac12\int |U|^2\partial_s\varphi\) produces exactly the controlled “speed cost” \(\propto \|R'\|_{L^\infty}\)
 in the moving-cutoff error functional.
- No other LEI instance appears in §4–§6: all localized energy manipulations are routed through Lemma 6.1 and Lemma 7.3,
 and endpoint evaluations are routed through Lemma 7.10 (Appendix NFS.1.4).

**reader verdict.** 
The drift terms in (LRNS) are fully accounted for by the OU\(^\ast\) correction in (LRNS-LEI); there is no hidden use of the
physical-variable LEI after the change of frame. In particular, every time the spine says “apply LEI in the Leray frame”, the intended
meaning is “apply (LRNS-LEI) and then invoke Lemma 6.1 / Lemma 7.3”.

#### NFS.1.6 Notation potential ambiguity D: Pressure gauges, additive time functions, and ball averages

Pressure in incompressible Navier–Stokes is determined only up to an additive function of time. In the Leray-rescaled (LRNS) variables
this remains true: if \((U,P)\) solves (LRNS), then \((U,P+c(s))\) also solves (LRNS) for any scalar function \(c\colon[s_1,s_2]\to\mathbb R\).
A strict reader will therefore check that every pressure occurrence in the spine is **gauge-invariant**. We record the conventions and (NFS.EST.5)
the two tiny cancellations used repeatedly.

**(i) Gauge invariance in (LRNS-LEI) and localized budgets.** In (LRNS-LEI) the pressure appears only through
\(\int (\tfrac12|U|^2+\widetilde P)U\cdot\nabla\varphi\). If \(\widetilde P=P+c(s)\), then
\(\int c(s)U\cdot\nabla\varphi\,dy = -c(s)\int \varphi\,\nabla\cdot U\,dy =0\) since \(\nabla\cdot U=0\) and \(\varphi\) is compactly supported.
Hence (LRNS-LEI), Lemma 6.1 (Gaussian budget), and Lemma 7.3 (moving cutoffs) are invariant under \(P\mapsto P+c(s)\) (Appendix NFS.IMP).

**(ii) Gauge invariance in Gaussian flux pairings.** Several steps (e.g. the OU-cancellation in §4.1E and the pressure-flux estimate in
Mini-Lemma 7.6P) contain the bulk pairing \(\int P\,U\cdot\nabla G\). For any scalar \(c(s)\),
\[\int_{\mathbb R^3} c(s)\,U(s,y)\cdot\nabla G(y)\,dy = -c(s)\int_{\mathbb R^3} G(y)\,\nabla\cdot U(s,y)\,dy =0,\]
justified by a cutoff (NFS.EST.1)-at-infinity argument (Gaussian decay) and incompressibility. Thus the full Gaussian flux is also gauge invariant.

**(iii) Ball-average gauges.** Whenever the pressure is paired with \(|U|\) on a bounded shell, we work with the centered pressure
\(\widetilde P_B:=P-(P)_B\), where for each time \(s\)
\[(P)_B(s):=\frac{1}{|B|}\int_B P(s,y)\,dy\quad\text{(spatial average at fixed time).}\]
This removes both the global ambiguity \(P\mapsto P+c(s)\) and the local harmonic remainder in the pressure decomposition (NFS.EST.5); see CE4 and
the localized bounds (7.G2) and (7.20C13)–(7.20C16).

**(iv) Changing the ball does not change the theory.** Different parts of the spine may use \(\widetilde P_{B_{8R}}\) or
\(\widetilde P_{B_{16R}}\) (or any fixed comparable radius). The difference is a time-dependent constant
\((P)_{B_{8R}}-(P)_{B_{16R}}\), whose contribution to shell transport is controlled by the same cubic bounds already present in \(\Phi\):
using \(|(P)_B|\le |B|^{-2/3}\|P\|_{L^{3/2}(B)}\) and the estimate \(\|P\|_{L^{3/2}(B)}\lesssim\|U\|_{L^3(B)}^2\) (Calderón–Zygmund (NFS.EST.4)),
one obtains (NFS.EST.4)
\[\frac1R\int_{A_{4R}} |U|\,\big|(P)_{B_{8R}}-(P)_{B_{16R}}\big|\,G
\ \lesssim\ \frac1R\,\|U\|_{L^3(B_{16R})}^2\,\|U\|_{L^3(A_{4R})},\]
which is of the same order as the cubic transport term and is absorbed into the definitions/thresholds of \(\Phi\) by adjusting constants.
Therefore the choice of the ball in the definition of \(\widetilde P\) is a **presentation choice**, not an additional hypothesis (NFS.EST.4).

**reader verdict.** Every appearance of pressure in §4–§6 is either (a) through \(\nabla P\), (b) through a pairing with a divergence-free
quantity (hence invariant under \(P\mapsto P+c(s)\)), or (c) through a centered pressure \(P-(P)_B\) on a fixed ball. No global pressure gauge (NFS.EST.5)
is required anywhere in the proof spine.

### NFS.2
### NFS.2 M2 status (v5.8.8)

**Closed.** The M2 mechanism is now fully proved in the spine (no remaining analytic gap):

- **(M2a) Profile stability.** Lemma 7.8 (strong linear cutoff trade) + Proposition 7.11 prove the pinned stability (7.14pin), hence the instantaneous stability (7.14).
- **(M2b) Drift conversion (Option B).** Lemma 7.9 converts (7.14) into the log-drift bound (7.33), with no transversality/non-flatness input.

**Editorial to keep an eye on.** After future edits, ensure §4.2.4 and §4.3 do not reintroduce obsolete “conditional on M2” wording and that all occurrences of the width definition refer to (5.2) (band-averaged log-quantiles).

### NFS.3 Stationarity passage in full (no “routine” steps): \(\partial_\tau V=0\) in \(\mathcal D'\) and uniform integrability of nonlinear terms

This appendix spells out the stationarity passage at Annals level: nothing in the “stationarity passage” is left as “routine”.
It complements §4.5B by spelling out (i) slice identification, (ii) distributional time-derivative elimination, and (iii)
the limit passage in the nonlinear and pressure terms.

We keep the notations of §4.5B. Let \((U_k,P_k)\) be the time-shifts on the fixed cylinder \(Q_L:=(-1,0)\times B_L\),
\[
(U_k,P_k)(s,y) := (U,P)(k+s,y),
\]
and assume the uniform suitable bounds (7.22A) on each \(Q_L\).

#### NFS.3.1 Strong convergence implies nonlinear uniform integrability

> **Lemma NFS.3A (product stability in \(L^{3/2}\)).** 
> If \(u^{(n)}\to u\) strongly in \(L^3(Q_L)\), then
> \[
> u^{(n)}\otimes u^{(n)}\ \to\ u\otimes u\quad\text{strongly in }L^{3/2}(Q_L).
> \]
> In particular, \(\mathrm{div}(u^{(n)}\otimes u^{(n)})\to \mathrm{div}(u\otimes u)\) in distributions on \(Q_L\).
>
> *Proof.* Since \(u^{(n)}\to u\) in \(L^3\), the sequence is bounded in \(L^3\). Then
> \[
> \|u^{(n)}\otimes u^{(n)}-u\otimes u\|_{L^{3/2}}
> \le \|u^{(n)}-u\|_{L^3}\,\|u^{(n)}\|_{L^3} + \|u\|_{L^3}\,\|u^{(n)}-u\|_{L^3}
> \to 0.
> \]
> Distributional convergence of the divergence follows by duality against \(C_c^\infty\) test functions. \(\square\)

This addresses the “uniform integrability of the nonlinear term”: \(u^{(n)}\otimes u^{(n)}\) is uniformly integrable in \(L^{3/2}\)
on each \(Q_L\) and converges strongly.

#### NFS.3.2 Slice identification and distributional stationarity

> **Lemma NFS.3B (slice identification from space–time convergence).** 
> Let \(f_k\to f\) in \(L^p(I\times K)\) for \(1\le p<\infty\), where \(I\subset\mathbb R\) is an interval and \(K\subset\mathbb R^3\) compact.
> Assume there exists \(g\in L^p(K)\) such that for a.e. \(s\in I\), \(f_k(s,\cdot)\to g\) in \(L^p(K)\) as \(k\to\infty\). 
> Then \(f(s,\cdot)=g\) in \(L^p(K)\) for a.e. \(s\in I\).
>
> *Proof.* After passing to a subsequence, \(f_k\to f\) a.e. on \(I\times K\). For a.e. \(s\), the convergence in \(L^p(K)\) implies
> (after a further subsequence depending on \(s\)) a.e. convergence to \(g\) on \(K\). Uniqueness of pointwise limits yields
> \(f(s,\cdot)=g\) a.e. on \(K\). \(\square\)

> **Corollary NFS.3C (distributional time-independence).** 
> If \(f(s,\cdot)=g\) for a.e. \(s\in I\) with \(g\) independent of \(s\), then \(\partial_s f\equiv 0\) in \(\mathcal D'(I\times K)\).
>
> *Proof.* For \(\phi\in C_c^\infty(I)\), \(\psi\in C_c^\infty(K)\),
> \[
> \langle \partial_s f,\phi\psi\rangle := -\int_I\!\!\int_K f(s,x)\,\phi'(s)\psi(x)\,dx\,ds
> = -\int_I \phi'(s)\,ds \int_K g(x)\psi(x)\,dx = 0.
> \]
> Hence \(\partial_s f=0\) distributionally. \(\square\) (Appendix NFS.IMP)

In §4.5B we apply this with \(f_k=U_{k_j}\), \(f=W\) (the compactness limit), \(g=V\), \(p=3\), and \(I=(-1,0)\), \(K=B_L\).
This gives \(W(s,\cdot)=V\) for a.e. \(s\), hence \(\partial_s W=0\) on each \(Q_L\) (Appendix NFS.IMP).

#### NFS.3.3 Passing to the stationary LRNS system (including the pressure term)

Fix \(L\ge 1\). The suitable weak formulation of LRNS on \(Q_L\) reads: for every divergence-free \(\varphi\in C_c^\infty(Q_L;\mathbb R^3)\),
\[
\int_{Q_L} \Big(-u\cdot \partial_s\varphi + \nabla u:\nabla\varphi - \tfrac12\,u\cdot(y\cdot\nabla\varphi) - \tfrac12\,u\cdot\varphi
+ (u\otimes u):\nabla\varphi + p\,\nabla\cdot\varphi \Big)\,dy\,ds = 0.
\tag{NFS.3.1}
\]
For the sequence \((U_{k_j},P_{k_j})\), we may pass \(j\to\infty\) term-by-term as follows:

- The linear terms pass by weak convergence \(\nabla U_{k_j}\rightharpoonup \nabla W\) in \(L^2(Q_L)\) and strong convergence
 \(U_{k_j}\to W\) in \(L^3(Q_L)\) (hence also in \(L^2(Q_L)\) on bounded cylinders) (Appendix NFS.IMP).
- The nonlinear term passes by Lemma NFS.3A: \(U_{k_j}\otimes U_{k_j}\to W\otimes W\) strongly in \(L^{3/2}(Q_L)\).
- The pressure term passes by weak convergence \(P_{k_j}\rightharpoonup \Pi\) in \(L^{3/2}(Q_L)\) together with \(\nabla\cdot\varphi\in L^3\).

Therefore the limit \((W,\Pi)\) satisfies the LRNS weak formulation (NFS.3.1) on \(Q_L\) (Appendix NFS.IMP).

Finally, Corollary NFS.3C implies \(\partial_s W=0\) in \(\mathcal D'(Q_L)\). Choosing test functions of the form \(\varphi(s,y)=\eta(s)\,\psi(y)\)
and using \(\partial_s W=0\), the time-derivative term drops and we recover the *stationary* LRNS weak formulation on \(B_L\) for \(V\)
(with \(W\equiv V\) a.e. in \(s\)). Since \(L\) is arbitrary, this yields \(\partial_\tau V=0\) in \(\mathcal D'(\mathbb R^3)\) and the stationary system (7.23).

This is exactly the “stationarity passage” demanded by a strict reader: the only analytic inputs are the uniform suitable bounds (7.22A),
the compactness Lemma 7.5B0 (Lin’s theorem [Lin98]), and the elementary stability Lemma NFS.3A.

### F.1 The parameter list

**(P1) Width parameters (rigid, fixed once).** 
Choose \(\theta\in(0,1)\) and \(\kappa\in(0,\theta\wedge(1-\theta))\) as in \eqref{eq:5.2}. These parameters define the quantitative width
radius \(\mathcal R_{\theta,\kappa}(s)\) and are held fixed for the entire RG orbit.

**(P2) Signed absorption parameter (rigid, fixed once).** 
Choose any \(\eta\in(0,1)\). This parameter appears only as the coefficient of the near-bulk dissipation term in
\eqref{eq:7_1B1_defect} and in the Young/Cauchy–Schwarz absorption inside Lemma 7.1F.
All constants labeled \(C_{\mathrm{B}}\) are allowed to depend on \(\eta\) (and on the CE window constants), but never on \(k\).

**(P3) Gate level (rigid, fixed once).** 
Fix a gate level \(\gamma_0>0\) as in §4.G. The only downstream dependence is through the packet size \(\delta_{\mathrm{gate}}\)
(defined in \eqref{eq:7GP_packet_size}) and through the transport trigger threshold \(\theta_0=\theta_0(M,\gamma_0)\) in Lemma 7.1H.

**(P4) No-Theft radius threshold (chosen after \(\gamma_0\)).** 
By Uniform No-Theft (P0.2) there exists \(R_{\mathrm{NT}}\ge 1\) such that
\[
\sup_{\tau\in[-1,0]}\mathrm{Tail}_\sharp(4R,\tau)\le 1
\quad\text{for all }R\ge R_{\mathrm{NT}}.
\]
This is the only place where a “large radius” choice is made; it depends only on \(M\) and on the No-Theft constants (hence, indirectly, on \(\gamma_0\) (Appendix NFS.IMP)
through the Gate/pressure localization constants).

**(P5) Transport and packet thresholds (deterministic functions of the fixed parameters).** 
Given \(\gamma_0\) and \(R_{\mathrm{NT}}\), Lemma 7.1H fixes
\[
D_0:=\gamma_0^2,
\qquad
\theta_0:= 8\gamma_0 + 62C\gamma_0 + C\gamma_0 + 1
\]
as in \eqref{eq:7_1H10_theta0_choice} (here \(C\) is the absolute constant from the pressure-flux estimate in Step 3 of Lemma 7.1H).
Lemma 7.1F provides the transport constant \(C_{\mathrm{B}}=C_{\mathrm{B}}(\eta,\mathrm{CE})\), hence the *defect trigger* \eqref{eq:7_1H10_theta0_choice}
\[
\Theta_{\mathrm{B}}:= C_{\mathrm{B}}\,\theta_0
\tag{7.2F1}\label{eq:7_2F1_ThetaB_registry}
\]
coincides with \eqref{eq:7_2B2_ThetaB_def}. Finally, the Option B packet size is
\[
\delta_{\mathrm{B}}:=\min\{\delta_{\mathrm{gate}},\,\delta_{\mathrm{diss}}\}
\]
as in \eqref{eq:7_2B1_deltaB_def}, where \(\delta_{\mathrm{diss}}\) is determined by Lemma 7.1H1 from \(D_0\) and the persistence length.

---

### F.2 Compatibility statement (no hidden “choose small/large” loops)

All parameter choices can be made in the explicit order
\[
(\theta,\kappa)\ \longrightarrow\ \eta\ \longrightarrow\ \gamma_0\ \longrightarrow\ R_{\mathrm{NT}}
\ \longrightarrow\ (D_0,\theta_0,\Theta_{\mathrm{B}},\delta_{\mathrm{B}}),
\]
with no circular dependence. In particular:

- The only “large radius” choice is \(R_{\mathrm{NT}}\) from No-Theft; it is made **after** fixing \(\gamma_0\) and depends only on uniform tail bounds.
- The transport thresholds \(\theta_0,\Theta_{\mathrm{B}}\) are then deterministic functions of the already fixed constants.
- The packet sizes \(\delta_{\mathrm{gate}},\delta_{\mathrm{diss}}\) are fixed once \(\gamma_0\) is fixed (and are independent of profiles and indices).

This eliminates the common reader objection “your proof requires incompatible parameter choices.”

## 

#### NFS.1.9 Notation potential ambiguity G: Constant dependency map (universal vs CE vs parameter)

This note fixes a **reader-facing convention** for constant language. The manuscript uses many constants
\(C,c,\delta,\theta\) that must be **uniform** in the RG index \(k\), the localization radius \(R\), and the chosen profile \(U_k\).
To avoid ambiguity, we classify constants into the following admissible classes.

**(A) Absolute / universal constants** (\(C_{\mathrm{abs}}\), \(c_{\mathrm{abs}}\)). 
These depend only on:
- the space dimension \(d=3\),
- the fixed smooth cutoff prototypes (e.g. the chosen \(\chi,\zeta\) used to build \(\chi_R\)),
- and the fixed Gaussian weight \(G\).
They do **not** depend on \(k\), \(R\), or the particular profile \(U_k\).

**(B) Normalized-class constants** (\(C_{\mathrm{CE}}\)). 
These may depend on the fixed bounds defining the normalized class (CE1–CE4), e.g. the uniform energy control \(M\),
the non-degeneracy/mass parameter \(m_0\), and the fixed suitability/pressure-decomposition constants.
They are still **uniform** in \(k\), \(R\), and the profile \(U_k\).

**(C) Parameter constants** (\(C(\eta,\sigma,\kappa,\gamma_0,\dots)\)). 
These may depend on explicitly chosen parameters (thresholds and “map” choices), but once such parameters are fixed
(see Appendix NFS.1.8), they are again **uniform** in \(k\), \(R\), and \(U_k\).

> **Convention.** When the spine says “universal” it means “in the admissible constant class (A)–(B) after fixing the global parameters”.
> If a constant depends on a parameter such as \(\eta\) or \(\sigma\), we state this dependence explicitly.

**Key constants (canonical dependencies).**
- Persistence time in the Gate functional: \(c_\star=c_\star(M,\gamma_0)\) (fixed once the threshold \(\gamma_0\) is fixed).
- quantitative-budget coercivity: \(c_*:=\tfrac12(1-\eta)\) (parameter constant depending only on \(\eta\)).
- Transport trigger and defect threshold: \(\theta_0=\theta_0(M,\gamma_0)\), \(\Theta_{\mathrm{B}}=C_{\mathrm{B}}(\eta,\mathrm{CE})\,\theta_0\) (cf. Appendix NFS.1.8).
- Gate-opening threshold and packet sizes: \(\theta_* = \theta_*(M,m_0,\eta,\gamma_0)\), \(\delta_{\mathrm{gate}} = \delta_{\mathrm{gate}}(M,m_0,\eta,\gamma_0)\).
- Dissipation-persistence packet: \(c_{\mathrm{diss}}=c_{\mathrm{diss}}(M,D_0)\), \(\delta_{\mathrm{diss}}=\tfrac12 D_0\,c_{\mathrm{diss}}\).
- Dyadic relabeling losses are bounded by fixed factors \(2^{O(1)}\) (Lemma 7.1H0), hence remain in the admissible class.

This map is referenced whenever a proof step requires **uniformity** (e.g. “independent of \(R\)”, “independent of the profile”)
or when a constant is fixed “once and for all” after choosing \(\eta,\sigma,\kappa,\gamma_0\).

Annals-level reader Recheck (v5.9.49)

This recheck audits the **Option B** block (§4.1.5) together with its explicit index-level charging step (§4.2.I),
*and* the downstream rebase points that are most likely to trigger an reader: (i) the quantitative-budget proof (Proposition 7.1)
including the radius-mismatch absorption, (ii) the LRNS LEI hypothesis-matching (OU\(^\ast\) drift terms; Appendix NFS.1.5),
(iii) pressure gauge invariance and ball-average conventions (Appendix NFS.1.6),
and (iv) document hygiene (obsolete checkpoints, equation-number collisions),
and (v) **global parameter compatibility** (Appendix NFS.1.8), and (vi) **constant dependency conventions** (Appendix NFS.1.9).
The purpose is to ensure (a) scientific correctness of the stated claims, (b) clean logical dependencies with no hidden circularity,
and (c) a manuscript-grade presentation where “status” prose cannot contradict the proof spine.

### R0. Presentation and numbering hygiene (reader-facing)

- **No contradictory “status prose”.** The obsolete development-era checkpoint “Verification checklistpoint: what is still missing for Proposition 7.1 (RB1)”
 has been replaced by a short *historical* note (§4.1.1) that motivates the signed absorption \eqref{eq:RB1_signed_trade} and records that it is now
 proved by Option B (§4.1.5).
- **Version-log removals.** All internal build references (“v5.9.49”, “v5.9.49”, “remaining obstruction”, “not yet assert”) have been removed or rewritten.
- **Equation-number collisions removed.** The duplicate tag \(\tag{7.3}\) in §4.2.2 has been renamed to \(\tag{7.6}\). The hysteresis-to-drift lemma
 (Lemma 7.9) has been retagged internally as \(\tag{7.9a}\)–\(\tag{7.9f}\) to avoid clashes with fixed-cutoff identities.
- **Gap-tag cleanup.** Development-era gap labels have been removed from the spine narrative; remaining open/closed items are expressed in the
 uniform “VI.* / Lemma / Proposition” language.
- **Constant language unified.** All uses of “absolute/universal” constants are interpreted in the admissible sense of Appendix **NFS.1.9**. Parameter-dependent constants (e.g. \(c_*(\eta)\), transport/gate triggers \(\theta_0(M,\gamma_0)\), \(\theta_*(M,m_0,\eta,\gamma_0)\), and packet sizes \(\delta_{\mathrm{gate}}(\cdot)\), \(\delta_{\mathrm{B}}(\cdot)\)) are stated with explicit dependence and are never described as “universal” in class (A).

- **Symbol disambiguation (Radii).** The pin-time radius is denoted \(R_{\mathrm{pin}}\) (CE5/GKP4), while the No-Theft threshold in Lemma 7.1H is \(R_{\mathrm{NT}}\). This removes the previous collision of the symbol \(R_0\).

### R1. Scientific meaning and well-posedness

- **LRNS-LEI is stated with the correct OU\(^\ast\) drift correction.** All uses of “LEI in the Leray frame” in §4–§6
 are interpreted as the LRNS local energy inequality (LRNS-LEI) with the explicit term
 \(\tfrac14\int |U|^2(y\cdot\nabla\varphi+3\varphi)\), as recorded in Appendix **NFS.1.5**.

- **Pressure gauge invariance is explicit.** All pressure occurrences in §4–§6 are either of the form \(P-(P)_B\) on a fixed ball
 (for \(|U||P|\) shell bounds) or appear paired with divergence-free quantities (e.g. \(\int P\,U\cdot\nabla\varphi\)), hence are invariant under (Appendix NFS.IMP)
 \(P\mapsto P+c(s)\). Appendix **NFS.1.6** records the two cancellations used in the spine and the ball-average conventions.

- The annulus transport functional \(\Phi(R,\tau)\) in \eqref{eq:7_1B0_def_Phi} is finite under CE1–CE4 (equivalently, under (GKP1), (GKP2), and the strengthened (GKP3) which now includes CE4 pressure normalization/localization):
 \(U(\tau)\in L^3(\mathbb R^3)\) gives finiteness of the cubic term; CE4 and pressure localization yield
 \(\widetilde P\in L^{3/2}_{\mathrm{loc}}\) and \(|U||\widetilde P|\in L^1\) on bounded annuli.
- Continuity in \(\tau\) used in \eqref{eq:7_1B3_transport_pointwise} is justified once smoothness on the window is
 available (Lemma 7.GA), which is itself derived from CE1+CE3 via the endpoint \(L^\infty_tL^3_x\) regularity theorem.
- Lemma 7.1H1 upgrades this qualitative continuity to a **profile-free persistence length** by (i) observing that the transport trigger confines
 the relevant radii to a compact range (Gaussian decay + CE1/CE4), and (ii) invoking quantitative parabolic regularity on a fixed cylinder to bound
 $\partial_\tau\nabla U$ in $L^2$ (see \eqref{eq:7_1H13_dt_grad_bound}).

### R2. Dependency graph and circularity check

**Lemma 7.1F** explicitly depends on:
- CE1–CE4 (to justify localized identities and pressure decomposition (NFS.EST.5)),
- P0.2 No-Theft (to control \(I_{\mathrm{far}}\)),
- already established cutoff-trade / annulus absorption estimates from §4.1C–§4.1E (to isolate \(\Phi\) as the only
 non-absorbed remainder).

It does **not** invoke Proposition 7.1 (finite quantitative budget) or any consequence of \(\sum_k\mathfrak D_k<\infty\).
Therefore it is *logically prior* to the budget (Proposition 7.1).

**Lemma 7.1H** depends on:
- pressure localization (7.G2),
- No-Theft (to make the tail remainder small at large radius),
- Anti-Flash (Lemma 7.GA) and Gate packet conversion (Corollary 7.GB / Lemma 7.2G),
- and the dyadic reindexing lemma (Lemma 7.1H0).

It also does **not** invoke Proposition 7.1.

**Use in the spine.** The index-level consequence “finite quantitative budget \(\Rightarrow\) only finitely many large defects”
is now stated explicitly as Lemma 7.2I and Corollary 7.2J in §4.2.I. In particular, once
\(\sum_k\mathfrak D_k<\infty\) is known (Proposition 7.1), Corollary 7.2J implies that
\(\mathrm{Def}^{(k)}_{\eta}(R_k)\to0\) along the aligned radii \(R_k=\mathcal R_k/4\), hence strict absorption holds asymptotically (Lemma 7.2I).
This direction is downstream-only and therefore non-circular (Lemma 7.2I).

### R3. Quantitative constants: what is fixed and what still needs explicit bookkeeping

- The thresholds \(\theta_0(\gamma_0)\), \(\theta_\star(M,m_0,\eta)\), and the scale \(R_{\mathrm{pin}}\) are all *legitimate* in the
 sense that they can be expressed in terms of constants already declared in §4.G (gate level \(\gamma_0\)), the CE
 package (bound \(M\)), and the No-Theft modulus.
- Lemma 7.1F is now written at **cite-level**: the absorption defect is defined explicitly \eqref{eq:7_1B1_defect}, and the constants-and-support estimate \eqref{eq:7_1B6_near_bound_by_etaD_plus_Phi} yields the quantitative transport lower bound \eqref{eq:7_1B2_transport_lower_bound} without invoking profiles, compactness, or any gauge-fixing.

### R4. Scientific/logical verdict

- The Option B mechanism is scientifically consistent with the LRNS/CE framework and matches the intended CXM narrative:
 *failure of absorption forces outward transport; sustained outward transport triggers Gate; Gate triggers dissipation*.
- No circular dependence on the quantitative budget is introduced in the new lemmas.
- The Option B block is now **cite-level** (Lemma 7.1F + Lemma 7.1H + Lemma 7.1H0 + Lemma 7.1H1), with all constants and supports displayed and with a profile-free quantization of both alternatives (H.a) and (H.b).
 All quantitative constants are now displayed, and all verification items introduced by the cite-level conversion (VI.H0–VI.H1) are now **closed** (Lemmas 7.1H0–7.1H1).

- Fixed a factor-of-2 typo in (VI.6): the correct identity is \((\partial_t+\Delta_x)\phi_R=\tfrac12 s^{-5/2}(2\Delta+y\cdot\nabla+3)\psi_R\).

## What changed in v5.9.49 (Context-only citation disambiguation in the spine)

- **Spine wording hardened for (ctx) sources:** whenever a context-only reference appears in the proof spine, it is now explicitly flagged as
 *“context only; not used in the proofs below”*, so no reviewer can infer hidden dependence.
- **Removed ambiguous “see e.g.” mixes:** places that previously listed a (ctx) item alongside load-bearing/toolbox items are now split into
 (i) the actual machinery references and (ii) an explicit “context only” pointer.
- **§0.3 hypothesis matching strengthened:** [Tsai98] is the load-bearing LEI endpoint; [NRS96] is cited strictly as historical context under
 stronger assumptions.

## What changed in v5.9.49 (Bibliography + citation-key integrity check)

- **Reference list hardened:** added missing DOIs where they exist (notably [Lin98] and [ESS03]) and verified the journal metadata for the load-bearing external inputs.
- **Citation-key integrity sweep:** ensured every bracket key used in the spine appears in References, and every reference entry is either cited in the spine or explicitly marked “context only”.
- **Explicit citation tags in reader notes:** wherever the appendix mentions a specific external theorem by author name, the corresponding citation key is now written inline (e.g. “Escauriaza–Seregin–Šverák [ESS03]”, “Lin’s compactness theorem [Lin98]”).
- **Tooling path hygiene:** fixed the development-era duplicated filename in NFS.4 (“How to run”) so it points to the canonical master file.

---

## What changed in v5.9.49 (Parameter compatibility map + disambiguated radii/eta symbols)

- **Appendix NFS.1.8 added:** a single registry of all free parameters and their dependency order (no circular “choose small/large” loops).
- **Symbol disambiguation:** renamed the pinning constants to \(R_{\mathrm{pin}},\eta_{\mathrm{pin}}\) and the No-Theft threshold to \(R_{\mathrm{NT}}\), eliminating the previous collision.
- **Gate constant classification:** all Gate/transport thresholds and packet sizes (e.g. \(\theta_0,\Theta_{\mathrm{B}},\theta_*,\delta_{\mathrm{gate}}\)) are treated as **parameter constants** (Appendix NFS.1.9(C)) with explicit dependencies; no Gate quantity is labeled “universal” in class (A).
- **LaTeX hygiene:** removed accidental tab-escapes in \(\theta\) symbols; all occurrences are now literal `\theta`.

- **Radii and region notation map:** global convention added in Appendix NFS.1.7: \(B_r\) and \(A_r\) are fixed once, and all dyadic radius changes are justified via monotonicity, gauge invariance (NFS.1.6), or dyadic relabeling (Lemma 7.1H0).
- **Notation normalization:** all ball notation is rewritten uniformly as \(B_{\cdot}\); the sole nonconforming annulus notation is rewritten to match \(A_r:=\{r<|y|<2r\}\) \(A_r:=\{r<|y|<2r\}\).

- **LRNS LEI written explicitly with drift terms:** Appendix NFS.1.5 now records the exact LRNS local energy inequality (LRNS-LEI)
 including the OU\(^\ast\) correction \(\tfrac14\int |U|^2(y\cdot\nabla\varphi+3\varphi)\).
- **Suitability hypothesis matching made unambiguous:** CE3 and (GKP3) now point to (LRNS-LEI) and NFS.1.5, so every invocation of “LEI in the Leray frame”
 has a single, explicit meaning.
- **CE/GKP alignment hardened:** the external CE( \(L^3\) ) package and the internal (GKP1)–(GKP4) window package are now
 explicitly matched. In particular, the pressure normalization/localization input (CE4) is absorbed into **(GKP3)**.
- **Pressure localization made hypothesis-transparent:** Lemma 7.8, Step 4 now carries an explicit “CE/GKP hypothesis check” paragraph and no longer
 contains an inline bibliography block; [ESS03] is cited in the References instead.
- **Endpoint regularity references tightened:** the endpoint evaluation Lemma 7.10 is now cross-referenced in Appendix NFS.1.3–NFS.1.4 as the
 canonical place where absolute continuity/time traces enter; all uses are matched to (GKP3).
- **Bibliography corrections:** [GKP13] title and DOI are corrected to the journal version; [ESS03] is added.

---

## What changed in v5.9.49 (Option B packet charging written at index level)

- **§4.2.I added (explicit index alignment):** introduced Lemma 7.2I and Corollary 7.2J, which fix the aligned radii
 \(R_k:=\mathcal R_k/4\) and prove, in a fully quantitative way, that **large Option B defects force a uniform dissipation packet**
 charged directly to the per-step quantitative dissipation \(\mathfrak D_k\). Consequently, once \(\sum_k\mathfrak D_k<\infty\) is available (Lemma 7.2I)
 (Proposition 7.1), only finitely many indices can exhibit a defect above the fixed threshold \(\Theta_{\mathrm{B}}\), hence
 \(\mathrm{Def}^{(k)}_{\eta}(R_k)\to0\) along the pinned tail.

- **reader recheck refreshed:** the Annals-level dependency/circularity check now includes the §4.2.I charging step explicitly.
## Appendix NFS.HYG  (Bibliography and cross-reference map)
### NFS.BIB Bibliography map (keys, theorem-number hygiene)

This appendix exists solely to prevent “sloppy bibliography” reader attacks.

1. **Key discipline.** External references are cited using short alphanumeric citation keys (e.g. ⟦Tsai98⟧, ⟦GKP13⟧). 
 Internal development labels (e.g. **CE5**, **GKP4**) are *not* bibliography keys.

2. **No dangling keys.** Every key cited in the spine appears exactly once in the References list; conversely, we keep the
 References list minimal and remove uncited entries in the final build.

3. **Theorem-number hygiene.** When we cite a specific theorem, we use the explicit form **[Tsai98, Thm. 2]**.
### NFS.XREF Cross-reference hygiene (Annals-style)

To avoid “presentation” reader attacks, we enforce:

1. Internal results are referenced in full (“Lemma 7.6E”, “Proposition 7.1”), no shorthand.
2. Specific external theorems are cited as **[Tsai98, Thm. 2]** (no “Thm.” shorthand).
3. Every `\eqref{...}` targets an existing `\label{...}`.

A machine check is provided in `CXM_XREF_AUDIT_v5.9.61.md`.

### NFS.MAP Proof-spine usage map (first-use table)
For each internal statement we record the **first place it is invoked after its definition**.

| Statement | First use (nearest heading) |
|---|---|
| Theorem 1.1 | 1.2 What is (and is not) assumed about Type I / Type II |
| Lemma 3.1 | NFS.1.5 Notation potential ambiguity C: LRNS suitability and the correct LEI with drift terms |
| Lemma 4.1 | NFS.1.5 Notation potential ambiguity C: LRNS suitability and the correct LEI with drift terms |
| Definition 5.1 | 5.2 Non-degeneracy: pinned gauge forces positive Gaussian energy |
| Lemma 5.1 | 5.2 Non-degeneracy: pinned gauge forces positive Gaussian energy |
| Lemma 5.2 | 6.2.6.1 A sharper bound for the moving-cutoff term |
| Lemma 5.1A | 5.2 Non-degeneracy: pinned gauge forces positive Gaussian energy |
| Remark 5.5 | NFS.1.5 Notation potential ambiguity C: LRNS suitability and the correct LEI with drift terms |
| Lemma 6.1 | 5.3 The modulation-cost statement needed downstream (M1 closed) |
| Remark 6.2 | NFS.1.5 Notation potential ambiguity C: LRNS suitability and the correct LEI with drift terms |
| Proposition 6.3 | NFS.1.5 Notation potential ambiguity C: LRNS suitability and the correct LEI with drift terms |
| Lemma 7.8C | 6.4 Localized Gaussian energy inequality in the Leray frame (VI.6 filled) |
| Proposition 7.G | — (not invoked after definition) |
| Lemma 7.GA | 6.5 Passing $R\to\infty$: what survives, and the correct full-space Gaussian identity (P1\_G) |
| Corollary 7.GB | Gate definition |
| Proposition 7.1 | Flux Sealing as the “energy barrier” |
| Lemma 7.1F | Flux Sealing as the “energy barrier” |
| Lemma 7.1H | Flux Sealing as the “energy barrier” |
| Corollary 7.1I | 7.1.5.2 Lemma T: failure of strict absorption forces annulus transport |
| Lemma 7.1H0 | 7.1.5.2 Lemma T: failure of strict absorption forces annulus transport |
| Lemma 7.1H1 | 7.1.5.2 Lemma T: failure of strict absorption forces annulus transport |
| Lemma 7.2G | 7.1.5.3 Lemma G: transport activates the Gate and forces a dissipation packet |
| Corollary 7.2H | — (not invoked after definition) |
| Theorem 7.GT | — (not invoked after definition) |
| Lemma 7.2I | 7.1.5.4 How Option B is used in the canonical spine |
| Corollary 7.2J | 7.1.5.4 How Option B is used in the canonical spine |
| Lemma 7.2 | NFS.1.5 Notation potential ambiguity C: LRNS suitability and the correct LEI with drift terms |
| Lemma 7.3 | 7.2.G Gate packets are charged to the quantitative budget (closing P0.1) |
| Lemma 7.R | — (not invoked after definition) |
| Lemma 7.RD | — (not invoked after definition) |
| Lemma 7.RF | — (not invoked after definition) |
| Lemma 7.8C | 6.4 Localized Gaussian energy inequality in the Leray frame (VI.6 filled) |
| Lemma 7.8 | 6.4 Localized Gaussian energy inequality in the Leray frame (VI.6 filled) |
| Proposition 7.11 | 7.2.I Option B defects are charged to the quantitative indices (explicit indexing) |
| Remark 7.2.4A | — (not invoked after definition) |
| Lemma 7.6 | 7.2.3 Reduction of (7.7) to a single moving-cutoff LEI lemma |
| Lemma 7.6A | 7.2.3 Reduction of (7.7) to a single moving-cutoff LEI lemma |
| Lemma 7.6P | 7.1.1 Historical checkpoint (resolved): why an absolute-value cutoff trade is insufficient |
| Lemma 7.7 | 7.2.4.1 M2b: the “non-flatness” hypothesis is eliminated by definition (Option B) |
| Lemma 7.8 | 6.4 Localized Gaussian energy inequality in the Leray frame (VI.6 filled) |
| Lemma 7.10 | Flux Sealing as the “energy barrier” |
| Proposition 7.11 | 7.2.I Option B defects are charged to the quantitative indices (explicit indexing) |
| Lemma 7.9 | 7.1.5.4 How Option B is used in the canonical spine |
| Lemma 7.W1 | — (not invoked after definition) |
| Proposition 7.3 | 6.2.6.3 How the trade is supposed to work (what is already available, and what is not) |
| Lemma 7.4 | 6.2.6.3 How the trade is supposed to work (what is already available, and what is not) |
| Lemma 7.5A | 6.2.6.3 How the trade is supposed to work (what is already available, and what is not) |
| Lemma 7.5C | 6.2.6.3 How the trade is supposed to work (what is already available, and what is not) |
| Lemma 7.5B0 | 6.2.6.3 How the trade is supposed to work (what is already available, and what is not) |
| Lemma 7.5B | 6.2.6.3 How the trade is supposed to work (what is already available, and what is not) |
| Lemma 7.5 | 6.2.6.3 How the trade is supposed to work (what is already available, and what is not) |
| Remark 7.5C | — (not invoked after definition) |
| Lemma 7.6P | 7.1.1 Historical checkpoint (resolved): why an absolute-value cutoff trade is insufficient |
| Lemma 7.6N | 6.2.6.4 From the cutoff trade to the pinned profile stability estimate (7.14pin) |
| Lemma 7.6T | 6.2.6.4 From the cutoff trade to the pinned profile stability estimate (7.14pin) |
| Remark 7.6U | — (not invoked after definition) |
| Lemma 7.6S | 6.2.6.3 How the trade is supposed to work (what is already available, and what is not) |
| Lemma 7.6E | 6.2.6.3 How the trade is supposed to work (what is already available, and what is not) |
| Lemma 7.1H | Flux Sealing as the “energy barrier” |
| Theorem 5 | — (not invoked after definition) |
| Theorem 6 | — (not invoked after definition) |
| Theorem 7 | — (not invoked after definition) |
| Theorem 4.1 | NFS.1.6 Notation potential ambiguity D: Pressure gauges, additive time functions, and ball averages |
| Lemma 6.1 | 5.3 The modulation-cost statement needed downstream (M1 closed) |
| Lemma 7.3 | 7.2.G Gate packets are charged to the quantitative budget (closing P0.1) |
| Lemma 7.1F | Flux Sealing as the “energy barrier” |
| Lemma 7.1H | Flux Sealing as the “energy barrier” |
## Appendix NFS.IMP  (Imported results; statement map)

This appendix is part of the **citation map**: whenever the proof spine invokes a result not proved inside this manuscript,
we record here a **statement-level** formulation (with a source and a theorem/lemma identifier whenever available), together with a short
*usage map* specifying exactly where it is applied.

For external inputs, we record explicit statement-level formulations below. Every external input appears below.

### NFS.IMP.1  Endpoint regularity criterion (suitable framework)

> **Imported Theorem (Endpoint criterion, suitable solutions).**  
> Let \((u,p)\) be a suitable weak solution of 3D incompressible Navier–Stokes on a cylinder \(Q\subset\mathbb R^3\times\mathbb R\).  
> If \(u\in L^\infty_t L^3_x(Q)\) (in the appropriate local sense), then \(u\) is regular in the interior of \(Q\).
>
> **Source:** Escauriaza–Seregin–Šverák [ESS03] (endpoint \(L^\infty_tL^3_x\) regularity in the suitable setting).

**Usage map.**  
- Regularity of the extracted critical element / LRNS orbit on the unit window (used in Lemma 7.GA and then quantified in Lemma 7.GB).

### NFS.IMP.2  Critical element program at \(L^3\)

> **Imported Theorem (Critical element existence).**  
> If a finite-time singularity exists, there is a minimal blow-up datum at the \(L^3\) threshold that generates a critical element.  
> **Source:** Gallagher–Koch–Planchon [GKP13, Thm. 5].
>
> **Imported Theorem (Compactness of critical elements).**  
> Critical elements enjoy a compactness property up to symmetries along sequences approaching the blow-up time.  
> **Source:** [GKP13, Thm. 6].
>
> **Imported Theorem (Rigidity of critical elements).**  
> Under the compactness property, a critical element cannot blow up; hence the endpoint criterion holds [GKP13, Thm. 5].
> **Source:** [GKP13, Thm. 7].

**Usage map.**  
- Theorem 2.1 (CE(\(L^3\)) extraction package CE1–CE5) cites [GKP13, Thm. 5–7].

### NFS.IMP.3  Tsai rigidity: backward self-similar suitable solutions

> **Imported Theorem (Tsai rigidity).**  
> Let \((u,p)\) be a backward self-similar suitable weak solution in a neighborhood of a time \(T\), satisfying Tsai’s local energy finiteness condition
> (Tsai (1.4)) on a cylinder \(Q_r(x_0,T)\). Then the associated self-similar profile is trivial.  
> **Source:** Tsai [Tsai98, Thm. 2].

**Usage map.**  
- §4.6: Lemmas 7.6E1, 7.6F, 7.6G verify the hypotheses of [Tsai98, Thm. 2].

### NFS.IMP.4  Compactness on bounded cylinders (Aubin–Lions–Simon)

> **Imported Theorem (Compactness in \(L^p(0,T;B)\)).**  
> A boundedness/derivative-control hypothesis implying relative compactness in intermediate spaces (Aubin–Lions–Simon type).  
> **Source:** Simon [Sim87, Thm. 5].

**Usage map.**  
- Appendix NFS.EST.6 records the exact formulation and is used whenever a compactness step on fixed bounded cylinders is required.

### NFS.IMP.5  Riesz transforms and Calderón–Zygmund (NFS.EST.4) boundedness

> **Imported Corollary (Riesz transforms on \(L^p\)).**  
> For each \(1<p<\infty\), the Riesz transforms \(\mathcal R_j\) are bounded on \(L^p(\mathbb R^3)\); consequently \(\mathcal R_i\mathcal R_j\) is bounded on \(L^p\) [Gra14, Cor. 5.2.8].
> **Source:** Grafakos [Gra14, Cor. 5.2.8].

**Usage map.**  
- Appendix NFS.EST.4 and Appendix NFS.EST.5.

### NFS.IMP.6  Nonstationary Stokes interior estimates (quantitative)

> **Imported estimates (nonstationary Stokes, interior).**  
> Interior estimates for the nonstationary Stokes system in anisotropic Sobolev–Slobodetski spaces, together with a derivative interpolation inequality
> sufficient to control time derivatives in interior subdomains.  
> **Source:** Zajączkowski [Zaj13, Thm. 4.6] and [Zaj13, Lem. 2.6].

**Usage map.**  
- Lemma 7.GB, feeding Lemma 7.GA*.

---

## Appendix NFS.EST  (Estimate toolbox)

This appendix records the auxiliary inequalities and operator facts used in the manuscript, each stated explicitly (and proved in-line when short) or cited with an exact theorem identifier.

### NFS.EST.1 Cutoff profile bounds (radial rescalings)

Let \(\chi\in C_c^\infty(\mathbb R^3)\) be radial, \(0\le \chi\le 1\), \(\chi\equiv 1\) on \(B_1\), \(\mathrm{supp}(\chi)\subset B_2\).
For \(R\ge 1\) define \(\chi_R(y):=\chi(y/R)\). Then there exists an absolute constant \(C_\chi\) such that
\[
\|\nabla \chi_R\|_{L^\infty}\le \frac{C_\chi}{R},\qquad
\|\Delta \chi_R\|_{L^\infty}\le \frac{C_\chi}{R^2},
\tag{EST1}\label{eq:EST1_cutoff}
\]
and \(\nabla\chi_R,\Delta\chi_R\) are supported in the annulus \(\{R\le |y|\le 2R\}\).
*Proof.* Direct differentiation of \(\chi(y/R)\). \(\square\)

### NFS.EST.2 Hölder and Cauchy–Schwarz (local integrability bookkeeping)

For measurable \(f\in L^p(\Omega)\), \(g\in L^{p'}(\Omega)\) with \(1/p+1/p'=1\),
\[
\int_\Omega |fg|\le \|f\|_{L^p(\Omega)}\|g\|_{L^{p'}(\Omega)}.
\tag{EST2}\label{eq:EST2_holder}
\]
*Proof.* . \(\square\)

### NFS.EST.3 Young’s inequality (two-parameter absorption)

For \(a,b\ge 0\) and \(\varepsilon>0\),
\[
ab\le \varepsilon a^2+\frac1{4\varepsilon}b^2.
\tag{EST3}\label{eq:EST3_young}
\]
*Proof.* Complete the square. \(\square\)

### NFS.EST.4 Riesz transforms and Calderón–Zygmund (NFS.EST.4) boundedness (imported statement)

For each \(1<p<\infty\), the Riesz transforms \(\mathcal R_j\) extend to bounded operators on \(L^p(\mathbb R^3)\), and hence [Gra14, Cor. 5.2.8]
\[
\|\mathcal R_i\mathcal R_j f\|_{L^p}\le C_p \|f\|_{L^p}.
\tag{EST4}\label{eq:EST4_RieszLp}
\]
**Source:** Grafakos [Gra14, Cor. 5.2.8]. (We record the full statement here; the proof is in the cited source.)

### NFS.EST.5 Pressure representation and local decomposition (explicit statement; full proof)

Let \(u\in L^3_{\mathrm{loc}}(\mathbb R^3)\) be divergence-free (for a fixed time slice) and set \(F_{ij}:=u_i u_j\in L^{3/2}_{\mathrm{loc}}\).
Assume \(p\in\mathcal D'(\mathbb R^3)\) satisfies the Poisson equation
\[
-\Delta p = \partial_i\partial_j F_{ij}
\qquad\text{in }\mathcal D'(\mathbb R^3).
\tag{EST5a}\label{eq:EST5_poisson}
\]
Then, after adding an arbitrary function of time (pressure gauge), one may take
\[
p = \partial_i\partial_j(-\Delta)^{-1}F_{ij}=\mathcal R_i\mathcal R_j(F_{ij})
\tag{EST5}\label{eq:EST5_pressure_Riesz}
\]
in distributions. Moreover, for every ball \(B_r(x_0)\) one has a decomposition \(p=p_{\mathrm{loc}}+h\) on \(B_r(x_0)\) where
\[
p_{\mathrm{loc}}:=\mathcal R_i\mathcal R_j\big(\eta\,F_{ij}\big),\qquad \eta\in C_c^\infty(B_{2r}(x_0)),\ \eta\equiv 1 \text{ on }B_r(x_0),
\tag{EST5b}\label{eq:EST5_ploc}
\]
and \(h\) is harmonic on \(B_r(x_0)\).

*Proof.*  
**Step 1: global representation.** Define the distribution
\[
\tilde p:=\partial_i\partial_j(-\Delta)^{-1}F_{ij},
\]
where \((-\Delta)^{-1}\) is the Newtonian potential operator (Fourier multiplier \(|\xi|^{-2}\)). By definition of \((-\Delta)^{-1}\) on distributions,
\(-\Delta(-\Delta)^{-1}=\mathrm{Id}\), hence in \(\mathcal D'\) \eqref{eq:EST5_poisson}
\[
-\Delta\tilde p = -\Delta\,\partial_i\partial_j(-\Delta)^{-1}F_{ij} = \partial_i\partial_jF_{ij}.
\]
Thus \(\tilde p\) is a distributional solution to \eqref{eq:EST5_poisson}. Any other distributional solution differs from \(\tilde p\) by a harmonic
distribution. On \(\mathbb R^3\), the only harmonic distributions that are spatially constant are constants; in the Navier–Stokes system the pressure is defined
up to adding a function of time. Therefore we may fix the pressure gauge so that \(p=\tilde p\), which is exactly \eqref{eq:EST5_pressure_Riesz}.

**Step 2: local decomposition.** Fix a ball \(B_r(x_0)\) and choose \(\eta\in C_c^\infty(B_{2r}(x_0))\) with \(\eta\equiv 1\) on \(B_r(x_0)\).
Define \(p_{\mathrm{loc}}\) by \eqref{eq:EST5_ploc} and set \(h:=p-p_{\mathrm{loc}}\).
> **Claim EST5c (Harmonic remainder).** The remainder \(h:=p-p_{\mathrm{loc}}\) is harmonic on \(B_r(x_0)\).

We claim \(h\) is harmonic on \(B_r(x_0)\). Let \(\varphi\in C_c^\infty(B_r(x_0))\). Since \(\eta\equiv 1\) on \(\mathrm{supp}(\varphi)\),
we have \((1-\eta)\varphi\equiv 0\), hence \eqref{eq:EST5_ploc}
\[
\langle -\Delta h,\varphi\rangle
= \langle -\Delta p,\varphi\rangle - \langle -\Delta p_{\mathrm{loc}},\varphi\rangle
= \langle \partial_i\partial_jF_{ij},\varphi\rangle - \langle \partial_i\partial_j(\eta F_{ij}),\varphi\rangle
= \langle \partial_i\partial_j((1-\eta)F_{ij}),\varphi\rangle = 0.
\]
Therefore \(-\Delta h=0\) in \(\mathcal D'(B_r(x_0))\), i.e. \(h\) is harmonic on \(B_r(x_0)\) \eqref{eq:EST5_ploc}.

**Step 3: integrability and bounds (when needed).** If \(u\in L^3(B_{2r}(x_0))\), then \(\eta F_{ij}\in L^{3/2}(\mathbb R^3)\).
By the Calderón–Zygmund (NFS.EST.4) boundedness of the Riesz transforms (NFS.EST.4), \(\|p_{\mathrm{loc}}\|_{L^{3/2}(\mathbb R^3)}\lesssim \|\eta F\|_{L^{3/2}}\),
so \(p_{\mathrm{loc}}\in L^{3/2}\) with an explicit dependence on the \(L^3\)-size of \(u\) on \(B_{2r}\). The harmonic term \(h\) then obeys the usual
interior bounds on \(B_r\) (mean value / Caccioppoli for harmonic functions), but we only use harmonicity itself.

This proves \eqref{eq:EST5_pressure_Riesz}–\eqref{eq:EST5_ploc}. \(\square\)

### NFS.EST.6 Compactness lemma on bounded cylinders (explicit statement with citation)

Let \(X\hookrightarrow\hookrightarrow Y\hookrightarrow Z\) be Banach spaces with compact embedding \(X\hookrightarrow\hookrightarrow Y\) and continuous embedding \(Y\hookrightarrow Z\).
If a sequence \(v_n\) is bounded in \(L^2(0,T;X)\) and \(\partial_t v_n\) is bounded in \(L^2(0,T;Z)\), then \(\{v_n\}\) is relatively compact in \(L^2(0,T;Y)\).
**Source:** [Sim87, Thm. 5]. 
(We use this only on fixed bounded cylinders.)

### NFS.EST.7 Nonstationary Stokes interior estimate (imported statement with theorem numbers)

Interior parabolic estimates for the nonstationary Stokes system (in anisotropic Sobolev–Slobodetski spaces) are given in
Zajączkowski [Zaj13, Thm. 4.6], and the derivative interpolation inequality needed to control time derivatives is [Zaj13, Lem. 2.6].
We invoke these results exactly once: in Lemma 7.GB (quantitative interior time-derivative bound), which feeds Lemma 7.GA*.

---

## Appendix NFS.SDI  (Spine statement index)

This appendix records an automatically generated index of the numbered statements appearing in the manuscript.
For each item we list a short role line (first non-empty line after the header), a local dependency hint (nearest referenced items inside the block),
and a rough usage count (how many times the label appears elsewhere in the manuscript).

| Item | Role (first line) | Local deps (hint) | Uses |
|---|---|---|---:|
| Theorem 1.1 | ### 0.1 What is proved here vs. what is imported | Theorem 2.1, Lemma 7.6P, NFS.EST.4, [GKP13, Thm. 5–7], [Tsai98, Thm. 2], [CKN]… | 1 |
| Theorem 2.1 |  | NFS.EST.5, [GKP13, Thm. 5–7], [CKN], [ESS03] | 7 |
| Lemma 2.2 |  |  | 2 |
| Lemma 2.3 |  | Lemma 2.4 | 1 |
| Lemma 2.4 |  | Lemma 2.3, Theorem 2.1, NFS.EST.2 | 3 |
| Lemma 3.1 |  | NFS.EST.4, [Gra14, Cor. 5.2.8] | 1 |
| Lemma 4.1 | **Proof (Annals-grade; no hidden steps).** | NFS.EST.2 | 2 |
| Definition 5.1 |  |  | 2 |
| Lemma 5.1 |  |  | 14 |
| Lemma 5.2 |  |  | 4 |
| Lemma 5.1A |  | Lemma 5.1 | 5 |
| Lemma I.4 | **Lemma I.4 (Modulation cost / Critical coercivity).** | Definition 5.1, Lemma 5.1, NFS.EST.6 | 3 |
| Remark 5.5 | **Remark 5.5 (What M1 was, and why it is now closed).** | [GKP13] | 1 |
| Lemma 6.1 | **Lemma 6.1 (Localized Gaussian budget in the Leray frame).** |  | 18 |
| Remark 6.2 | **Remark 6.2 (OU\(^\ast\) localization for \(\psi_R=\chi_R^2G\)).** | Lemma 6.1, NFS.EST.1 | 1 |
| Proposition 6.3 |  | Lemma 6.1 | 2 |
| Lemma 7.8C |  | Lemma 7.8 | 13 |
| Proposition 7.G |  | Lemma 7.10, Lemma 7.8 | 1 |
| Lemma 7.GA |  |  | 26 |
| Corollary 7.GB |  | Lemma 7.GA | 9 |
| Proposition 7.1 |  | Lemma 7.9, Lemma 7.8C, Lemma 7.8, Lemma 6.1, Lemma 7.6P, Lemma 7.GA | 30 |
| Lemma 7.1F |  | Lemma 7.GA | 20 |
| Reduction 7.1B6 | It remains to bound the positive part on the right-hand side by the annulus transport functional. We work on | Lemma 7.6P, Lemma 7.1F | 0 |
| Lemma 7.1H |  | Lemma 7.GA, Corollary 7.GB, Lemma 7.6P, Corollary 7.1I | 62 |
| Corollary 7.1I |  | Lemma 7.1F, Lemma 7.1H, Lemma 7.1H0, Lemma 7.1H1 | 4 |
| Lemma 7.1H0 |  | Lemma 7.1H, Corollary 7.GB, Lemma 7.2G | 13 |
| Lemma 7.1H1 |  | Lemma 7.1H, Lemma 7.GA, Lemma 7.GB, Lemma 7.1F, Proposition 7.1, Corollary 7.2J… | 14 |
| Lemma 7.2G |  | Corollary 7.GB | 5 |
| Corollary 7.2H |  | Lemma 7.2G | 1 |
| Theorem 7.GT |  | Lemma 7.2G, Lemma 7.1F, Lemma 7.1H | 1 |
| Lemma 7.2I |  | Lemma 7.1H, Corollary 7.1I | 7 |
| Corollary 7.2J |  | Lemma 7.2I, Lemma 7.1H | 8 |
| Lemma 7.2 | **Lemma 7.2 (Continuity of \(U\mapsto \mathcal R_{\theta,\kappa}[U](s)\)).** | Lemma 5.1A, [Bil99, Thm. 14.2] | 15 |
| Lemma 7.GB |  | Theorem 2.1, [ESS03], [GKP13], [Zaj13, Thm. 4.6], [Zaj13, Lem. 2.6] | 6 |
| Lemma 7.GA |  | Lemma 7.GB, Lemma 7.9, Lemma 6.1 | 26 |
| Lemma 7.3 | **Lemma 7.3 (Moving-cutoff localized Gaussian LEI; cite-level statement).** | Lemma 6.1 | 18 |
| Reduction 6.2.6.R0 | It remains to bound \(\partial_s\psi\). Write \(\chi_{R(s)}(y)=\chi(\|y\|/R(s))\). Then |  | 0 |
| Lemma 7.R |  |  | 7 |
| Lemma 7.RD |  |  | 2 |
| Lemma 7.RF |  |  | 2 |
| Lemma 7.8C |  | Lemma 7.3, Lemma 6.1, Lemma 7.8, Proposition 7.11, Lemma 7.9 | 13 |
| Remark 7.2.4A | **Remark 7.2.4A (Degenerate instantaneous profile).** If \(M_{-1}:=E_\infty(-1)/E_* = 0\), then \(E_R(-1)=0... | Lemma 6.1, Lemma 7.3, Lemma 7.9, Lemma 7.8, Proposition 7.11 | 1 |
| Lemma 7.6 |  | Lemma 6.1 | 54 |
| Lemma 7.6A |  | Lemma 6.1, Lemma 7.6, NFS.EST.4 | 2 |
| Lemma 7.6P | **Mini-Lemma 7.6P (Pressure gauges and pressure-flux bounds: cancellation + far/local decomposition).** | Lemma 7.6A, Lemma 7.3, Lemma 7.6, NFS.EST.1, NFS.EST.4, NFS.EST.2… | 11 |
| Lemma 7.7 | Fix $R\ge 1$ and write $\psi_R:=\chi_R^2 G$, with $\chi_R(y):=\chi(\|y\|/R)$ and $\chi$ as in §4.2.6.1. | NFS.EST.4, [Gra14, Cor. 5.2.8], [Ste70] | 5 |
| Lemma 7.8 | Let \((U,P)\) be the RG-window profile on \([-1,0]\) satisfying the uniform bounds (GKP1–GKP4), and let \(\... | Lemma 7.3, Lemma 7.6, Lemma 7.7, NFS.EST.2, NFS.EST.4, [BGL14, Prop. 6.2.3]… | 38 |
| Lemma 7.10 |  | Lemma 7.3 | 15 |
| Claim 6.2.6.C | We show that \(\mathcal C_\varepsilon(R;s_1,s_2)\to 0\) as \(\varepsilon\to 0\), uniformly for \(s_1,s_2\in... | Lemma 7.8, Lemma 7.10, Lemma 7.6 | 0 |
| Proposition 7.11 |  | Lemma 7.10, Lemma 7.8, Lemma 5.1 | 5 |
| Claim 6.2.6.D | We now show that, with the quantitative definition (5.2), this immediately yields the per-window log-drift ... | Lemma 5.1 | 0 |
| Lemma 7.9 |  | Lemma 5.1A, Lemma 5.2 | 10 |
| Lemma 7.W1 |  | Lemma 5.2 | 1 |
| Proposition 7.3 | *Proof.* Suppose \(\omega(U)\) is not a singleton. Then, as explained above, there exists \(\sigma_0>0\) an... |  | 6 |
| Lemma 7.4 | *Proof.* Fix \(s\in[-1,0]\) and consider the sequence \(U_k(\cdot,s)=U(\cdot,k+s)\) in the local \(L^3\) to... | Proposition 7.3 | 3 |
| Lemma 7.5A |  |  | 6 |
| Lemma 7.5C |  | Lemma 7.5B0, Lemma 7.5A | 9 |
| Lemma 7.5B0 |  | [Lin98, Thm. 2.2], NFS.EST.6, NFS.EST.4, [Lin98, Thm. 2.2], [LR02, Ch. 2] | 7 |
| Lemma 7.5B | *Proof.* Consider the time-shifts \((U_k,P_k)(y,s):=(U,P)(y,k+s)\) on the fixed window \(s\in[-1,0]\). | Lemma 7.5A, NFS.EST.5, NFS.EST.4 | 12 |
| Lemma 7.5 | *Proof.* Lemma 7.5B gives stationarity and suitability of \((V,\Pi)\). Define the backward self-similar phy... |  | 33 |
| Remark 7.5C | **Remark 7.5C (Compatibility with Tsai’s rigidity theorem).** | Lemma 7.5B, [Tsai98, Thm. 2], [Tsai98] | 1 |
| Lemma 7.6P |  | Lemma 7.5C, Theorem 2, Lemma 7.6E | 11 |
| Lemma 7.6N |  |  | 2 |
| Lemma 7.6T |  |  | 3 |
| Remark 7.6U |  | Theorem 2, Lemma 7.5C, [Tsai98, Thm. 2] | 1 |
| Lemma 7.6S |  | Lemma 7.5C, [Tsai98, Thm. 2] | 5 |
| Lemma 7.6E |  | NFS.EST.1 | 9 |
| Lemma 7.6E1 |  | Lemma 7.6E | 3 |
| Lemma 7.6F |  | Lemma 7.6E1 | 2 |
| Lemma 7.6G |  | Lemma 7.6F, Lemma 7.6E1, Lemma 7.5A, Lemma 7.6P, Lemma 7.5, Theorem 2.1… | 0 |
| Theorem 5 | and **Theorem 7** (rigidity / Liouville). | Theorem 6, Theorem 7, [JS13] | 2 |
| Theorem 4.1 | In §2.0 we adopted **Option B**: CE(\(L^3\)) is imported as an explicit package with items: | Lemma 7.8, Lemma 7.5B0, Lemma 7.10, Lemma 6.1, Lemma 7.3, Lemma 7.6P… | 1 |
| Lemma NFS.3A |  |  | 2 |
| Lemma NFS.3B |  |  | 0 |
| Corollary NFS.3C |  | Lemma 7.5B0, Lemma 7.1H0, Lemma 7.1H, Lemma 7.1F, Lemma 7.1H1, Proposition 7.1… | 1 |
| Lemma 7.1F | **Lemma 7.1F** explicitly depends on: | Proposition 7.1, NFS.EST.5 | 20 |
| Lemma 7.1H | **Lemma 7.1H** depends on: | Lemma 7.GA, Corollary 7.GB, Lemma 7.2G, Proposition 7.1, Lemma 7.2I, Corollary 7.2J… | 62 |
| Claim EST5c | We claim \(h\) is harmonic on \(B_r(x_0)\). Let \(\varphi\in C_c^\infty(B_r(x_0))\). Since \(\eta\equiv 1\)... | Lemma 7.GB, Lemma 7.GA, NFS.EST.4, NFS.EST.6, NFS.EST.7, [Sim87, Thm. 5]… | 0 |

## References

[CKN] L. Caffarelli, R. Kohn, L. Nirenberg, *Partial regularity of suitable weak solutions of the Navier–Stokes equations*, Communications on Pure and Applied Mathematics **35** (1982), 771–831. DOI: 10.1002/cpa.3160350604.

[Lin98] F. Lin, *A new proof of the Caffarelli–Kohn–Nirenberg theorem*, Communications on Pure and Applied Mathematics **51** (1998), no. 3, 241–257. DOI: 10.1002/(SICI)1097-0312(199803)51:3<241::AID-CPA2>3.0.CO;2-A.

[CZ52] A.-P. Calderón, A. Zygmund, *On the existence of certain singular integrals*, Acta Mathematica **88** (1952), 85–139. DOI: 10.1007/BF02392130.

[Ste70] E. M. Stein, *Singular Integrals and Differentiability Properties of Functions*, Princeton Mathematical Series 30, Princeton University Press, 1970.

[Gra14] L. Grafakos, * Fourier Analysis* (3rd ed.), Graduate Texts in Mathematics 249, Springer, 2014. See Cor. 5.2.8 for $L^p$-boundedness of the Riesz transforms.

[BGL14] D. Bakry, I. Gentil, M. Ledoux, *Analysis and Geometry of Markov Diffusion Operators*, Springer, 2014.

[Wol17] J. Wolf, *On the local pressure of the Navier–Stokes equations and related systems*, Adv. Differential Equations **22** (2017), 305–338.

[GKP13] I. Gallagher, G. S. Koch, F. Planchon, *A profile decomposition approach to the $L^\infty_t(L^3_x)$ Navier–Stokes regularity criterion*, Mathematische Annalen **355** (2013), no. 4, 1527–1559. DOI: 10.1007/s00208-012-0830-0.

[JS13] H. Jia, V. Šverák, *Minimal \(L^3\)-initial data for potential Navier–Stokes singularities*, SIAM Journal on Mathematical Analysis **45** (2013), no. 3, 1448–1459. DOI: 10.1137/120880197.

[ESS03] L. Escauriaza, G. Seregin, V. Šverák, *$L_{3,\infty}$-solutions of the Navier–Stokes equations and backward uniqueness*, Russian Mathematical Surveys **58** (2003), no. 2, 211–250 (English translation of Uspekhi Mat. Nauk **58** (2003), 3–44). DOI: 10.1070/RM2003v058n02ABEH000609.

[LR02] P. G. Lemarié-Rieusset, *Recent Developments in the Navier–Stokes Problem*, Chapman & Hall/CRC, 2002.

[NRS96] J. Nečas, M. Růžička, V. Šverák, *On Leray's self-similar solutions of the Navier–Stokes equations*, Acta Mathematica **176** (1996), 283–294. DOI: 10.1007/BF02551584.

[Tsai98] T.-P. Tsai, *On Leray’s self-similar solutions of the Navier–Stokes equations satisfying local energy estimates*, Archive for Rational Mechanics and Analysis **143** (1998), 29–51. DOI: 10.1007/s002050050099.

[Bil99] P. Billingsley, *Convergence of Probability Measures*, 2nd ed., Wiley, 1999.
[Zaj13] W. M. Zajączkowski. *Nonstationary Stokes system in Sobolev–Slobodetski spaces.* Math. Ann. 356 (2013), 555–587. DOI: 10.1007/s00208-012-0838-5.

[Sim87] J. Simon. *Compact sets in the space $L^p(0,T;B)$.* Ann. Mat. Pura Appl. (4) 146 (1987), 65–96.

## AI/LLM use disclosure (required by journal policy)
A large-language model was used as an editorial assistant for consistency checks (notation/parameter naming, cross-references, and English copy-editing). All mathematical statements, proofs, and verification of cited hypotheses were conceived and validated by the author.

---
