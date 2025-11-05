# Stella AI Testing Question List

## 🟢 Level 1: Basic Conversation Tests (Easy)

### 1. Simple Greeting
```
Hi
```

### 2. Basic Definition
```
What is DNA?
```

### 3. Simple Explanation
```
Explain what PCR is in simple terms
```

---

## 🟡 Level 2: Tool Usage Tests (Medium)

### 4. Web Search
```
Search for the latest news about CRISPR technology
```

### 5. Academic Search
```
Find recent papers about gene editing in cancer therapy
```

### 6. Data Query
```
What are the main functions of the TP53 gene?
```

### 7. Literature Summary
```
Search PubMed for papers about CAR-T therapy and summarize the key findings
```

---

## 🟠 Level 3: File Processing Tests (Medium+)

### 8. Read Text File
**Prepare file:** `test_genes.txt`
```txt
BRCA1
TP53
EGFR
KRAS
MYC
```

**Test question:**
```
Read the file test_genes.txt and tell me what these genes are known for
```

---

### 9. Analyze CSV Data
**Prepare file:** `gene_expression.csv`
```csv
Gene,Expression_Level,Condition,P_Value
BRCA1,2.5,Cancer,0.001
TP53,0.8,Cancer,0.005
EGFR,3.2,Cancer,0.002
KRAS,1.5,Normal,0.450
MYC,2.1,Cancer,0.010
```

**Test question:**
```
Analyze the gene expression data in gene_expression.csv. Which genes are significantly upregulated in cancer?
```

---

### 10. Process Sequence File
**Prepare file:** `dna_sequence.txt`
```txt
ATCGATCGATCGATCGTAGCTAGCTAGCTAGCTAGCT
GCTAGCTAGCTAGCTAGCTAGCTAGCTAGCTAGCTAG
ATCGATCGATCGATCGATCGATCGATCGATCGATCG
```

**Test question:**
```
Calculate the GC content of each sequence in dna_sequence.txt
```

---

### 11. Large File Processing
**Prepare file:** `protein_sequences.fasta` (contains multiple protein sequences)
```fasta
>Protein1
MKTIIALSYIFCLVFADYKDDDDK
>Protein2
AGCTTAGCTTAGCTTAGCTTAGCT
>Protein3
MKLAVLAVLAVLAVLAVLAVLAVL
```

**Test question:**
```
How many protein sequences are in protein_sequences.fasta? What's the average length?
```

---

## 🔴 Level 4: Multi-turn Conversation Tests (Medium+)

### 12. Consecutive Questions - Test Context Memory

**Question 1:**
```
What is CRISPR?
```

**Question 2 (follow-up):**
```
What are its main applications?
```

**Question 3 (follow-up):**
```
Which companies are leading in this field?
```

**Question 4 (follow-up):**
```
Compare the first two applications you mentioned
```

---

### 13. Reference Previous Results

**Question 1:**
```
Search for papers about mRNA vaccines
```

**Question 2 (after receiving results):**
```
Summarize the methodology of the first paper you found
```

**Question 3 (follow-up):**
```
Compare it with the second paper
```

---

## 🟣 Level 5: Complex Task Tests (Hard)

### 14. Multi-step Task
```
Search PubMed for papers about CAR-T therapy published in 2024, summarize the top 3 papers, and create a comparison table of their key findings
```

---

### 15. Data Analysis + Visualization
**Prepare file:** `clinical_trial_data.csv`
```csv
Drug,Phase,Success_Rate,Sample_Size,Year
Drug_A,Phase1,85,50,2023
Drug_A,Phase2,70,150,2024
Drug_B,Phase1,90,45,2023
Drug_B,Phase2,65,120,2024
Drug_C,Phase1,75,60,2023
```

**Test question:**
```
Analyze clinical_trial_data.csv and create a visualization comparing success rates across different phases. Which drug shows the most promise?
```

---

### 16. Literature + Data Integration
**Prepare file:** Use `gene_expression.csv` from above

**Test question:**
```
Based on the genes in gene_expression.csv, search for recent papers about their role in cancer, then create a summary table linking each gene to its main cancer-related functions
```

---

## 🔥 Level 6: Tool Creation Tests (Hard)

### 17. Create Simple Tool
```
Create a tool that calculates the GC content of a DNA sequence
```

**Then test the new tool:**
```
Use the GC content tool to analyze this sequence: ATCGATCGATCGTAGCTAGCTAGCT
```

---

### 18. Create Data Processing Tool
```
Create a tool that finds all palindromic sequences in a DNA string (sequences that read the same forwards and backwards)
```

**Then test:**
```
Use the palindrome tool on this sequence: ATCGATCGATCGTAGCTAGCTAGCT
```

---

### 19. Create Complex Tool
```
Create a tool that takes a protein sequence and predicts its secondary structure (alpha helix, beta sheet, random coil) based on simple rules
```

---

## 🎯 Level 7: Stress and Boundary Tests

### 20. Rapid Consecutive Questions (interval < 2 seconds)
```
What is PCR?
```
```
What is qPCR?
```
```
What's the difference between them?
```

---

### 21. Long Input Test
```
I have a research project about understanding the molecular mechanisms of CRISPR-Cas9 gene editing in mammalian cells, specifically focusing on off-target effects and how to minimize them. I need to: 1) Find relevant recent papers, 2) Identify the main off-target detection methods, 3) Compare their accuracy, 4) Suggest the best approach for my specific use case which involves editing the BRCA1 gene in human cell lines. Can you help me with this comprehensive analysis?
```

---

### 22. Invalid Request Test
```
Read the file that_does_not_exist.txt
```

---

### 23. Vague Request Test
```
Do something with genes
```

---

### 24. Project Switching Test

**In Project A:**
```
Search for papers about CRISPR and give me a detailed summary (this is a long task)
```

**Immediately switch to Project B, then:**
```
Hello
```

---

## 🧪 Level 8: Specific Feature Tests

### 25. Time Display Test
```
What time is it now?
```
(Then check if message timestamps display in local time)

---

### 26. Tool List View
```
What tools do you have access to?
```

---

### 27. Memory Function Test

**Day 1:**
```
My favorite gene to study is BRCA1
```

**Day 2 (new session):**
```
What's my favorite gene?
```

---


## 📋 File Preparation Checklist

Prepare the following files before testing:

- [ ] `test_genes.txt` - Gene list
- [ ] `gene_expression.csv` - Gene expression data
- [ ] `dna_sequence.txt` - DNA sequences
- [ ] `protein_sequences.fasta` - Protein sequences
- [ ] `clinical_trial_data.csv` - Clinical trial data

Quick file creation templates:

**test_genes.txt:**
```
BRCA1
TP53
EGFR
KRAS
MYC
```

**gene_expression.csv:**
```
Gene,Expression_Level,Condition,P_Value
BRCA1,2.5,Cancer,0.001
TP53,0.8,Cancer,0.005
EGFR,3.2,Cancer,0.002
KRAS,1.5,Normal,0.450
MYC,2.1,Cancer,0.010
```

**dna_sequence.txt:**
```
ATCGATCGATCGATCGTAGCTAGCTAGCTAGCTAGCT
GCTAGCTAGCTAGCTAGCTAGCTAGCTAGCTAGCTAG
ATCGATCGATCGATCGATCGATCGATCGATCGATCG
```

**protein_sequences.fasta:**
```
>Protein1
MKTIIALSYIFCLVFADYKDDDDK
>Protein2
AGCTTAGCTTAGCTTAGCTTAGCT
>Protein3
MKLAVLAVLAVLAVLAVLAVLAVL
```

**clinical_trial_data.csv:**
```
Drug,Phase,Success_Rate,Sample_Size,Year
Drug_A,Phase1,85,50,2023
Drug_A,Phase2,70,150,2024
Drug_B,Phase1,90,45,2023
Drug_B,Phase2,65,120,2024
Drug_C,Phase1,75,60,2023
```

---

## 🎯 Recommended Testing Sequences

### Quick Test (15 minutes)
Test questions: 1, 2, 4, 8, 12, 25

### Standard Test (45 minutes)
Test questions: 1-15, 20, 25, 26

### Complete Test (2 hours)
All test questions: 1-28
