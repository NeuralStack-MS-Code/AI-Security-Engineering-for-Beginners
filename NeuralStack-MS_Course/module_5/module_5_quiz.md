### Module 5 Quiz

1. What distinguishes indirect prompt injection from direct prompt injection?
   a) Indirect injection requires physical access to the server
   b) The malicious instruction is hidden in content the model processes, not typed directly by the user
   c) Indirect injection only affects image models
   d) There is no meaningful difference

2. Why is prompt injection considered structurally hard to fully solve?
   a) LLMs encrypt all instructions automatically
   b) LLMs lack a reliable built-in separation between instructions and the data they operate on
   c) It only affects models smaller than 1 billion parameters
   d) It was solved in the 2023 OWASP edition

3. How does jailbreaking differ from prompt injection?
   a) They are identical concepts
   b) Jailbreaking bypasses safety training to produce disallowed content; prompt injection hijacks the task the model performs
   c) Jailbreaking only applies to image generation
   d) Prompt injection always requires jailbreaking first

4. What does "privilege separation for agent tool access" mean in practice?
   a) Giving every agent unrestricted access to all tools
   b) Scoping an agent's permissions as narrowly as possible to its current task
   c) Removing all tool access from every agent
   d) Encrypting the agent's output

5. Human-in-the-loop controls primarily address which OWASP risk category?
   a) LLM02 — Sensitive Information Disclosure
   b) LLM06 — Excessive Agency, specifically excessive autonomy
   c) LLM09 — Misinformation
   d) LLM03 — Supply Chain

**Answer key:** 1-b, 2-b, 3-b, 4-b, 5-b
