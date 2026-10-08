# VYOM+ IntelliVoucher AI

## 1. Project Name

**VYOM+ IntelliVoucher AI**

An open-source AI-powered system for context-aware, explainable and reliable accounting voucher classification.

---

## 2. Problem Statement

Financial transactions contain multiple interconnected attributes such as seller, buyer, invoice details, item descriptions, quantities, GST, payment information, returns, orders and other transaction metadata.

Correctly identifying the appropriate accounting voucher type requires understanding the complete transaction context rather than relying on individual keywords.

VYOM+ IntelliVoucher AI aims to automatically classify structured financial transactions into the appropriate voucher category using an open-source/open-weight LLM while handling incomplete and ambiguous transaction information.

---

## 3. Project Overview

VYOM+ IntelliVoucher AI is a transaction intelligence system that processes structured financial transaction data from Excel and predicts the appropriate accounting voucher category.

The system combines:

- Structured transaction preprocessing
- Multi-field contextual understanding
- Open-source LLM reasoning
- Voucher classification
- Evidence extraction
- Confidence estimation
- Ambiguity detection
- Output validation
- Human review for uncertain cases
- Quantitative evaluation

### Core Workflow

```text
Structured Excel Dataset
          |
          v
Data Preprocessing
          |
          v
Transaction Context Builder
          |
          v
Open-Source LLM
          |
          v
Contextual Reasoning
          |
          v
Voucher Classification
          |
          v
Evidence + Confidence
          |
          v
Validation
          |
          v
Auto Classification / Human Review
          |
          v
Structured Output
```

---

## 4. Proposed Solution

The proposed system will analyze the complete transaction record before determining the appropriate voucher category.

Instead of performing direct keyword-based classification, the system will:

1. Normalize and validate transaction fields.
2. Build a structured representation of the transaction.
3. Analyze relationships between multiple transaction fields.
4. Predict the most appropriate voucher category.
5. Identify the transaction fields supporting the prediction.
6. Estimate classification confidence.
7. Detect ambiguous or competing categories.
8. Route low-confidence transactions for human verification.
9. Generate structured machine-readable output.

The approach is designed to distinguish semantically similar categories such as Purchase vs Sales, Purchase Return vs Sales Return, Payment vs Receipt, Journal vs conventional transactions, and Import vs Export.

---

## 5. Objectives

### Primary Objectives

- Automate accounting voucher classification from structured transaction data.
- Use an open-source/open-weight LLM as the primary intelligence layer.
- Understand relationships between multiple transaction fields.
- Distinguish semantically similar voucher categories.
- Handle incomplete and ambiguous transaction records.
- Provide evidence supporting each classification.
- Estimate confidence for every prediction.
- Identify transactions requiring human verification.
- Generate consistent machine-readable outputs.
- Evaluate the system using reproducible classification metrics.

---

## 6. Target Users / Use Case

### Target Users

- Accounting professionals
- Finance teams
- Businesses processing large transaction volumes
- ERP and accounting software providers
- Financial automation platforms

### Primary Use Case

A user uploads an Excel dataset containing structured transaction information.

The system processes each transaction and generates the appropriate voucher classification.

```text
Upload Excel Dataset
        |
        v
Process Transactions
        |
        v
Understand Transaction Context
        |
        v
Classify Voucher
        |
        v
Show Evidence + Confidence
        |
        v
Review Uncertain Cases
        |
        v
Export Results
```

---

## 7. Open-Source AI Technology Selected

### Qwen2.5-7B-Instruct

Qwen2.5-7B-Instruct is proposed as the primary open-source/open-weight language model for:

- Transaction understanding
- Contextual reasoning
- Voucher classification
- Structured output generation

The final model configuration will be validated according to the computational environment available during the final implementation.

---

## 8. Why This Technology Was Selected

The problem requires understanding relationships between multiple transaction fields rather than identifying a single keyword.

The selected model is intended to provide:

- Contextual understanding
- Instruction following
- Multi-field reasoning
- Structured output generation
- Practical inference requirements

The technology choice is therefore driven by the reasoning requirements of the problem rather than simply selecting a popular model.

---

## 9. AI's Role in the System

The AI model will act as the primary transaction-classification intelligence layer.

For each transaction, it will analyze available information such as:

```text
Seller / Supplier
Buyer / Customer
Invoice Information
Item Description
Quantity
Taxable Value
GST
Discount
Freight
Payment Information
Return Information
Order References
Import / Export Details
Other Metadata
```

The AI will produce:

- Predicted voucher type
- Supporting evidence
- Confidence score
- Alternative category where relevant
- Human-review requirement for uncertain cases

---

## 10. System Architecture

```text
                    +--------------------------+
                    |   Structured Excel      |
                    |       Dataset            |
                    +------------+-------------+
                                 |
                                 v
                    +--------------------------+
                    | Data Cleaning &          |
                    | Validation               |
                    +------------+-------------+
                                 |
                                 v
                    +--------------------------+
                    | Transaction Context     |
                    | Builder                  |
                    +------------+-------------+
                                 |
                                 v
                    +--------------------------+
                    | Qwen2.5-7B-Instruct      |
                    | Reasoning Engine         |
                    +------------+-------------+
                                 |
                                 v
                    +--------------------------+
                    | Voucher Classification   |
                    +------------+-------------+
                                 |
                    +------------+-------------+
                    |                          |
                    v                          v
          +------------------+       +------------------+
          | Evidence         |       | Alternative      |
          | Extraction       |       | Category Check   |
          +--------+---------+       +--------+---------+
                   |                          |
                   +------------+-------------+
                                |
                                v
                    +--------------------------+
                    | Confidence &             |
                    | Uncertainty Assessment   |
                    +------------+-------------+
                                 |
                    +------------+-------------+
                    |                          |
                    v                          v
          +------------------+       +------------------+
          | High Confidence  |       | Low Confidence  |
          | Auto-Classification|     | Human Review    |
          +--------+---------+       +--------+---------+
                   |                          |
                   +------------+-------------+
                                |
                                v
                    +--------------------------+
                    | Validation & Structured  |
                    | Output Generation        |
                    +------------+-------------+
                                 |
                                 v
                    +--------------------------+
                    | JSON / CSV / Dashboard   |
                    +--------------------------+
```

---

## 11. Component-Level Architecture

| Component | Responsibility |
|---|---|
| Dataset Processor | Reads and preprocesses Excel transactions |
| Data Validator | Identifies missing or invalid fields |
| Context Builder | Creates a standardized transaction representation |
| LLM Reasoning Engine | Performs contextual transaction analysis |
| Classification Engine | Predicts the voucher category |
| Evidence Extractor | Identifies supporting transaction fields |
| Confidence Engine | Estimates classification certainty |
| Conflict Detector | Identifies ambiguous or competing categories |
| Validation Layer | Checks output consistency |
| Human Review Module | Handles low-confidence cases |
| Evaluation Engine | Calculates performance metrics |
| Result Interface | Displays and exports predictions |

---

## 12. Data / Information Flow

```text
Excel Dataset
      |
      v
Read Transaction
      |
      v
Clean & Normalize
      |
      v
Validate Available Fields
      |
      v
Build Transaction Context
      |
      v
LLM Reasoning
      |
      v
Predict Voucher Type
      |
      v
Extract Supporting Evidence
      |
      v
Estimate Confidence
      |
      v
Check Ambiguity / Conflicts
      |
      +--------------------------+
      |                          |
      v                          v
High Confidence            Low Confidence
      |                          |
      v                          v
Auto-Classify              Human Review
      |                          |
      +------------+-------------+
                   |
                   v
          Structured JSON / CSV
```

---

## 13. Agentic Workflow

A complex multi-agent architecture is not required for the initial system.

The proposed solution will use a focused AI reasoning pipeline consisting of:

1. **Transaction Understanding**  
   Analyze available transaction fields and their relationships.

2. **Voucher Classification**  
   Predict the most appropriate voucher category.

3. **Evidence Extraction**  
   Identify the transaction fields supporting the prediction.

4. **Confidence Assessment**  
   Estimate the certainty of the classification.

5. **Conflict Detection**  
   Identify competing or ambiguous voucher categories.

6. **Validation**  
   Verify the prediction and structured output.

7. **Human Review**  
   Route low-confidence or ambiguous transactions for verification.

This focused workflow keeps the architecture technically meaningful while remaining feasible within the final hackathon.

---

## 14. Technology Stack

| Layer | Technology |
|---|---|
| AI Model | Qwen2.5-7B-Instruct |
| Backend | Python, FastAPI |
| Data Processing | Pandas |
| Frontend | React |
| Evaluation | Scikit-learn |
| Input | Excel (.xlsx) |
| Output | JSON / CSV |
| Optimization | Quantization / Efficient Inference |
| Deployment | Docker / Cloud |
| Version Control | GitHub |

---

## 15. Expected Features

### Core Features

- Excel transaction upload
- Batch transaction processing
- Automatic voucher classification
- Multi-field transaction reasoning
- Support for required voucher categories
- Structured JSON/CSV output

### Advanced Features

- Evidence-backed predictions
- Confidence scoring
- Ambiguity detection
- Competing-category analysis
- Human-review routing
- Input-grounded explanations
- Batch evaluation
- Confusion matrix
- Category-wise performance analysis
- Error analysis

### Key Differentiation

Unlike a simple:

```text
Excel → LLM → Voucher
```

pipeline, IntelliVoucher AI will provide:

```text
Transaction Context
        |
        v
AI Reasoning
        |
        v
Voucher Prediction
        |
        +----> Supporting Evidence
        |
        +----> Confidence
        |
        +----> Alternative Category
        |
        v
Validation
        |
        +----> High Confidence → Auto-Classify
        |
        +----> Low Confidence → Human Review
```

The goal is to make the system **evidence-backed, explainable and uncertainty-aware**, rather than treating every AI prediction as automatically correct.

---

## 16. Implementation Approach

### Phase 1 — Data Preparation

- Load the provided Excel dataset.
- Validate available fields.
- Normalize transaction values.
- Handle missing information.

### Phase 2 — Context Construction

- Identify relevant transaction attributes.
- Build a standardized transaction representation.
- Preserve relationships between important fields.

### Phase 3 — AI Reasoning

- Provide the structured transaction context to the open-source LLM.
- Generate a constrained voucher classification.
- Compare relevant competing categories where necessary.

### Phase 4 — Evidence and Confidence

- Identify supporting transaction fields.
- Generate a confidence estimate.
- Detect ambiguous or conflicting cases.

### Phase 5 — Validation

- Validate the predicted voucher category.
- Validate the structured output.
- Check evidence against the original transaction fields.
- Route uncertain transactions for human review.

### Phase 6 — Evaluation

- Test using previously unseen records.
- Calculate classification metrics.
- Generate category-wise performance.
- Analyze incorrect and ambiguous predictions.

### Phase 7 — User Interface

- Provide dataset upload.
- Display predictions.
- Highlight low-confidence transactions.
- Display evidence and confidence.
- Export structured results.

---

## 17. Expected Final Output

### High-Confidence Classification

```json
{
  "invoice_number": "INV-2026-1042",
  "voucher_type": "Purchase",
  "confidence": 0.94,
  "evidence": [
    "Supplier transaction",
    "Goods purchased",
    "GST input information"
  ],
  "review_required": false
}
```

### Ambiguous Classification

```json
{
  "invoice_number": "INV-2026-1088",
  "voucher_type": "Purchase",
  "confidence": 0.56,
  "alternative_category": "Expense",
  "review_required": true
}
```

The output will be machine-readable and suitable for programmatic evaluation and potential downstream accounting workflows.

---

## 18. Future Scope / Scalability

The proposed architecture can be extended to:

- ERP and accounting-system integration
- Automated voucher creation
- Real-time transaction classification
- Human-in-the-loop learning
- Domain-specific model fine-tuning
- LoRA / QLoRA adaptation
- Continuous model evaluation
- Large-scale transaction processing
- Additional financial document workflows
- Integration with automated accounting pipelines

---

## 19. Open-Source Dependencies / Components

The proposed implementation will use appropriately licensed open-source/open-weight components, including:

- **Qwen2.5-7B-Instruct**
- **Python**
- **Pandas**
- **FastAPI**
- **Scikit-learn**
- **React**
- Open-source inference and optimization libraries
- Git and GitHub tooling

Exact versions, licenses and model configurations will be documented during the final implementation.

---

## 20. Expected Challenges and Mitigation

| Challenge | Proposed Mitigation |
|---|---|
| Purchase vs Sales | Multi-field contextual reasoning |
| Purchase Return vs Sales Return | Transaction-direction and relationship analysis |
| Payment vs Receipt | Party and payment-context analysis |
| Journal vs conventional transactions | Full transaction-context evaluation |
| Missing transaction fields | Robust context construction |
| Ambiguous transactions | Confidence scoring and human review |
| Incorrect AI output | Structured output validation |
| Unsupported explanations | Evidence restricted to provided transaction fields |
| Model hallucination | Input-grounded evidence validation |
| Model latency | Quantization and optimized inference |
| Category imbalance | Per-category metrics and error analysis |
| Misclassification | Confusion matrix and systematic error analysis |
