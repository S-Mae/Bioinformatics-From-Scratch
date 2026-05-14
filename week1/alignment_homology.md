# Day 3 — Sequence Alignment and Homology

---

## Overview

Sequence alignment compares biological sequences to identify similarities, evolutionary relationships, and conserved regions.

Alignment helps reveal whether sequences may share similar functions, structures, or ancestry.

---

## Speciation vs Gene Duplication

| | Speciation | Gene Duplication |
|---|---|---|
| **Process** | One species diverges into multiple species | A gene is copied within the same genome |
| **Results in** | Orthologues | Paralogues |
| **Example** | β-globin in mouse vs humans | α-globin vs β-globin in humans |

```text
Speciation → Orthologues        Gene Duplication → Paralogues

      ● Ancestor                       ● Ancestor
     / \                              / \
  Mouse  Human                  Gene A   Gene B
```

---

## Homologues, Orthologues and Paralogues

- **Homologues** — genes related by common ancestry (umbrella term)
- **Orthologues** — homologous genes in different species separated by speciation  
  Example: Human IL6 vs Mouse IL6
- **Paralogues** — homologous genes in the same species separated by gene duplication  
  Example: IL6 vs IL11 in humans

> Sequence similarity may suggest homology, but homology represents shared evolutionary ancestry.

### Example — IL6 Phylogenetic Tree (BLAST)

<img width="1149" height="325" alt="Phylogenetic Tree" src="https://github.com/user-attachments/assets/701e367f-c145-4909-9f26-88039b446308" />
*Phylogenetic tree of IL6 orthologues generated from BLAST pairwise alignments. 
Green = primates, pink = odd-toed ungulates, blue = even-toed ungulates.*
---

## Clade

A clade is a monophyletic group consisting of a common ancestor and all of its descendants.

---

## Conserved Regions

Conserved regions are sequence regions that remain similar across different organisms or genes over evolutionary time.

Highly conserved regions often indicate important biological or functional roles because harmful mutations in these regions are less tolerated.

---

## Global vs Local Alignment

| | Global Alignment | Local Alignment |
|---|---|---|
| **Approach** | End-to-end alignment | Finds best matching regions |
| **Best for** | Similar length sequences | Partially similar sequences |
| **Algorithm** | Needleman-Wunsch | Smith-Waterman, BLAST |

### Example - BLAST Multiple Sequence Alignment of IL6 

<img width="795" height="257" alt="image" src="https://github.com/user-attachments/assets/44f85793-9dac-418a-953b-c5d1a9bbf3a4" />
*BLAST multiple sequence alignment of IL6 across 118 sequences. Red blocks indicate positions that differ from the query. Organisms include Homo sapiens, Pan troglodytes, Callithrix jacchus and other primates.*

---

## Manual Alignment Exercise

### Original Sequences

```text
ACTGAC
ACGAC
```

### Alignment

```text
ACTGAC
AC-GAC
```

A gap was introduced at position 3 to maximise similarity and improve alignment quality.

---

## Alignment Scoring

### Scoring Scheme

| Event | Score |
|---|---|
| Match | +1 |
| Mismatch | -1 |
| Gap | -2 |

---

### Score Calculation

| Position | Seq1 | Seq2 | Event | Score |
|---|---|---|---|---|
| 1 | A | A | Match | +1 |
| 2 | C | C | Match | +1 |
| 3 | T | - | Gap | -2 |
| 4 | G | G | Match | +1 |
| 5 | A | A | Match | +1 |
| 6 | C | C | Match | +1 |

### Final Score

```text
+3
```

Higher alignment scores generally indicate greater sequence similarity.

> Scoring schemes vary by tool. BLAST default nucleotide scoring commonly uses +1/−2/−2, while protein alignments often use substitution matrices such as BLOSUM62.

---

## Interpreting BLAST Results

- **Percent Identity** — percentage of aligned positions that are identical
- **E-value** — likelihood that the alignment occurred by chance; lower values indicate stronger significance
- **Query Cover** — percentage of the query sequence included in the alignment

Low E-values and high query coverage generally suggest biologically meaningful alignments.

---

## Biological Importance of Homology

Homologous genes are important because they:
- help trace evolutionary relationships
- reveal conserved biological functions
- support comparative genomics studies
- help identify functionally important regions

Orthologues often retain similar functions across species while paralogues may evolve specialised or entirely new functions.

---

## Key Concepts Learned

- Speciation produces orthologues while duplication produces paralogues
- Similarity does not automatically mean homology
- Conserved regions often indicate functional importance
- Low E-values generally indicate biologically meaningful alignments
- Alignment quality depends on scoring systems and gap placement
