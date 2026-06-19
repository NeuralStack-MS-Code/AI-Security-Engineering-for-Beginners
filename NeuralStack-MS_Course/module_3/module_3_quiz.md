### Module 3 Quiz

1. Why is data often the highest-leverage attack surface in AI systems?
   a) Data is always encrypted, making it the hardest target
   b) Compromising what goes into a model is usually easier than compromising the model itself
   c) Data has no effect on model behavior
   d) Attackers cannot access training data under any circumstances

2. Which poisoning type causes a model to behave normally except when a specific trigger pattern appears?
   a) Label flipping
   b) Availability poisoning
   c) Backdoor / trigger poisoning
   d) Clean-label poisoning

3. Why is clean-label poisoning particularly hard to detect?
   a) It only affects encrypted data
   b) The poisoned samples have correct, plausible-looking labels
   c) It never affects model accuracy
   d) It requires no access to the dataset at all

4. What question does data provenance and lineage tracking help answer?
   a) How fast can the model run inference?
   b) Which dataset, version, or source is responsible for a model's misbehavior
   c) How many parameters does the model have?
   d) What programming language was used to build the model

5. At which stages of the model lifecycle can data poisoning occur?
   a) Only during pre-training
   b) Only during deployment
   c) Pre-training, fine-tuning, and embedding generation
   d) Only after the model is publicly released

**Answer key:** 1-b, 2-c, 3-b, 4-b, 5-c