# TakeMeter

## Overview

TakeMeter is a discourse classification system that classifies NBA discussion comments into one of three categories:

- Analysis
- Hot Take
- Reaction

The goal is to understand the style of discussion rather than the basketball topic itself.

---

## Community

Community Selected:

r/nba

The NBA subreddit contains a mixture of analytical discussion, emotional reactions, and opinion-driven debates, making it well suited for discourse classification.

---

## Label Taxonomy

### Analysis

Comments that use evidence, statistics, basketball reasoning, comparisons, or tactical explanations.

Examples:

- Jokic's efficiency is significantly higher than league average.
- Boston's defensive rating explains their success.

### Hot Take

Strong opinions expressed with little or no supporting evidence.

Examples:

- LeBron is completely overrated.
- This team is a first-round exit.

### Reaction

Immediate emotional responses to a game, player, or event.

Examples:

- LET'S GOOOOOO!
- I can't believe that happened.

---

## Dataset

Total Examples: 200

Label Distribution:

| Label | Count |
|---------|---------|
| Analysis | 70 |
| Hot Take | 65 |
| Reaction | 65 |

Dataset File:

```text
takemeter_synthetic_dataset_200.csv
```

---

## Difficult Examples

### Example 1

Text:

```text
This is painful to watch.
```

Could be interpreted as either a reaction or a hot take.

Final Label:

Reaction

Reason:

The statement primarily expresses emotion.

---

### Example 2

Text:

```text
New York should be embarrassed to call themselves contenders.
```

Final Label:

Hot Take

Reason:

Strong opinion without supporting evidence.

---

### Example 3

Text:

```text
The bench reaction is everything.
```

Final Label:

Reaction

Reason:

Emotional observation rather than analysis.

---

## Model

Fine-tuned Model:

```text
distilbert-base-uncased
```

Training Configuration:

- Epochs: 3
- Learning Rate: 2e-5
- Batch Size: 16

---

## Baseline Model

Model:

```text
llama-3.3-70b-versatile
```

Prompt:

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

Validation Accuracy:

```text
0.767
```

### Groq Baseline

Accuracy:

```text
0.967
```

---

## Error Analysis

Several errors occurred between the Reaction and Hot Take classes.

Examples:

| Text | True Label | Predicted |
|---------|---------|---------|
| This is painful to watch. | Reaction | Hot Take |
| I need overtime now. | Reaction | Hot Take |
| This is hilarious. | Reaction | Hot Take |

Reason:

The distinction between emotional reactions and opinionated statements can be subtle when comments are very short.

---

## Confusion Matrix

See:

```text
confusion_matrix.png
```

---

## AI Usage

AI tools were used in the following ways:

1. Brainstorming label definitions.
2. Creating and refining annotation guidelines.
3. Generating synthetic examples for experimentation.
4. Analyzing model errors.
5. Assisting with project documentation.

All final project decisions and implementation steps were reviewed manually.

---

## Reflection

The Groq baseline outperformed the fine-tuned DistilBERT model on this dataset. One possible explanation is that the dataset is relatively small and the baseline model already possesses strong language understanding capabilities.

The project demonstrated the challenges of discourse classification and the importance of clear label boundaries, especially between Reaction and Hot Take categories.
