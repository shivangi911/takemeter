# TakeMeter Planning

## Community

I chose r/nba because it contains a large variety of discussions ranging from emotional reactions to detailed basketball analysis. This makes it a good community for discourse classification because different types of opinions naturally occur.

## Labels

### Analysis

A post that supports a claim using statistics, comparisons, historical context, or logical reasoning.

Examples:

- Jokic leads the league in PER and efficiency, which is why he deserves MVP.
- The Celtics rank top three in both offensive and defensive rating, making them championship favorites.

### Hot Take

A strong opinion stated confidently with little or no supporting evidence.

Examples:

- LeBron is the most overrated player ever.
- Luka is already better than Kobe.

### Reaction

An emotional response to a player, game, or event.

Examples:

- LET'S GOOOOOO!!!
- I can't believe they blew that lead.

## Hard Edge Cases

Some posts contain both an opinion and a statistic.

Example:

"LeBron is overrated because his playoff win percentage against top seeds is below .500."

Decision Rule:

If the evidence is being used to support a reasoned argument, label it Analysis.

If the statistic appears mainly to strengthen a strong opinion, label it Hot Take.

## Data Collection Plan

Source:
r/nba subreddit

Target Distribution:

- Analysis: 70 examples
- Hot Take: 65 examples
- Reaction: 65 examples

If one category becomes underrepresented, I will collect additional examples specifically for that category.

## Evaluation Metrics

I will use:

- Accuracy
- Precision
- Recall
- F1 Score

Accuracy measures overall performance while Precision, Recall, and F1 help evaluate performance for each individual class.

## Definition of Success

The classifier will be considered successful if:

- Accuracy exceeds 75%
- Each class achieves an F1 score above 0.70
- The fine-tuned model outperforms the zero-shot baseline

## AI Tool Plan

### Label Stress Testing

I will use ChatGPT to generate ambiguous NBA comments that sit between labels to test the clarity of my definitions.

### Annotation Assistance

I may use ChatGPT to suggest labels for comments, but every label will be manually reviewed before inclusion in the dataset.

### Failure Analysis

After evaluation, I will use ChatGPT to identify common themes among misclassified examples and verify those patterns manually.
