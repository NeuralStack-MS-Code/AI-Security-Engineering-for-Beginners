## Module 1: Why AI Systems Need a Different Security Model

**Learning objectives**
- Explain why classic security principles still apply to AI systems but the attack surface differs
- Define the core vocabulary: model, weights, training, fine-tuning, inference, embeddings, tokens, context window
- Map the AI system value chain and identify where an attacker can intervene at each stage

### Lesson

Traditional application security asks: can someone access data, code, or infrastructure they shouldn't? AI security engineering asks the same question, but the "data, code, and infrastructure" now includes things classic security tooling was never built to inspect: a model's learned parameters, the data it was trained or fine-tuned on, the prompts and context flowing into it at runtime, and increasingly, the actions an AI agent is permitted to take on a user's behalf.

The underlying security principles don't change. Confidentiality, integrity, and availability — the CIA triad — still apply. What changes is *where* those properties get violated. A confidentiality breach in a traditional system usually means someone read a file they shouldn't have. In an AI system, it might mean a model regurgitates a training example containing someone's personal data, or an attacker reconstructs sensitive information by repeatedly querying a model and analyzing its outputs.

Before going further, a few terms you'll see throughout this course:

- **Model**: the trained artifact that takes an input and produces an output. For large language models, this is a neural network with billions of learned parameters.
- **Weights / parameters**: the numerical values inside a model that were adjusted during training. This is what gets "learned."
- **Training**: the process of adjusting weights using a large dataset so the model produces useful outputs.
- **Fine-tuning**: a second, smaller training pass on a pretrained model to specialize it for a narrower task or dataset.
- **Inference**: running a trained model on new input to get an output. This is what happens every time you send a prompt to a deployed model.
- **Embedding**: a numerical vector representation of text (or images, audio, etc.) that captures semantic meaning, used to measure similarity between pieces of content.
- **Token**: the basic unit of text an LLM processes — roughly a word or word-fragment.
- **Context window**: the total amount of text (measured in tokens) a model can consider at once, including the prompt, retrieved documents, and conversation history.

### The AI value chain

Think of an AI system as a pipeline with five stages, and remember that an attacker doesn't need to compromise all of them — one weak link is enough:

1. **Data** — collected, labeled, and stored before training ever begins.
2. **Training / fine-tuning** — the data is used to produce or adjust a model.
3. **Model artifact** — the trained weights, often distributed as a file or pulled from a model hub.
4. **Deployment / inference infrastructure** — the serving environment that runs the model and exposes it via an API.
5. **Application / agent layer** — the product logic, prompts, retrieved context, and any tools or permissions wrapped around the model.

A critical mental shift for beginners: **the model itself is rarely the actual attack surface.** Most real-world AI security incidents happen in stages 1, 4, and 5 — the data feeding the model, the infrastructure serving it, and the permissions granted to whatever wraps around it. Treat the model as one component in a larger system, not the system itself.

### Key takeaways

- AI security engineering applies familiar security principles to an unfamiliar set of assets: data, weights, prompts, and agent permissions.
- The AI value chain has five stages — data, training, model, deployment, and application/agent — and each is a potential entry point.
- Most real incidents occur around the data and the application layer, not inside the model's weights.