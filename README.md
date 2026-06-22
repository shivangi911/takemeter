# TakeMeter

## Overview

TakeMeter is a discourse classification system that categorizes NBA-related discussion comments into one of three discourse types:

* Analysis
* Hot Take
* Reaction

Rather than identifying basketball topics, the goal is to classify the style of communication used in a comment.

---

## Community

**Community Focus:** r/nba

The NBA subreddit contains a wide variety of discussion styles, including statistical analysis, player debates, emotional reactions to games, and opinion-driven commentary. These characteristics make it an appropriate community for discourse classification.

---

## Problem Statement

Online communities contain different forms of discussion that often get mixed together. Some comments provide evidence and reasoning, others express strong opinions, and others simply react emotionally to events.

The objective of this project is to automatically classify comments into one of three discourse categories:

1. Analysis
2. Hot Take
3. Reaction

---

## Label Taxonomy

### Analysis

Comments that use evidence, basketball reasoning, comparisons, statistics, or tactical explanations.

**Examples**

* Jokic's efficiency is significantly higher than league average.
* Boston's defensive rating explains their success.
* The team's spacing improved once they added another shooter.

---

### Hot Take

Strong opinions expressed confidently with little or no supporting evidence.

**Examples**

* LeBron is completely overrated.
* This team is a first-round exit.
* The coach has no idea what he is doing.

---

### Reaction

Immediate emotional responses to a game, player, team, or event.

**Examples**

* LET'S GOOOOOO!
* I can't believe that happened.
* What a comeback!

---

## Data Source

This project focuses on NBA-style discourse inspired by discussions commonly found in r/nba.

A dataset of 200 NBA-related comments was created and labeled across the three discourse categories defined above.

---

## Dataset Statistics

### Total Examples

200

### Label Distribution

| Label    | Count |
| -------- | ----: |
| Analysis |    70 |
| Hot Take |    65 |
| Reaction |    65 |

The dataset was intentionally balanced to reduce class imbalance and provide sufficient examples for each category.

---

## Labeling Process

Each comment was assigned exactly one label.

Labeling decisions were based on the following hierarchy:

1. If the comment primarily provided evidence or reasoning → Analysis
2. If the comment primarily expressed a strong unsupported opinion → Hot Take
3. If the comment primarily expressed emotion or immediate reaction → Reaction

Ambiguous examples were reviewed manually and categorized according to the dominant discourse type.

---

## Difficult Examples

### Example 1

**Text**

```text
This is painful to watch.
```

**Final Label:** Reaction

**Reason**

The statement primarily communicates emotion rather than opinion or analysis.

---

### Example 2

**Text**

```text
New York should be embarrassed to call themselves contenders.
```

**Final Label:** Hot Take

**Reason**

This is a strong opinion without supporting evidence.

---

### Example 3

**Text**

```text
The bench reaction is everything.
```

**Final Label:** Reaction

**Reason**

The comment focuses on an emotional response rather than basketball reasoning.

---

## Model

### Fine-Tuned Model

```text
distilbert-base-uncased
```

### Training Configuration

| Parameter     | Value |
| ------------- | ----- |
| Epochs        | 3     |
| Learning Rate | 2e-5  |
| Batch Size    | 16    |

---

## Baseline Model

### Model

```text
llama-3.3-70b-versatile
```

### Prompt

```text
You are classifying NBA discussion comments into exactly one label.

analysis:
Uses basketball reasoning, statistics, comparisons, tactical explanations, or evidence.

hot_take:
Strong opinion with little or no evidence.

reaction:
Immediate emotional response to a game, player, or event.

Return ONLY one label:
analysis
hot_take
reaction
```

---

## Results

### Fine-Tuned DistilBERT

**Test Accuracy**

```text
0.7333
```

### Groq Baseline

**Test Accuracy**

```text
0.9667
```

### Model Comparison

| Model                 | Accuracy |
| --------------------- | -------: |
| Fine-Tuned DistilBERT |   0.7333 |
| Groq Baseline         |   0.9667 |

The Groq baseline substantially outperformed the fine-tuned DistilBERT model on this dataset.

---

## Confusion Matrix

| Actual \ Predicted | Analysis | Hot Take | Reaction |
| ------------------ | -------: | -------: | -------: |
| Analysis           |       11 |        0 |        0 |
| Hot Take           |        1 |        9 |        0 |
| Reaction           |        1 |        6 |        2 |

### Observations

* Analysis examples were classified perfectly.
* Most errors occurred between the Reaction and Hot Take categories.
* Six Reaction examples were incorrectly classified as Hot Take.
* Short emotional statements often resembled opinion-based comments.

---

## Error Analysis

### Example 1

**Text**

```text
This is painful to watch.
```

True Label: Reaction

Predicted Label: Hot Take

Reason:

The model interpreted emotional frustration as an opinion.

---

### Example 2

**Text**

```text
I need overtime now.
```

True Label: Reaction

Predicted Label: Hot Take

Reason:

The statement is short and lacks explicit emotional markers.

---

### Example 3

**Text**

```text
This is hilarious.
```

True Label: Reaction

Predicted Label: Hot Take

Reason:

The model struggled to distinguish emotional commentary from evaluative language.

---

## Sample Classifications

| Comment                                                        | Predicted Label |
| -------------------------------------------------------------- | --------------- |
| Jokic leads the league in efficiency and controls the offense. | Analysis        |
| LeBron is completely overrated.                                | Hot Take        |
| LET'S GOOOOOO!                                                 | Reaction        |
| This team is a first-round exit.                               | Hot Take        |
| I can't believe that happened.                                 | Reaction        |

---

## AI Usage

AI tools were used for:

1. Brainstorming label definitions.
2. Refining annotation guidelines.
3. Generating NBA-style discourse examples.
4. Assisting with error analysis.
5. Improving project documentation and reporting.

All model training, evaluation, and final project decisions were reviewed manually.

---

## Spec Reflection

One helpful aspect of the project specification was requiring label definitions before model training. This made annotation decisions more consistent and improved dataset organization.

A challenge encountered during implementation was distinguishing between Reaction and Hot Take comments. Many short comments contained both emotional and opinionated language, making label boundaries less clear than expected.

The project demonstrated how strongly modern foundation models perform on discourse classification tasks and highlighted the difficulty of improving performance with limited training data.

---

## Repository Contents

```text
planning.md
README.md
takemeter_synthetic_dataset_200.csv
evaluation_results.json
confusion_matrix.png
```
