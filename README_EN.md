# 🧠 Multi-Agent Prompt Design

> This project demonstrates how to implement a complex, reusable multi-agent workflow through Prompt design featuring "multi-role collaboration + clear task segmentation + verifiable output".
> This Prompt can be directly used in AI environments with code context understanding such as **Cursor / Claude / ChatGPT (GPT-5)**.

---

## 🌐 Core Philosophy

The efficiency of this Prompt comes from **systematic multi-role design** and **verifiable task layering structure**.
It doesn't just make AI "answer questions", but makes AI "execute a complete professional workflow".

### 🚀 Core Features

| Design Element                        | Description                                                                 |
| ------------------------------------- | --------------------------------------------------------------------------- |
| **Role-Playing**                      | Set different expert identities in global and local tasks to activate AI's domain knowledge. |
| **Task Decomposition**                 | Break down tasks into multiple stages (Stage) and steps (Task) with clear hierarchy. |
| **Precision**                         | All operations are described in imperative language to avoid ambiguity and uncertainty. |
| **Thinking Framework**                | Guide AI to analyze problems in a structured way through expert inner monologue. |
| **Completion Criteria**               | Clearly define the output and verification conditions for each stage to ensure task closure. |
| **Rich Output**                       | Require multi-dimensional expressions such as Markdown tables, Mermaid diagrams, SQL and pseudocode to enhance comprehensibility and verifiability. |

---

## 📖 Detailed Explanation of Core Features (Using Database Table Index Analysis as an Example)

### 1. Deep Application of Role-Playing

#### 1.1 Global Role
At the beginning of the conversation, set AI as **"top-tier Database Administrator (DBA) and Backend Performance Engineer"**, establishing a professional tone from the start.

#### 1.2 Contextual Roles
Further refine role positioning in each analysis step:
- **Architect** (Step 1: Bird's-eye view of the whole)
- **DBA** (Step 2: Deep dive into performance)
- **Final Decision Maker** (Step 3: Weigh pros and cons)

This layered role-playing greatly activates the model's professional thinking, making its reasoning process closer to real experts.

---

### 2. Clear Task Segmentation (Task Decomposition)

#### 2.1 Step-by-Step Structure
The entire analysis is broken down into three clear steps with clear hierarchy.

#### 2.2 Logical Progression
The analysis process strictly follows the expert's solution path:

| Step | Name           | Goal                    |
| ---- | -------------- | ----------------------- |
| Step 1 | Scenario Classification | Identify database usage scenarios |
| Step 2 | Query Analysis | Deep analysis of performance bottlenecks |
| Step 3 | Solution Design | Propose final index and optimization solutions |

Structurally, it achieves logical progression from macro → micro, from analysis → decision.

---

### 3. Introduction of "Thinking Framework"

#### 3.1 Framework Essence
This is the soul of the entire Prompt. It not only tells AI **"what to do"**, but also guides it **"how to think"**.

#### 3.2 Perspective Injection
Through role-playing inner monologue (e.g., "As an architect, I first need to get a bird's-eye view..."), help the model enter the correct analytical thinking path.

#### 3.3 Guiding Questions
The framework embeds concrete question prompts, such as:
- "Is the WHERE condition key?"
- "Can we seek covering indexes?"

This is like an expert-level Checklist, ensuring systematic and comprehensive analysis, avoiding missing key elements.

---

### 4. Precision and Unambiguity of Instructions

#### 4.1 Intelligent Variable Recognition
Require the model to intelligently recognize the naming style of `{{TABLE_NAME}}` (Pascal case, camelCase, etc.),
adapt to diverse ORM scenarios, thereby enhancing the robustness of the Prompt.

#### 4.2 Input-Output Constraints
Each step clearly specifies:
- **Input content**: such as `@codebase` or SQL paragraphs
- **Output format**: such as Markdown tables, lists, SQL code blocks

Ensuring results have **predictability** and **verifiability**.

---

### 5. Clear Delivery Standards (Verifiable Deliverables)

#### 5.1 Step-by-Step Delivery
Each step must generate clear, structured output formats.

#### 5.2 Final Deliverables
The final step (Step 3) outputs a complete index design solution:
- Includes `CREATE INDEX` SQL statements
- Provides **design rationale** and logical connection to the analysis results of the first two steps
- Forms a **closed-loop analysis chain**

---

### 6. Rich Output Formatting Requirements

#### 6.1 Readability and Structure
Require AI to use:
- **Markdown tables**
- **Formatted SQL code blocks**

---

## 🧩 Role Definitions

| Role              | Description                                                                 |
| ----------------- | --------------------------------------------------------------------------- |
| 🧑‍💻 **Global Role** | "Software Analyst" - Responsible for coordinating overall task flow and structure design. |
| 🧠 **Contextual Role** | Switch to more specific roles in each stage, such as "Senior DBA", "Performance Engineer" or "Architect". |
| 📊 **Reviewer Role** | Responsible for checking output format and analysis completeness according to completion criteria. |

---

## ⚙️ Usage Instructions

### 1️⃣ Activate Rule

Enter in the **Cursor / ChatGPT** dialog:

```
Enable rule: Universal Database Table Index Analysis
```

### 2️⃣ Specify Target Table

Enter the command:

```
Run index analysis rule for tb_user_profile table
```

> AI will scan all code files referencing this table based on the current `@codebase` context and initiate three-phase analysis.

---

## 🧱 Analysis Structure Overview

| Stage      | Name                    | Core Goal                                    | Output Format      |
| ---------- | ----------------------- | -------------------------------------------- | ------------------ |
| **Step 1** | Operation Scenario Classification & Load Assessment | Clarify table usage scenarios, operation types and load intensity | Markdown table     |
| **Step 2** | Query Pattern Deep Analysis | Identify query bottlenecks and potential index candidate fields | List & analysis notes |
| **Step 3** | Final Index Solution & SQL | Output deployable index solution with rationale | SQL + explanation text |

---

## 🧠 Prompt Main Content

### Rule Name: Universal Database Table Index Analysis

---

#### Step 1: Operation Scenario Classification & Load Assessment

**🎯 Goal:**

Identify the business usage scenarios and database load types (read-intensive / write-intensive / mixed load) of `{{TABLE_NAME}}`.

**🧩 Thinking Framework:**

> "As an architect, I need to globally scan the usage patterns of `{{TABLE_NAME}}`.
> I need to identify the business intent, type (SELECT / INSERT / UPDATE / DELETE), call frequency, and key fields of each operation."

**📤 Output Format (Markdown table):**

| Business Scenario Description | Operation Type | Key Fields           | Estimated Frequency | Source File Reference                    |
| ----------------------------- | -------------- | -------------------- | ------------------- | ---------------------------------------- |
| User login verification       | Read           | user_id, email       | High                | src/services/authService.ts             |
| Update user profile           | Write          | user_id, updated_at  | Medium              | src/controllers/profileController.js     |

---

#### Step 2: Query Pattern Deep Analysis

**🎯 Goal:**

Analyze all **read operations** queries related to this table, identify optimizable index field combinations.

**🧩 Thinking Framework:**

> "I need to look at each query like a DBA:
>
> * Which fields appear most frequently in WHERE conditions?
> * Can ORDER BY / GROUP BY be optimized through indexes?
> * What are the join fields in JOINs?
> * Are there scenarios where covering queries can be achieved through composite indexes?"

**📤 Output Format (Markdown list):**

* **Query Pattern:** Filter active users based on user status and role
* **Index Candidate:** `(status, role, last_login_time)`

  > Rationale: `status` and `role` are high-frequency combinations in WHERE, `last_login_time` is used for sorting. This index can significantly reduce scan volume and form a covering index.

---

#### Step 3: Final Index Solution & SQL

**🎯 Goal:**

Balance read-write performance, generate final deployable index creation statements.

**🧩 Thinking Framework:**

> "More indexes mean slower writes. I want to cover the most scenarios with the fewest indexes.
> Merge candidate indexes, leverage the leftmost prefix principle, avoid redundancy."

**📤 Output Format (SQL + Rationale):**

```sql
/* Index 1: Optimize active user queries */
CREATE INDEX idx_status_role_login ON {{TABLE_NAME}} (status, role, last_login_time DESC);
```

> **Rationale:** Supports the "query active users by status and role" scenario identified in Step 2. This index balances filtering and sorting, covering high-frequency read operations.

```sql
/* Index 2: Optimize user profile update conflict detection */
CREATE INDEX idx_userid_updated ON {{TABLE_NAME}} (user_id, updated_at);
```

> **Rationale:** This index can accelerate duplicate detection logic before updates, balancing write performance with read efficiency.

---

## ✅ Completion Criteria

* [x] Generate Markdown table (Step 1)
* [x] Output index candidate analysis list (Step 2)
* [x] Generate at least 1 `CREATE INDEX` statement with explanation (Step 3)
* [x] All output content can be traced back to actual source code references

---

## 📁 Recommended Project Structure (Optional)

```
multi-agent-db-index-analysis/
├── README.md
├── prompts/
│   ├── rule_db_index_analysis.md     ← This document
│   └── rule_api_latency_analysis.md  ← Other rule examples
└── examples/
    ├── tb_user_profile_analysis.md
    └── tb_order_record_analysis.md
```

---

## 🧭 Extended Applications

This structured Prompt template is not only suitable for database index analysis, but can also be extended to:

* Code architecture dependency analysis
* Performance bottleneck identification
* Log pattern optimization
* Microservice topology reconstruction

---

## 📜 License

This project follows the MIT License, can be freely reused and modified, but please retain author and source repository information when referencing.

