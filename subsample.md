# SubSample

Linkage disequilibrium and allelic heterogeneity explain variation in coronary artery disease risk at 9p21 across populations and reduced effect in Africans
<https://pubmed.ncbi.nlm.nih.gov/42385718/>

"The non-replication of 9p21.3 in African ancestry is not due to absent risk alleles, reduced power, or poorer imputation of risk alleles due to weaker LD; rather, it reflects greater haplotype diversity that disperses risk alleles across configurations, attenuating case-control contrast. These findings illustrate how ancestry-specific LD and multi-causal haplotype architecture modulate association detectability.”

I wonder if this concept is relevant to the DO.

Here is an article about what we discussed. I didn’t understand the suggestion about hierarchical modeling.

Hierarchical analysis would give exactly the same result if nesting is balanced (same number of islets per animal). If not balanced, as weighted analysis (weight = number of islets per animal) would be equivalent. Not worth it generally. You are fine.

Here is the article cited in the paper I sent you that describes hierarchical analysis. We routinely do islet experiments with multiple islet samples from mice. We do the conservative approach of averaging the technical replicates and then doing t-tests or ANOVA with n = number of mice. I wonder if we should be using a hierarchical analysis. What do you think? Can you show me how to do it?

Alan

<https://academic.oup.com/cardiovascres/article/113/14/1743/4098132>

Right. It is known as pseudoreplication. The nesting idea is that islet cells are nested within individuals (multiple islet cells come from a particular individual). Individuals may be assigned to groups (healthy, sick) while the islet cells are assigned to those groups through their nesting within individuals. Sometimes this is presented in anova tables with entries, with n individuals and c cells per individual.

```
term                    levels   df
group                   2        1
individual              n        n-2
cell(individual)        n*c      n*(c-1)
```
