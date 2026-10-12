# Customer-feedback-analysis-using-NL
Customer Feedback Analysis using NLP and Machine Learning
# Customer Feedback Analysis Using NLP and Machine Learning

## Project Overview

Customer reviews contain valuable information about customer satisfaction, product quality, pricing, and purchasing behaviour. However, analysing large volumes of unstructured text manually can be time-consuming.

This project uses Natural Language Processing (NLP) and machine learning to analyse a sample of 30,000 customer reviews. The objective is to classify sentiment, identify influential words and recurring feedback themes, and explore potential customer intent using rule-based text analysis.

The project demonstrates how unstructured customer feedback can be transformed into structured insights to support customer experience analysis and business decision-making.

## Business Objectives

- Classify customer reviews into positive, neutral, and negative sentiment categories.
- Compare machine learning models for sentiment classification.
- Identify words and phrases associated with different sentiment categories.
- Explore recurring customer feedback themes, including taste and flavour, product quality, value for money, and purchase intent.
- Use rule-based NLP to identify potential customer intentions, such as repurchasing, recommending a product, or requesting a refund.
- Translate analytical findings into potential business recommendations.

## Dataset

The analysis uses a sample of 30,000 reviews from a customer product-review dataset.

The dataset includes fields such as:

- `Score`: Customer rating from 1 to 5.
- `Summary`: Short review summary.
- `Text`: Full customer review.
- `ProductId`: Product identifier.
- `Time`: Review timestamp.

A reproducible random sample was selected using a fixed random seed.

### Sentiment labelling

Sentiment labels were derived from customer ratings:

| Rating | Sentiment |
|---|---|
| 1–2 stars | Negative |
| 3 stars | Neutral |
| 4–5 stars | Positive |

These labels represent rating-based sentiment proxies rather than manually verified sentiment annotations.

## Tools and Technologies

- **Python** — Data processing and analysis
- **Pandas and NumPy** — Data manipulation
- **Matplotlib** — Data visualisation
- **Scikit-learn** — Text vectorisation, model training and evaluation
- **TF-IDF** — Converting text into numerical features
- **Logistic Regression** — Sentiment classification
- **Linear Support Vector Machine (SVM)** — Sentiment classification
- **Regular expressions** — Text cleaning and rule-based customer-intent extraction
- **Google Colab and Jupyter Notebook** — Development environment

## Project Workflow

### 1. Data cleaning and exploratory analysis

- Loaded and inspected the dataset.
- Examined missing values and duplicate records.
- Analysed customer rating distributions.
- Investigated review lengths and text characteristics.
- Combined review summaries and full review text into a single text field.

The sample contained one missing review summary and no exact duplicate rows. Missing summaries were handled when constructing the combined review text.

### 2. Text preprocessing

Review text was converted to lowercase, HTML tags and URLs were removed, non-letter characters were filtered, and whitespace was standardised.

This preprocessing helped create a consistent text representation for subsequent analysis.

### 3. Sentiment classification

TF-IDF vectorisation was used to transform review text into numerical features, including individual words and two-word combinations.

The data was split into training and testing sets using an 80:20 ratio, with stratification to preserve sentiment proportions.

Two classification models were trained and evaluated:

- Logistic Regression
- Linear Support Vector Machine (SVM)

### 4. Model evaluation

The models were assessed using accuracy, precision, recall, F1-score, and confusion matrices.

| Model | Accuracy | Macro F1-score |
|---|---:|---:|
| Logistic Regression | 83.47% | 0.68 |
| Linear SVM | 87.25% | 0.69 |

The Linear SVM achieved higher overall accuracy and a slightly higher macro F1-score.

However, its performance varied across sentiment classes. It performed particularly well on positive reviews but struggled to distinguish neutral reviews consistently.

### 5. Feature importance and sentiment patterns

The analysis examined influential TF-IDF features associated with each sentiment class.

Examples included:

- **Negative:** “disappointing”, “horrible”, and “not good”
- **Neutral:** “okay”, “three stars”, and “nothing special”
- **Positive:** “great”, “delicious”, and “excellent”

These features help illustrate how language patterns contribute to the models' predictions. They should be interpreted as model-associated features rather than proof of causation.

### 6. Customer feedback themes

Keyword-based analysis was used to explore recurring themes across sentiment groups.

The themes included:

- Taste and flavour
- Product quality
- Value and price
- Purchase intent
- Enjoyment
- Dietary attributes

Taste and flavour appeared frequently across all three sentiment groups. This suggests that product experience is an important area to investigate, although the analysis does not establish whether a particular theme causes positive or negative sentiment.

### 7. Rule-based customer-intent analysis

A rule-based function was developed to identify potential customer intentions from review text.

The categories included:

- Likely to repurchase
- Unlikely to repurchase
- Likely to recommend
- Unlikely to recommend
- Price-sensitive
- Potential return/refund
- Expressed need
- Unclear

The results were:

| Customer intent | Reviews | Percentage |
|---|---:|---:|
| Unclear | 20,576 | 68.59% |
| Expressed need | 3,758 | 12.53% |
| Likely to recommend | 2,692 | 8.97% |
| Price-sensitive | 1,127 | 3.76% |
| Unlikely to repurchase | 723 | 2.41% |
| Likely to repurchase | 687 | 2.29% |
| Potential return/refund | 285 | 0.95% |
| Unlikely to recommend | 152 | 0.51% |

The high proportion of reviews classified as unclear indicates that the keyword rules captured only a limited range of expressions. It highlights an opportunity to improve intent detection using more advanced contextual language models or a larger set of carefully validated rules.

These categories represent possible intentions expressed in review text, not confirmed customer actions.

## Key Findings

1. **The Linear SVM achieved the highest overall accuracy.** It recorded 87.25% accuracy compared with 83.47% for Logistic Regression.
2. **Neutral sentiment remained challenging.** The Linear SVM achieved a neutral-class F1-score of 0.38, highlighting the difficulty of distinguishing mixed or moderate opinions.
3. **Customer ratings were imbalanced.** Positive reviews represented 78.08% of the sample, which makes class-specific evaluation important.
4. **Product experience themes appeared across sentiment groups.** Taste and flavour, product quality, and value-related language were recurring themes.
5. **Rule-based customer-intent detection had limited coverage.** The 68.59% unclear category demonstrates that simple keyword matching cannot capture every expression of customer intent.

## Potential Business Applications

The analytical approach demonstrated in this project could help businesses:

- Monitor customer sentiment across product reviews.
- Identify recurring product complaints and positive feedback.
- Investigate customer concerns about pricing and product quality.
- Explore potential recommendation and repurchase signals.
- Prioritise areas for further customer experience investigation.

These are potential applications of the analysis; the project does not measure actual changes in customer retention, revenue, or business performance.

## Limitations

- Sentiment labels were derived from star ratings rather than manually annotated review text.
- The dataset was analysed using a 30,000-review sample, so findings may not represent the entire dataset.
- Positive reviews were overrepresented relative to neutral and negative reviews.
- TF-IDF models rely on learned word and phrase patterns and may struggle with sarcasm, context, and complex language.
- Rule-based theme and intent detection depends on predefined keywords and phrases.
- The customer-intent categories are estimates and do not confirm actual customer behaviour.
- An optional OpenAI API experiment was explored but could not be completed because the API account had exhausted its available quota. The completed analysis therefore relies on local NLP and machine learning methods rather than LLM-generated results.

## Conclusion

This project demonstrates an end-to-end text analytics workflow, from data cleaning and exploratory analysis to NLP preprocessing, sentiment classification, model evaluation, theme exploration, and rule-based customer-intent analysis.

The Linear SVM achieved 87.25% accuracy, although its weaker neutral-class performance shows why accuracy alone is not sufficient to evaluate a sentiment classifier.

The project also highlights the strengths and limitations of keyword-based analysis. While it offers an interpretable starting point for extracting customer insights, improved contextual modelling and validation would be needed for more reliable customer-intent detection.

Overall, the project demonstrates practical skills in Python, NLP, machine learning, data visualisation, model evaluation, and translating analytical findings into potential business applications.


## Author

**Xiluva Mabasa**

Data Science | Machine Learning | NLP | Data Analytics
