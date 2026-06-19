## Module 6: Governance, Risk Frameworks, and Your AI Security Career Path

**Learning objectives**
- Recognize the major AI governance frameworks practitioners are expected to know
- Understand where AI security engineering sits relative to traditional security roles
- Identify concrete next steps for skill-building and portfolio development

### Lesson

You don't need to become a compliance expert to work in AI security, but you do need enough fluency in the major governance frameworks to know when they're relevant and who to loop in when they are. Three are worth knowing by name:

**NIST AI Risk Management Framework (AI RMF)** — organized around four functions: *Govern* (establishing organizational culture and accountability for AI risk), *Map* (identifying context and risks of a specific AI system), *Measure* (assessing and tracking those risks with appropriate tools), and *Manage* (prioritizing and acting on the highest risks). It's voluntary guidance rather than law, but it's become the de facto vocabulary U.S. organizations use to structure AI risk programs.

**ISO/IEC 42001** — an international management system standard for AI, structurally similar to how ISO 27001 standardizes information security management. It gives organizations a certifiable framework for how they govern AI systems across their lifecycle.

**EU AI Act** — categorizes AI systems by risk tier (unacceptable, high, limited, and minimal risk), with obligations scaling accordingly. This is evolving regulation, not static law you can memorize once — treat any specific compliance question as one to route to a legal or compliance specialist rather than something to answer from memory.

You don't need deep expertise in any of these on day one. What you need is to recognize the names, understand roughly what each governs, and know that OWASP and MITRE ATLAS operate at a more technical, hands-on layer underneath these higher-level governance frameworks — the frameworks define *what* organizations must demonstrate, OWASP and ATLAS give you the technical vocabulary for *how* you'd actually go test and demonstrate it.

### Where AI security engineering sits

AI security is not a replacement for traditional security roles — it's an emerging specialization that sits at the intersection of application security, ML engineering, and data engineering. Most teams hiring for this today aren't looking for someone who only knows AI-specific risks; they want someone who already understands conventional security fundamentals (access control, secure SDLC, threat modeling) and can extend that thinking to AI-specific assets. This is precisely why a background in LLM or ML engineering is a genuine differentiator in this field: you already understand how these systems are built, which means you can reason about how they fail in ways a security generalist without that background often can't.

### Next steps

If you're serious about moving into this field, a sensible sequence looks like this:

1. **Build a conventional security foundation first.** A foundational certification (such as CompTIA Security+) and hands-on practice through platforms like TryHackMe, PortSwigger's Web Security Academy, and Hack The Box will teach you the access control, network, and web application fundamentals that almost everything in AI security still rests on.
2. **Layer in AI-specific frameworks.** Study the OWASP Top 10 for LLM Applications and MITRE ATLAS in depth — not just the category names, but real documented incidents and red-team writeups that illustrate each one.
3. **Get hands-on with AI-specific offensive practice.** Practice prompt injection and RAG-poisoning scenarios in deliberately vulnerable, legal sandbox environments — never against production systems you don't have explicit authorization to test.
4. **Build a portfolio.** Document a small, original proof-of-concept — a prompt injection scenario you constructed and mitigated, a writeup of a RAG poisoning experiment in a sandboxed environment, or an analysis of a public AI security incident through the OWASP/ATLAS lens. This is the single most useful thing you can show a hiring manager, more than any certification.
5. **Engage with the community.** The OWASP AI Exchange and DEF CON's AI Village are active, practitioner-driven communities where this field's vocabulary and best practices are actively being shaped — participating, even just by reading and discussing, keeps you current in a field that's changing quickly.

### Key takeaways

- NIST AI RMF, ISO/IEC 42001, and the EU AI Act are the governance frameworks worth recognizing by name and general purpose.
- AI security sits at the intersection of application security, ML engineering, and data engineering — it extends conventional security thinking rather than replacing it.
- A documented, original portfolio piece is more valuable for breaking into this field than any single certification.