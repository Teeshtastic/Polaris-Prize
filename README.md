# Music Theme Classification Project

## Project Task
I have been an avid fan of the Polaris Prize, which is a Canadian music award that recognizes the best full-length Canadian album based on artistic merit, regardless of genre, sales, or record label. The 2025 long list was just realized and I'm listening to each of the top 40 albums right now in anticipation of the short list of the ten best albums before the ultimate crowning of the winner this fall. Each year I predict which albums will be short-listed and which will win and have been achieving fairly high accuracy. I built a text classification model to automatically categorize music albums by their themes. The model reads album descriptions and predicts one of 6 music themes:

- **Love & Relationships** - Songs about romance and dating
- **Identity & Heritage** - Cultural identity and personal growth  
- **Social Commentary** - Political and social justice messages
- **Introspection & Philosophy** - Deep thoughts and spirituality
- **Place & Landscape** - Songs about locations and nature
- **Experimental & Abstract** - Avant-garde and artistic music

## Dataset
**Source**: Polaris Music Prize dataset (Canadian music awards)
- **Total**: 200 albums from 2020-2024
- **Training**: 160 albums (80%)
- **Validation**: 40 albums (20%)

**Features used**:
- Album title and artist name
- Music genre
- Album description
- Critical reviews

I combined all the text into one feature like this:
`"Album: [title] | Artist: [name] | Genre: [genre] | Description: [description]"`

## Pre-trained Model
**Model**: XLM-RoBERTa-base

**Why I chose this model**:
- Works with multiple languages (good for Canadian French/English content)
- Pre-trained on lots of text data
- Good performance on classification tasks
- Right size for the size of the dataset 

## Performance Metrics
**Final Results**:
- **Accuracy**: 87.5% on validation data
- **Best performing theme**: Experimental & Abstract (92% precision)
- **Most challenging theme**: Place & Landscape (79% precision)

**Detailed Results**:
| Theme | Precision | Recall |
|-------|-----------|--------|
| Love & Relationships | 88% | 85% |
| Social Commentary | 91% | 83% |
| Identity & Heritage | 79% | 90% |
| Introspection & Philosophy | 85% | 82% |
| Place & Landscape | 83% | 79% |
| Experimental & Abstract | 92% | 87% |

## Hyperparameters
**Key settings that worked best**:

- **Learning Rate**: 2e-5 (standard for transformer models)
- **Batch Size**: 4 (small because of limited data)
- **Epochs**: 6 (stopped when validation accuracy peaked)
- **Max Length**: 512 tokens 

**Why these worked**:
- Small batch size prevented overfitting on our small dataset
- 6 epochs was enough time to learn without overfitting
- Learning rate of 2e-5 is recommended for fine-tuning transformers

## Relevant Links
- **Dataset**: Polaris Music Prize album data (2020-2024) - compiled through web research with AI-assisted data collection
- **Source**: [Polaris Music Prize Official Website](https://polarismusicprize.ca/)
- **Code Repository**: https://github.com/Teeshtastic/Polaris-Prize.git


## What I Learned
- How to fine-tune transformer models for classification
- Importance of proper train/validation splits
- Text preprocessing for music data
- How to evaluate model performance with multiple metrics
- Working with multilingual text data

## Future Improvements
- Train on more data to improve accuracy
- Test on music from other countries
- Add more theme categories
- Try different transformer models