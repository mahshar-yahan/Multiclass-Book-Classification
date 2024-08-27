# Bangla Text Preprocessing and BERT Model Fine-Tuning

This project focuses on preprocessing Bangla text data and fine-tuning the `banglabert` model for a downstream text classification task. The dataset undergoes extensive preprocessing to ensure high-quality inputs for the model, followed by fine-tuning and parameter optimization.

## Data Pre-processing

We perform several steps to clean and prepare the dataset:

1. **Exploration:**
   - Initial exploration of the dataset to understand text orientation and identify 'NaN' values.
   - Columns with 'NaN' values are removed from the training set.

2. **Text Length Visualization:**
   - Analyzed text length to determine the average length and adjust preprocessing steps accordingly.

3. **Text Cleaning:**
   - Removed stop words, punctuation, and unnecessary whitespace.
   - Normalized text and converted all English text to lowercase.
   - Removed 'href' links from the dataset.
   - Converted "%" symbols to the Bangla equivalent 'শতাংশ'.
   - Removed optional occurrences of ZWNJ or ZWJ from Bangla text.
   - Converted emojis to their respective text descriptions.

## Modeling and Parameter Setting

### Data Splitting
- The dataset is split into training and validation sets with an 80:20 ratio.

### Model Fine-Tuning
- We fine-tuned the `banglabert` model for this specific downstream task.
- Set the maximum text length to 320 for tokenization of the summary.
- Enabled truncation and padding during tokenization.
- For training and validation, only `input_ids`, `attention_mask`, and labels are kept. For testing, only `input_ids` and `attention_mask` are retained.

### Inference Parameters
- **Learning Rate:** `2e-5`
- **Warmup Ratio:** `0.1`
- **Weight Decay:** `0.01`
- **Epochs:** `5`
- **Batch Size:** `8`
- **Optimizer:** `Adafactor`
- **Dropout Rate:** `0.3`

## Getting Started

### Prerequisites
- Python 3.x
- Transformers library (Hugging Face)
- Pandas, NumPy, and other data processing libraries

### Installation
Clone the repository:
```bash
git clone https://github.com/yourusername/bangla-text-preprocessing.git
cd bangla-text-preprocessing
