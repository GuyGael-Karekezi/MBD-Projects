# Assignment 2 Report - Social Media Extremism Detection

## Team
- Lynne Chepkwony (lchepkwo)
- Mohammed Abubakari Sadic (abubakam)
- Emile Lucky Muhigira (emuhigir)
- Ishimwe Karekezi Guy Gael (iguygael)

## A. Quantitative Analysis
### Dataset statistics
- Dataset loaded from `extremism_data_final.csv`.
- Initial shape reported in notebook outputs: 2777 rows, 2 columns.
- Class balance is close to even (NON_EXTREMIST slightly higher).
- Duplicate check: 0 duplicates in the initial dataset.
- Missing data handling: missing `Original_Message` rows were imputed with `[MISSING_TEXT]` to preserve rows and satisfy imputation requirement.

### Text characteristics
Added:
- `text_length`
- `word_count`
- `avg_word_length`

Compared statistics by class and visualized:
- Class distribution bar chart
- Histograms for all three text-feature columns

### Linguistic analysis
- Top-20 words overall
- Top-20 words per class
- Word clouds for EXTREMIST and NON_EXTREMIST
- Two most prominent words per class reported in notebook

## B. Qualitative Analysis
### Annotation sample
- Built balanced 30-example sample (15 EXTREMIST, 15 NON_EXTREMIST)
- Added `id` column
- Exported as `mbd_annotation_sample_30.csv`

### Annotation process
- Independent human annotation by all group members
- `original_label` hidden during annotation
- No discussion until all annotations completed

### IRR
Computed:
- Pairwise percentage agreement for annotator pairs
- Pairwise Krippendorff alpha between annotators and versus `original_label`

### Disagreement analysis
- Computed inter-human disagreement rate
- Identified most-disagreed examples (3-1 split rows since no 2-2 rows)
- Compared majority vote with original labels and interpreted implications for label quality

## C. ML Baseline
- Built canonical cleaned modeling dataframe
- Stratified split 70/15/15 with `random_state=42`
- TF-IDF vectorization using default parameters
- LogisticRegression using default parameters
- Validation evaluation with classification report and confusion matrix

## D. Error Analysis
### Systematic review
- Found all misclassifications on validation set and separated into FP/FN in notebook.
- Exported 10-example manual review file as required: `errors_validation_10.csv`.

### Insights and improvements
Manual review patterns:
- Context/stance confusion (reporting vs promoting extremism)
- Noisy/slang text causing lexical overlap errors

Proposed improvements:
1. Class-weighting and threshold tuning for better extremist recall
2. Contextual embeddings
3. Domain-specific linguistic features (violence + target + negation cues)

Tried improvement:
- MiniLM sentence embeddings + Logistic Regression
- Small validation gain and slight FN reduction
