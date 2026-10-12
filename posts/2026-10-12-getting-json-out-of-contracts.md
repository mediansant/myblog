---
layout: post
title: "Getting JSON out of contracts is easy. Proving it's right is the project."
date: 2026-10-12
author: "Santosh Kumar Panda"
categories: [DuckDB, evaluation, LLM, structured-output]
tags: [LLM, EVALUATION, STRUCTURED-OUTPUT, DUCKDB]
description: "An LLM pipeline for legal contracts, scored field by field against 510 expert-labelled agreements."
---

An LLM pipeline for legal contracts, scored field by field against 510 expert-labelled agreements.

PDF to Markdown to typed record to DuckDB, with precision and recall per field. What the numbers said, and why the honest ones are the interesting ones.

<!-- Add your full article body below -->

## Introduction

Extracting structured data from complex legal text seems straightforward with modern LLMs and tool calling features. However, moving from a proof-of-concept to a production-grade system requires rigorous engineering and comprehensive evaluation. 

## The Pipeline Architecture

Our ingestion architecture follows a predictable, reproducible sequence:
1. **PDF to Markdown Conversion:** Parsing unstructured layouts into standardized markdown text.
2. **Typed Record Extraction:** Using structured JSON outputs constrained by strict Pydantic schemas.
3. **Analytical Data Store:** Loading the validated records directly into DuckDB for fast relational querying and analysis.

## Evaluation Methodology

To ground our metrics in reality, we established a benchmark baseline utilizing **510 expert-labelled agreements**. Every single extracted field was subjected to unit-level scoring across primary criteria:

* **Precision:** Ensuring the extracted information strictly belongs in the target property without hallucinated details.
* **Recall:** Measuring how effectively the model captures every relevant clause without missing critical terms.

The results highlighted a stark contrast between superficially clean outputs and robust data models. It is the edge cases—and the honest failures—that provide the most actionable engineering insights.
