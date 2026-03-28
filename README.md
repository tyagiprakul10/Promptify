# Promptify — Master Prompt Architect for Claude

> Transform any vague, rough, or incomplete idea into a precision-engineered Master Prompt
> that gets Claude's most accurate, reliable, and complete response — every time.

---

## What is Promptify?

Most people know what they want from Claude, but don't know how to ask for it in a way
that unlocks its full capability. The result is generic, incomplete, or off-target
responses that require multiple follow-ups and wasted effort.

**Promptify solves this.**

It's a Claude skill that acts as your personal prompt engineer. You describe your problem
in plain language — as rough or as vague as you like — and Promptify guides you through
a structured, conversational interview to extract everything Claude needs to give you its
absolute best output.

The result is a **Master Prompt**: a fully structured, copy-paste-ready prompt built on
Anthropic's official prompt engineering research, tailored precisely to your task.

---

## How It Works

```
User types:  /promptify [their rough idea or request]
     │
     ▼
Promptify acknowledges and begins the interview
     │
     ▼
One-question-at-a-time clarification (as many as needed)
  ├── Role & expertise needed
  ├── Background context & audience
  ├── Task steps & success criteria
  ├── Examples (if any)
  ├── Output format, length & tone
  └── Accuracy & reasoning requirements
     │
     ▼
Master Prompt generated — clean, structured, copy-paste ready
     │
     ▼
Section-by-section explanation of what was filled and why
     │
     ▼
"How to use" tip to get the most out of the prompt
```

---

## The Master Prompt Structure

Every prompt Promptify generates follows this battle-tested structure:

```
[SYSTEM / ROLE]
You are a [specific role] with [expertise] specializing in [domain].

<context>
[Background · Audience · Purpose · Constraints · Prior state]
</context>

<instructions>
1. [Step one]
2. [Step two]
3. [Step three — as many as needed]
</instructions>

<examples>
  <example>
    <input>[Sample input]</input>
    <o>[Ideal output]</o>
  </example>
</examples>

<output_format>
[Exact format · Length · Tone · Style]
</output_format>

<thinking>
Think step-by-step before answering.
</thinking>

<guardrails>
Only use the provided context. Say "I don't know" if unsure.
</guardrails>

[ACTUAL QUERY — always last]
```

> `<examples>`, `<thinking>`, and `<guardrails>` are included only when relevant to
> the task. They are omitted when not needed.

This structure is grounded in Anthropic's official prompt engineering documentation and
is optimised specifically for how Claude 4.x processes instructions.

---

## Key Features

| Feature | Detail |
|---|---|
| **Conversational interview** | One question at a time — no overwhelming forms |
| **Unlimited questions** | Asks as many as needed to get the full picture |
| **Gap detection** | Flags skipped or vague answers and rephrases to re-ask |
| **Smart defaults** | If a gap can't be filled, makes a reasonable assumption and states it |
| **Universal scope** | Works for any domain: code, writing, research, business, legal, medical, creative, and more |
| **Clean output** | Master Prompt delivered in a fenced code block — ready to copy |
| **Section explanations** | Every section explained in plain language after generation |
| **Usage tip** | Practical guidance on how to use and refine the generated prompt |

---

## Installation

### Option 1 — Install from `.skill` file

1. Download `promptify.skill` from this repository
2. Open [Claude.ai](https://claude.ai)
3. Go to **Settings → Skills**
4. Click **Install Skill** and upload `promptify.skill`
5. Done — `/promptify` is now available in your conversations

### Option 2 — Manual install

1. Clone or download this repository
2. Open [Claude.ai](https://claude.ai)
3. Go to **Settings → Skills → Create Skill**
4. Copy the contents of `SKILL.md` into the skill editor
5. Save and activate

---

## Usage

```
/promptify [your rough idea, question, or request]
```

### Examples

```
/promptify write me something about marketing
/promptify help with my python code
/promptify I need a prompt for analysing legal contracts
/promptify make me a diet plan
/promptify generate a business plan outline
/promptify explain machine learning to my team
```

You can also trigger it naturally by saying:
- *"Help me write a better prompt for..."*
- *"Turn this into a master prompt: ..."*
- *"I want the best possible prompt to get Claude to..."*
- *"Improve my prompt: ..."*

---

## Why Master Prompts Work

Claude 4.x models follow instructions **literally and precisely**. This means:

- Vague prompts → vague outputs
- Structured prompts → structured, accurate, reliable outputs

The Master Prompt structure works because it:

1. **Sets the role** — gives Claude a clear expert perspective to reason from
2. **Provides context first** — Claude processes all background before generating
3. **Uses XML tags** — Claude is fine-tuned to recognise XML structure natively
4. **Uses positive framing** — tells Claude what to do, not what to avoid
5. **Specifies output format** — removes ambiguity about what "done" looks like
6. **Asks last** — the query comes after all context, maximising relevance

---

## Who Is This For?

Promptify is designed to be universal:

- **Beginners** who don't know how to structure a prompt
- **Professionals** who want reliable, consistent outputs for repeated tasks
- **Developers** building prompts for applications or automations
- **Researchers** who need precise, sourced, well-reasoned responses
- **Anyone** who wants to stop re-prompting and get it right the first time

---

## File Structure

```
promptify/
├── SKILL.md        # The skill definition (loaded by Claude)
└── README.md       # This file
```

---

## Contributing

Pull requests and issues are welcome. If you have ideas for improving the question flow,
the Master Prompt structure, or the output format — open an issue and let's discuss.

---

## License

MIT License — free to use, modify, and distribute.

---

## Acknowledgements

Built on top of Anthropic's official prompt engineering research and documentation.
The Master Prompt structure is derived from best practices published at
[docs.anthropic.com](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview).
