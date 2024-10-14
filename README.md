# Ammharic Ecommerce Entity Extractor

## Overview
This project focuses on implementing a real-time data ingestion system for EthioMart to consolidate e-commerce activities from various Telegram channels into a centralized platform. The primary goal is to develop an Amharic Named Entity Recognition (NER) system capable of extracting key business entities such as product names, prices, and locations.

With the rise of Telegram as a platform for e-commerce transactions in Ethiopia, multiple independent channels have emerged, creating a fragmented experience for vendors and customers. EthioMart's vision is to unify these channels into a single platform that facilitates easier product discovery, order placement, and communication.

## Key Objectives
- **Real-time Data Extraction**: Develop a system to fetch messages, images, and documents from Ethiopian-based Telegram e-commerce channels.
- **Fine-tune LLM for Amharic NER**: Train models to extract entities like product names, prices, and locations.

## Major Tasks
1. **Data Ingestion**: 
   - The Telethon library was used to develop a script for scraping data from Telegram channels.
  
2. **Preprocess Text Data**:
   - Handling missing message data
   - Emoji removal
   - Tokenization: A rule-based approach was implemented using regular expressions to tokenize text, capturing all non-whitespace characters.
  
3. **Label a Subset of Dataset in CoNLL Format**:
   - Entity detection: A rule-based approach was implemented to tokenize and label relevant entities in the dataset. Specific rules were defined for identifying various entities such as products, prices, locations, and phone numbers.

   - **Phone Numbers**: Tokens matching a pattern of 10 consecutive digits are labeled as `I-PHONE`.
   - **Prices**: Tokens representing prices (e.g., numbers followed by currency indicators like "ETB", "ብር", “birr” or "$") are labeled as `I-PRICE`.
   - **Locations**: Tokens that match known location names (e.g., 'Addis Ababa', 'ለቡ', 'ቦሌ', etc.) are labeled as `I-LOC`.
   - **General Tokens**: All other tokens are labeled as `O` (outside any entities).

4. **Fine-tune NER Model**:
   - Fine-tuned a Named Entity Recognition (NER) model to extract key entities (products, prices, phone numbers, and locations) from Amharic Telegram messages.
   - Pre-labeled data in CoNLL format was used to fine-tune the model.
   - Pre-trained models like `bert-base-multilingual-cased`, `distilbert-base-uncased`, and `xlm-roberta-base` were utilized for the fine-tuning process.

## Prerequisites
- **Python 3.x**: Ensure Python is installed on your system.
- **Virtual Environment**: Recommended for managing project dependencies.


