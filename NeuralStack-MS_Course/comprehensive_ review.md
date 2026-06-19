## Comprehensive Review

A mixed 10-question review pulling from every module. Use it to check your overall readiness before moving on to more advanced NeuralStack | MS content.

1. Which stage of the AI value chain is most often the actual point of compromise in real incidents?
2. Name three of the ten OWASP Top 10 for LLM Applications categories.
3. What is the difference between label flipping and backdoor poisoning?
4. Why can't a RAG system inherently distinguish a retrieved document from a trusted instruction?
5. What is the difference between direct and indirect prompt injection?
6. Why is prompt injection considered structurally unsolved as of today?
7. Name one mitigation that reduces the blast radius of a successful prompt injection, even if it doesn't prevent it.
8. What are the four functions of the NIST AI RMF?
9. What does MITRE ATLAS add that the OWASP Top 10 does not?
10. What is the single most valuable artifact for someone trying to break into AI security engineering as a career?

**Answer key:** 1) Data, deployment infrastructure, or the application/agent layer — rarely the model's weights themselves. 2) Any three of: Prompt Injection, Sensitive Information Disclosure, Supply Chain, Data and Model Poisoning, Improper Output Handling, Excessive Agency, System Prompt Leakage, Vector and Embedding Weaknesses, Misinformation, Unbounded Consumption. 3) Label flipping mislabels correct data to degrade accuracy broadly; backdoor poisoning crafts samples so the model behaves normally except under a specific attacker-chosen trigger. 4) Because instructions and retrieved content arrive through the same channel (the context window) with no built-in mechanism to flag one as more trustworthy than the other. 5) Direct injection is typed by the user themselves; indirect injection is hidden in external content the model processes on someone's behalf. 6) Because LLMs lack a reliable, built-in separation between instructions and the data they operate on. 7) Any of: privilege separation for agent tools, human-in-the-loop for high-risk actions, input/output filtering, treating external content as untrusted. 8) Govern, Map, Measure, Manage. 9) Adversary tactics and techniques modeled step-by-step on ATT&CK, complementing OWASP's risk categories with a kill-chain view of how an attacker actually proceeds. 10) A documented, original portfolio piece — a real proof-of-concept or writeup — rather than a certification alone.