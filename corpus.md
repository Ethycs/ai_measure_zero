Catastrophes are generic in smooth function families.  This implies
Catastrophic (stable) maps are dense in function space and in standard NN families; with smooth parameterizations, non-catastrophic parameters are measure zero.

We show that for broad smooth-activation neural network families, catastrophic (Thom–Mather stable) maps form an open-dense (residual) subset of function space and occur for almost every parameter (the unstable set is meagre and Lebesgue-null under absolutely continuous priors). We further obtain finite catastrophic $\varepsilon$-nets for compact parameter images and prove a data-manifold restriction theorem: generic stability persists when restricting to the data manifold. These results clarify that expressivity alone cannot ensure robustness and formalize the necessity of geometry-aware training biases.

The high level flow is that under theory, the trained network is a perfectly smooth function that is arbitrarily close to a network containing a catastrophe (best case). We that show that under absolutely continuous randomness and finite precision the network is almost surely being put in a regime with elementary catastrophes and beyond. 

A Catastrophe is the technical definition for generic and structurally stable discontinuities that emerge in dynamical systems. They are not defects or errors, they are deep geometrical features of the system. 
### Core contributions

1. **Parametric almost everywhere stability (anchor theorem):** residual/open-dense set of parameters yields stable maps; null/meagre complement.
    
2. **Finite catastrophic $\varepsilon$-nets:** existence inside compact model images.
    
3. **Data-manifold restriction:** stability genericity along $M\subset K$.
    
4. **ReLU compatibility:** smooth-approximation clause; optionally a PL analogue as a remark.
    

### Theorem skeletons

- **Thm B1 (Parametric a.e. stability).**  
    With smooth non-polynomial activation, compact $K$, and Mather’s nice dimensions, there exists residual $\Theta_{\mathrm{stab}}\subset\Theta$ such that fθf_\thetafθ​ is stable for $\theta\in\Theta_{\mathrm{stab}}$​. For any absolutely continuous prior on $\Theta$, $\Theta\setminus\Theta_{\mathrm{stab}}$​ has measure zero.
    
- **Cor B1.1 (Density in the family).**  
    Catastrophic networks are dense in $\Phi(\Theta)$ (every network is arbitrarily close to a catastrophic one).
    
- **Thm B2 (Finite catastrophic $\varepsilon$-net).**  
    If $\Theta$ is compact and $\Phi$ continuous, then for all $\varepsilon>0$ there exists a **finite** set of catastrophic networks $\{g_i\}$​ such that $\forall f\in\Phi(\Theta)\ \exists i:\|f-g_i\|_\infty<\varepsilon$.
    
- **Thm B3 (Data-manifold restriction).**  
    For a $C^r$ submanifold $M\subset K$(dimension $d$), and appropriate dimension conditions on $(d,m)$ the restriction $f_\theta|_M$​ is stable for a residual set of parameters.
    
- **Remark B4 (ReLU).**  
    For any ReLU network $g$ and $\delta>0$ there exists a smooth-activation $f$ with $\|f-g\|_\infty<\delta$; by Thm B1, $f$ can be taken stable. Hence ReLU families lie arbitrarily close (in $C^0$) to catastrophic smooth maps.
    

 Assertion: the smooth case is actually the best case with the non-smooth case being worse for catastrophes and unpredictable with classical catastrophe theory in some terms. Our work suggests that the situation is no better for arbitrary non-smooth functions but does not have the predictability of the smooth theory. 

In suitable (Mather “nice”) dimensions, the set of **stable (Thom–Mather)** maps is **open and dense** in $C^r(K,\mathbb R^m)$. Therefore, for any universal-approximation class $\mathcal A\subset C(K,\mathbb R^m)$ that is dense in $C(K,\mathbb R^m)$, **catastrophic maps are dense in $\mathcal A$**: every network can be approximated arbitrarily well by a catastrophic one.

*Clarify that our theorem is more general and does not need the "nice" maps*

While a stable (catastrophic) network has a singular set $\Sigma(f)$ that is a Whitney–stratified subset of codimension $\ge 1$ (hence measure zero and nowhere dense in the input domain), the class of such networks is open and dense in the hypothesis space; thus every network can be approximated arbitrarily well by a catastrophic one.

## Stronger, parametric “almost surely” version (under a mild sampling assumption)

If $\Theta\subset\mathbb{R}^P$ is finite-dimensional and your initialization/perturbations define a measure **absolutely continuous** w.r.t. Lebesgue on $\Theta$, then by **parametric transversality** the set of **non-stable** parameters has **measure zero**.  
**Hence, with probability 1 the trained network itself is catastrophic** (not just ε-close), regardless of the achieved training error.  
_(Caveat: an optimizer that concentrates on a lower-dimensional subset can evade this; that requires an explicit bias assumption.)_

**Knife-edge Lemma (parametric).**  
Let $\Delta$ be the non-stable parameter set for a smooth-activation NN family. Then $\Delta$ is a Whitney-stratified subset of **codimension ≥ 1**.  
(i) For any $\theta\in\Delta$, the set of directions $v$ for which $\theta+t v\in\Delta$ for all sufficiently small $t$ has **measure zero** on the unit sphere; hence a random small perturbation leaves $\Delta$ with probability 1, yielding a **catastrophic** network.  
(ii) For any $\theta\notin\Delta$, there exists $\delta>0$ such that the ball $B(\theta,\delta)\cap\Theta$ contains **only** catastrophic networks.

**Knife-edge ⇒ sensitivity of vulnerability.**  
Because the non-stable set in parameter space is thin, **small, generic parameter nudges** tend to create/annihilate folds or move the boundary, causing **sudden changes in margin** for some inputs. That explains the empirically observed brittleness to tiny retraining/seed changes.

For expressive networks, **almost any** nearby parameter choice is a stable/catastrophic map whose **robust risk at small ε grows linearly** with a coefficient that **inflates** where boundary gradient is small—often the case near elementary catastrophes along the data manifold.

The nudge:

“Catastrophes are **not dense in input space**, but they are **structurally inevitable in parameter space under finite precision**: the non-stable set is a knife-edge, so rounding/quantization/pruning almost surely yields a Thom–Mather stable (‘catastrophic’) map.”


- **Structural inevitability (parameter space).**  
    Non-stable parameters form a **knife-edge** (meagre, Lebesgue-null). Any **finite-precision** perturbation (rounding/quantization/pruning/ε-tolerance) almost surely **lands in or keeps you in** the stable (“elementary-catastrophe”) regime.
    
- **No uniform ε-safety from expressivity.**  
    For any universally approximating class, there is **no architecture-only, data-only procedure** that guarantees ε-robust safety across all tasks.
    
- **Small-ε robust-risk law (CRS).**  
    Robust/adversarial risk grows **linearly** in ε with slope = data-weighted boundary area **divided by** boundary gradient norm; near elementary catastrophes on the data manifold this **inflates** markedly.
    
- **Every model is ε-close to catastrophe.**  
    Catastrophic maps are **dense in the hypothesis class**; for any network and any ε>0 there exists a catastrophic network within ε, **independent of training error**.

## Closing Loopholes

It is necessary and sufficient for any absolutely continuous probability to be described by a probability density function. Any randomly process that satisfies or introduces this process induces catastrophes

Moreover finite precision almost surely introduces catastrophes as does any form of quantization whatsoever. 

**Admissible priors.** We restrict to priors that are (i) **task-independent** and (ii) **absolutely continuous** w.r.t. Lebesgue (covering all standard inits). For such priors, the ε-safe parameter set $S_T$​ is Lebesgue-null ⇒ $P(S_T)=0$ for all $T$; any PAC-Bayes certificate of ε-safety is vacuous.  
**Hence a prior cannot “save the day.”**  
Allowing arbitrary priors merely relocates the burden: any prior assigning non-negligible mass to $S_T$​ **must encode task-specific information** at a granularity comparable to specifying a safe policy, _equivalent to having a trained agent a priori_. We therefore exclude such task-dependent priors when claiming distribution-free guarantees.

Short answer: **Yes—if you state your assumptions cleanly.**  
You can _remove the “a clever prior saves the day” escape hatch_ in two rigorous ways:

---

### 1) For **natural** priors (absolutely continuous, task-independent): prior cannot help at all

Let $\Theta\subset\mathbb R^P$ be the parameter space of an expressive NN class (UAT level).  
For each task/distribution $T$, let $S_T\subset\Theta$ be the set of **ε-safe** parameters (e.g., robust risk =0 on $T$ at radius ε).

> **Lemma (Safe set is null).**  
> Under our semialgebraic/PL/smooth hypotheses, $S_T$ is contained in a finite union of **codimension ≥1** manifolds (or algebraic varieties) in $\Theta$. Hence $S_T$ is **Lebesgue-null**.

> **Corollary (No prior rescue for a.c. priors).**  
> If the prior $P$ on $\Theta$ is **absolutely continuous** w.r.t. Lebesgue and **task-independent**, then $P(S_T)=0$ for every $T$.  
> In PAC-Bayes, any posterior $Q$ supported on $S_T$ has $\mathrm{KL}(Q\|P)=\infty$ ⇒ **no non-vacuous bound**.  
> **Conclusion:** Gaussian/Uniform/Xavier-style priors (or any a.c. prior) **cannot** “save the day.”

### 2) For **arbitrary** priors: any prior that _does_ save you is effectively “a trained agent baked in”

Two formalizations make this precise.
#### (A) Task-uniform requirement ⇒ prior must encode the task

Suppose you want **uniform ε-safety guarantees across a family of tasks** $\mathcal T$. Then for a fixed prior $P$,

$\inf_{T\in\mathcal T} P(S_T) \;>\; 0$

must hold to keep PAC-Bayes non-vacuous uniformly. But because each $S_T$ is null (and varies with $T$), for any fixed $P$ **independent of $T$** this infimum is **0**.  
Thus, to keep $P(S_T)$ bounded away from 0, $P$ must **depend on $T$** (i.e., encode the task/environment) which is exactly what a _trained/hand-crafted agent a priori_ is.

#### (B) Description-length lower bound

Even if you allow $P$ to be singular, to assign mass $\ge \delta$ to $S_T$ you must specify the safe set to within quantization $\eta$:

$\text{bits} \;\;\gtrsim\;\; -\log P(S_T) \;\;\ge\;\; c\,\log\!\frac{1}{\eta}$

where $c$ scales with the **codimension** and covering number of $S_T$. Across a broad family of tasks, the total description blows up; a prior that achieves this is **informationally equivalent** to shipping a trained policy (or the task description) _in advance_.

> **Proposition (Anti-prior, informal).**  
> Fix any countable or bounded-description prior PP independent of TT. Then there exists a task TT with $P(S_T)=0$.  
> _(Diagonalization/Enumeration-Paradox style: pick $T$ whose safe set avoids the support/atoms of $P$.)_

## Bottom line

- For **natural** (a.c., task-independent) priors: **provably no rescue**.
    
- For **artificial** priors that do rescue: they **encode the solution** (or the task) and don’t constitute distribution-free alignment — i.e., _equivalent to a trained agent a priori_.


> **Claim (Structural inevitability up to ε).**  
> For any universally approximating hypothesis class $\mathcal H\subset C(K,\mathbb R^m)$ with a smooth non-polynomial activation, catastrophic (Thom–Mather stable) maps are dense in the ambient function space and occur for almost every parameter in finite-dimensional parameterizations with absolutely continuous priors. Consequently, **every model in $\mathcal H$** is **ε-close** to a catastrophic model, independent of its training error; without explicit bias, typical parameter choices are themselves catastrophic.

> **Claim (No uniform ε-safety).**  
> For any learning rule producing $f\in\mathcal H$, there exists a distribution over $(X,Y)$ for which the **ε-robust risk** of $f$$ is bounded below by a positive constant. Thus **no architecture-only or data-only pipeline** can guarantee ε-safety across all tasks.

UAT makes defects **unavoidable in principle** (you’re always ε-close, and generically in them), but not **inevitable in every trained model**; what’s impossible is a **uniform ε-safety guarantee** without adding strong priors/regularization about the model’s local geometry near the data.


**Generic-Inevitability Lemma**  
Let $\mathcal{F}_\text{UAT}$ be any finite-dimensional parameterization of a _universally approximating_ neural-network family on a compact domain $\subset\mathbb R^{d}$.  
Assume the training / deployment stack contains

1. **Finite precision** arithmetic (fp16 / fp32 / int8, etc.), and
    
2. At least one source of **absolutely-continuous (a.c.) randomness** – e.g. random weight initialization, real-valued data augmentation, Gaussian gradient noise, stochastic/dithered rounding, or hardware non-determinism.
    

For any fixed task distribution $D$ whose Bayes decision boundary intersects positive data density and for **any** radius $0<\varepsilon\le\varepsilon_{0}$, the model produced by the stack satisfies, with probability 1:

1. **Parameter-space genericity** – the learned weight vector lies in the open, dense _general-position / stable_ region (the complement of a lower-dimensional “knife-edge” set).
    
2. **Input-space vulnerability** – there exists a non-empty ε-tube of inputs such that a perturbation of size ≤ε\le\varepsilon≤ε flips the prediction; quantitatively
    
	$R_{\mathrm{rob}}^D(f,\varepsilon)\;=\;c_{\mathrm{CRS}}\;\varepsilon\;+\;o(\varepsilon), \qquad c_{\mathrm{CRS}}=2\!\int_{\partial\mathcal C}\frac{\rho(x)}{\|\nabla g(x)\|}\,d\mathcal H^{d-1}\;>\;0 .$

Put plainly: **after finite-precision implementation and any tiny continuous noise, an expressive network is _almost surely_ ε-catastrophic for every sufficiently small ε.**

However (a.c.) is sufficient without finite precision
