## Module 3: Data Security in the AI Pipeline

**Learning objectives**
- Explain why data is the highest-leverage attack surface in most AI systems
- Identify where in an ETL pipeline malicious or poisoned data can be introduced
- Distinguish the main types of data poisoning
- Describe data provenance and lineage as security controls

### Lesson

If a model is only as trustworthy as the data it learned from, then data is the attack surface that matters most — and it's also the one most beginners overlook, because it doesn't look like a "security" problem at first glance. Compromising a model's behavior rarely requires touching the model file itself; it's almost always easier to manipulate what goes into it.

### Where the ETL pipeline is exposed

Most training data passes through an ETL (Extract, Transform, Load) pipeline before it ever reaches a model. Each stage has its own exposure:

- **Extraction** — data is pulled from external sources (web scrapes, user-generated content, third-party datasets, partner feeds). This is the easiest stage for an attacker to influence, since they often don't need any access to your infrastructure at all — just the ability to publish content somewhere your scraper will eventually collect it.
- **Transformation** — data is cleaned, labeled, normalized, or augmented. A compromised transformation step (a tampered labeling tool, a malicious preprocessing script) can quietly corrupt data at scale without anyone touching the raw source.
- **Loading** — data is written into the storage system the training pipeline reads from. Weak access controls here mean an attacker with any foothold in your infrastructure can inject or modify training data directly.

### Types of data poisoning

- **Label flipping** — correct data paired with incorrect labels, degrading the model's accuracy on the affected category.
- **Backdoor / trigger poisoning** — a small number of samples are crafted so the model behaves normally on regular input but produces a specific, attacker-chosen output when a particular trigger pattern appears. This is especially dangerous because the model passes normal evaluation and only misbehaves under the attacker's chosen condition.
- **Clean-label poisoning** — poisoned samples that have correct, plausible-looking labels, making them far harder to detect through manual review than mislabeled data.
- **Availability poisoning** — the goal isn't a targeted misbehavior but broad degradation of model performance, sometimes used to make a model unusable rather than subtly wrong.

Poisoning can occur at three points in a model's lifecycle: during **pre-training** on large, often loosely-vetted datasets; during **fine-tuning**, where smaller, more targeted datasets make poisoning proportionally easier to pull off with fewer samples; and during **embedding generation**, where manipulated inputs distort the vector space a retrieval system relies on.

### Provenance and lineage as security controls

Data provenance is the record of where a piece of data came from. Data lineage is the record of every transformation it went through to get to its current state. Together, they answer a question that's hard to answer after the fact but essential during an investigation: *if this model is misbehaving, which dataset, which version, which source is responsible?* Without provenance tracking, you can't meaningfully audit a poisoning incident — you're left guessing which of potentially millions of training samples caused the problem.

Baseline mitigations worth knowing at this stage: validating and statistically profiling new data before it enters a training set, running anomaly detection against historical data distributions, enforcing access controls on every stage of the ETL pipeline (not just the final dataset), and versioning datasets so any training run can be traced back to an exact, reproducible snapshot of its inputs.

### Key takeaways

- Data is usually the highest-leverage and most accessible attack surface in an AI system.
- Extraction, transformation, and loading each present distinct opportunities for an attacker to introduce bad data.
- Backdoor and clean-label poisoning are the hardest types to catch because the model and the data both look normal under casual inspection.
- Provenance and lineage tracking turn "something is wrong with this model" into an answerable, auditable question.