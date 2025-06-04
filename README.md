

# CDocRAG_Bench

## 🚀Overview

​	Document retrieval–augmented generation (RAG) systems have shown great promise for enhancing language models with external knowledge, but their evaluation has so far been limited to synthetic or unimodal benchmarks that overlook essential dimensions of real-world use cases. 

​	To address this gap, we introduce **CDOCRAG-BENCH**, the first large-scale, multilingual, multimodal benchmark designed specifically for document RAG. The benchmark comprises an extensive corpus of over 62,000 pages, featuring multilingual and multi-type documents. 2,000 single-hop and 2,000 multi-hop queries are synthesized and examined using a knowledge-graph-driven pipeline and fine-grained principles, with evidence labels searched exhaustively. Crucially, to ensure high precision, all ground-truth annotations are then refined through expert human review. We evaluate seven state-of-the-art embedding models and three end-to-end RAG frameworks, demonstrating that multimodal embeddings yield significant retrieval gains up to 15.48% compared to textual embeddings, and current frameworks still struggle with effective pipelines for multi-page understanding. By diagnosing key shortcomings of current approaches and offering a comprehensive evaluation framework, CDOCRAG-BENCH provides a rigorous foundation for future research in multimodal document retrieval-augmented generation.

![pipeline](D:\Python Project\backup\git_project\DocRAG_Bench\asset\pipeline.png)



## 💡 Highlights
- 🔥 **Large-scale**: CDocRAG-Bench is the first large-scale multilingual and multimodal benchmark for document retrieval-augmented generation, featuring an extensive corpus of over 62,000 pages across diverse document types and languages.
- 🔥 **High-quality annotation**: It synthesizes single-hop and multi-hop queries using a knowledge-graph-driven pipeline and fine-grained principles, with all ground-truth annotations refined through expert human review to ensure high precision.
- 🔥 **Comprehensive evaluation**: The benchmark provides a comprehensive evaluation framework, conducting extensive experiments with seven state-of-the-art embedding models and three advanced RAG frameworks, uncovering key insights and challenges for future research.



## 🔍Benchmark

We save our benchmark  in `./cDocRAG_Bench.`

- This is an example of a single-hop question in our CDOCRAG-BENCH benchmark. It includes a unique identifier (`uid`), the query content (`question`), a reference answer (`answer`), and metadata such as the original file name (`file_name`), reference page numbers (`reference_page`), data source type (`source_type`), and language (`language`).

```
{
    "uid": "680_en",
    "question": "What does the historical population data suggest about demographic changes in Yorkton from 1901 to 2021?",
    "answer": "The historical population data indicates a significant increase in Yorkton's population from 700 in 1901 to 16,280 in 2021, reflecting substantial demographic growth over the 120-year span.",
    "file_name": "Farrell_Agencies_Arena",
    "reference_page": [ 3,4,12],
    "source_type": "table",
    "language": "en"
}
```
- This is an example of a multi-hop question in our CDOCRAG-BENCH benchmark. It includes a unique identifier (uid), the query content (question), a reference answer (answer), and metadata such as the original file name (file_name), reference page numbers (reference_page), and language (language). Additionally, it contains a steps section that breaks down the multi-hop reasoning process into individual steps, each with its own question, answer, and reference page numbers.

```
{
    "uid": "3281_en",
    "file_name": "txdw0217",
    "question": "What significantly reduces the incidence and severity of the condition that the drug evaluated in the pilot evaluation for treating hot flashes has been shown to reduce in phase II trials by 75% to 90% in clinical trials?",
    "answer": "Hormone therapy",
    "reference_page": [12,15,29,31,34,35,36,40,41,42],
    "steps": [
      {
        "question0": "What drug was evaluated in the pilot evaluation for treating hot flashes?",
        "answer0": "Gabapentin",
        "reference_page": [15,29]
      },
      {
        "question1": "What condition has Gabapentin been shown to reduce in phase II trials?",
        "answer1": "Hot flushes",
        "reference_page": [29,36,40,42]
      },
      {
        "question2": "What significantly reduces the incidence and severity of hot flushes by 75% to 90% in clinical trials?",
        "answer2": "Hormone therapy",
        "reference_page": [12,15,31,34,35,36,41]
      }
    ],
    "language": "en"
  }
```

