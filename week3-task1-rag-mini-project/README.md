# Week 3 — RAG Mini-Project: Chat With Your Own Document

**Aila Nasir · Generative AI & Prompt Engineering Intern · NeuroFive Solutions**

## Objective
To build a small Retrieval-Augmented Generation (RAG) pipeline using a no-code tool (NotebookLM), test it with real content questions on a chosen document, check for hallucinations, and compare answer quality against a plain prompt with no document grounding.

## Document Used
"A Primer on Machine Learning for Fraud Detection" — Stripe's official technical guide explaining how Stripe Radar uses machine learning (feature engineering, embeddings, supervised models) to detect payment fraud at scale.
Source: stripe.com/guides/primer-on-machine-learning-for-fraud-protection

## Tool Used
NotebookLM (Google) — the document was uploaded as a PDF source and all questions were answered strictly from that source.

## Q&A Testing (NotebookLM, grounded in the document)

**Q1: What is unsupervised learning and how is it used for fraud detection according to this document?**
The document doesn't use the exact term "unsupervised learning," but describes a related concept, embeddings, which lets the system learn higher-level concepts without explicit labeling. Stripe uses embeddings to capture similarity between entities (e.g. recognizing Uber and Lyft have similar transaction patterns), enabling it to transfer learnings from one merchant to another and automatically catch a fraud pattern in one region if it already appeared in another.

**Q2: How does Stripe Radar detect friendly fraud?**
The document doesn't use the term "friendly fraud" explicitly, but describes the underlying mechanism: Radar leverages network-wide data (90% of cards have been seen before), ground-truth dispute data from card networks, and hundreds of engineered features (like IP address history) to distinguish legitimate transactions from fraudulent disputes while minimizing false positives.

**Q3: What role does feature engineering play in fraud detection?**
Feature engineering is described as one of the most critical parts of the system — formulating predictive signals (e.g. IP address history), encoding categorical data via embeddings (merchant, issuing bank, day of week), and enabling real-time computation with low latency so the fraud check doesn't disrupt checkout. Better features directly improve precision and recall.

**Q4: How does Stripe use IP address data as a fraud signal?**
Stripe tracks the two most frequently used IP addresses for every card seen on its network, and compares new transactions against this history — a payment from a familiar IP (like home or work) is considered lower risk than one from an unfamiliar location. Businesses can also set manual rules to flag IP-country/card-country mismatches.

**Q5: What types of fraud does this guide mention beyond payment fraud?**
The guide focuses almost exclusively on online credit card and payments fraud — stolen card fraud, card-not-present transactions, and fraudulent disputes/chargebacks. It does not detail other fraud categories like account takeover or identity theft outside the stolen-card context.

## Hallucination Test

*Trick question: "What was Stripe's exact fraud detection accuracy percentage in 2022?" (this figure does not exist in the document — the guide was last updated December 2021)*

**NotebookLM (with document):** Correctly stated that no exact accuracy percentage for 2022 exists in the source. Instead of guessing, it surfaced the real metrics the document did contain — a 20% year-over-year machine learning improvement and up to a 0.5 percentage point monthly recall increase — and explained that a single "accuracy" number is misleading in fraud detection because of the precision/recall trade-off.

**Plain Gemini (no document):** Confidently fabricated specific statistics not present anywhere in the source: a 0.1% false positive rate, a 32% average fraud reduction, and a 97% detection rate for card testing attacks. These numbers sounded precise and credible but were entirely invented — a clear hallucination.

## Comparison: RAG vs. Plain Prompt

| Question | NotebookLM (RAG, with document) | Plain Gemini (no document) |
|---|---|---|
| Unsupervised learning at Stripe | Grounded in the source — explained embeddings, merchant similarity, and transfer learning between merchants (e.g. Uber/Lyft), all traceable to the document | Detailed but entirely fabricated — invented mechanisms (autoencoders, botnet clustering, zero-day fraud detection) that do not appear in the source |
| Exact 2022 fraud detection accuracy | Correctly stated this figure is not in the document; surfaced only the real metrics the document contained (20% YoY improvement, 0.5%/month recall gain) | Hallucinated specific, confident-sounding statistics: 0.1% false positive rate, 32% average fraud reduction, 97% detection rate — none of which appear in the source |
| Grounding / verifiability | 100% traceable to the source document | 0% — plausible-sounding but unverifiable and fabricated |

## Summary
The difference between the two approaches was starkest on the fact-check question. When asked for Stripe's exact 2022 fraud detection accuracy, NotebookLM correctly identified that this figure does not exist in the source document and instead surfaced the real, verifiable metrics the document did contain. Plain Gemini, with no document to ground it, confidently fabricated a set of precise-sounding statistics that do not appear anywhere in the source and cannot be verified — a textbook hallucination: specific, confident, and completely invented. The same pattern held on the unsupervised learning question, where plain Gemini produced a detailed, well-written answer built on mechanisms that sound plausible but were never in the document, while NotebookLM's answer stayed tied to what Stripe actually described. This is the core value of RAG: grounding doesn't just add citations, it removes the model's ability to guess confidently when it doesn't actually know.

## Submission Links

**GitHub Repo:** https://github.com/ailanasirai/neurofive-genai-internship

**Full Doc (Google Docs):** https://docs.google.com/document/d/1Bb5CekfhzbaA8h4L1HLIejc4OqMD9DKxEsGs4Ft3xao/edit?tab=t.0#heading=h.dgau9j1m2fpp

**LinkedIn Profile:** https://www.linkedin.com/in/aila-nasir/
