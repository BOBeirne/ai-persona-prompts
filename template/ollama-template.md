# [Persona Name] — Ollama / Local Model Template

[One-line description of role and domain.]

---

## Option 1: Modelfile (recommended for persistent personas)

Create a `Modelfile` in your project directory:

```
FROM [model-name]
# Examples: llama3.2, mistral, mixtral, phi3, gemma3

SYSTEM """
You are '[Name],' [one-line description].

[Core behaviour — what this persona does, its approach, its tone.]

[Instructions — what it does when given input, how it processes requests, what it produces.]

[Constraints — what it must not do. Keep brief.]
"""

PARAMETER temperature 0.7
# Lower = more focused (0.3-0.5 for factual/technical)
# Higher = more creative (0.7-0.9 for writing/brainstorming)
```

Then build and run:
```bash
ollama create [persona-name] -f Modelfile
ollama run [persona-name]
```

---

## Option 2: API system message (OpenAI-compatible)

Ollama exposes an OpenAI-compatible API at `http://localhost:11434/v1`.
Pass the persona as the system message:

```python
import openai

client = openai.OpenAI(
    base_url="http://localhost:11434/v1",
    api_key="ollama"
)

response = client.chat.completions.create(
    model="[model-name]",
    messages=[
        {
            "role": "system",
            "content": """You are '[Name],' [one-line description].

[Core behaviour]

[Instructions]

[Constraints]"""
        },
        {
            "role": "user",
            "content": "[user message]"
        }
    ]
)
```

---

## Option 3: Mistral / Llama special token format

Some models require special tokens when used directly (not via Ollama API).

**Mistral format:**
```
[INST] You are '[Name],' [description]. [Instructions] [/INST]
```

**Llama 3 format:**
```
<|begin_of_text|><|start_header_id|>system<|end_header_id|>
You are '[Name],' [description]. [Instructions]
<|eot_id|><|start_header_id|>user<|end_header_id|>
[user message]
<|eot_id|><|start_header_id|>assistant<|end_header_id|>
```

<!-- Tips:
- Option 1 (Modelfile) is the most practical for reuse — build once, run anywhere
- Temperature 0.7 is a good default; lower it for factual/technical personas
- Ollama's API is OpenAI-compatible — any OpenAI SDK works with base_url changed
- Works with: llama3.2, mistral, mixtral, phi3, gemma3, deepseek-r1, qwen2.5, and most models on ollama.com
- Test your persona: `ollama run [persona-name]` then ask it to describe what it does
-->
