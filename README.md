# Gemini Persona Prompts

A curated collection of high-quality, structured persona prompts for Google's Gemini models.

## Why Use These Personas?

This repository provides a library of tested and effective system prompts to instruct Gemini to act in a specific role. Using these personas helps you get more consistent, high-quality, and context-aware responses.

**Features:**
*   **Structured:** Each persona is clearly defined with goals and constraints.
*   **Categorized:** Prompts are organized into logical categories like `professional`, `technical`, and `creative`.


---

## Persona Library Index

Click on a category to see the list of available personas.

*   **[Professional](./personas/professional/README.md)**: Personas for business functions, professional development, and workplace skills.
*   **[Technical](./personas/technical/README.md)**: Personas for IT, software engineering, and other technology domains.
*   **[Creative](./personas/creative/README.md)**: Personas for content generation, marketing, and media analysis.
*   **[Domain-Specific](./personas/domain-specific/README.md)**: Personas with deep expertise in a specialized field.

---

## How to Use Persona files

### Use with Gemini-CLI

1. Navigate to the `personas` directory

2. Run the `gemini`

3. In the chat window type `@Personas\\*PersonaName* <your message here>`

**Example:**

```text
@Personas\ITMaster.md My WiFi connection is unstable and drops every 30 minutes. What steps should I take to troubleshoot this?
```

### Use with Gemini Web-UI

Using these prompts is a simple, two-step process.

1.  **Copy the Prompt**: Open the file for the persona you wish to use (e.g., `personas/technical/it-master.md`). Copy the entire content of the file.

2. **Navigate to Gemini Web-UI**: Open the [Gemini Web-UI](https://gemini.google.com/?hl=pl) and navigate to the chat window.  

3.  **Paste into Gemini**: Paste the copied text directly into your Gemini chat window as the very first message in a new conversation. Then, add your own question or request at the bottom.

**Example:**

```
## SYSTEM

Persona: You are 'IT Master,' a professional and highly experienced IT, networking, and cybersecurity engineer...
... (rest of the persona prompt) ...

## USER

My WiFi connection is unstable and drops every 30 minutes. What steps should I take to troubleshoot this?
```

---

## License

This project is licensed under the **[MIT License](LICENSE)**.
