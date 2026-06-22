# TakeMeter Planning

## Community

I chose r/nba because it contains a wide variety of discussion styles, including statistical analysis, player debates, emotional reactions, and opinion-driven commentary. This makes it a strong community for discourse classification because different forms of discourse naturally occur within the same topic area.

---

## Labels

### Analysis

A comment that supports a claim using statistics, comparisons, basketball reasoning, historical context, or logical explanation.

Examples:

* Jokic leads the league in PER and efficiency, which is why he deserves MVP.
* The Celtics rank in the top three for both offensive and defensive rating, making them championship favorites.
* The team's spacing improved significantly after adding another perimeter shooter.

---

### Hot Take

A strong opinion expressed confidently with little or no supporting evidence.

Examples:

* LeBron is the most overrated player ever.
* Luka is already better than Kobe.
* This team is a first-round exit.

---

### Reaction

An emotional response to a player, game, team, or event.

Examples:

* LET'S GOOOOOO!!!
* I can't believe they blew that lead.
* What a comeback!

---

## Hard Edge Cases

Some comments contain both an opinion and supporting evidence.

Example:

"LeBron is overrated because his playoff win percentage against top seeds is below .500."

Decision Rule:

* If the evidence is being used to support a reasoned argument, label the comment as Analysis.
* If the evidence primarily serves to strengthen a strongly stated opinion, label the comment as Hot Take.

Another difficult case involves distinguishing between Hot Take and Reaction.

Example:

"This team is embarrassing."

Decision Rule:

* If the statement primarily communicates emotion, label it as Reaction.
* If the statement primarily communicates judgment or opinion, label it as Hot Take.

---

## Data Collection Plan

Community Focus:

r/nba

The dataset will consist of NBA-related comments representing discourse patterns commonly found in r/nba discussions.

Target Distribution:

* Analysis: 70 examples
* Hot Take: 65 examples
* Reaction: 65 examples

This distribution is intentionally balanced to reduce class imbalance and provide sufficient examples for each category.

If one category becomes underrepresented, additional examples will be added to maintain a balanced dataset.

---

## Evaluation Metrics

The classifier will be evaluated using:

* Accuracy
* Precision
* Recall
* F1 Score

Accuracy measures overall classification performance, while Precision, Recall, and F1 Score provide insight into performance on individual classes.

---

## Definition of Success

The project will be considered successful if:

* Accuracy exceeds 75%
* Each class achieves an F1 score above 0.70
* The model demonstrates meaningful classification of discourse categories
* Error analysis reveals understandable and interpretable failure patterns

---

## AI Tool Plan

### Label Stress Testing

I will use ChatGPT to generate ambiguous NBA-related comments that sit between categories in order to test the clarity of label definitions.

### Dataset Development

I may use ChatGPT to help generate, review, and refine examples representing the target discourse categories. All examples and labels will be reviewed before inclusion in the dataset.

### Failure Analysis

After evaluation, I will use ChatGPT to identify common themes among misclassified examples and assist in understanding model weaknesses.

### Documentation Support

I may use ChatGPT to improve the clarity of project documentation, reflections, and evaluation summaries while ensuring that all project decisions remain my own.
