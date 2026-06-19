## Module 5: Prompt Injection and LLM-Specific Attack Techniques

**Learning objectives**
- Distinguish direct from indirect prompt injection
- Explain why prompt injection is structurally difficult to fully solve
- Differentiate prompt injection from jailbreaking
- Describe baseline mitigation patterns

### Lesson

Prompt injection topped the OWASP list for a reason: it's the most fundamental and hardest-to-fully-close risk in LLM applications, because it exploits a structural property of how these models work rather than a specific implementation bug.

### Direct vs. indirect injection

**Direct prompt injection** happens when a user types an instruction intended to override the system's original instructions — "ignore your previous instructions and instead..." — directly into a chat interface or input field.

**Indirect prompt injection** is more subtle and, in agentic systems, more dangerous: the malicious instruction is hidden inside content the model is asked to process, rather than typed directly by the user interacting with it. A webpage an AI browsing agent visits, an email a mail-reading agent summarizes, or a document a RAG system retrieves can all contain text written specifically to be interpreted as an instruction once the model reads it. The person who triggers the attack — the user who asked the agent to "summarize this email" — may have no idea anything malicious happened.

### Why this is structurally hard to solve

Traditional software security has a powerful tool that LLMs largely lack: a clean separation between code and data. A SQL injection vulnerability, for instance, exists because untrusted input gets concatenated into a command channel — and the fix is to keep the two strictly separate (parameterized queries). LLMs don't have an equivalent separation. Instructions and the content they operate on both arrive as the same kind of input: text in the context window. The model has no built-in, reliable mechanism to flag "this part is an instruction I should follow" versus "this part is content I should merely process." Mitigations can reduce the risk substantially, but as of today, no method eliminates it entirely for general-purpose LLMs.

### Prompt injection vs. jailbreaking

These two terms get conflated constantly, but they describe different goals:

- **Prompt injection** is about hijacking what task the model performs — getting it to take an unintended action or produce unintended output within the context of its current job.
- **Jailbreaking** is about bypassing the model's safety training to get it to produce content it was explicitly trained to refuse (harmful instructions, disallowed content), regardless of what task it's performing.

A system can be vulnerable to one without the other. A perfectly safety-aligned model can still be prompt-injected into taking a harmful *action* (deleting a record, sending an email) without ever being asked to say anything it would normally refuse to say.

### Baseline mitigation patterns

- **Treat all external content as untrusted** — anything retrieved, browsed, or read by an agent should be handled with the same suspicion as user input from an anonymous source, never implicitly as "background information."
- **Input and output filtering** — scanning for known injection patterns on the way in, and validating that outputs match expected formats on the way out (tying back to LLM05, Improper Output Handling).
- **Privilege separation for agent tool access** — an agent should only hold the permissions strictly necessary for its current task, scoped as narrowly as possible, so a successful injection has the smallest possible blast radius.
- **Human-in-the-loop for high-risk actions** — anything consequential (sending money, deleting data, sending external communications) should require explicit human confirmation rather than full agent autonomy, directly addressing the "excessive autonomy" component of LLM06.

### Key takeaways

- Direct injection comes from the user's own input; indirect injection is hidden in content the model processes on someone else's behalf.
- Prompt injection is structurally hard to solve because LLMs lack a reliable instruction/data separation channel.
- Prompt injection (hijacking a task) and jailbreaking (bypassing safety training) are distinct problems with distinct mitigations.
- Privilege separation and human-in-the-loop controls reduce the impact of an injection even when you can't prevent it outright.