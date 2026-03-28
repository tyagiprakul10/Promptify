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
> "Got it! I'm going to ask you a series of questions — one at a time — to make sure
> your Master Prompt is as powerful and precise as possible. Take your time with each
> one. Let's start:"

---

### Step 2 — The Clarification Interview

Ask questions **one at a time**, in a natural conversational flow. There is no fixed
limit — ask as many questions as needed to fully fill every section of the Master Prompt
structure. The goal is to leave no ambiguity.

Follow the question order below, but adapt naturally based on what the user's initial
input already reveals. Skip a question only if it was already clearly answered.

#### Question Track (in order)

**Track A — Role & Expertise**
- Who should Claude act as for this task? (e.g. expert, coach, analyst, writer, developer)
- What level of expertise or specialization is needed?
- Is there a specific industry or domain this person should be grounded in?

**Track B — Context & Background**
- What is the background or situation that Claude needs to understand?
- Who is the audience for the final output? (e.g. yourself, a client, a team, the public)
- What is the ultimate purpose or goal of this task?
- Are there any constraints, limitations, or boundaries Claude must respect?
- Is there any prior work, existing content, or state Claude should know about?

**Track C — Task & Instructions**
- What exactly do you want Claude to do? (Be as specific as possible)
- Are there multiple steps or phases to this task?
- Are there things Claude should absolutely do — or absolutely avoid?
- What does "done well" look like for this task?

**Track D — Examples**
- Do you have an example of an input and what a good output looks like?
- Is there a style, format, or tone you've seen before that you'd like to match?
- (If no examples exist, skip this section in the final prompt)

**Track E — Output Format**
- What format should the output be in? (e.g. bullet list, paragraph, table, JSON, code)
- How long or detailed should the response be?
- What tone or voice should Claude use? (e.g. formal, casual, technical, simple)
- Should there be any specific sections, headers, or structure in the response?

**Track F — Reasoning & Accuracy**
- Does this task require careful step-by-step reasoning or logic?
- How important is accuracy? (e.g. casual use vs. high-stakes professional use)
- Should Claude only use the context you provide, or is general knowledge okay?
- What should Claude do if it doesn't know something — guess, flag it, or skip it?

---

### Step 3 — Handling Incomplete or Skipped Answers

If the user skips a question, gives a vague non-answer, or says "I don't know":

1. **Acknowledge** their response without judgment.
2. **Explain briefly why** that detail matters for the prompt quality.
3. **Rephrase and ask again** in a simpler or more concrete way.

Example:
> "No worries! Just to make sure the prompt works perfectly — knowing the audience helps
> Claude adjust its language and depth. For instance, is this for you personally, or
> will someone else be reading the output? Even a rough answer helps a lot."

If after a second attempt the user genuinely cannot answer, make a **reasonable smart
default**, state it clearly, and move on:
> "I'll assume this is for a general professional audience — you can always refine that
> later."

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

- Be warm, encouraging, and conversational during the interview
- Never make the user feel judged for a vague or poorly worded initial prompt — that
  is exactly what this skill is for
- Be concise in your questions — one clear question per turn, no lists of questions
  bundled together
- When generating the Master Prompt, shift to a precise, professional tone
- Never reveal the internal question track labels (Track A, Track B, etc.) to the user

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
