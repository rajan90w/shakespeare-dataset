# Shakespeare Complete Works Dataset 🎭

A comprehensive, clean dataset containing the complete works of William Shakespeare, preprocessed and optimized for AI/ML research, NLP tasks, and language model training.

## Dataset Overview

This repository contains **The Complete Works of William Shakespeare** in a machine-learning-friendly format, featuring:

- **196,399 lines** of authentic Shakespeare text
- **966,506+ words** of literary content
- **~750K-950K tokens** (approx. 5.4 MB)
- All **37 plays** (tragedies, comedies, histories)
- **154 sonnets** and narrative poems
- Project Gutenberg edition (updated August 2025)

## Dataset Statistics

| Metric | Value |
|--------|-------|
| **Lines** | 196,399 |
| **Words** | 966,506 |
| **Characters** | 5,378,701 |
| **File Size** | 5.4 MB |
| **Tokens (GPT-style)** | ~743,466 |
| **Tokens (Average)** | ~953,781 |
| **Language** | English (Early Modern English) |
| **License** | Public Domain (Project Gutenberg) |

## Contents

### Plays Included (37 total)
**Tragedies:**
- Hamlet, Prince of Denmark
- Macbeth
- Othello, the Moor of Venice
- King Lear
- Romeo and Juliet
- Julius Caesar
- Antony and Cleopatra
- Coriolanus
- Titus Andronicus

**Comedies:**
- A Midsummer Night's Dream
- Much Ado About Nothing
- The Merchant of Venice
- As You Like It
- Twelfth Night
- The Taming of the Shrew
- All's Well That Ends Well
- Measure for Measure
- The Comedy of Errors
- Love's Labour's Lost
- The Merry Wives of Windsor
- Pericles, Prince of Tyre
- Cymbeline
- The Winter's Tale
- The Tempest
- The Two Gentlemen of Verona
- Two Noble Kinsmen

**Histories:**
- Henry IV, Part 1
- Henry IV, Part 2
- Henry V
- Henry VI, Part 1
- Henry VI, Part 2
- Henry VI, Part 3
- Henry VIII
- King John
- Richard II
- Richard III

**Poetry:**
- 154 Sonnets
- A Lover's Complaint
- The Passionate Pilgrim
- The Phoenix and the Turtle
- The Rape of Lucrece
- Venus and Adonis

## Use Cases

### 📚 NLP & Machine Learning
- **Language Model Fine-tuning** - Train models on Shakespearean language patterns
- **Text Generation** - Generate Shakespearean-style poetry and dialogue
- **Style Transfer** - Learn to write in Early Modern English
- **Sentiment Analysis** - Analyze emotions in classic literature
- **Named Entity Recognition** - Extract character names and locations

### 🎓 Academic Research
- **Computational Linguistics** - Study linguistic patterns and evolution
- **Literary Analysis** - Automated analysis of themes, meter, and structure
- **Authorship Attribution** - Stylometry and authorship verification
- **Language Modeling** - Build domain-specific language models

### 🎮 Creative Projects
- **Chatbots** - Create Shakespeare-inspired conversational AI
- **Game Development** - Generate NPC dialogue and narratives
- **Text Adventure Games** - Create story-driven experiences
- **Interactive Theater** - Generate adaptive dramatic scenes

## File Format

**main dataset file:** `final_dataset.txt`

The dataset is provided as a plain text file with:
- Clear structural markers (ACT, SCENE, character names)
- Preserved original formatting and punctuation
- UTF-8 encoding
- Unix line endings (LF)

```
Example structure:
THE SONNETS

1

From fairest creatures we desire increase,
That thereby beauty's rose might never die,
...

THE TRAGEDY OF HAMLET, PRINCE OF DENMARK

ACT I.

SCENE I.—ELSINORE. A PLATFORM BEFORE THE CASTLE.
...
```

## Token Count Reference

For budget planning and API usage:

| Model | Tokens | Est. Context Windows |
|-------|--------|----------------------|
| Claude 3.5 Sonnet | ~743K-950K | Fits in 3-4 windows |
| GPT-4 | ~743K-950K | Fits in 3-4 windows |
| Llama 2 | ~750K | Fits in context |

**API Cost Estimate (Claude 3.5):**
- Input tokens: ~745K × $0.015/1K = **~$11.18**
- Recommended: Use batch processing for cost savings

## Getting Started

### Download the Dataset
```bash
# Clone the repository
git clone https://github.com/yourusername/shakespeare-dataset.git
cd shakespeare-dataset

# View the dataset
cat final_dataset.txt | head -100

# Get statistics
wc -l final_dataset.txt
wc -w final_dataset.txt
```

### Quick Analysis
```bash
# Count total words
wc -w final_dataset.txt

# Find specific play
grep -n "HAMLET" final_dataset.txt | head -5

# Extract sonnets
sed -n '/THE SONNETS/,/THE TRAGEDY/p' final_dataset.txt > sonnets.txt
```

### Using with Python
```python
# Load the dataset
with open('final_dataset.txt', 'r', encoding='utf-8') as f:
    shakespeare_text = f.read()

# Basic statistics
word_count = len(shakespeare_text.split())
char_count = len(shakespeare_text)

print(f"Words: {word_count:,}")
print(f"Characters: {char_count:,}")

# Tokenize with popular libraries
from transformers import AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("gpt2")
tokens = tokenizer.encode(shakespeare_text)
print(f"Tokens (GPT-2): {len(tokens):,}")
```

### Using with LLMs

**With Claude API:**
```python
import anthropic

client = anthropic.Anthropic()

with open('final_dataset.txt', 'r') as f:
    shakespeare_text = f.read()

response = client.messages.create(
    model="claude-3-5-sonnet-20241022",
    max_tokens=1024,
    messages=[
        {
            "role": "user",
            "content": f"Analyze the themes in this Shakespeare text:\n\n{shakespeare_text[:50000]}"
        }
    ]
)

print(response.content[0].text)
```

**For Fine-tuning:**
```bash
# Prepare data in JSONL format for batch processing
python prepare_for_finetuning.py --input final_dataset.txt --output shakespeare_training.jsonl
```

## Dataset Quality

✅ **Advantages:**
- **Complete and Authentic** - All 37 plays plus poetry
- **Well-Structured** - Clear scene and act divisions
- **Public Domain** - Free to use commercially
- **High Quality** - Project Gutenberg standard
- **Consistent Formatting** - Easy to parse and process
- **Large Enough** - Sufficient for meaningful ML tasks

## License

This dataset is derived from **Project Gutenberg eBook #100** and is in the **Public Domain**.

You are free to:
- ✅ Use for commercial purposes
- ✅ Redistribute
- ✅ Modify
- ✅ Use in academic research
- ✅ Create derivative works

**Attribution:** While not required, we appreciate credit to:
- William Shakespeare (Original Author)
- Project Gutenberg (Digitization)

## Citation

If you use this dataset in research, please cite:

```bibtex
@dataset{shakespeare_complete_works_2025,
  title={Complete Works of William Shakespeare - ML Dataset},
  author={Shakespeare, William and Project Gutenberg},
  year={2025},
  url={https://github.com/yourusername/shakespeare-dataset}
}
```

## Repository Structure

```
shakespeare-dataset/
├── README.md                          # This file
├── final_dataset.txt                  # Complete works (5.4 MB)
├── DATASET_ANALYSIS.md               # Detailed statistics
├── LICENSE                            # Public Domain
├── examples/
│   ├── load_dataset.py               # Python loading example
│   ├── tokenize_shakespeare.py        # Tokenization examples
│   └── fine_tune_example.py           # Fine-tuning template
├── scripts/
│   ├── extract_play.py                # Extract specific plays
│   ├── extract_sonnets.py             # Extract sonnets
│   └── statistics.py                  # Generate statistics
└── data/
    └── statistics.json                # Pre-computed statistics
```

## Statistics & Insights

### Word Distribution
- **Average words per line:** ~4.9
- **Total unique words (estimated):** ~30,000+
- **Archaic/rare words:** ~15% (opportunity for linguistic study)

### Play Length (approximate)
- **Shortest play:** The Comedy of Errors (~13K words)
- **Longest play:** Hamlet (~29K words)
- **Average play:** ~26K words

### Sonnet Information
- **Total sonnets:** 154
- **Words per sonnet:** ~111 (on average)
- **Form:** 14 lines, iambic pentameter

## Contributing

Contributions welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines:

- 🐛 Report bugs
- 💡 Suggest improvements
- 🧪 Share research findings
- 📝 Add documentation
- 🔧 Optimize code examples

## Contact & Support

- **Issues:** Use GitHub Issues for bugs or questions
- **Discussions:** Check GitHub Discussions for community chat
- **Email:** your-email@example.com

## FAQ

**Q: Can I use this commercially?**
A: Yes! It's public domain. No restrictions.

**Q: Is this the complete works?**
A: Yes, all 37 plays, 154 sonnets, and narrative poems.

**Q: What encoding is used?**
A: UTF-8, with Unix line endings (LF).

**Q: Can I split this into individual plays?**
A: Yes! See `scripts/extract_play.py` for examples.

**Q: How accurate is the token count?**
A: ~743K-950K tokens depending on tokenizer. See dataset analysis for details.

**Q: Can I use this for commercial LLM training?**
A: Yes, but consider licensing obligations of your LLM framework.

## Related Resources

- [Project Gutenberg Shakespeare Collection](https://www.gutenberg.org/ebooks/100)
- [Stanford OpenData Shakespeare Corpus](http://www.stanford.edu/~ralam/shakespeare_data/)
- [No Fear Shakespeare](https://www.sparknotes.com/nofear/shakespeare/)
- [Shakespeare Birthplace Trust](https://www.shakespearebirthplace.org.uk/)

## Acknowledgments

- **William Shakespeare** - The Original Author
- **Project Gutenberg** - For digitization and maintenance
- **Community Contributors** - For suggestions and improvements

---

⭐ If you find this dataset useful, please give it a star! It helps other researchers discover it.

**Last Updated:** November 2025
**Dataset Version:** 1.0
