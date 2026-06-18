---
layout: page
title: COVID Information Retrieval
description: Comparative study of IR models for ranking CORD-19 literature with strong MAP performance.
img: /assets/img/projects/covid.jpg
importance: 1
category: Generative Models & NLP
related_publications: true
paper: https://arxiv.org/abs/2305.12528
report: /assets/pdf/reports/covid_ir_paper.pdf
---

## Problem

Evaluate retrieval frameworks for ranking COVID-19 research documents from the CORD-19 corpus.

## What I Built

- Used BM25 as a lexical baseline on titles and abstracts.
- Implemented dense retrieval with Contriever and BERT embeddings.
- Benchmarked results against TREC-COVID labeled relevance data.

## Outcomes

- Reached a peak MAP score around 0.72.
- Published as {% cite jain2023covid %} (archived in Europe PMC).

## Technologies

- Python
- BM25
- BERT/Contriever embeddings
- Information retrieval evaluation metrics
