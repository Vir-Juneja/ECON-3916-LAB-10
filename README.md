# ECON-3916-LAB-10# Correlation & Causality: Confounders, Colliders and the Limits of Controls

## Objective

To understand why correlation does not always imply causation, how different causal structures affect regression estimates, and why adding controls can sometimes create bias rather than remove it.

## Methodology

- Simulated three datasets representing true causation, pure confounding, and pure selection. Each produced a correlation near 0.65, despite having different true causal effects.
- Used `networkx` to draw directed graphs showing a confounder, a collider, and a mediator.
- Compared regression estimates with and without controls to see when adjusting for a variable helps recover the true causal effect.
- Demonstrated collider bias by controlling for a common effect of two independent variables, creating a statistically significant association where none existed.
- Constructed an M-bias example to show that controlling for a variable measured before treatment can still introduce bias.
- Wrote a function, `coef_on_d()`, to calculate the treatment coefficient under different sets of controls. Used it to show how adding one of the hidden causes, `u1`, closes the biasing path.
- Reproduced the LaLonde (1986) comparison between a randomized job-training experiment and an observational comparison group from the Current Population Survey (CPS).
- Compared the experimental treatment effect with the naive CPS estimate and the estimate after covariate adjustment to measure how much of the gap the controls explained.

## Key Findings

- **Correlation does not establish causation:** All three simulated worlds produced correlations near 0.65, even though their true causal effects were 2.0, 0.0, and 0.0, respectively.
- **Controlling for confounders can remove bias:** Adjusting for a common cause of treatment and outcome helped recover the true causal effect.
- **Controlling for colliders can introduce bias:** Conditioning on a collider created a large, highly significant association between two variables that were actually independent. The estimated effect was [YOUR VALUE], despite the true effect being 0.
- **Pre-treatment controls are not automatically safe:** In the M-bias example, adding a control measured before treatment produced a biased coefficient of [YOUR VALUE]. Adding `u1` as another control changed the estimate to [YOUR VALUE], showing how blocking the opened path can remove the bias.
- **Observational estimates can differ substantially from experimental results:** In the LaLonde example, the randomized experiment estimated a treatment effect of $[YOUR VALUE], compared with $[YOUR VALUE] using the naive CPS comparison group. After adding controls, the estimate was $[YOUR VALUE], closing [YOUR VALUE]% of the gap between the experimental and observational estimates.

## Conclusion

This lab showed me that variables can be strongly correlated without having a causal relationship. I learned that choosing controls requires understanding the causal structure rather than simply adding more variables to a regression. Confounders can create misleading associations, while controlling for colliders can introduce new bias. The M-bias example showed that even variables measured before treatment are not always appropriate controls. The LaLonde comparison reinforced why randomized experiments provide a useful benchmark when evaluating estimates from observational data.
