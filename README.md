# Week 2 -> Day 3 ->  Prompt Engineering - RTCFR
---

## Table of Contents

1. [What is a Prompt?](#what-is-a-prompt)
   - [System_Prompt_vs_User_Prompt](System_Prompt_vs_User_Prompt.md)
2. [What is Prompt Engineering?](#what-is-prompt-engineering)
3. [Why Prompt Engineering Matters](#why-prompt-engineering-matters)
4. [The RTCFR Framework](#the-rtcfr-framework)
   - [R — Role](#r--role)
   - [T — Task](#t--task)
   - [C — Context](#c--context)
   - [F — Format](#f--format)
   - [R — Reference / Restrictions](#r--reference--restrictions)
5. [RTCFR Combined Example](#rtcfr-combined-example)
6. [Best Practices Summary](#best-practices-summary)

---

## What is a Prompt?

In the world of Artificial Intelligence — especially with **Large Language Models (LLMs)** like GPT, Claude, Gemini, or LLaMA — a **prompt** is the input or instruction you give to the AI model to get a response.

Think of it as a question, command, or conversation starter that tells the AI:
- **What** to do
- **How** to do it
- **What tone or style** to use
- **What constraints** to respect

### Simple Analogy

> Imagine you're hiring a new employee. A **prompt** is the job brief you hand them. A vague brief → vague output. A crisp, detailed brief → excellent output.

### Types of Prompts

| Type | Description | Example |
|---|---|---|
| **Zero-shot** | No examples given | "Translate this to French: Hello" |
| **One-shot** | One example given | "Cat → Chat. Dog → ?" |
| **Few-shot** | Multiple examples given | 3–5 input/output pairs before the task |
| **Instructional** | Explicit step-by-step instructions | "List 5 steps to bake a cake." |
| **Conversational** | Dialog-style back and forth | Chat messages in sequence |
| **System Prompt** | Background instruction to set AI behavior | "You are a legal assistant. Always be formal." |

---

## What is Prompt Engineering?

**Prompt Engineering** is the art and science of designing, refining, and optimizing prompts to get the most accurate, useful, and reliable responses from AI models.

It is a **skill-based discipline** that sits at the intersection of:
- Linguistics (how you word things)
- Psychology (how models "think")
- Domain expertise (what you know about the subject)
- Iterative testing (trying variations)

### Core Goals of Prompt Engineering

- ✅ Get **accurate and relevant** outputs
- ✅ Reduce **hallucinations** (AI making things up)
- ✅ Control **tone, style, and format**
- ✅ Maximize **consistency** across runs
- ✅ Minimize **token usage** (cost efficiency)

### Who Uses Prompt Engineering?

- Developers integrating AI into products
- Data scientists building AI pipelines
- Content creators using AI tools
- Business analysts automating reports
- Researchers running AI experiments

---

## Why Prompt Engineering Matters

The same AI model can produce **vastly different results** based purely on how you phrase your prompt.

### Example: Bad vs. Good Prompt

**Bad Prompt:**
```
Tell me about climate.
```
*Result: A vague, broad 500-word essay covering everything from weather to politics.*

---

**Good Prompt:**
```
You are an environmental scientist. In 3 bullet points, explain the main causes
of climate change to a 10-year-old child. Use simple language and avoid jargon.
```
*Result: Three clear, child-friendly bullet points — precisely what was needed.*

The difference? **Prompt Engineering.**

---

## The RTCFR Framework

**RTCFR** is one of the most powerful and structured frameworks in prompt engineering. It ensures you never leave the AI guessing by covering five critical dimensions of a great prompt.

```
R — Role
T — Task
C — Context
F — Format
R — Reference / Restrictions
```

Each element adds a layer of precision to your prompt.

---

## R — Role

### What it is

The **Role** element tells the AI *who it should be* or *what persona to adopt* when responding. This dramatically shifts the model's tone, vocabulary, depth, and approach.

### Why it matters

LLMs are trained on vast data. When you assign a role, you activate a specific "mode" of reasoning, expertise, and communication style.

### Syntax Pattern

```
You are a [role/persona]. ...
Act as a [profession] with [X years] of experience in [domain].
```

---

### Example 1 — Without Role

**Prompt:**
```
Explain machine learning.
```

**Output:**
> Machine learning is a subset of AI where systems learn from data to make decisions...

*(Generic textbook-style response)*

---

### Example 2 — With Role (Expert Scientist)

**Prompt:**
```
You are a Senior Machine Learning Engineer with 15 years of experience at top tech
companies. Explain machine learning.
```

**Output:**
> Machine learning fundamentally comes down to optimization — you're defining a loss function
> and using gradient descent (or variants) to minimize it. In production systems, the real
> challenge is rarely the model itself but data quality, feature engineering, and distribution
> shift over time...

*(Deep, practical, professional response)*

---

### Example 3 — With Role (Teacher for Kids)

**Prompt:**
```
You are a fun and friendly science teacher for 8-year-olds. Explain machine learning.
```

**Output:**
> Imagine you're teaching a puppy to sit! At first, it doesn't know what "sit" means.
> But every time it sits, you give it a treat. Soon it learns the pattern! Machine learning
> works the same way — we show computers lots of examples until they learn the pattern too! 🐶

*(Simple, engaging, child-appropriate)*

---

**Key Takeaway:** The same question. Three completely different, highly useful responses — all driven by the **Role**.

---

## T — Task

### What it is

The **Task** is the explicit instruction — the *what you want the AI to do*. It should be a clear, specific, actionable directive.

### Why it matters

Vague tasks lead to vague outputs. The more precise your task, the more focused and useful the response.

### Syntax Pattern

```
Your task is to [action verb] [specific object/topic].
Write / Summarize / List / Compare / Analyze / Create / Translate / Fix...
```

---

### Example 1 — Vague Task

**Prompt:**
```
Do something with this product review:
"The battery dies in 2 hours. Terrible build quality. Returned it."
```

**Output:**
> This seems like a negative review. The customer was unhappy with the battery and build quality.

*(Unclear what was wanted — AI guesses)*

---

### Example 2 — Specific Task

**Prompt:**
```
Your task is to analyze the following product review and:
1. Identify the top 2 customer complaints
2. Suggest one product improvement for each complaint
3. Rate overall sentiment as: Positive / Neutral / Negative

Review: "The battery dies in 2 hours. Terrible build quality. Returned it."
```

**Output:**
> **Complaint 1:** Battery life — *Improvement: Upgrade to a 5000mAh battery cell*
> **Complaint 2:** Build quality — *Improvement: Use reinforced aluminum casing*
> **Sentiment:** Negative

*(Precise, structured, directly actionable)*

---

### Example 3 — Task in Code Generation

**Prompt:**
```
Your task is to write a Python function that:
- Accepts a list of integers
- Returns only the even numbers
- Includes a docstring and one usage example
```

**Output:**
```python
def filter_even(numbers):
    """
    Filters and returns even numbers from a list.

    Args:
        numbers (list): A list of integers.

    Returns:
        list: A list containing only even integers.
    """
    return [n for n in numbers if n % 2 == 0]

# Example usage
print(filter_even([1, 2, 3, 4, 5, 6]))  # Output: [2, 4, 6]
```

---

**Key Takeaway:** A well-defined **Task** eliminates ambiguity and gives the AI a precise target to aim for.

---

## C — Context

### What it is

**Context** provides background information, situational details, or relevant data the AI needs to tailor its response appropriately. It answers *why, who, where, and what surrounds* the task.

### Why it matters

Without context, the AI operates in a vacuum. Context anchors the response to your specific reality — your audience, your industry, your constraints, your goals.

### Syntax Pattern

```
Background: [relevant information]
The audience is [describe audience].
This is for [purpose/use case].
The situation is: [explain circumstances]
```

---

### Example 1 — Without Context

**Prompt:**
```
Write an email about a project delay.
```

**Output:**
> Dear Team,
> I wanted to inform you that our project has been delayed. We are working to resolve
> the issues. Thank you for your patience.

*(Generic, no substance)*

---

### Example 2 — With Context

**Prompt:**
```
Context: I am a project manager at a software startup. We promised delivery of a
mobile app to our client (a retail company) by March 1st. Due to unexpected API
integration issues with their legacy ERP system, we need 2 more weeks.
The client is a long-term partner and is generally understanding.

Write an email about a project delay.
```

**Output:**
> Subject: Project Update — Revised Delivery Timeline
>
> Dear [Client Name],
>
> I hope this message finds you well. I'm writing to provide a transparent update
> on the MyShop mobile app project.
>
> During final integration testing, our team encountered compatibility issues between
> the new app and your existing ERP system's API endpoints. Resolving this correctly —
> without compromising data integrity — requires an additional two weeks of engineering work.
>
> **Revised delivery date: March 15th**
>
> We remain fully committed to delivering a seamless, high-quality product. I'd welcome
> a quick call this week to walk you through our resolution plan.
>
> Warm regards,
> [Your Name]

*(Professional, specific, appropriate in tone)*

---

### Example 3 — Context in Data Analysis

**Prompt:**
```
Context: I work at an e-commerce company. Our sales dropped 30% in January 2025.
We ran a 20% discount campaign in December 2024. Our main products are electronics.

Why might our January sales have dropped?
```

**Output:**
> Several factors likely contributed to the January dip:
> 1. **Post-holiday demand hangover** — customers heavily purchased in December during your discount campaign, leaving little immediate demand in January.
> 2. **Discount pull-forward effect** — the 20% promotion likely accelerated purchases that would have naturally occurred in January.
> 3. **Electronics seasonality** — consumer electronics typically peak in Q4 (gifting season) and cool significantly in Q1.
> 4. **Budget exhaustion** — post-holiday consumer spending generally drops as credit card bills arrive.

*(Contextually accurate, specific to the business situation)*

---

**Key Takeaway:** **Context** is the difference between a generic answer and one that feels tailor-made for your exact situation.

---

## F — Format

### What it is

**Format** specifies the structure, style, length, and presentation of the output. It tells the AI *how the answer should look*.

### Why it matters

Even a perfect answer can be useless if it's in the wrong format. A developer needs JSON. A manager needs a table. A student needs bullet points. Format makes output immediately usable.

### Syntax Pattern

```
Respond in [format: bullet points / table / JSON / markdown / numbered list].
Keep the response under [X words / X sentences].
Use [headers / bold / code blocks] where appropriate.
```

---

### Example 1 — No Format Specified

**Prompt:**
```
Compare Python and JavaScript.
```

**Output:**
> Python and JavaScript are both popular languages. Python is used for data science and
> backend development while JavaScript is used for web development. Python uses indentation
> while JavaScript uses curly braces... [continues in plain paragraph form]

*(Readable, but hard to scan or use in a presentation)*

---

### Example 2 — Table Format

**Prompt:**
```
Compare Python and JavaScript. Respond in a markdown table with columns:
Feature, Python, JavaScript. Cover: primary use, typing, syntax style, performance, community.
```

**Output:**

| Feature | Python | JavaScript |
|---|---|---|
| Primary Use | Data science, backend, scripting | Web frontend, backend (Node.js) |
| Typing | Dynamically typed | Dynamically typed |
| Syntax Style | Indentation-based | Curly brace-based |
| Performance | Moderate (fast with C extensions) | Fast (V8 engine) |
| Community | Huge (ML/AI focused) | Huge (web-dev focused) |

---

### Example 3 — JSON Format (for developers)

**Prompt:**
```
List 3 programming languages with their primary use case and year created.
Return the result as a valid JSON array only. No explanation.
```

**Output:**
```json
[
  { "language": "Python", "primary_use": "Data Science & AI", "year_created": 1991 },
  { "language": "JavaScript", "primary_use": "Web Development", "year_created": 1995 },
  { "language": "Rust", "primary_use": "Systems Programming", "year_created": 2010 }
]
```

---

### Example 4 — Word Limit Format

**Prompt:**
```
Explain quantum computing in exactly 3 sentences. Use plain English. No jargon.
```

**Output:**
> Classical computers store information as bits — either 0 or 1. Quantum computers use
> "qubits" that can be 0, 1, or both at the same time, allowing them to explore many
> solutions simultaneously. This makes them incredibly powerful for complex problems like
> drug discovery, cryptography, and optimization.

---

**Key Takeaway:** **Format** makes the output plug-and-play — ready to use, present, or integrate without extra editing.

---

## R — Reference / Restrictions

### What it is

The second **R** in RTCFR covers two closely related concepts:

- **Reference:** Source material, data, examples, or knowledge the AI should draw from or stay grounded in.
- **Restrictions:** Boundaries, rules, exclusions, or constraints the AI must respect.

### Why it matters

Without references, AI may hallucinate facts. Without restrictions, it may go off-topic, use inappropriate language, or include irrelevant content.

### Syntax Pattern

```
Base your response only on the following data: [paste data]
Do NOT include [X, Y, Z].
Avoid [technical jargon / opinions / specific topics].
Only use information from the text provided below.
```

---

### Example 1 — Reference (Grounding in Source Material)

**Prompt:**
```
Reference the following product description ONLY. Do not add any external information.
Write a 3-sentence marketing tagline.

Product Description: "The NovaSleep Pro is a smart pillow with built-in sensors that
track sleep cycles, detect snoring, and gently vibrate to encourage better sleep positions.
It connects via Bluetooth to the NovaSleep app on iOS and Android."
```

**Output:**
> Sleep smarter, not harder — NovaSleep Pro tracks your cycles, detects snoring, and
> guides you to your best rest automatically. Seamlessly synced to your phone, it's your
> personal sleep coach built right into your pillow. Wake up refreshed, every single morning.

*(Stays strictly within product info — no invented claims)*

---

### Example 2 — Restrictions (What NOT to do)

**Prompt:**
```
Write 5 tips for healthy eating.

Restrictions:
- Do NOT mention any specific diets (keto, vegan, paleo, etc.)
- Do NOT use the word "calories"
- Keep each tip under 20 words
- Write for a general adult audience
```

**Output:**
> 1. Fill half your plate with vegetables at every meal.
> 2. Drink water before meals to stay hydrated and avoid overeating.
> 3. Choose whole grains over refined grains whenever possible.
> 4. Eat slowly and stop when you feel comfortably full.
> 5. Limit processed snacks and opt for fresh fruits or nuts instead.

*(All restrictions respected perfectly)*

---

### Example 3 — Reference + Restrictions Combined

**Prompt:**
```
You are a financial assistant.

Reference: Use only the Q3 2024 data below to answer:
- Revenue: ₹48 Crore
- Expenses: ₹31 Crore
- Net Profit: ₹17 Crore
- Growth vs Q2: +12%

Task: Write a 4-sentence executive summary of Q3 performance.

Restrictions:
- Do NOT speculate about Q4
- Do NOT mention competitor comparisons
- Use formal business language
```

**Output:**
> The company delivered strong financial performance in Q3 2024, recording a revenue of
> ₹48 Crore against total expenses of ₹31 Crore. Net profit for the quarter stood at
> ₹17 Crore, reflecting healthy operational efficiency. Quarter-on-quarter growth of 12%
> underscores sustained momentum in core business activities. The management remains focused
> on maintaining this trajectory through disciplined cost management and continued revenue expansion.

*(Accurate, grounded in data, restrictions fully honored)*

---

**Key Takeaway:** **References** keep the AI honest and factual. **Restrictions** keep it in bounds. Together they produce trustworthy, focused output.

---

## RTCFR Combined Example

Here's a complete, real-world prompt using all five RTCFR elements together:

```
[ROLE]
You are an experienced HR consultant specializing in tech industry hiring.

[TASK]
Write a job description for a Senior Data Scientist position.

[CONTEXT]
The company is a 3-year-old AI startup in Bangalore with 80 employees.
We are hiring for our product analytics team. The team works on recommendation
systems and NLP models. The company culture is collaborative and fast-paced.

[FORMAT]
Structure the job description with these sections:
- About the Role (3 sentences)
- Key Responsibilities (5 bullet points)
- Required Skills (5 bullet points)
- Nice to Have (3 bullet points)
- What We Offer (3 bullet points)
Keep the total length under 400 words. Use professional but friendly language.

[RESTRICTIONS]
- Do NOT mention salary figures
- Do NOT use buzzwords like "rockstar", "ninja", "guru"
- Do NOT include discriminatory language
- Only include skills relevant to data science and ML
```

This single, well-engineered prompt will produce a complete, professional, on-brand job description — with zero revision needed.

---

## Best Practices Summary

| Principle | Do ✅ | Avoid ❌ |
|---|---|---|
| Be Specific | "List 5 causes in bullet points" | "Tell me about causes" |
| Assign a Role | "You are a tax lawyer..." | No persona assigned |
| Provide Context | Explain audience and purpose | Assume AI knows your situation |
| Define Format | Specify table, JSON, bullets | Leave format open-ended |
| Set Restrictions | "Do NOT include X" | Hope AI stays on track |
| Iterate | Refine based on output | Accept first result as final |
| Use Examples | Show a sample output | Describe output vaguely |

---

## Quick Reference Card

```
┌─────────────────────────────────────────────────────────┐
│                  RTCFR PROMPT FRAMEWORK                  │
├──────────┬──────────────────────────────────────────────┤
│  R - Role│ Who should the AI be?                        │
│  T - Task│ What should the AI do?                       │
│  C - Ctx │ What background info does the AI need?       │
│  F - Fmt │ How should the output look?                  │
│  R - Ref │ What sources/rules should the AI follow?     │
└──────────┴──────────────────────────────────────────────┘
```

---

*Great prompts are not written — they are engineered.*
*Master RTCFR and you master the art of communicating with AI.*


# RTCFR Prompt Engineering — Real World Use Cases
### 3 Detailed, Practical Examples Across Industries

---

## Table of Contents

1. [Use Case 1 — Customer Support Automation (E-Commerce)](#use-case-1--customer-support-automation-e-commerce)
2. [Use Case 2 — Medical Report Summarization (Healthcare)](#use-case-2--medical-report-summarization-healthcare)
3. [Use Case 3 — Code Review Assistant (Software Development)](#use-case-3--code-review-assistant-software-development)

---

## Quick RTCFR Recap

Before diving in, here is a quick reminder of the five elements:

```
R — Role         → Who the AI should be
T — Task         → What the AI should do
C — Context      → Background info the AI needs
F — Format       → How the output should look
R — Reference /  → Source material to use + rules to follow
    Restrictions
```

---

---

# Use Case 1 — Customer Support Automation (E-Commerce)

## Scenario

**Company:** ShopNest — a mid-sized Indian e-commerce platform selling electronics and home appliances.

**Problem:** The customer support team receives 500+ emails daily. Common complaints include delayed deliveries, wrong items received, and refund status queries. Agents spend hours drafting repetitive replies.

**Goal:** Use an AI model with a carefully engineered RTCFR prompt to automatically draft professional, empathetic, and policy-compliant email replies — reducing agent effort by 70%.

---

## RTCFR Breakdown

### R — Role

```
You are a senior customer support specialist at ShopNest, a trusted Indian
e-commerce company. You are known for being empathetic, solution-oriented,
and always maintaining a warm, professional tone with customers.
```

**Why this Role?**
Assigning a "senior specialist" role activates a tone that is experienced, calm, and reassuring — not robotic or defensive. The brand name grounds the AI in a specific identity. This prevents generic, cold corporate language and encourages human-like empathy.

---

### T — Task

```
Your task is to read the customer's complaint email below and draft a
complete, professional reply that:
1. Acknowledges the customer's frustration
2. Provides the current status or explanation
3. States the resolution or next steps clearly
4. Ends with a warm, reassuring closing
```

**Why this Task?**
Breaking the task into 4 numbered sub-tasks ensures the AI doesn't skip any critical element. A vague task like "reply to the email" would miss the empathy step or the resolution step. The numbered breakdown acts like a checklist the AI must fulfill.

---

### C — Context

```
Context:
- ShopNest's standard refund processing time is 5-7 business days.
- If a wrong item is delivered, a reverse pickup is arranged within 48 hours
  and a replacement is shipped within 3 business days after pickup.
- The customer's order ID is #SNT-209847.
- Our internal system shows the refund was initiated on June 10th and is
  currently in the bank processing stage.
- The customer has been shopping with ShopNest for 3 years (loyal customer).
```

**Why this Context?**
Without this context, the AI would write a hollow reply: "We are looking into your issue." With it, the AI can write a specific, factually grounded response mentioning the exact refund date, the 5-7 day timeline, and even acknowledge the customer's loyalty — making the response feel personal and trustworthy.

---

### F — Format

```
Format:
- Start with "Dear [Customer Name],"
- Use 3-4 short paragraphs (no bullet points in the email body)
- Maintain a warm, professional tone — not overly formal or casual
- End with: "Warm regards, ShopNest Customer Support Team"
- Total length: 150-200 words
```

**Why this Format?**
Customer support emails should feel human, not like a system-generated wall of text. Specifying short paragraphs, a warm sign-off, and a word limit ensures the output is clean, readable, and ready to send without heavy editing. Without format instructions, the AI might produce a bullet-point reply that feels impersonal.

---

### R — Reference / Restrictions

```
Reference: Use only the context provided above. Do not invent order details,
dates, or policies not mentioned here.

Restrictions:
- Do NOT make promises beyond the stated policy (e.g., do not promise
  same-day resolution unless stated)
- Do NOT use "We apologize for the inconvenience" as an opener — it sounds
  hollow; instead, acknowledge the specific issue directly
- Do NOT mention competitor brands
- Do NOT use legal or technical jargon
```

**Why these Restrictions?**
The classic opener "We apologize for the inconvenience" has been so overused that customers find it dismissive. By banning it explicitly, the AI is forced to write something more genuine. Restricting invented promises protects the company legally. Grounding replies in provided facts prevents hallucinations.

---

## The Full Engineered Prompt

```
You are a senior customer support specialist at ShopNest, a trusted Indian
e-commerce company. You are known for being empathetic, solution-oriented,
and always maintaining a warm, professional tone with customers.

Your task is to read the customer's complaint email below and draft a
complete, professional reply that:
1. Acknowledges the customer's frustration
2. Provides the current status or explanation
3. States the resolution or next steps clearly
4. Ends with a warm, reassuring closing

Context:
- ShopNest's standard refund processing time is 5-7 business days.
- If a wrong item is delivered, a reverse pickup is arranged within 48 hours
  and a replacement is shipped within 3 business days after pickup.
- The customer's order ID is #SNT-209847.
- Internal system: refund initiated on June 10th, currently in bank processing stage.
- The customer has been shopping with ShopNest for 3 years (loyal customer).

Format:
- Start with "Dear [Customer Name],"
- Use 3-4 short paragraphs (no bullet points in the email body)
- Warm, professional tone
- End with: "Warm regards, ShopNest Customer Support Team"
- Total length: 150-200 words

Reference: Use only the context provided above.

Restrictions:
- Do NOT invent order details, dates, or policies not mentioned.
- Do NOT use "We apologize for the inconvenience" as an opener.
- Do NOT make promises beyond stated policy.
- Do NOT use legal or technical jargon.

--- Customer Email ---
Subject: Where is my refund?? It's been 10 days!

"I ordered a mixer grinder, you sent me the wrong model. I returned it
10 days ago and still haven't received my refund. This is completely
unacceptable. I want my money back immediately."
```

---

## AI Output

> Dear Priya,
>
> Thank you for reaching out, and I completely understand how frustrating it must feel
> to wait this long after returning a wrong item — especially when you've trusted us
> with your purchases for so long.
>
> I've checked your order #SNT-209847, and I can confirm that your refund was
> successfully initiated on June 10th. It is currently in the final bank processing
> stage, which typically takes 5-7 business days from initiation. You should see the
> amount credited to your account by June 17th at the latest.
>
> If the refund does not reflect by then, please reply to this email and we will
> escalate it directly with our payments team on priority.
>
> We truly value your continued trust in ShopNest and are committed to making
> this right for you.
>
> Warm regards,
> ShopNest Customer Support Team

---

## Impact of RTCFR

| Without RTCFR | With RTCFR |
|---|---|
| Generic "we're looking into it" reply | Specific refund date and status mentioned |
| No empathy, robotic tone | Warm, loyal-customer acknowledgment |
| May invent wrong timelines | Strictly follows the 5-7 day policy |
| Manual drafting takes hours | Ready in seconds, agent just reviews |

---
---

# Use Case 2 — Medical Report Summarization (Healthcare)

## Scenario

**Organization:** CarePoint Hospitals — a multi-specialty hospital chain.

**Problem:** Doctors spend 15-20 minutes per patient reading dense lab reports and radiology findings before consultations. For high-volume OPDs (100+ patients/day), this is unsustainable.

**Goal:** Use an AI model with a carefully engineered RTCFR prompt to summarize complex medical reports into a clean, concise 1-page brief that a doctor can review in under 2 minutes — without losing clinical accuracy.

---

## RTCFR Breakdown

### R — Role

```
You are a highly experienced clinical documentation specialist with 20 years
of experience working in multi-specialty hospitals. You have deep knowledge
of interpreting lab reports, radiology findings, and patient vitals. You
assist consulting physicians by preparing accurate, concise patient briefs
before appointments.
```

**Why this Role?**
A "clinical documentation specialist" role activates medical vocabulary, structured thinking, and an understanding of what a doctor actually needs before seeing a patient. This is very different from a "general assistant" role, which might over-explain basic medical terms or miss clinical red flags entirely.

---

### T — Task

```
Your task is to read the patient's complete medical report below and prepare
a structured pre-consultation brief for the attending physician that includes:
1. Patient snapshot (age, gender, chief complaint)
2. Key abnormal findings (lab values outside normal range, flagged clearly)
3. Normal findings (brief, to confirm what is clear)
4. Radiology summary (if present)
5. Suggested areas of focus for the doctor's consultation
```

**Why this Task?**
Doctors don't need the AI to re-read the whole report — they need it synthesized. The 5-point task structure mirrors exactly what a physician looks for before a consult: who is the patient, what's wrong, what's okay, what do scans show, and where should I focus? This task is modeled on actual clinical workflow.

---

### C — Context

```
Context:
- Patient: Rajesh Mehta, 54-year-old male
- Chief Complaint: Fatigue, mild shortness of breath on exertion for 3 weeks
- Attending Physician: Dr. Ananya Sharma, Cardiologist
- Known history: Type 2 Diabetes (on Metformin 500mg twice daily)
- No prior cardiac events on record
- Reports are from a routine annual checkup with additional cardiac panel
  requested by the GP
```

**Why this Context?**
Knowing the attending physician is a cardiologist tells the AI to emphasize cardiac and metabolic findings above all else. Knowing the patient's diabetes history means the AI should flag HbA1c and glucose values specifically. Without this context, a summary might bury the most critical cardiac markers under routine CBC data.

---

### F — Format

```
Format:
- Use clearly labeled sections with bold headers
- For abnormal values: show the result, the normal range, and flag with a warning marker
- For normal values: list briefly in a single sentence or small table
- Radiology: 2-3 sentence summary
- Consultation focus: 3-5 bullet points maximum
- Total length: fit within one A4 page (approx. 300-350 words)
- Use clinical but readable language suitable for a specialist physician
```

**Why this Format?**
Doctors scan, they don't read. Bold headers, warning flags, and a strict one-page limit respect the physician's time. Visual flags on abnormal values mean a doctor's eye goes directly to the critical items. This format is designed to reduce cognitive load, not add to it.

---

### R — Reference / Restrictions

```
Reference: Base the summary strictly on the lab report data provided below.
Do not add clinical opinions, diagnoses, or treatment suggestions — those
are the physician's domain.

Restrictions:
- Do NOT suggest a diagnosis (e.g., do not write "This suggests heart failure")
- Do NOT recommend medications or treatments
- Do NOT omit any flagged abnormal value, even if minor
- Do NOT use abbreviations without expanding them on first use
- Maintain strict patient confidentiality language
```

**Why these Restrictions?**
This is legally and ethically critical. AI must not diagnose — that is the licensed physician's responsibility. Restricting diagnosis language prevents liability. Banning omission of abnormal values ensures nothing clinically important is glossed over. Expanding abbreviations ensures even a covering doctor unfamiliar with the patient can read the brief without confusion.

---

## The Full Engineered Prompt

```
You are a highly experienced clinical documentation specialist with 20 years
of experience in multi-specialty hospitals. You assist consulting physicians
by preparing accurate, concise patient briefs before appointments.

Your task is to read the patient's complete medical report below and prepare
a structured pre-consultation brief for the attending physician that includes:
1. Patient snapshot (age, gender, chief complaint)
2. Key abnormal findings (flagged with warning markers, with normal range shown)
3. Normal findings (brief summary)
4. Radiology summary (if present)
5. Suggested areas of focus for the doctor's consultation

Context:
- Patient: Rajesh Mehta, 54-year-old male
- Chief Complaint: Fatigue, mild shortness of breath on exertion for 3 weeks
- Attending Physician: Dr. Ananya Sharma, Cardiologist
- Known history: Type 2 Diabetes Mellitus (T2DM), on Metformin 500mg twice daily
- No prior cardiac events on record
- Reports: Annual checkup + additional cardiac panel

Format:
- Bold section headers
- Flag all abnormal values with result and normal range
- One A4 page, 300-350 words
- Clinical but readable language for a specialist

Reference: Use only the report data below. No external assumptions.

Restrictions:
- Do NOT suggest a diagnosis
- Do NOT recommend medications or treatments
- Do NOT omit any abnormal finding
- Expand all abbreviations on first use

--- Patient Report Data ---
CBC: Hemoglobin 11.2 g/dL (Normal: 13.5-17.5), WBC 7,400/uL (Normal),
Platelets 210,000/uL (Normal)
Lipid Panel: LDL 162 mg/dL (Normal: <100), HDL 38 mg/dL (Normal: >40),
Triglycerides 210 mg/dL (Normal: <150), Total Cholesterol 240 mg/dL (Normal: <200)
Metabolic: HbA1c (Glycated Hemoglobin) 8.1% (Normal: <7.0 for diabetics),
Fasting Glucose 148 mg/dL (Normal: 70-100)
Cardiac Markers: Troponin I: 0.01 ng/mL (Normal: <0.04) — Normal
ECG: Mild left ventricular hypertrophy pattern noted. No acute ischemic changes.
Chest X-Ray: Mild cardiomegaly. Lung fields clear. No effusion.
```

---

## AI Output

> **Pre-Consultation Brief — Rajesh Mehta, 54M**
> *Prepared for: Dr. Ananya Sharma, Cardiologist*
>
> ---
>
> **Patient Snapshot**
> Rajesh Mehta, 54-year-old male. Presents with a 3-week history of fatigue and mild
> exertional breathlessness. Known Type 2 Diabetes Mellitus (T2DM) on Metformin 500mg
> twice daily. No prior cardiac events.
>
> ---
>
> **[!] Abnormal Findings**
>
> | Parameter | Result | Normal Range |
> |---|---|---|
> | [!] Hemoglobin (Hb) | 11.2 g/dL | 13.5-17.5 g/dL |
> | [!] LDL Cholesterol | 162 mg/dL | < 100 mg/dL |
> | [!] HDL Cholesterol | 38 mg/dL | > 40 mg/dL |
> | [!] Triglycerides | 210 mg/dL | < 150 mg/dL |
> | [!] Total Cholesterol | 240 mg/dL | < 200 mg/dL |
> | [!] HbA1c | 8.1% | < 7.0% (diabetic target) |
> | [!] Fasting Glucose | 148 mg/dL | 70-100 mg/dL |
>
> ---
>
> **Normal Findings**
> WBC (White Blood Cell count), Platelets, and Troponin I are all within normal limits,
> with no acute inflammatory or myocardial injury markers detected.
>
> ---
>
> **Radiology Summary**
> ECG shows a mild left ventricular hypertrophy (LVH) pattern with no acute ischemic
> changes. Chest X-ray reveals mild cardiomegaly with clear lung fields and no
> pleural effusion.
>
> ---
>
> **Suggested Areas of Focus for Consultation**
> - Evaluate mild anemia (Hb 11.2) in context of fatigue and exertional symptoms
> - Review dyslipidemia profile — significantly elevated LDL and total cholesterol
> - Assess glycemic control — HbA1c at 8.1% indicates suboptimal T2DM management
> - Correlate LVH pattern and mild cardiomegaly with the patient's symptom history
> - Consider functional assessment given exertional breathlessness presentation

---

## Impact of RTCFR

| Without RTCFR | With RTCFR |
|---|---|
| Full report re-printed or loosely paraphrased | Clean 1-page structured brief |
| Doctor must hunt for abnormal values | Warning flags make critical values instantly visible |
| AI may suggest a diagnosis (liability risk) | Strictly factual — no diagnosis offered |
| Generic medical summary | Tailored to a cardiologist's exact priorities |

---
---

# Use Case 3 — Code Review Assistant (Software Development)

## Scenario

**Team:** FinTrack — a 12-person fintech startup building a personal finance management app.

**Problem:** Junior developers submit pull requests that often contain bugs, security vulnerabilities, poor naming conventions, and inefficient logic. Senior engineers spend 2-3 hours per day reviewing code — time better spent building features.

**Goal:** Use an AI model with a carefully engineered RTCFR prompt to perform a thorough first-pass code review — catching bugs, security issues, and style violations — so senior engineers only need to do a final human review.

---

## RTCFR Breakdown

### R — Role

```
You are a Principal Software Engineer with 12 years of experience in backend
development, specializing in Python, RESTful API design, and fintech security
standards. You are meticulous, direct, and constructive in your code reviews.
You always explain *why* something is wrong, not just what is wrong.
```

**Why this Role?**
A "Principal Engineer" role brings seniority, security awareness, and a mentorship tone. The phrase "explains why, not just what" is critical — it instructs the AI to produce reviews that teach junior devs, not just criticize them. This transforms the AI from a linter into a mentor.

---

### T — Task

```
Your task is to perform a detailed code review of the Python function below.
Your review must cover:
1. Bugs — logic errors, incorrect outputs, edge cases not handled
2. Security vulnerabilities — especially around user inputs and data handling
3. Performance issues — inefficient loops, unnecessary operations
4. Code readability — naming conventions, comments, clarity
5. Best practice violations — PEP8, error handling, use of anti-patterns
For each issue found, provide: the line reference, the problem, and a
corrected code snippet.
```

**Why this Task?**
This task is structured like an actual engineering review rubric covering 5 dimensions. Asking for "line reference + problem + fix" for every issue means the output is immediately actionable — a junior dev can open the file and fix issues line by line. Without this structure, AI might give a general critique like "The code could be more secure" — which is useless.

---

### C — Context

```
Context:
- Language: Python 3.11
- Framework: FastAPI
- This function handles user login and returns a JWT (JSON Web Token)
- The app is a fintech product — security is the highest priority
- The codebase follows PEP8 conventions and uses type hints throughout
- Junior developer wrote this — feedback should be constructive and educational
- The team uses PostgreSQL with SQLAlchemy as the ORM
```

**Why this Context?**
Knowing this is a fintech login function immediately elevates security scrutiny to maximum. Knowing the junior dev wrote it shifts the tone to mentorship. Knowing the stack (FastAPI, SQLAlchemy, PEP8) means the AI reviews against the right standards — not generic Python, but this team's specific Python.

---

### F — Format

```
Format:
- Start with a brief overall assessment (2-3 sentences)
- Use numbered issues: Issue #1, Issue #2, etc.
- For each issue use this structure:
    Location: [line number or function section]
    Severity: [Critical / High / Medium / Low]
    Problem: [explain the issue and why it matters]
    Fix: [provide corrected code in a code block]
- End with a "Summary Scorecard" table rating the code on:
  Security, Readability, Performance, Best Practices (each out of 10)
```

**Why this Format?**
The severity rating (Critical/High/Medium/Low) helps the junior dev prioritize — fix Critical issues before touching Low ones. Separating Problem from Fix in distinct labeled blocks means the developer understands the issue before seeing the solution. The scorecard at the end gives a holistic sense of where to improve — not just for this function, but as a developer.

---

### R — Reference / Restrictions

```
Reference:
- PEP8 Python style guide
- OWASP Top 10 security vulnerabilities (especially A01-A03: broken access
  control, cryptographic failures, injection)
- FastAPI best practices for authentication
- JWT security best practices (short expiry, no sensitive data in payload)

Restrictions:
- Do NOT rewrite the entire function from scratch — review what is written
- Do NOT flag style preferences as bugs (e.g., single vs double quotes)
- Do NOT use condescending language — this is for a junior developer
- Focus only on the code provided; do not speculate about other files
```

**Why these Restrictions?**
Referencing OWASP Top 10 directs the AI to the gold standard of security vulnerabilities — ensuring no known vulnerability class is missed. Restricting full rewrites keeps the review educational (the dev should understand their own code). Banning condescending language protects team culture and psychological safety — critical in fast-moving startups.

---

## The Full Engineered Prompt

```
You are a Principal Software Engineer with 12 years of experience in backend
development, specializing in Python, RESTful API design, and fintech security
standards. You are meticulous, direct, and constructive. You always explain
*why* something is wrong, not just what is wrong.

Your task is to perform a detailed code review of the Python function below.
Cover:
1. Bugs — logic errors, edge cases not handled
2. Security vulnerabilities — especially user inputs and data handling
3. Performance issues — inefficient operations
4. Code readability — naming, comments, clarity
5. Best practice violations — PEP8, error handling, anti-patterns
For each issue: provide the line reference, the problem, and a corrected snippet.

Context:
- Python 3.11, FastAPI framework
- This is a user login function returning a JWT token
- Fintech product — security is the highest priority
- PEP8 + type hints are the team standard
- Junior developer wrote this; be constructive and educational
- Stack: PostgreSQL + SQLAlchemy ORM

Format:
- 2-3 sentence overall assessment first
- Numbered issues with: Location | Severity | Problem | Fix (code block)
- End with a Summary Scorecard table:
  Security, Readability, Performance, Best Practices — each out of 10

Reference: PEP8, OWASP Top 10 (A01-A03), FastAPI auth best practices,
JWT security standards.

Restrictions:
- Do NOT rewrite the entire function
- Do NOT flag style preferences as bugs
- Do NOT use condescending language
- Focus only on the code provided

--- Code to Review ---
@app.post("/login")
def login(username, password, db):
    user = db.execute(f"SELECT * FROM users WHERE username = '{username}'")
    if user:
        if user.password == password:
            token = jwt.encode({"user": username, "password": password},
                               "secret", algorithm="HS256")
            return {"token": token}
    return {"error": "Login failed"}
```

---

## AI Output

> **Overall Assessment**
> This function has several critical security vulnerabilities that must be addressed
> before this code goes anywhere near production — particularly the SQL injection risk
> and plaintext password comparison. The logic structure is understandable, which is
> a good foundation, but security and error handling need significant attention.

---

> **Issue #1**
>
> Location: Line 3 — db.execute(f"SELECT * FROM users...")
> Severity: CRITICAL
>
> Problem: String interpolation in a raw SQL query creates a direct SQL Injection
> vulnerability (OWASP A03). An attacker can input ' OR '1'='1 as the username
> and bypass authentication entirely, gaining access to any account.
>
> Fix:
> ```python
> user = db.query(User).filter(User.username == username).first()
> ```
> Use SQLAlchemy ORM queries — they automatically parameterize inputs and
> prevent injection attacks.

---

> **Issue #2**
>
> Location: Line 4-5 — if user.password == password
> Severity: CRITICAL
>
> Problem: This compares plaintext passwords directly (OWASP A02 — Cryptographic
> Failure). Passwords must never be stored or compared in plaintext. If the database
> is ever breached, every user's password is fully exposed.
>
> Fix:
> ```python
> from passlib.context import CryptContext
> pwd_context = CryptContext(schemes=["bcrypt"], deprecated="auto")
>
> if not pwd_context.verify(password, user.hashed_password):
>     raise HTTPException(status_code=401, detail="Invalid credentials")
> ```

---

> **Issue #3**
>
> Location: Line 6 — JWT payload contains "password": password
> Severity: CRITICAL
>
> Problem: Embedding a password in a JWT payload is a severe security mistake.
> JWTs are base64-encoded, not encrypted — anyone who intercepts the token can
> decode and read the payload in seconds. Never put sensitive data in a JWT.
>
> Fix:
> ```python
> token = jwt.encode(
>     {"sub": username, "exp": datetime.utcnow() + timedelta(minutes=30)},
>     settings.SECRET_KEY,
>     algorithm="HS256"
> )
> ```
> Include only a subject (sub) and an expiry (exp). Use a secret key from
> environment config — never hardcode the string "secret".

---

> **Issue #4**
>
> Location: Function signature — def login(username, password, db)
> Severity: HIGH
>
> Problem: No type hints on parameters, which violates the team's PEP8 + type hint
> standard and breaks FastAPI's automatic request validation and OpenAPI documentation.
>
> Fix:
> ```python
> from fastapi import Depends
> from sqlalchemy.orm import Session
> from app.schemas import LoginRequest
>
> @app.post("/login")
> def login(payload: LoginRequest, db: Session = Depends(get_db)):
> ```

---

> **Issue #5**
>
> Location: Line 8 — return {"error": "Login failed"}
> Severity: MEDIUM
>
> Problem: Returning a 200 OK status with an error message body is incorrect HTTP
> semantics and can confuse client applications and monitoring tools. FastAPI
> provides HTTPException for proper error responses.
>
> Fix:
> ```python
> raise HTTPException(status_code=401, detail="Invalid credentials")
> ```

---

> **Summary Scorecard**
>
> | Dimension | Score | Notes |
> |---|---|---|
> | Security | 2 / 10 | SQL injection, plaintext password, insecure JWT — all critical |
> | Readability | 6 / 10 | Logic flow is clear; naming is acceptable |
> | Performance | 7 / 10 | No major performance issues for this scope |
> | Best Practices | 3 / 10 | Missing type hints, wrong HTTP codes, hardcoded secret key |
>
> **Overall: Requires critical fixes before any further review or merge.**

---

## Impact of RTCFR

| Without RTCFR | With RTCFR |
|---|---|
| "There are some security issues in this code" | 5 specific issues with severity, location, and fix |
| Senior engineer still spends 2 hrs on review | Senior engineer spends 15 mins on final check |
| Junior dev doesn't understand what to fix | Each fix comes with an explanation of *why* |
| Generic Python review | Tailored to FastAPI + fintech security + team standards |

---
---

## Cross-Use-Case Summary

| | Use Case 1 | Use Case 2 | Use Case 3 |
|---|---|---|---|
| **Domain** | E-Commerce | Healthcare | Software Dev |
| **Role** | Senior Support Specialist | Clinical Documentation Specialist | Principal Software Engineer |
| **Task** | Draft a customer reply email | Prepare pre-consultation brief | Perform structured code review |
| **Context** | Refund status, loyal customer, order ID | Patient history, attending specialty | Tech stack, dev seniority, security priority |
| **Format** | Email structure, 150-200 words | Bold headers, warning flags, 1 page | Severity labels, code blocks, scorecard |
| **Restrictions** | No invented policies, no hollow openers | No diagnosis, no omissions | No rewrites, no condescension, OWASP ref |
| **Primary Benefit** | 70% reduction in agent drafting time | Doctor consult prep in under 2 minutes | Senior eng review time cut by 80% |

---

*The RTCFR framework works across any domain. The more precisely you fill each element,*
*the more the AI behaves like a true expert in your field.*
