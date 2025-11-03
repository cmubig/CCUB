# CCUB Dataset: Cross-Cultural Understanding Benchmark

[![arXiv](https://img.shields.io/badge/arXiv-2301.12073-b31b1b.svg)](https://arxiv.org/abs/2301.12073)
[![Project Page](https://img.shields.io/badge/Project-Page-green)](https://github.com/cmubig/CCUB)

## Overview

The **Cross-Cultural Understanding Benchmark (CCUB)** is a culturally curated dataset of text-image pairs designed to evaluate and improve cultural representation in text-to-image synthesis models. Each image and caption is validated by people with personal connections to the respective cultures to ensure authentic representation and avoid stereotypes.

**Paper**: [Towards Equitable Representation in Text-to-Image Synthesis Models with the Cross-Cultural Understanding Benchmark (CCUB) Dataset](https://arxiv.org/abs/2301.12073)  
**Published**: AAAI Workshop on Creative AI Across Modalities, 2023  
**Authors**: Zhixuan Liu, Youeun Shin, Beverley-Claire Okogwu, Youngsik Yun, Lia Coleman, Peter Schaldenbrand, Jihie Kim, Jean Oh

For fine-tuning applications using this dataset, see our follow-up work: [SCoFT: Self-Contrastive Fine-Tuning for Equitable Image Generation](https://arxiv.org/abs/2401.08053)

## Dataset Structure

### Data Schema

| Field | Type | Description |
|-------|------|-------------|
| `country_code` | String | 3-letter country/region code (e.g., "KOR") |
| `category_code` | String | Cultural category (ARCH, CLOTH, CITIES, FOOD, etc.) |
| `url` | String | Direct URL to the image |
| `caption` | String | Culturally accurate description |
| `created_at` | Timestamp | ISO 8601 formatted date |

### Coverage

- **Countries**: 5 cultures including Korea, China, Nigeria, and others
- **Categories**: 9 categories (Architecture, Clothing, Cities, Food, Art, Festivals, Nature, Daily Life, etc.)
- **Size**: ~140 text-image pairs per culture
- **Total**: Approximately 700-1000 curated pairs

### Example Entry
```
country_code: KOR
category_code: FOOD
url: https://upload.wikimedia.org/wikipedia/commons/2/22/Tteok-bokki_3.jpg
caption: a plate of rice cake tteokbokki covered in spicy sauce on a table
created_at: 2024-07-01T12:02:12Z
```

## Usage

### Accessing the Dataset

The dataset is organized in **multiple sheets** (one per country) in a single Google Sheets document.

**Google Sheets URL**: [https://docs.google.com/spreadsheets/d/1dbSXgwCZuu9zpDZyUQ-pKDZGRYhzeaXCR5geRYNUwEA/](https://docs.google.com/spreadsheets/d/1dbSXgwCZuu9zpDZyUQ-pKDZGRYhzeaXCR5geRYNUwEA/)

### Download Methods

#### Option 1: Download All Sheets as ZIP
1. Open the Google Sheets link
2. Go to `File` → `Download` → `Comma Separated Values (.csv)`
3. This downloads all sheets as separate CSV files

#### Option 2: Download Individual Sheets
Each country has its own sheet with a unique `gid`:

```python
import pandas as pd

# Sheet URLs for each country (replace gid values)
sheets = {
    'KOR': 'https://docs.google.com/spreadsheets/d/1dbSXgwCZuu9zpDZyUQ-pKDZGRYhzeaXCR5geRYNUwEA/export?format=csv&gid=1345336179',
    'CHN': 'https://docs.google.com/spreadsheets/d/1dbSXgwCZuu9zpDZyUQ-pKDZGRYhzeaXCR5geRYNUwEA/export?format=csv&gid=567535443',
    # Add other countries with their gid values
}

# Load a specific country
df_korea = pd.read_csv(sheets['KOR'])
df_china = pd.read_csv(sheets['CHN'])

# Or load all countries
all_data = []
for country, url in sheets.items():
    df = pd.read_csv(url)
    all_data.append(df)

df_all = pd.concat(all_data, ignore_index=True)
```

### Applications

- **Text-to-Image Model Evaluation**: Benchmark cultural understanding and bias
- **Fine-Tuning**: Improve cultural representation in generative models (see [SCoFT](https://arxiv.org/abs/2401.00805))
- **Cultural Bias Research**: Study representation in vision-language models
- **Dataset Bias Analysis**: Compare against web-scraped datasets

## Dataset Curation

All images and captions are curated and validated by cultural insiders:

1. **Selection**: Images chosen by people with personal connections to each culture
2. **Captioning**: Native people (cultural experts) give caption the images
3. **Validation**: Cultural experts manually correct misinterpretations and errors
4. **Quality Control**: Focus on authentic representation, containing both traditional and modern representation, avoiding stereotypes

## Citation

```bibtex
@misc{liu2023equitablerepresentationtexttoimagesynthesis,
      title={Towards Equitable Representation in Text-to-Image Synthesis Models with the Cross-Cultural Understanding Benchmark (CCUB) Dataset}, 
      author={Zhixuan Liu and Youeun Shin and Beverley-Claire Okogwu and Youngsik Yun and Lia Coleman and Peter Schaldenbrand and Jihie Kim and Jean Oh},
      year={2023},
      eprint={2301.12073},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2301.12073}, 
}
```
```bibtex
@inproceedings{liu2024scoft,
  title={SCoFT: Self-contrastive fine-tuning for equitable image generation},
  author={Liu, Zhixuan and Schaldenbrand, Peter and Okogwu, Beverley-Claire and Peng, Wenxuan and Yun, Youngsik and Hundt, Andrew and Kim, Jihie and Oh, Jean},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  pages={10822--10832},
  year={2024}
}
```

**Links**:
- Paper: [arXiv:2301.12073](https://arxiv.org/abs/2301.12073)
- Dataset: [Google Sheets](https://docs.google.com/spreadsheets/d/1dbSXgwCZuu9zpDZyUQ-pKDZGRYhzeaXCR5geRYNUwEA/)
- Fine-tuning Method: [SCoFT (arXiv:2401.00805)](https://arxiv.org/abs/2401.00805)

## Team

**Carnegie Mellon University**: Zhixuan Liu, Beverley-Claire Okogwu, Lia Coleman, Peter Schaldenbrand, Jean Oh  
**Dongguk University**: Youeun Shin, Youngsik Yun, Jihie Kim

## Contact

For questions or collaborations: [github.com/cmubig/CCUB](https://github.com/cmubig/CCUB)

## License

Verify individual image licenses before use. Dataset compilation follows academic research guidelines.
