# VYOM-IntelliVoucher-AI
1. Project Name
VYOM+ IntelliVoucher AI
An open-source AI-powered system for context-aware, explainable and reliable accounting voucher classification.
2. Problem Statement
Financial transactions contain multiple interconnected attributes such as:
- Seller / Supplier
- Buyer / Customer
- Invoice details
- Item descriptions
- Quantity and value
- GST and tax information
- Discounts and freight
- Payment information
- Return information
- Order and delivery references
- Import / Export information
Determining the correct accounting voucher type from these fields requires understanding the overall transaction context rather than relying on individual keywords.
The system aims to automatically classify each transaction into the appropriate voucher category using an open-source/open-weight LLM, while handling incomplete or ambiguous information. This directly follows the core technical challenge specified by VYOM+. Hacktober_Fest_4_Problem_Statem… Hacktober_Fest_4_Problem_Statem…
3. Project Overview
VYOM+ IntelliVoucher AI is an AI-based transaction intelligence system that converts structured financial transaction data into appropriate accounting voucher classifications.
The system combines:
- Structured data preprocessing
- Multi-field transaction understanding
- Open-source LLM reasoning
- Voucher classification
- Evidence extraction
- Confidence estimation
- Validation
- Human review for uncertain cases
- Quantitative evaluation
Core Workflow
Transaction Dataset
        ↓
Data Preprocessing
        ↓
Transaction Context Builder
        ↓
Open-Source LLM
        ↓
Contextual Reasoning
        ↓
Voucher Classification
        ↓
Evidence + Confidence
        ↓
Validation
        ↓
Auto Classification / Human Review

4. Proposed Solution
We propose a context-aware voucher intelligence pipeline that analyzes the complete transaction record before predicting a voucher category.
Instead of directly asking an LLM to classify a row, the system will:
1. Normalize and validate transaction fields.
2. Build a structured representation of the transaction.
3. Analyze relationships between relevant fields.
4. Generate the most appropriate voucher category.
5. Identify the transaction fields supporting the prediction.
6. Estimate prediction confidence.
7. Detect ambiguous or conflicting cases.
8. Route low-confidence cases for human verification.
9. Produce structured machine-readable output.
This approach addresses the requirement to reason over multiple transaction fields and distinguish semantically similar voucher categories. Hacktober_Fest_4_Problem_Statem…
5. Objectives
Primary Objectives
- Automate accounting voucher classification from structured transaction data.
- Understand relationships between multiple transaction fields.
- Use an open-source/open-weight LLM as the primary intelligence layer.
- Distinguish semantically similar voucher categories.
- Handle incomplete and ambiguous transaction records.
- Provide evidence supporting each prediction.
- Estimate confidence for every classification.
- Route uncertain transactions for human verification.
- Generate consistent machine-readable output.
- Evaluate the system using reproducible classification metrics.
6. Target Users / Use Case
Target Users
- Accounting professionals
- Finance teams
- Businesses processing large transaction volumes
- ERP and accounting software providers
- Financial automation platforms
Primary Use Case
A user uploads an Excel dataset containing structured transaction information.
The system:
Upload Dataset
      ↓
Process Transactions
      ↓
Understand Transaction Context
      ↓
Classify Voucher
      ↓
Show Evidence & Confidence
      ↓
Review Uncertain Cases
      ↓
Export Results

7. Open-Source AI Technology Selected
Qwen2.5-7B-Instruct
The proposed system will use Qwen2.5-7B-Instruct as its primary open-source/open-weight language model for:
- Transaction understanding
- Contextual reasoning
- Voucher classification
- Structured output generation
The final model configuration will be validated according to the computational environment available during implementation.
The official challenge explicitly permits open-source/openly available LLM/SLM approaches and lists Qwen among suitable model families. Hacktober_Fest_4_Problem_Statem…
8. Why This Technology Was Selected
Qwen2.5-7B-Instruct is proposed because the problem requires more than conventional keyword-based classification.
The model will be used for:
- Multi-field contextual understanding
- Instruction following
- Reasoning over transaction relationships
- Constrained classification
- Structured output generation
The model choice is therefore driven by the reasoning requirements of the problem, rather than simply selecting a popular AI model.
9. AI's Role in the System
The AI acts as the primary intelligence layer.
For each transaction, it will analyze available information such as:
Seller
Buyer
Items
Amount
GST
Payment
Returns
Orders
Import / Export
Other Metadata

and determine the most appropriate voucher category.
AI Output
- Predicted voucher type
- Supporting evidence
- Confidence score
- Review requirement
The AI will specifically address difficult distinctions such as Purchase vs Sales, Purchase Return vs Sales Return, Payment vs Receipt, Journal vs conventional transactions, and Import vs Export. Hacktober_Fest_4_Problem_Statem…
10. System Architecture
┌──────────────────────────────┐
│   Structured Excel Dataset   │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│ Data Cleaning & Validation   │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│ Transaction Context Builder  │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│ Qwen2.5-7B-Instruct          │
│ Contextual Reasoning Engine  │
└──────────────┬───────────────┘
               ↓
┌──────────────────────────────┐
│ Voucher Classification       │
└──────────────┬───────────────┘
               ↓
      ┌────────┴─────────┐
      ↓                  ↓
 Evidence Extraction   Alternative
      ↓                Category Check
      └────────┬─────────┘
               ↓
┌──────────────────────────────┐
│ Confidence & Uncertainty     │
│ Assessment                   │
└──────────────┬───────────────┘
               ↓
       ┌───────┴────────┐
       ↓                ↓
 High Confidence    Low Confidence
       ↓                ↓
 Auto Classification Human Review
       └────────┬───────┘
                ↓
┌──────────────────────────────┐
│ Validation & Structured      │
│ Output Generation            │
└──────────────────────────────┘

11. Component-Level Architecture
Component	Responsibility
Dataset Processor	Reads and preprocesses Excel transactions
Data Validator	Identifies missing/invalid fields
Context Builder	Creates a standardized transaction representation
LLM Reasoning Engine	Performs contextual transaction analysis
Classification Engine	Predicts the voucher category
Evidence Extractor	Identifies supporting transaction fields
Confidence Engine	Estimates classification certainty
Conflict Detector	Identifies ambiguous or competing categories
Validation Layer	Checks output consistency
Human Review Module	Handles low-confidence cases
Evaluation Engine	Calculates performance metrics
Result Interface	Displays and exports predictions


12. Data / Information Flow
Excel Dataset
     ↓
Read Transaction
     ↓
Clean & Normalize
     ↓
Validate Available Fields
     ↓
Build Transaction Context
     ↓
LLM Reasoning
     ↓
Predict Voucher Type
     ↓
Extract Supporting Evidence
     ↓
Estimate Confidence
     ↓
Check Ambiguity / Conflicts
     ↓
 ┌───────────────┬────────────────┐
 │ High Confidence│ Low Confidence │
 │ Auto-Classify │ Human Review   │
 └───────────────┴────────────────┘
     ↓
Structured JSON / CSV Output

13. Agentic Workflow
A complex multi-agent architecture is not required for the initial system.
The proposed solution will use a focused reasoning pipeline consisting of:
1. Transaction understanding
2. Voucher classification
3. Evidence extraction
4. Confidence assessment
5. Validation
This keeps the architecture technically meaningful while remaining feasible within the final hackathon.
14. Technology Stack
Layer	Technology
AI Model	Qwen2.5-7B-Instruct
Backend	Python, FastAPI
Data Processing	Pandas
Frontend	React
Evaluation	Scikit-learn
Input	Excel (.xlsx)
Output	JSON / CSV
Optimization	Quantization / efficient inference
Deployment	Docker / Cloud
Version Control	GitHub


15. Expected Features
Core Features
- Excel transaction upload
- Batch transaction processing
- Automatic voucher classification
- Multi-field transaction reasoning
- Support for all required voucher categories
- Structured JSON/CSV output
Advanced Features
- Evidence-backed predictions
- Confidence scoring
- Ambiguity detection
- Competing-category analysis
- Human-review routing
- Input-grounded explanations
- Batch evaluation
- Confusion matrix and error analysis
The official challenge defines a broad set of voucher categories and expects the system to handle semantically similar transaction types. Hacktober_Fest_4_Problem_Statem…
16. Implementation Approach
Phase 1 — Data Preparation
- Load the provided Excel dataset.
- Validate available fields.
- Normalize transaction values.
Phase 2 — Context Construction
- Identify relevant transaction attributes.
- Build a standardized AI-ready transaction representation.
Phase 3 — AI Reasoning
- Pass transaction context to the open-source LLM.
- Generate a constrained voucher classification.
Phase 4 — Evidence & Confidence
- Identify supporting input fields.
- Estimate prediction confidence.
- Detect competing or ambiguous categories.
Phase 5 — Validation
- Validate predicted categories.
- Check structured output.
- Route uncertain records for human review.
Phase 6 — Evaluation
- Test using previously unseen records.
- Generate classification metrics.
- Perform category-wise error analysis.
Phase 7 — User Interface
- Provide dataset upload.
- Display classifications.
- Highlight uncertain transactions.
- Allow result export.
17. Expected Final Output
High-Confidence Transaction
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

Ambiguous Transaction
{
  "invoice_number": "INV-2026-1088",
  "voucher_type": "Purchase",
  "confidence": 0.56,
  "alternative_category": "Expense",
  "review_required": true
}

The official challenge specifies transaction/invoice identification and voucher type as the minimum output, while confidence and explanation may additionally be provided. Hacktober_Fest_4_Problem_Statem…
18. Future Scope / Scalability
The proposed architecture can be extended to:
- ERP/accounting system integration
- Automated voucher creation
- Real-time transaction classification
- Human-in-the-loop learning
- Domain-specific fine-tuning
- LoRA/QLoRA adaptation
- Continuous model evaluation
- Large-scale batch processing
- Additional financial document workflows
19. Open-Source Dependencies / Components
The proposed implementation will use appropriately licensed open-source/open-weight components, including:
- Qwen2.5-7B-Instruct
- Python
- Pandas
- FastAPI
- Scikit-learn
- React
- Open-source inference/optimization libraries
- Git/GitHub tooling
Exact versions, licenses and configurations will be documented in the final implementation.
20. Expected Challenges and Mitigation
Challenge	Proposed Mitigation
Purchase vs Sales	Multi-field contextual reasoning
Purchase Return vs Sales Return	Relationship and transaction-direction analysis
Payment vs Receipt	Party and payment-context analysis
Journal vs conventional transactions	Full transaction-context evaluation
Missing fields	Robust context construction
Ambiguous transactions	Confidence scoring + human review
Incorrect AI output	Structured output validation
Unsupported explanations	Evidence restricted to provided transaction fields
Model latency	Quantization and optimized inference
Category imbalance	Per-category metrics and error analysis
