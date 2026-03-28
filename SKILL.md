---
name: promptify
description: >
  Transforms any vague, rough, or incomplete prompt into a structured Master Prompt that
  gets Claude's best, most accurate, and most reliable output. Use this skill whenever a
  user types /promptify followed by any request, idea, or problem — no matter how rough,
  short, or unstructured. Also trigger when a user says things like "help me write a
  better prompt", "turn this into a good prompt", "improve my prompt", "make a master
  prompt for", "craft a prompt for", or "I want the best prompt for". This skill is
  universal — it works for any domain, field, or task: coding, writing, business,
  research, design, legal, medical, creative, technical, or anything else. Always use
  this skill when the goal is producing the highest-quality prompt possible.
---

# Promptify — Master Prompt Architect

## Purpose

Promptify takes any vague, rough, or incomplete user input and transforms it into a
structured **Master Prompt** — a precisely engineered prompt that gets Claude's best,
most accurate, and most reliable response. It works for every domain, every skill level,
and every kind of task.

The output Master Prompt follows the structure Claude responds best to, based on
Anthropic's official prompt engineering research.

---

## Master Prompt Structure (Reference)

The final output will always follow this exact structure:

```
[SYSTEM / ROLE]
You are a [role] with [expertise] specializing in [domain].

<context>
[Background info · Audience · Purpose · Constraints · Prior state]
</context>

<instructions>
1. [First step]
2. [Second step]
3. [Third step — as many as needed]
</instructions>

<examples>
  <example>
    <input>[Sample input]</input>
    <output>[Ideal output]</output>
  </example>
</examples>

<output_format>
[Exact format: length · structure · tone · style]
</output_format>

<thinking>
Think step-by-step before answering.
</thinking>

<guardrails>
Only use the provided context. Say "I don't know" if unsure.
</guardrails>

[ACTUAL QUERY — always last]
```

> Note: `<examples>`, `<thinking>`, and `<guardrails>` are included only when relevant.
> They are omitted if not needed for the task.

---

## Workflow

### Step 1 — Receive the Initial Input

When the user invokes `/promptify` followed by their request, acknowledge warmly and
immediately begin the clarification interview. Never generate the Master Prompt without
first completing the interview.

Example acknowledgement:
> "Got it! I'm going to ask you everything I need in one go — just answer each question
> as best you can and I'll build your Master Prompt from there. Skip anything that
> doesn't apply, I'll fill in smart defaults for those. Here we go:"

---

### Step 2 — The Clarification Interview

Ask **all questions in a single message** as a clean numbered list. The user answers
everything at once, then you generate the Master Prompt immediately after.

Analyse the user's initial input first — if a question is already clearly answered by
what they wrote, skip it. Only ask what is genuinely unknown. The goal is one round of
questions → one round of answers → Master Prompt. No back-and-forth.

Present the questions like this:

> "To build your Master Prompt I just need a few details — answer what you can,
> skip anything that doesn't apply:
>
> 1. Who should Claude act as? (e.g. expert, coach, analyst, writer, developer — and in what field?)
> 2. What's the background or situation Claude needs to understand?
> 3. Who is the audience for the output? (yourself, a client, a team, the public?)
> 4. What exactly do you want Claude to do? Any specific steps or phases?
> 5. Is there anything Claude should absolutely do — or avoid?
> 6. Do you have an example of what a good output looks like? (optional)
> 7. What format should the output be in? (bullet list, paragraph, table, code, etc.)
> 8. How long or detailed should the response be?
> 9. What tone? (formal, casual, technical, simple?)
> 10. How important is accuracy — is this casual use or high-stakes?
> 11. Should Claude use only what you provide, or draw on general knowledge too?
> 12. What should Claude do if it doesn't know something — flag it, skip it, or best-guess?"

Adapt this list dynamically — if the user's initial input already answers some of these,
drop those questions. If the task is simple and clearly scoped, fewer questions are fine.
The list above is the maximum — trim it down whenever context allows.

Never number the tracks or reveal internal labels (Track A, Track B, etc.) to the user.

---

### Step 3 — Handling Incomplete or Skipped Answers

When the user returns their answers, some may be vague, skipped, or marked "not sure."

**Do not ask follow-up questions.** Instead:

1. For **skipped or blank answers** — apply a reasonable smart default and state it
   clearly in the section explanation (e.g. "Assumed general professional audience —
   adjust if needed").
2. For **vague answers** — use your best interpretation based on the overall context
   of what the user is trying to do, and note the interpretation.
3. For **contradictory answers** — pick the interpretation that best serves the task
   and flag it briefly.

The only exception: if a critical answer is missing and no reasonable default exists
(e.g. the domain or task itself is completely unclear), ask one single targeted
follow-up before generating. Keep it to one question maximum.

---

### Step 4 — Generate the Master Prompt

Once sufficient context has been gathered across all relevant tracks, generate the
Master Prompt.

**Generation rules:**
- Fill every section with specific, concrete language — no placeholder brackets left
  behind in the final output
- Use XML tags exactly as specified in the structure
- Omit `<examples>` if the user had none
- Include `<thinking>` only if the task involves reasoning, analysis, logic, math,
  or multi-step decisions
- Include `<guardrails>` only if accuracy is critical or the user wants Claude to
  stay within provided context
- Place the actual query **last**, after all context and instructions
- Write instructions in positive framing ("do X") not negative ("don't do Y")
- Match the tone of the instructions to the domain (formal for legal/medical,
  conversational for casual tasks)

---

### Step 5 — Final Output Format

Deliver the result in exactly this order:

---

#### 1. The Master Prompt (clean, copy-paste ready)

Present the full Master Prompt inside a fenced code block so the user can copy it
cleanly without any extra formatting.

```
[Full Master Prompt here — no brackets, no placeholders]
```

---

#### 2. Section-by-Section Explanation

After the code block, provide a brief explanation of each section that was filled,
written in plain language. Format as a compact list:

- **Role** — [Why this role was chosen]
- **Context** — [What background was included and why]
- **Instructions** — [What the steps cover]
- **Examples** — [What the examples demonstrate, or "Omitted — none provided"]
- **Output format** — [What format/length/tone was specified]
- **Thinking** — [Included/Omitted and why]
- **Guardrails** — [Included/Omitted and why]

---

#### 3. How to Use This Prompt

End with a short, practical tip block — 3 to 5 sentences max — telling the user:
- Where to paste this prompt (new Claude conversation)
- Whether they should modify anything before using it
- One thing they can do to make it even better (e.g. "add a real example to the
  `<examples>` section if you have one")

---

## Tone & Style Guidelines

- Be warm, encouraging, and conversational when presenting the question list
- Never make the user feel judged for a vague or poorly worded initial prompt — that
  is exactly what this skill is for
- Present all questions clearly as a numbered list — easy to scan, easy to answer
- When generating the Master Prompt, shift to a precise, professional tone
- Never reveal the internal question track labels (Track A, Track B, etc.) to the user
- The entire interaction should feel like: one ask → one answer → one great prompt

---

## Quality Checklist (internal — run before delivering)

Before outputting the Master Prompt, verify:

- [ ] Role is specific and domain-grounded, not generic ("expert" alone is not enough)
- [ ] Context block answers: who, what, why, for whom, any constraints
- [ ] Instructions are numbered, positive, and sequential
- [ ] No placeholder brackets `[like this]` remain in the output
- [ ] Output format specifies length, structure, AND tone
- [ ] `<thinking>` included only if task needs reasoning
- [ ] `<guardrails>` included only if accuracy is high-stakes
- [ ] Query is last, clear, and specific
- [ ] The entire prompt could be handed to Claude cold and produce an excellent result

---

## Examples of Skill Triggering

These are the kinds of inputs that should trigger this skill:

- `/promptify write me something about marketing`
- `/promptify I need help with my code`
- `/promptify make a prompt for analysing contracts`
- `help me write a better prompt for summarising research papers`
- `turn this into a master prompt: explain machine learning to me`
- `I want the best possible prompt to get Claude to help me with my business plan`
- `improve my prompt: give me a diet plan`
