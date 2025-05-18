# More or Less Wrong: A Benchmark for Directional Bias in LLM Comparative Reasoning

## Overview
MATHCOMP is a diagnostic benchmark designed to probe how Large Language Models (LLMs) reason under comparative linguistic framing. The dataset reveals that LLMs exhibit systematic directional biases when answering logically equivalent comparison questions that are framed with terms like "more", "equal", or "less".

Unlike prior robustness studies focusing on surface-level variations, we examine the influence of semantic framing and its placement within prompts across different LLM families (GPT, Claude, and Qwen). Our controlled experiments demonstrate that:

- Models predict "more", "less", or "equal" depending on how questions are framed, even when the correct answer is different
- Chain-of-thought and structured outputs offer partial improvements but don't eliminate the bias
- Protected attributes such as gender or race can interact with framing, shifting model predictions even when the math remains unchanged

## Dataset Structure

MATHCOMP comprises 300 base comparative math scenarios, each instantiable with multiple identity markers and evaluable with 14 framing-prompt variants, yielding thousands of distinct evaluation cases.

### Dataset Fields

Each scenario includes:

| Field | Description |
|-------|-------------|
| `scenario_id` | Unique identifier for the comparison scenario |
| `context_a` | Math word problem involving Person A |
| `context_b` | Math word problem involving Person B |
| `task` | The specific activity (e.g., caregiving, coding, reading) |
| `category` | Broader category (e.g., health, shopping, dining) |
| `quantity` | The compared values (time, money, or other measurable quantities) |
| `number_format` | Format of numbers used (standard or verbal expressions) |
| `gold_label` | Correct comparison result ("more", "equal", or "less") |
| `prompt_variants` | Array of 14 different framing prompts for each scenario |

### Prompt Variants

Each scenario includes 14 distinct prompt variants, crossing three dimensions:
- **Framing type**: neutral, direct, indirect
- **Framing term**: "more", "less", "equal"
- **Framing position**: beginning vs. end of prompt

### Demographic Extensions

The dataset supports identity-augmented evaluation by replacing placeholders with demographic markers:
- **Gender**: male, female
- **Race/ethnicity**: White, Black, Asian, Hispanic, African

## Key Findings

1. **Systematic Directional Bias**: LLMs show predictable patterns of answering "more", "less", or "equal" based on how questions are framed.

2. **Model Scale Effects**: Directional drift diminishes with model capacity, but even the largest models exhibit significant sensitivity to framing.

3. **Chain-of-Thought Helps**: Explicit reasoning reduces framing-induced bias but doesn't eliminate it completely.

4. **Demographic Interactions**: Identity references in prompts can amplify or reverse framing effects, especially in stereotype-associated domains.

5. **Mitigation Strategies**: Structured outputs and chain-of-thought prompting offer partial improvements.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
