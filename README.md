---
author:
- Sachit Kuhar
date: 2023-02-13
title: CS7545 Lecture 9
---

# Rademacher complexity

Let $F=\{f: x \rightarrow \mathbb{R}\}$ and $s=\{(x_i, y_i)\}_{i-1}^m \sim D^m$

We assume $\sigma_i= \begin{cases}1 & wp=1/2 \\
-1 & wp=-1 / 2\end{cases}$

Rademacher complexity is
$\hat{\mathbb{R}}_s(F)=\underset{\sigma}{E}[\sup _{f \in F} \frac{1}{m} \sum_{i=1}^m r f(x_i)]$

Definition for a set of vectors $A \subseteq \mathbb{R}^m$, and
$a=(a_1, a_2, \ldots, a_m)$.

The Rademacher complexity of $A$ is:
$R(A)=\underset{\sigma}{E}[\sup _{a \in A} \frac{1}{m} \sum_{i=1}^m \sigma_i a_i]$

We could set $A=\{(f(x_1), \ldots, f(x_m)), f \in F\}$

# Why Rademacher complexity?

1.  Nice properties / lemmas \"Rademacher calculus\"

2.  Nearly tight bound on
    $\sup _{f \in F}\left|L(f)-\hat{L}_s(f)\right|$

# Properties of Rademacher complexity?

1.  $R(c A)=|c| R(A)$ $where \hspace{10pt} cA=\{c*a : a \in A\}$\

2.  $A^{\prime} \subseteq A \Rightarrow R\left(A^{\prime}\right) \leq R(A)$\

3.  $R\left(A+A^{\prime}\right)=R(A)+R\left(A^{\prime}\right)$\
    where Minkowski Sum is
    $A+A^{\prime}=\left\{a+a^{\prime}: a \in A, a^{\prime} \in A^{\prime}\right\}$\

4.  $R(\operatorname{Conv}(A))=R(A)$\
    \
    $\text {where  Conv }(.) \text { is convex hull }$ and
    $\operatorname{conv}(A)=\left\{\sum w_i a_i, \quad \sum w_i=1 \text{ and } w_i>=0 \right\}$.

5.  Massart's Lemma: If $|A|<\infty$,
    $R(A)=\max _{a \in A}\|a\|_2\frac{\sqrt{2 \log |A|}}{m .}$\

6.  Talagrad's contraction lemma: If
    $\phi: \mathbb{R} \rightarrow \mathbb{R}$ is L-Lipschitz, then
    $R(\phi(A)) \leq \operatorname{LR}(A)$\
    \
    where $\phi(A)=\{\phi(a): a \in A\}$ and
    $\phi(a)=\left(\phi_1\left(a_1\right), \phi_2\left(a_2\right), \ldots, \phi_m\left(a_m\right)\right)$\
    \
    and the definition of $\phi_i$ that is $L-L_{i p s c h i t z}$ in
    $R$ is $|\phi_i(x)-\phi_i(y)| \leqslant L|x-y|$\

# Proof of Massart's Lemma

Study
$A^{\prime}=\\{\lambda a : a \in A\\}, \lambda \in \mathbb{R}$

$$\begin{aligned}
& m R(A^{\prime})={\mathbb{E}}_\sigma[\max _{a^{\prime} \in A^{\prime}} \sum_{i=1}^m \sigma_i a_i^{\prime}] \\
& ={\mathbb{E}}_\sigma[\log \max _{a^{\prime} \in A^{\prime}} \exp (\sum_{i=1}^m \sigma_i a_i^{\prime})] \\
& \leq {\mathbb{E}}_\sigma[\log \sum_{a^{\prime} \in A^{\prime}} \exp (\sum_{i=1}^m \sigma_i a_i^{\prime})] \\
\end{aligned}$$ 

By Jensen's inequality, we have: $$\begin{aligned}
& \leqslant \log \mathbb{E}_\sigma[\sum_{a^{\prime} \in A^{\prime}} \exp (\sum_{i=1}^m \sigma_i a_i^{\prime})] \\
& =\log \mathbb{E}_\sigma[\sum_{a^{\prime} \in A^{\prime}} \prod_{i=1}^m \exp (\sigma_i a_i^{\prime})] \\
& =\log \sum_{a^{\prime} \in A^{\prime}} \prod_{i=1}^m \mathbb{E}_{\sigma_i}[\exp (\sigma_i, a_i^{\prime})] \\
\end{aligned}$$ 

We know that $$\begin{aligned}
& \mathbb{E}_{\sigma_i}\left[\exp \left(\sigma_i, a_i^{\prime}\right)\right]=\frac{1}{2} \exp \left(a_i^{\prime}\right)+\frac{1}{2} \exp \left(-a_i^{\prime}\right) \leq \exp \left(\frac{a_i^2}{2}\right) \\
\end{aligned}$$ Hence, $$\begin{aligned}
& m R\left(A^{\prime}\right)=\log \sum_{a^{\prime} \in A^{\prime}} \prod_{i=1}^m \exp \left(\frac{a_i^{\prime 2}}{2}\right) \\
& =\log \sum_{a^{\prime} \in A^{\prime}} \exp \left(\frac{\left\|a^{\prime}\right\|_2^2}{2}\right) \\
& \leqslant \log \left|A^{\prime}\right| \max _{a^{\prime} \in A^{\prime}} \exp \left(\frac{\left\|a^{\prime}\right\|_2^2}{2}\right) \\
& =\log \left|A^{\prime}\right|+\log \max _{a^{\prime} \in A^{\prime}}\left(\exp \left(\frac{\left\|a^{\prime}\right\|_2^2}{2}\right)\right). \\
& =\log \left|A^{\prime}\right|+\max _{a^{\prime} \in A^{\prime}} \frac{\left\|a^{\prime}\right\|_2^2}{2} 
\end{aligned}$$ By property 1, we have
$R(A) =\frac{1}{\lambda} R\left(A^{\prime}\right)$. Therefore, we have
$$\begin{aligned}
R(A) & \leq \frac{\log \left|A^{\prime}\right|+\lambda^2 \max_{a \in A} \frac{\|a\|_2^2}{2}}{\lambda m} \\
\text{Pick } & \lambda=\sqrt{\frac{2 \log |A|}{\max\|a\|^2}} \\
R(A) & \leq \max_{a \in A}\|a\|_2 \frac{\sqrt{2 \log |A|}}{m .}
\end{aligned}$$
