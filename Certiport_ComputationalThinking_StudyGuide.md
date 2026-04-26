# Certiport ITS Computational Thinking — Student Study Guide

A self-paced review for the Certiport / GMetrix Information Technology Specialist (ITS) Computational Thinking certification exam.

---

## How to Use This Guide

This guide is structured as **fourteen short modules**, building from the foundational mindset (the four pillars of computational thinking) up through pseudocode, data, project management, and finishing with test-taking strategy. Work through them in order — each module assumes the ones before it.

Every module follows the same rhythm:

1. **Concept** — read the explanation.
2. **Anchor** — a small diagram, table, or rule of thumb you should be able to redraw from memory.
3. **Self-check** — exam-style question(s) plus "explain the distractor" practice.

The single most powerful study habit for this exam is **explaining why the wrong answers are wrong**. If you can do that, the right answer takes care of itself.

### What This Exam Tests Most Heavily

Across the practice exam (50 questions), the heaviest weight is on:

- **The four pillars** — decomposition, pattern recognition, abstraction, algorithm design.
- **Pseudocode tracing** — walking loops and conditionals line by line and predicting final values.
- **Choosing the right tool** — flowchart vs. pathfinding algorithm vs. database vs. survey for a given scenario.
- **Data types** — Boolean, integer, float, string, date, image, video, audio.
- **Data collection and quality** — picking the right method (interview, focus group, survey, observation) and the right quality concept (validity, reliability, completeness, uniformity).

Lighter but reliable: number systems (binary / hex), probability, SDLC models, and stakeholder roles.

---

## Table of Contents

1. [The Four Pillars of Computational Thinking](#module-1--the-four-pillars-of-computational-thinking)
2. [The Problem-Solving Process](#module-2--the-problem-solving-process)
3. [Decomposition: Breaking Problems into Parts](#module-3--decomposition-breaking-problems-into-parts)
4. [Pattern Recognition and Abstraction](#module-4--pattern-recognition-and-abstraction)
5. [Variables, Data Types, and Operators](#module-5--variables-data-types-and-operators)
6. [Boolean Logic and Conditional Expressions](#module-6--boolean-logic-and-conditional-expressions)
7. [Algorithms, Pseudocode, and Iteration](#module-7--algorithms-pseudocode-and-iteration)
8. [Functions and Their Trade-Offs](#module-8--functions-and-their-trade-offs)
9. [Flowcharts and Choosing the Right Tool](#module-9--flowcharts-and-choosing-the-right-tool)
10. [Data Collection, Quality, and Ethics](#module-10--data-collection-quality-and-ethics)
11. [Visualization, Surveys, and Probability](#module-11--visualization-surveys-and-probability)
12. [Number Systems and Structured Data](#module-12--number-systems-and-structured-data)
13. [SDLC, Project Management, and Stakeholders](#module-13--sdlc-project-management-and-stakeholders)
14. [Test-Taking Strategy and Final Review](#module-14--test-taking-strategy-and-final-review)
15. [Exam-Day Cheat Card](#exam-day-cheat-card)
16. [Master Glossary](#master-glossary)

---

## Module 1 — The Four Pillars of Computational Thinking

### Concept

Computational thinking is the discipline of solving problems the way computers are good at — by breaking them down, finding patterns, hiding unnecessary detail, and writing clear ordered steps. Almost every other concept on the exam slots into one of four named pillars. Memorize them and you'll recognize what kind of question you're being asked.

### Anchor: The Four Pillars

```
   DECOMPOSITION              PATTERN RECOGNITION
   "Break the problem         "Find what's common
    into smaller parts."       and repeating."

   ABSTRACTION                ALGORITHM DESIGN
   "Hide unnecessary          "Define clear, ordered
    detail; keep the           steps to solve it."
    essentials."
```

| Pillar               | One-Sentence Definition                                                  | Quick Example                                       |
| -------------------- | ------------------------------------------------------------------------ | --------------------------------------------------- |
| **Decomposition**    | Breaking a large problem into smaller, manageable sub-problems.          | "Prepare meal" → side, main course, dessert.        |
| **Pattern Recognition** | Spotting what's common, repeating, or shared across cases.            | "Every other house has a red door."                 |
| **Abstraction**      | Representing the essential without all the detail.                       | A subway map; a `square_root()` function.           |
| **Algorithm Design** | Writing clear, ordered steps that solve a problem.                       | A recipe; pseudocode for a payment calculation.     |

### Self-Check

> A team is building a mobile app. They split the project into "user login," "messaging," "settings," and "notifications," each assigned to a different developer. Which pillar is this?
> A) Pattern recognition
> B) Decomposition
> C) Abstraction
> D) Algorithm design

**Answer:** B.
**Why the others are wrong:** A would be noticing repeated structures across the modules. C would be hiding implementation details behind an interface. D would be writing the actual ordered steps inside a module.

> A subway map ignores the real geography of the city and shows only the stations and the lines connecting them. Which pillar is this?
> A) Decomposition
> B) Algorithm design
> C) Abstraction
> D) Pattern recognition

**Answer:** C.

---

## Module 2 — The Problem-Solving Process

### Concept

Most "what do you do first?" questions on the exam test a five-step framework. The order matters: you can't analyze before defining the problem, and you can't interpret before analyzing.

### Anchor: The Five Steps (in order)

```
1. DEFINE      what you need to know        (frame the problem)
2. DECIDE      what data you need
                and how to gather it
3. COLLECT     the data
4. ANALYZE     the data
5. INTERPRET   the results
```

A common trap: distractors put "collect data" or "analyze data" first. The first step is **always** to *define what you need to know*. Without that, you don't know what data to collect.

### Anchor: Applying the Framework

| Scenario                                         | Step 1 (Define)                       | Step 5 (Interpret)                          |
| ------------------------------------------------ | ------------------------------------- | ------------------------------------------- |
| Improving a check-in process                     | "Where do guests get stuck?"          | "The bottleneck is at room-key issuance."   |
| Evaluating a new vitamin                         | "Does it improve resting heart rate?" | "Heart rate dropped 6 bpm on average."      |
| Surveying customers about a redesign             | "Do customers prefer layout A or B?"  | "Layout B preferred by 62% of respondents." |

### Self-Check

> A company wants to know whether to keep its on-site office or go fully remote. Which step should come **first**?
> A) Survey employees
> B) Analyze attendance logs
> C) Define what they need to know (e.g., "Are people more productive remotely?")
> D) Choose a charting tool

**Answer:** C. Define before you decide what data to collect.

---

## Module 3 — Decomposition: Breaking Problems into Parts

### Concept

Decomposition shows up two ways on the exam: as a definition question, and as a *diagram* question — given a hierarchical tree, identify which item belongs where.

### Anchor: A Decomposition Tree

```
                Prepare Meal
               /     |       \
             Side  Main      Dessert
                   Course
```

Things to memorize when reading these:

- The **parent** is the bigger task; **children** are sub-tasks that *make up* the parent.
- An item that comes **before** or **after** the parent (e.g., "Clean the kitchen" before cooking) belongs as a **sibling** of the parent in a larger tree, not as a child.
- A child task should be smaller and contained within the parent's scope.

### Anchor: When to Decompose

Decompose any problem that:

- Is too large to solve in one step.
- Can be split among multiple people / teams.
- Has clearly distinguishable sub-parts.

### Self-Check

> In a decomposition diagram for "Plan a Birthday Party," which of the following is **not** a child of the parent task?
> A) Order cake
> B) Send invitations
> C) Drive to work the next morning
> D) Decorate the venue

**Answer:** C. Driving to work isn't part of planning the party.

---

## Module 4 — Pattern Recognition and Abstraction

### Concept

These two pillars are easy to confuse, so the exam tests the difference. **Pattern recognition** is about *what's repeating* across many cases. **Abstraction** is about *what to keep and what to throw away* in any single representation.

### Anchor: Pattern vs. Individual Fact

A *pattern* is a statement about a class of things; an *individual fact* describes only one specific case.

| Statement                                   | Pattern or Individual Fact?     |
| ------------------------------------------- | ------------------------------- |
| "Every other house on this street has a red door." | **Pattern**                |
| "My house has a kitchen."                   | **Individual fact**             |
| "Most students who study daily score above 80." | **Pattern**                  |
| "Maria scored 92 on the test."              | **Individual fact**             |

### Anchor: Abstract vs. Concrete

Something is **abstract** when it represents the essential idea without all the real-world detail.

| Item                              | Abstract or Concrete?           |
| --------------------------------- | ------------------------------- |
| A subway map                      | **Abstract** (geography removed) |
| A real building                   | **Concrete**                    |
| A `square_root()` function        | **Abstract** (hides the math)   |
| A physical fridge                 | **Concrete**                    |
| A flowchart of a checkout process | **Abstract**                    |

### Self-Check

> Which is an example of **abstraction**?
> A) A real airport
> B) A specific airline ticket with a seat number
> C) A simplified diagram showing only major airports and the routes between them
> D) A photograph of the inside of a plane

**Answer:** C.

> "Customers who buy bread also tend to buy milk." This is best described as:
> A) Abstraction
> B) Pattern recognition
> C) Decomposition
> D) An individual fact

**Answer:** B.

---

## Module 5 — Variables, Data Types, and Operators

### Concept

You should be able to (1) name the standard data types, (2) recognize which type fits a given value, and (3) evaluate an arithmetic expression with the correct precedence.

### Anchor: The Standard Data Types

| Type        | What It Holds                                       | Example                |
| ----------- | --------------------------------------------------- | ---------------------- |
| **Boolean** | True / False only                                   | `True`                 |
| **Integer** | Whole numbers, no decimal                           | `42`                   |
| **Long**    | Integer that holds **larger** values than `Integer` | `9_000_000_000`        |
| **Float / Numeric** | Numeric value with a decimal point          | `1.3`, `3.14`          |
| **String**  | One or more characters (letters, digits, symbols)   | `"hello"`, `"3.14"` (as text) |
| **Date**    | A calendar date                                     | `7/4/2021`             |
| **Image**   | A photograph                                        | `cat.png`              |
| **Video**   | Film clips or news footage                          | `clip.mp4`             |
| **Audio**   | Sound files                                         | `song.mp3`             |

A trap to memorize: a number stored inside quotes (e.g., `"3.14"`) is a **string** — it has no numeric value and you can't do math on it.

### Anchor: Variables and Assignment

A variable is a named placeholder for data:

```
SET cost = 0
SET name = "Ada"
SET is_active = TRUE
```

### Anchor: Order of Operations

```
1.  ( )   parentheses first
2.  *  /  multiplication and division
3.  +  -  addition and subtraction
```

Compound assignment: `+=` adds to the current value.

### Anchor: A Worked Trace

Given `myNumber = 21`, evaluate:

```
myNumber += 7 * 3 + 1
```

Steps:

1. `7 * 3` → `21`
2. `21 + 1` → `22`
3. `myNumber += 22` → `21 + 22` → **`43`**

### Self-Check

> Which type best stores the value `7/4/2021`?
> A) String
> B) Integer
> C) Date
> D) Boolean

**Answer:** C.

> Given `x = 10`, what is the value of `x` after `x += 2 * 3`?
> A) `36`
> B) `16`
> C) `12`
> D) `60`

**Answer:** B. `2 * 3 = 6`, then `x = 10 + 6 = 16`.

---

## Module 6 — Boolean Logic and Conditional Expressions

### Concept

Boolean expressions evaluate to `True` or `False`. The exam tests whether you can read a comparison or a logical combination and predict the result, plus whether you can pick the right operator for a description.

### Anchor: Comparison Operators

| Operator | Meaning                |
| -------- | ---------------------- |
| `==`     | Equal to               |
| `!=`     | Not equal to           |
| `<`      | Less than              |
| `>`      | Greater than           |
| `<=`     | Less than or equal     |
| `>=`     | Greater than or equal  |

### Anchor: Logical Operators

| Operator | Result Is True When…                                |
| -------- | --------------------------------------------------- |
| `AND`    | **Both** sides are true                             |
| `OR`     | **At least one** side is true                       |
| `NOT`    | The single side is **false**                        |

### Anchor: The Conditional Pattern

```
IF condition THEN
   do something
ELSE IF other condition THEN
   do something else
ELSE
   do the fallback
END IF
```

The order is fixed: `IF` always comes first, `ELSE IF` (if used) comes after, and `ELSE` (if used) comes last.

### Self-Check

> Given `age = 17`, which expression is `True`?
> A) `age >= 18`
> B) `age == 18`
> C) `age != 17`
> D) `age < 18`

**Answer:** D.

> A discount applies only when a customer is a member **and** has spent over $100. Which logical operator joins the two conditions?
> A) `OR`
> B) `AND`
> C) `NOT`
> D) `==`

**Answer:** B.

---

## Module 7 — Algorithms, Pseudocode, and Iteration

### Concept

This is the highest-leverage technical module. You should be able to read a small block of pseudocode and produce a **trace table** showing the value of each variable at every iteration.

### Anchor: The Three Building Blocks

```
SEQUENCE       →  steps run in order
SELECTION      →  IF / ELSE IF / ELSE
ITERATION      →  WHILE, FOR, and NESTED loops
```

### Anchor: A `WHILE` Loop Trace

```
SET X = 0
SET Y = 4
WHILE (X < 5)
    Y = Y + 2
    X = X + 1
END WHILE
```

Trace it iteration by iteration:

| Iteration | X (before) | Y (before) | X (after) | Y (after) |
| --------- | ---------- | ---------- | --------- | --------- |
| 1         | 0          | 4          | 1         | 6         |
| 2         | 1          | 6          | 2         | 8         |
| 3         | 2          | 8          | 3         | 10        |
| 4         | 3          | 10         | 4         | 12        |
| 5         | 4          | 12         | 5         | 14        |

Final values: **X = 5, Y = 14**.

### Anchor: When to Use Iteration

Iteration is appropriate when an action **repeats**. Match scenarios to "loop" or "no loop":

| Scenario                                                     | Loop?  |
| ------------------------------------------------------------ | ------ |
| Background music playing on a continuous loop                | ✅     |
| Calculating payments across many interest rates and terms    | ✅ (nested) |
| Asking the user for their name once at the start             | ❌     |
| Ending the program                                           | ❌     |

### Anchor: Nested Loops

When one loop runs inside another, the inner loop completes fully for each step of the outer loop. Classic scenario: car-payment table.

```
FOR each interest rate in [3%, 4%, 5%]
    FOR each term in [36, 48, 60] months
        compute payment
    END FOR
END FOR
```

That's 3 × 3 = 9 payment calculations.

### Self-Check

> Trace this loop. What is `X` when it ends?
>
> ```
> SET X = 1
> WHILE (X < 10)
>     X = X * 2
> END WHILE
> ```
>
> A) `8`
> B) `10`
> C) `16`
> D) `32`

**Answer:** C. The loop runs while `X < 10`: 1 → 2 → 4 → 8 → 16. The condition `16 < 10` is false, so it exits with `X = 16`.

> Which scenario is **not** a good fit for iteration?
> A) Reading every line of a file until end-of-file
> B) Asking the user for their name a single time at startup
> C) Looping through every player in a tournament bracket
> D) Polling a sensor every second

**Answer:** B.

---

## Module 8 — Functions and Their Trade-Offs

### Concept

A function is a named, reusable block of code that takes inputs and (often) returns a value. The exam tests both the **calling syntax** in pseudocode and the **pros and cons** of using functions.

### Anchor: Calling a Function in Pseudocode

```
SET v4 = CALL my_function WITH v1, v2 RETURNING v3
```

Read it as: "Call `my_function`, pass it `v1` and `v2`, capture the returned value as `v3`, and assign it to `v4`."

### Anchor: Pros and Cons

| ✅ Functions help…                                        | ❌ Functions don't…                                         |
| --------------------------------------------------------- | ----------------------------------------------------------- |
| Make code **easier to test and debug** (bugs are isolated) | Eliminate the need for abstraction — they *implement* it    |
| Allow **reuse** across the program                        | Make it good practice to reuse the same variable names everywhere — that hurts readability |
| Support **abstraction** (hide implementation)             | Replace careful design                                      |

### Self-Check

> Which is a benefit of using functions?
> A) They eliminate the need to think about abstraction.
> B) They isolate logic so bugs are easier to find.
> C) They make it best practice to reuse the same variable names everywhere.
> D) They are required only when writing object-oriented code.

**Answer:** B.

---

## Module 9 — Flowcharts and Choosing the Right Tool

### Concept

Flowcharts show a process visually; they're the right tool when **decisions branch on conditions**. The exam tests the symbol shapes plus the broader question of *which artifact* (flowchart, pathfinding algorithm, database, survey) fits a scenario.

### Anchor: Flowchart Symbols

```
   ╭──────────╮       Terminator (rounded) — start / end
   │  Start   │
   ╰──────────╯

   ┌──────────┐       Process (rectangle) — an action or step
   │  Step 1  │
   └──────────┘

      ⟢   Decision (diamond) — branching based on a condition
     ╱ ╲
    ╱   ╲
   ╱     ╲
  ⟢       ⟣

   ╱──────────╲       Input / Output (parallelogram)
  ╱ Read input ╲
  ╲────────────╱
```

| Symbol         | Shape         | Meaning                                  |
| -------------- | ------------- | ---------------------------------------- |
| Terminator     | Rounded oval  | Start / end of the process               |
| Process        | Rectangle     | An action or step ("turn computer off")  |
| Decision       | Diamond       | Conditional branch (Yes / No)            |
| Input / Output | Parallelogram | Getting data from / sending to a user    |

When to reach for a flowchart: any time the logic involves **multiple decisions** (e.g., programming a robot vacuum's behavior).

### Anchor: Tool-to-Scenario Matching

| Scenario                                            | Right Tool / Artifact          |
| --------------------------------------------------- | ------------------------------ |
| Multi-decision logic (robot vacuum behavior)        | **Flowchart**                  |
| Shortest route between two points (gas station finder) | **Pathfinding algorithm**   |
| Managing large amounts of varied records            | **Database**                   |
| Gathering stakeholder feedback                      | **Survey**                     |
| Required input for any pathfinding solution         | **Map data**                   |

### Anchor: A Robot/Path Algorithm Skeleton

For a robot navigating a maze with no dead ends and limited moves (forward, turn left, check wall):

```
LOOP
    IF wall in front THEN
        turn left 90°
    ELSE
        move forward
    END IF
END LOOP
```

Teach this as a primer for state-driven loops.

### Self-Check

> Which flowchart symbol represents a decision point?
> A) Rectangle
> B) Diamond
> C) Parallelogram
> D) Rounded oval

**Answer:** B.

> A delivery company wants to find the shortest route between a depot and a customer. Which tool fits best?
> A) Flowchart
> B) Pathfinding algorithm
> C) Database
> D) Online survey

**Answer:** B.

---

## Module 10 — Data Collection, Quality, and Ethics

### Concept

Three related clusters share this module: which **collection method** to use, which **quality concept** is being tested, and what **ethical principles** govern data use.

### Anchor: Collection Methods

| Method                          | Best For                                                                              |
| ------------------------------- | ------------------------------------------------------------------------------------- |
| **Video interview**             | Visual cues + textual detail with interaction                                         |
| **Focus group**                 | Opinions / preferences in a group discussion (not for in-depth detail)                |
| **In-depth (1-on-1) interview** | Detailed, empathetic understanding of one client                                      |
| **Observation**                 | How a process actually flows; can be biased if subjects know they're watched          |
| **Online survey**               | Broad feedback from many people; no visual cues                                       |
| **Filming subjects unaware**    | Capturing unaltered behavior (e.g., a player's batting stance)                        |
| **Game film / historical records** | Retrospective data                                                                 |
| **Self-reported logs**          | Longitudinal self-report data (e.g., a nutrition log over weeks)                      |

### Anchor: Collaboration Tools

| Tool                  | Best For                                                  |
| --------------------- | --------------------------------------------------------- |
| **Online spreadsheet** | Team members entering, editing, and charting shared values |
| **Online survey**     | Collecting data only — not for editing or manipulation    |
| **Video conferencing**| Real-time discussion with follow-up questions             |
| **Email**             | Asynchronous communication; not ideal for discussion      |
| **Online forms**      | Data collection — not Q&A                                 |

### Anchor: Data Quality Concepts

| Concept                    | What It Means                                                    |
| -------------------------- | ---------------------------------------------------------------- |
| **Data cleaning**          | Checking for missing or impossible values                        |
| **Identifying data conflicts** | Finding contradictions across records                        |
| **Duplication checks**     | Preventing multiple records for the same entity                  |
| **Data profiling**         | Analyzing a set to find outliers / improbable values             |
| **Reliability**            | Consistent results across repeated studies                       |
| **Validity**               | Measuring what you actually intend to measure                    |
| **Completeness**           | All anticipated data is included                                 |
| **Uniformity**             | Absence of inconsistency in format or units                      |

### Anchor: Ethics — The Purpose-Limitation Principle

> Data collected for one stated reason should not be repurposed for another without consent.

| Scenario                                                                  | Ethically OK?           |
| ------------------------------------------------------------------------- | ----------------------- |
| Medical data collected to monitor health → used to sell medicine          | ❌ Problematic          |
| Non-anonymized location data shared with third parties                    | ❌ Problematic          |
| Properly **anonymized** usage statistics                                  | ✅ Generally fine       |
| Location data used **inside the app** to show your position on the map    | ✅ Fine                 |

### Self-Check

> A nutritionist wants to understand one specific client's eating habits in depth. Which method is best?
> A) Focus group
> B) In-depth one-on-one interview
> C) Online survey of 1,000 people
> D) Filming the client unaware

**Answer:** B.

> A team finds three records for the same customer in the database. Which data-quality activity addresses this?
> A) Data profiling
> B) Duplication checks
> C) Validity testing
> D) Completeness checking

**Answer:** B.

---

## Module 11 — Visualization, Surveys, and Probability

### Concept

This module groups three small, reliable question types: matching a chart to a purpose, drawing conclusions from survey data, and basic probability counting.

### Anchor: Chart-to-Purpose

| Chart Type       | Best For                                                         |
| ---------------- | ---------------------------------------------------------------- |
| **Pie chart**    | Breakdown / proportion of a whole (e.g., cost breakdown of a school) |
| **Line chart**   | Trends over time (e.g., sales by year)                           |
| **Bar chart**    | Comparison across categories                                     |
| **Multi-line chart** | Comparing two or more series side by side                    |
| **Forecast chart** | Data extending past the last known year (predictive)           |

### Anchor: Reading a Survey

A common question pattern: a paragraph reports survey counts, and you must pick the conclusion the data supports.

> "70 of 110 respondents prefer **on-site**. 25 prefer **both** on-site and virtual. 15 prefer **virtual only**."

Valid conclusions:

- The **majority prefer on-site** (70/110 = ~64%).
- Respondents who chose "both" are **neutral** — they could go either way.
- Only ~14% want virtual exclusively.

When you see ranges or age brackets ("ages 30–39 all scored ≥ 70"), look for the pattern across the bracket.

### Anchor: Probability — Two Dice

Rolling two dice gives **6 × 6 = 36 total outcomes**. The probability of any specific sum is:

```
P(sum) = (number of ways to roll that sum) / 36
```

| Sum | Ways | Probability |
| --- | ---- | ----------- |
| 2   | 1    | 1/36        |
| 3   | 2    | 2/36        |
| 7   | 6    | 6/36        |
| 11  | 2    | 2/36        |
| 12  | 1    | 1/36        |

### Self-Check

> Which chart best shows how a year's total expenses are split among rent, salaries, utilities, and supplies?
> A) Line chart
> B) Pie chart
> C) Scatter plot
> D) Histogram

**Answer:** B.

> Two dice are rolled. What is the probability the sum is 7?
> A) `1/12`
> B) `1/6`
> C) `6/36` (or `1/6`)
> D) `7/36`

**Answer:** C. There are 6 ways to roll a 7 out of 36 outcomes.

---

## Module 12 — Number Systems and Structured Data

### Concept

A small but reliable cluster of questions tests the basics of binary, hexadecimal, and the difference between structured and unstructured data.

### Anchor: Binary (base-2) and Hexadecimal (base-16)

| System            | Digits Used                       | Example   |
| ----------------- | --------------------------------- | --------- |
| **Binary**        | `0, 1`                            | `010101`  |
| **Hexadecimal**   | `0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F` | `1C` |

In hex, after `9` you continue counting with `A (10), B (11), C (12), D (13), E (14), F (15)`. After `F`, the next number rolls over to `10` (which equals 16 in decimal).

A common drill: **continue a hex sequence by adding 4 each time**:

```
14, 18, 1C, 20, 24, 28, …
```

Notice `1C + 4 = 20`. Why? `C = 12`; `12 + 4 = 16`, which is `10` in hex with a carry → `1C` becomes `20`.

### Anchor: Structured vs. Unstructured Data

| Structured                              | Unstructured                                         |
| --------------------------------------- | ---------------------------------------------------- |
| Pre-defined format / data model         | No fixed format                                       |
| Stored in fixed fields                  | Stored in audio, video, text, NoSQL stores            |
| Rows and columns                        | Free-form                                             |
| Queried with SQL                        | Not SQL-queryable                                     |
| Examples: relational DB tables          | Examples: emails, photos, voicemails, social posts    |

### Self-Check

> Which is a valid hexadecimal digit?
> A) `G`
> B) `J`
> C) `E`
> D) `Z`

**Answer:** C. Hex uses `0–9` and `A–F`.

> A company stores customer emails, support call recordings, and social-media posts. This data is best classified as:
> A) Structured
> B) Unstructured
> C) Tabular
> D) Relational

**Answer:** B.

---

## Module 13 — SDLC, Project Management, and Stakeholders

### Concept

The non-technical side of the exam: which software development model fits a situation, the triple constraint of project management, and how to identify who's a decision-maker vs. a collaborator vs. an end user.

### Anchor: Software Development Models

| Model               | Best When…                                                                                                                |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **Incremental**     | You need a quick first release with a prioritized requirement list. Each module goes through requirements → design → implementation → testing. (e.g., a city website launches the landing page first, with other sections added in releases.) |
| **Waterfall**       | Sequential — each phase must complete before the next begins. Best when requirements are extremely well known up front.   |
| **Agile / iterative** | Short cycles with frequent feedback. Best when requirements evolve.                                                     |

### Anchor: The Triple Constraint of Project Management

```
       TIME
        ⟍
         ⟍
          ⟍
           ⟍
            ⟍ SCOPE
            ╱
           ╱
          ╱
         ╱
       COST
```

A project lives in tension among **Time**, **Scope**, and **Cost**. Increase one, and at least one of the others usually has to give.

**Scope** — the goals, milestones, deliverables, constraints, and acceptance criteria. The client's *required* features are in scope; optional features may be out of scope.

### Anchor: Stakeholder Roles

| Role                | Plain English                                              | Example                                            |
| ------------------- | ---------------------------------------------------------- | -------------------------------------------------- |
| **Decision-maker**  | Must approve plans, budgets, and changes                    | Mall property managers                             |
| **Collaborator**    | Contributes to or benefits from the work                   | Shop owners, hired artists                         |
| **End user / public** | The audience the project ultimately serves                | Mall visitors                                      |

### Self-Check

> A city wants its new website live in two months but can keep adding sections after launch. Which development model fits best?
> A) Waterfall
> B) Incremental
> C) Big-bang release
> D) Pure research

**Answer:** B.

> A property management company hires you to design a holiday display in a mall. The shop owners contribute ideas; the mall managers approve the budget; visitors enjoy the display. Who are the **decision-makers**?
> A) Shop owners
> B) Visitors
> C) Mall managers
> D) The hired designers

**Answer:** C.

---

## Module 14 — Test-Taking Strategy and Final Review

### The Distractor-Autopsy Method

For every practice question, do this:

1. Pick your answer.
2. **For each *wrong* option, write one sentence explaining why it is wrong.**
3. Only then check the answer key.

If you can articulate why every distractor is wrong, you have actually mastered the concept. If you can't, that's where to study next.

### Reading Pseudocode Under Time Pressure

When pseudocode appears, before reading the answer choices:

1. **Identify the construct** — sequence, selection (`IF`), iteration (`WHILE` / `FOR`).
2. **Set up a trace table** with one column per variable.
3. **Walk one iteration at a time**, updating the table.
4. **Stop when the loop condition becomes false.**
5. **Then evaluate the answer choices.**

### Spotting "Pattern vs. Fact" Traps

When a question asks "is this a pattern?" — ask yourself:

> Does this statement describe a class of cases (pattern), or just one specific instance (fact)?

If you can imagine a counter-example that still fits the rule, it's a pattern.

### One Sentence to Repeat During the Exam

Pick one of these and repeat it under your breath whenever you get stuck:

- *"Decompose, find patterns, abstract, then write the algorithm."*
- *"Define before you collect; analyze before you interpret."*
- *"Diamond is a decision; rectangle is a process."*
- *"Pattern = class; fact = single case."*
- *"`AND` needs both; `OR` needs one."*

### Mock Quiz (12 Questions Across the Whole Exam)

Try these timed — about 75 seconds per question.

1. Which pillar splits a big problem into smaller sub-problems?
2. What is the **first** step of the problem-solving process?
3. "Every other house has a red door" — pattern or individual fact?
4. A subway map is an example of which pillar?
5. What is the value of `x` after `x = 5; x += 2 * 3`?
6. Trace this loop. Final value of `Y`?
   ```
   SET X=0, Y=4
   WHILE (X<5)
       Y = Y + 2
       X = X + 1
   END WHILE
   ```
7. Which flowchart symbol is a decision?
8. Which collection method best gives one person's deep, empathetic detail?
9. A team finds duplicate customer records. Which quality activity addresses this?
10. Which chart type is best for trends over time?
11. Which is a valid hexadecimal digit — `G`, `J`, `E`, or `Z`?
12. In a project, who must approve plans and budgets — decision-makers, collaborators, or end users?

#### Answer Key (cover until done)

1. **Decomposition** — Module 1.
2. **Define what you need to know** — Module 2.
3. **Pattern** — Module 4.
4. **Abstraction** — Module 1 / 4.
5. **`11`** (`2*3=6`, `5+6=11`) — Module 5.
6. **`14`** — Module 7.
7. **Diamond** — Module 9.
8. **In-depth one-on-one interview** — Module 10.
9. **Duplication checks** — Module 10.
10. **Line chart** — Module 11.
11. **`E`** — Module 12.
12. **Decision-makers** — Module 13.

---

## Exam-Day Cheat Card

Read this on the morning of the exam. It's the whole guide compressed into a single paragraph:

> The four pillars of computational thinking are **decomposition** (break a big problem into smaller parts), **pattern recognition** (find what's repeating across cases — a *pattern* describes a class, an individual fact describes one case), **abstraction** (keep the essentials, throw away unnecessary detail — a subway map, a `square_root()` function), and **algorithm design** (clear, ordered steps). The five-step problem-solving process is **define → decide what data → collect → analyze → interpret** — never start by collecting; never analyze before defining. Variables hold data; standard types are Boolean, integer, long, float/numeric, string, date, image, video, audio. A number in quotes is a string. Order of operations: parentheses → `*` `/` → `+` `-`. `+=` adds to the current value. Comparisons (`==`, `!=`, `<`, `>`, `<=`, `>=`) return Booleans; logicals are `AND` (both true), `OR` (at least one), `NOT` (flip). Pseudocode has three building blocks — sequence, selection (`IF` / `ELSE IF` / `ELSE` in that order), and iteration (`WHILE`, `FOR`, nested loops). Trace loops with a table; iterate until the condition is false. Use loops when an action repeats; don't loop for one-time actions like asking a name once. Functions support reuse, testability, and abstraction; they don't eliminate abstraction. Flowchart symbols: rounded oval = terminator (start/end), rectangle = process, diamond = decision, parallelogram = input/output. Reach for a flowchart when logic branches on multiple decisions, a pathfinding algorithm for shortest routes, a database for varied records, a survey for stakeholder feedback. Pick collection methods to fit the goal: in-depth interview for one client's detail, focus group for group preferences, observation for process flow, survey for broad feedback. Data quality terms: **reliability** (consistent across studies), **validity** (measures what you intend), **completeness** (all data included), **uniformity** (no format inconsistency); plus cleaning, profiling, conflict checks, and dedup. Purpose limitation: data collected for one reason shouldn't be repurposed without consent. Charts: pie for parts of a whole, line for trends, bar for comparison, multi-line for two series, forecast charts extend past the last known data point. With two dice, 36 outcomes; `P(sum) = ways / 36`. Binary uses `0,1`; hex uses `0–9, A–F` (so `1C + 4 = 20`). Structured data has fixed fields and is queried with SQL; unstructured data (audio, video, text) is not. Software models: **incremental** for quick first release with prioritized requirements, **waterfall** for known requirements, **agile** for evolving requirements. Project's triple constraint is **time, scope, cost**; scope defines goals, milestones, deliverables, constraints, acceptance criteria. Decision-makers approve, collaborators contribute, end users are the audience.

---

## Master Glossary

**Abstraction** — representing the essential idea while hiding unnecessary detail (one of the four pillars).

**Algorithm** — a clear, ordered set of steps to solve a problem.

**Algorithm Design** — the pillar of computational thinking concerned with writing those steps.

**`AND` / `OR` / `NOT`** — logical operators: `AND` requires both true, `OR` at least one, `NOT` flips.

**Bar Chart** — visualization for comparing categories.

**Binary** — base-2 number system using only `0` and `1`.

**Boolean** — data type with only `True` / `False`.

**Comparison Operators** — `==`, `!=`, `<`, `>`, `<=`, `>=`; return Booleans.

**Completeness** — quality dimension: all anticipated data is included.

**Conditional / Selection** — `IF` / `ELSE IF` / `ELSE` constructs.

**Data Cleaning** — checking for missing or impossible values.

**Data Profiling** — analyzing data to find outliers and improbable values.

**Date** — data type representing a calendar date.

**Decision-Maker** — stakeholder who must approve plans and budgets.

**Decomposition** — breaking a large problem into smaller sub-problems (one of the four pillars).

**Duplication Check** — preventing multiple records for the same entity.

**End User** — the audience a project ultimately serves.

**Flowchart** — diagram of a process using terminators, processes, decisions, and input/output symbols.

**Float / Numeric** — data type for numbers with a decimal point.

**Focus Group** — collection method for group opinions and preferences.

**Forecast Chart** — chart whose data extends past the last known period to predict future values.

**Function** — reusable named block of code that can take inputs and return a value.

**Hexadecimal** — base-16 number system using digits `0–9` and letters `A–F`.

**In-Depth Interview** — one-on-one method for detailed, empathetic understanding.

**Incremental Model** — SDLC model with prioritized modules each going through their own requirements/design/implementation/testing cycle.

**Individual Fact** — a statement about one specific case (contrast with *pattern*).

**Integer** — data type for whole numbers.

**Iteration** — looping; repeating an action via `WHILE`, `FOR`, or nested loops.

**Line Chart** — visualization for trends over time.

**Long** — integer type that holds larger values than a standard integer.

**Multi-Line Chart** — line chart with multiple series for side-by-side comparison.

**Observation** — collection method for studying how a process flows in practice.

**Online Survey** — method for collecting broad feedback at scale.

**Pathfinding Algorithm** — algorithm for finding the shortest route between points.

**Pattern Recognition** — finding what's common or repeating across cases (one of the four pillars).

**Pie Chart** — visualization for parts of a whole.

**Process (Flowchart Symbol)** — rectangle representing an action or step.

**Project Triple Constraint** — Time, Scope, and Cost — the three competing project dimensions.

**Pseudocode** — language-agnostic, English-like representation of an algorithm.

**Purpose Limitation** — ethical principle that data collected for one stated reason should not be repurposed without consent.

**Reliability (Data Quality)** — consistency of results across repeated studies.

**Robot/Path Algorithm** — state-driven loop pattern such as "if wall ahead, turn left; else move forward; repeat."

**Scope** — project dimension defining goals, milestones, deliverables, constraints, and acceptance criteria.

**Sequence** — pseudocode steps that run in order.

**Stakeholder** — anyone with a vested interest in a project: decision-makers, collaborators, or end users.

**String** — data type for one or more characters; numbers stored in quotes are strings, not numeric values.

**Structured Data** — data with a pre-defined model, fixed fields, queryable with SQL.

**Terminator (Flowchart Symbol)** — rounded oval representing start or end.

**Trace Table** — table tracking variable values across iterations of a loop or steps of an algorithm.

**Uniformity** — quality dimension: absence of inconsistency in format or units.

**Unstructured Data** — data without a pre-defined format (audio, video, free text); not SQL-queryable.

**Validity** — quality dimension: actually measuring what you intend to measure.

**Variable** — named placeholder that stores data.

**Video Interview** — collection method providing both visual cues and textual detail with interaction.

**Waterfall Model** — sequential SDLC where each phase completes before the next begins.

**`WHILE` Loop** — iteration construct that runs while a condition is true; checked before each pass.
