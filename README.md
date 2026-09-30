# Email-Eu-core – Departmental Homophily Hypothesis Test

This project was completed for **Laboratory 3: Hypothesis Testing in Network Analysis** for the Social Media Analytics course.

The objective is to determine whether an observed network pattern is unusual relative to an explicitly defined null/reference model.

## Dataset

The analysis uses the **Email-Eu-core Network** from the Stanford Large Network Dataset Collection (SNAP).

Dataset source:

[https://snap.stanford.edu/data/email-Eu-core.html](https://snap.stanford.edu/data/email-Eu-core.html)

The network contains:

- **1,005 nodes**
- **25,571 directed email relationships**
- **42 departments**

A node represents a member of the research institution.

A directed edge represents an email relationship from one member to another.

The graph is analyzed as a **directed and unweighted network**.

The dataset also contains department labels for the network nodes.

## Research Question

**Are members of the same department connected by email more often than would be expected under random assignment of department labels?**

## Network Mechanism

The mechanism investigated is **homophily**, specifically **departmental homophily**.

Homophily refers to the tendency of similar actors to form relationships more frequently than dissimilar actors.

In this analysis, department membership is used as the similarity attribute.

## Hypotheses

### H0

Department labels are unrelated to the observed email network structure.

The proportion of same-department edges should be similar to what would be expected if the existing department labels were randomly assigned to network nodes.

### H1

Members of the same department are connected by email more frequently than expected under random assignment of department labels.

The result would be consistent with a departmental homophily pattern.

## Observed Statistic

The statistic used is the proportion of directed email relationships connecting two members from the same department.

Observed results:

| **Measure** | **Result** |
| ------------------------- | ---------- |
| Nodes | 1,005 |
| Directed edges | 25,571 |
| Departments | 42 |
| Same-department edges | 9,287 |
| Same-department proportion | 0.3632 |
| Same-department percentage | 36.32% |

## Descriptive Network Results

Several descriptive measures were calculated to provide context for the network.

| **Measure** | **Result** |
| ------------------------------- | ---------- |
| Nodes | 1,005 |
| Directed edges | 25,571 |
| Network density | 0.025342 |
| Average in-degree | 25.44 |
| Average out-degree | 25.44 |
| Average clustering coefficient | 0.3994 |

The network density indicates that only a relatively small proportion of all possible directed email relationships are present.

The average in-degree and out-degree are both 25.44, meaning that members have approximately 25 incoming and 25 outgoing email relationships on average.

The average clustering coefficient of 0.3994 indicates a noticeable level of local interconnectedness in the network.

## Null Model

A **label-permutation null model** was used.

The network structure was kept unchanged while the department labels were randomly shuffled among network nodes.

The null model preserves:

- all 1,005 nodes;
- all 25,571 directed edges;
- the complete network topology;
- each node's network connections;
- the number of nodes in each department.

Only the assignment of department labels to individual nodes was randomized.

This null model is appropriate because the research question concerns whether department membership is associated with the existing email relationships.

## Permutation Test

A total of **2,000 permutations** were generated.

For every permutation:

1. the department labels were randomly reassigned to nodes;
2. the network structure remained unchanged;
3. the proportion of same-department edges was calculated;
4. the resulting statistic was stored in the null distribution.

Results:

| **Measure** | **Result** |
| ------------------------- | ---------- |
| Observed proportion | 0.3632 |
| Observed percentage | 36.32% |
| Number of permutations | 2,000 |
| Extreme permutations | 0 |
| Corrected p-value | 0.00050 |

None of the 2,000 randomized label assignments produced a same-department proportion as large as the observed value.

## Visualization

The figure below shows the null distribution generated from the 2,000 permutations together with the observed statistic.

The observed same-department proportion is far outside the range produced by the null model.

![Null distribution](lab3_homophily_null_distribution.png)

## Interpretation

The permutation test produced a corrected one-sided **p-value of 0.00050**.

The observed same-department proportion of **36.32%** is substantially higher than the values produced under the label-permutation null model.

The result is therefore consistent with **departmental homophily** in the Email-Eu-core network.

However, this result should not be interpreted as proof that department membership caused the observed email relationships.

Other possible explanations include:

- shared projects;
- similar organizational roles;
- common supervisors;
- physical location;
- other institutional responsibilities.

The analysis therefore shows that the observed network structure is not compatible with random placement of department labels under the selected null model, but it does not establish the causal mechanism that produced the observed pattern.

## AI Use Statement

Generative AI was used as a supporting tool during this laboratory.

ChatGPT was used to help:

- structure the analysis;
- formulate the research question and hypotheses;
- develop and check Python code;
- implement the label-permutation test;
- create the null-distribution visualization;
- explain and interpret the statistical results.

All code was executed and verified using the actual Email-Eu-core dataset.

One methodological choice that was specifically checked was the null model. The network structure was kept fixed and only the department labels were randomly permuted. This was appropriate because the research question concerns whether department membership is associated with the existing email relationships.

The interpretation was also checked to ensure that the result was presented as an association consistent with homophily rather than as proof of causality.

## Project Structure

```text
├── Social_Media_Analytics_Lab3_Homophily_Analysis.ipynb
├── README.md
├── requirements.txt
│
├── data/
│   ├── email-Eu-core.txt
│   └── email-Eu-core-department-labels.txt
