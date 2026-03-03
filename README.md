# AI Persona Prompts

A collection of structured system prompts for giving AI models specific professional roles. Each persona is available in multiple formats for different models and platforms.

## Personas

| Persona | Description |
|---------|-------------|
| [DocumentAdvocate](personas/DocumentAdvocate/) | High-stakes institutional correspondence — draft, review, and adversarial critique of medical, legal, and regulatory documents |
| [PsychNavigator](personas/PsychNavigator/) | Evidence-based psychology guide — CBT, DBT, ACT, psychiatry, neuroscience, with built-in bias checking |
| [PromptEngineer](personas/PromptEngineer/) | AI prompt co-pilot — analyses, refines, and explains prompts for any model |
| [ITMaster](personas/ITMaster/) | Senior IT, networking, and cybersecurity engineer — diagnose-first, step-by-step, explains the why |
| [SecurityTutor](personas/SecurityTutor/) | CompTIA Security+ and CySA+ exam prep with practical labs and drill mode |
| [CareerAdvisor](personas/CareerAdvisor/) | Data-informed career strategy — skill gaps, training plans, location-specific salary ranges |
| [MEDical](personas/MEDical/) | Clinical knowledge instructor for medical students — high-yield answers, pathophysiology, exam prep |
| [Writer](personas/Writer/) | Ghost-writer in the user's own voice — correspondence, complaints, formal letters |

## Formats

Each persona includes versions for:

| File | Platform | Notes |
|------|----------|-------|
| `claude.xml` | [Claude](https://claude.ai) / [Claude Code](https://claude.ai/code) | XML format. Use as `--system-prompt` or paste at session start |
| `gemini.md` | [Gemini](https://gemini.google.com) / [Gemini CLI](https://github.com/google-gemini/gemini-cli) | `## SYSTEM` / `## USER` format. Paste into Gemini or use `@Personas/` in CLI |
| `gpt.md` | [ChatGPT](https://chat.openai.com) / GPT-4o | Markdown. Paste as system prompt in custom GPT or at conversation start. Compatible with DeepSeek and other OpenAI-compatible APIs |
| `m365-copilot.md` | [Microsoft 365 Copilot](https://copilot.microsoft.com) | Plain prose, positive framing. Paste into Copilot Settings > Custom instructions, or Copilot Studio agent Instructions field |
| `ollama.md` | [Ollama](https://ollama.com) / Mistral / Llama | Modelfile format with tuned temperature. Works with any model on ollama.com |

## Usage

### Claude
```bash
claude --system-prompt personas/DocumentAdvocate/claude.xml
```

### Gemini CLI
```
@Personas/DocumentAdvocate
```
Or paste the contents of `gemini.md` as your first message.

### ChatGPT / GPT-4o
Paste the contents of `gpt.md` as the system prompt in a custom GPT, or as your opening message in a new conversation.

### Microsoft 365 Copilot
1. Open [Copilot](https://copilot.microsoft.com) or the Copilot app in Teams
2. Go to Settings > Custom instructions
3. Paste the contents of `m365-copilot.md`

For Copilot Studio agents: paste into the agent's Instructions field.

### Ollama
```bash
# Copy the Modelfile contents from ollama.md, then:
ollama create persona-name -f Modelfile
ollama run persona-name
```

## Templates

The [`template/`](template/) directory contains blank scaffolds for each format. Use these to build your own personas.

| Template | Format |
|----------|--------|
| `claude-template.xml` | Claude XML |
| `gemini-template.md` | Gemini markdown |
| `gpt-template.md` | GPT markdown |
| `m365-copilot-template.md` | M365 Copilot prose |
| `ollama-template.md` | Ollama Modelfile + API variants |

## Contributing

Contributions welcome. To add a new persona:
1. Create a folder under `personas/[PersonaName]/`
2. Add at least one format version using the relevant template
3. Name files consistently: `claude.xml`, `gemini.md`, `gpt.md`, `m365-copilot.md`, `ollama.md`
4. Remove any personal file paths, credentials, or user-specific context before submitting — use `[YOUR_PATH]` placeholders

To add a new model format to an existing persona, follow the naming convention and note the format quirks in the template comments.

## License

MIT
