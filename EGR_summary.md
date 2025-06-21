
### A Causal‑graph growth

1. **Birth weight**

$$
\boxed{\displaystyle 
\Pr(P_v)=\frac{\gamma^{\,|P_v|}\,
            \exp\!\bigl[-\alpha\sum_{p<q\in P_v}d_{pq}^2/\ell_0^{\,2}\bigr]}
           {\sum_{k=1}^{k_{\max}}\binom{n(t)}{k}\gamma^k\,
            \overline e^{-\alpha\cdots}}}
\tag{A1}
$$

2. **Expected vertex density**

$$
n(t)\;=\;\beta\,t^{\,4}\qquad(\text{coarse time }t)
\tag{A2}
$$

---

### B Local Hilbert algebra and stabiliser code

3. **Vertex algebra**

$$
\mathcal A_v \;=\;M_N(\mathbb C)\;\otimes\;\mathrm{Cliff}(d,1)
\tag{B1}
$$

4. **Stabiliser map (birth projection)**

$$
S_v \;=\;\exp\!\Bigl[i\frac{g}{N}\sum_{p\in P_v}\!
      \bigl(\operatorname{Tr}U_{p\!\to v}+\operatorname{Tr}U_{v\!\to p}^\dagger\bigr)\Bigr]
\tag{B2}
$$

5. **Code distance (hypergraph‑product $U(N)$ code)**

$$
d_{\text{code}}\;=\;c_0\,N^{1/2}\,e^{\xi R_{\text{code}}/\ell_0}
\tag{B3}
$$

---

### C Entanglement → geometry map

6. **Mutual‑information two‑form**

$$
\mathcal I_{vw}=S(\rho_v)+S(\rho_w)-S(\rho_{vw})
\tag{C1}
$$

7. **Coarse‑grained entanglement density**

$$
\overline{\mathcal I}(x)=\frac1{\text{cell}}\sum_{v,w\in\text{cell}}\mathcal I_{vw}
\tag{C2}
$$

8. **Emergent metric**

$$
\boxed{\displaystyle 
g_{\mu\nu}(x)=\frac{4\ell_P^{\,2}}{\ln 2}\;
             \partial_\mu\partial_\nu\!
             \bigl[\;\overline{\mathcal I}(x)\bigr]}
\tag{C3}
$$

---

### D Tensor gauge field

9. **Gauge potential from link fluctuations**

$$
H^{a}{}_{\mu}(x)\;=\;\bigl\langle\operatorname{Tr}
   (T^a U_{v\!\to w})\bigr\rangle_{\!v,w\in\text{cell}}
\tag{D1}
$$

10. **Field‑strength / torsion**

$$
S^{a}_{\mu\nu}=\partial_\mu H^{a}_{\nu}-\partial_\nu H^{a}_{\mu}
\tag{D2}
$$

---

### E Effective action & coupling

11. **Coupling constant scaling**

$$
\kappa\;=\;\frac{N\,\ell_0^{\,2}}{4\pi},
\quad
G_N=\frac{1}{8\pi\kappa}
\tag{E1}
$$

12. **Low‑energy action**

$$
\boxed{\displaystyle 
S_{\text{eff}}=\int d^4x\sqrt{-g}\,
  \Bigl[\tfrac12\kappa\,S^{a}_{\mu\nu}S_{a}^{\;\mu\nu}
        +\Lambda_{\text{ent}}\Bigr]}
\tag{E2}
$$

13. **Entanglement cosmological constant**

$$
\Lambda_{\text{ent}}=\frac{\ln 2}{R_{\text{code}}^{\,2}}
\tag{E3}
$$

---

### F Emergent field equations

14. **Teleparallel Einstein equations**

$$
G_{\mu\nu}+\Lambda_{\text{ent}}g_{\mu\nu}=8\pi G_N\,T_{\mu\nu}^{\text{(edge)}}
\tag{F1}
$$

15. **Matter edge‑mode stress tensor**

$$
T_{\mu\nu}^{\text{(edge)}}=
  \frac{-2}{\sqrt{-g}}\,
  \frac{\delta S_{\text{edge}}}{\delta g^{\mu\nu}}
\tag{F2}
$$

---

### G UV behaviour and running

16. **One‑loop beta function (symbolic)**

$$
\beta_{g}=-\frac{b_1}{N}\,g^3+\mathcal O\!\left(\frac{1}{N^2}\right)
\tag{G1}
$$

17. **Running Newton constant**

$$
G(k)=\frac{G_0}{1+\frac{\beta_1}{N}\ln(k/k_0)}
\tag{G2}
$$

---

### H Phenomenological corrections

18. **Modified Newton potential (sub‑mm)**

$$
\Phi(r)=-\frac{G_0 M}{r}\,
         \bigl[1+\alpha e^{-r/R_{\text{code}}}\bigr],
\quad
\alpha\sim\frac1N
\tag{H1}
$$

19. **Graviton dispersion**

$$
\omega^2=k^2\Bigl[1+\frac{c_2}{N}(\ell_P k)^2+\dots\Bigr]
\tag{H2}
$$

---

### I Black‑hole thermodynamics

20. **Logical‑qubit entropy**

$$
S_{\text{BH}}=\frac{A}{4\ell_P^{\,2}}\;\ln N
\tag{I1}
$$

---

### J Spectral‑dimension flow (numerical result)

21. **Return probability & flow**

$$
D_s(\sigma)=-2\,\frac{d\ln P(\sigma)}{d\ln\sigma},
\quad
P(\sigma)=\text{Tr}\,e^{\sigma\Delta}
\tag{J1}
$$

with

$$
\lim_{\sigma\gg\ell_0^{\,2}}D_s=4,
\qquad
\lim_{\sigma\ll\ell_0^{\,2}}D_s=2
\tag{J2}
$$

---

These 21 equations constitute the spine of EGR—from microscopic birth rules to macroscopic gravity, UV running, and black‑hole entropy.
