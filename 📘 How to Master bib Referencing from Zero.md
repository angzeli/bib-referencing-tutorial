# 📘 How to Master .bib Referencing from Zero

*(for Overleaf + LaTeX Lab Reports)*

---

## **1. What is a .bib file?**

A .bib file (short for **bibliography**) is your personal **reference database**.

- It stores all your citation details (authors, title, year, DOI, etc.) in a structured format readable by LaTeX.
- You’ll only ever need **one .bib file per project** — it can hold dozens or even hundreds of references.

---

## **2. Basic Project Structure**

```python
main.tex          ← your main report file
references.bib    ← your reference database
figures/          ← folder for images (optional)
```

---

## **3. Step-by-Step Setup in Overleaf**

### **Step 1 — Create the .bib file**

In Overleaf, click **“New File” → name it references.bib**.

---

### **Step 2 — Add Reference Entries**

Each reference is one BibTeX entry. Example:

```python
@article{qu2002cdse,
  author    = {Lidong Qu and Xiaogang Peng},
  title     = {Control of Photoluminescence Properties of CdSe Nanocrystals by Surface Modification},
  journal   = {Journal of the American Chemical Society},
  year      = {2002},
  volume    = {124},
  number    = {9},
  pages     = {2049--2055},
  doi       = {10.1021/ja0171476}
  }
```

- `@article` = reference type
- `qu2002cdse` = **citation key** (you’ll use this to cite in LaTeX so must be unique)
- Fields like *author*, *title*, *journal* etc. define the metadata.

### **Step 3 — Add the bibliography section to main.tex**

At the end of your document (before `\end{document}`):

```python
\bibliographystyle{chem-acs}  ← or unsrt, rsc, etc. for different ref style
\bibliography{references}     ← matches your .bib file name (no extension)
```

---

### **Step 4 — Cite in your text**

Use the citation key from your .bib entry:

```python
According to Qu and Peng \cite{qu2002cdse}, 
CdSe nanocrystals exhibit tunable PL.
```

- When you compile twice in Overleaf, LaTeX automatically formats and lists all references.
- Note that only the papers _actually cited_ in the text will exist in the reference section at the end.

---

### **Step 5 — Compile correctly**

- Click **“Recompile” twice** in Overleaf (LaTeX needs two passes).
- If your references don’t appear, check:
    - The .bib filename matches your command.
    - The citation keys are consistent.

---

## **4. Common Bibliography Styles**

| **Style** | **Example Format** | **Recommended For** |
| --- | --- | --- |
| `unsrt` | [1], [2] (in citation order) | General lab reports |
| `plain` | Sorted by author name | Essays or dissertations |
| `chem-acs` | ACS journal style | Chemistry reports (Imperial standard) |
| `rsc` | RSC style | Royal Society of Chemistry |
| `nature` | Nature-style | Research papers |

---

## **5. Example Minimal Working Setup**

In **main.tex**:

```python
\documentclass[a4paper,12pt]{article}
\begin{document}

\section{Introduction}
Quantum dots show size-dependent optical properties\cite{qu2002cdse}.

\bibliographystyle{chem-acs}
\bibliography{references}

\end{document}
```

In **references.bib**:

```python
@article{qu2002cdse,
  author  = {Lidong Qu and Xiaogang Peng},
  title   = {Control of Photoluminescence Properties of CdSe Nanocrystals by Surface Modification},
  journal = {J. Am. Chem. Soc.},
  year    = {2002},
  volume  = {124},
  pages   = {2049--2055},
  doi     = {10.1021/ja0171476}
}
```

---

## **6. Bonus Tips**

### **a) Generate BibTeX entries instantly**

Use either method:

- **Google Scholar → Cite → BibTeX**
- **DOI → BibTeX generator** (e.g. [https://doi2bib.org](https://doi2bib.org/))

Simply copy the generated entry and paste it into your existing references.bib.

### **b) Organise your .bib with comment sections**

If you have many references, group them with % comments for clarity:

```python
% --- Quantum Dots Section ---
@article{qu2002cdse, ...}

% --- Computational Section ---
@article{kohn1965self, ...}

% --- Soft Matter Section ---
@article{degennes1979scaling, ...}
```

These comments don’t affect compilation — they just help you stay organised.

---

## **7. Quick Checklist**

- Only **one** `.bib` file per project
- Use **unique** keys for each reference
- Cite with `\cite{key}`
- Add `\bibliography{references}` at the end
- Compile **twice**
- Style with `\bibliographystyle{chem-acs}` or rsc
