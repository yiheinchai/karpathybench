# KarpathyBench

An open-ended benchmark for evaluating coding agents on deep technical understanding, pedagogy, and end-to-end multimodal synthesis.

## The Prompt

```text
Make a Karpathy-style video (MP4) teaching how <target> works from scratch.
```

*(Replace `<target>` with any repository, pull request, file, or paper.)*

---

## Why KarpathyBench? (Comparison to Pelican Bench)

Simon Willison's **[Pelican Bench](https://simonwillison.net/)** (*"Generate an SVG of a pelican riding a bicycle"*) became a classic LLM gut-check because it uses **one simple, open-ended prompt with zero scaffolding**:
- Models cannot rely on a memorized template.
- It forces spatial reasoning, concept composition, and valid code generation in one shot.
- Anyone can look at the resulting SVG and judge quality immediately.

**KarpathyBench applies the same philosophy to autonomous coding agents:**

| Dimension | Pelican Bench | KarpathyBench |
| :--- | :--- | :--- |
| **Prompt** | *"Generate an SVG of a pelican riding a bicycle."* | *"Make a Karpathy-style video (MP4) teaching how `<target>` works from scratch."* |
| **Output Artifact** | A single `.svg` image | A self-contained `.mp4` video lecture with audio narration |
| **Scaffolding Provided** | None | **None** — no pre-built video renderer, no cue DSL, no rubric hints |
| **What It Tests** | Single-turn spatial reasoning & SVG code generation | Codebase comprehension, first-principles pedagogy, real code execution, audio/video synthesis, and multimodal self-review |
| **Human Evaluation** | Glance at the SVG | Watch the `.mp4` — is it clear, accurate, engaging, and visually legible? |

## Rules

1. **Zero harness:** Give the agent only the prompt in [`PROMPT.md`](./PROMPT.md) pointed at `<target>`. Do not provide rendering scripts, templates, or multi-page instructions.
2. **Self-contained output:** The agent must produce a playable `.mp4` file with synchronized visuals and spoken narration.
3. **Clean target:** If `<target>` is a local git repository, its worktree must remain clean when the agent finishes.
