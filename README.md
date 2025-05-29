# AI Code Assistants

This repo was used during the AI Code Assistants workshop at the [Engineering Meetup on May 30th, 2025](TODO://link_to_recording). The purpose is to walk us through the use of Copilot in VS Code.

## FAQS

**Can I use Cursor/ Claude Code / another tool instead?**
Other coding assistants such as Cursor or Claude Code can be used in a similar way to Copilot, but there are some differences that you'd need to figure out for yourself as you followed along.

**I don't use VS Code or related IDE, can I use X instead?**
Theoretically, yes although, depending on what you're using instead, you might not have access to all of the features we'll be discussing. Feel free to follow along using your editor and code assistant of choice though.

**I don't have a Copilot license, how do I get one?**
Ask in the #eng-core channel in Slack if you need a license and don't have one yet.

## Prerequisites

- [ ] [VS Code](https://code.visualstudio.com/docs/setup/setup-overview) (or other editor of choice set up and ready to go)
- [ ] [Copilot](https://code.visualstudio.com/docs/copilot/setup) (or other code assistant of your choice set up and ready to go)

## Activites

- [1. Introduction to copilot in VS Code](#1-introduction-to-copilot-in-vs-code)
- [2. Caveats](#2-caveats)
- [3. Start with research](#3-start-with-research)
- [4. Ask AI to plan and wait for your approval before writing code](#4-ask-ai-to-plan-and-wait-for-your-approval-before-writing-code)
- [5. Save conversations](#5-save-conversations)
- [6. Save design decisions](#6-save-design-decisions)
- [7. Save plans](#7-save-plans)
- [8. Working with persistent prompts (i.e. TODO.md)](#8-working-with-persistent-prompts-ie-todomd)
- [9. Capture repeated instructions (i.e. instructions/rules)](#9-capture-repeated-instructions-ie-instructionsrules)

### 1. Introduction to copilot in VS Code

1. We can open Copilot by opening our secondary side bar on the right hand side of the VS Code editor window. Either click the <!--TODO: add image of button --> button or use the keyboard shortcut (`cmd + opt + b` on Mac).
2. The chat input window is at the bottom of the panel.
3. At the bottom right of the chat input we have the option to select the mode and the model we want to use.
  a. If we want Copilot to just answer a question and not to write or change code, we use ***Ask mode***.
  b. If we want Copilot to write or change code, we use ***Agent mode***. This provides Copilot with the ability to inspect our codebase too, and we can specifically drawn its attention to certain pieces of context too, which we'll get to in a bit.
  c. We'll use `Claude 3.7 Sonnet` for this workshop as Claude models are usually better at coding that GPT models. Feel free to experiment though. We could also use `Claude Sonnet 4`, which may well give us better results, but we should avoid the "thinking" version outside of generating plans and answers that don't generate code as it's slower.
4. At the top left of the window is the selector that lets us specifically add context to our prompts. Agent mode _should_ read through our codebase for the information it needs anyway, so we don't always have to explicitly add all pertinent files. We'll cover this in more detail as we go. The current file that is opened and focused in our editor is always auto-selected.

### 2. Caveats

Before we get stuck in, here are some things to keep in mind when working with AI code assistants:

1. AI is ***non-deterministic*** - We’re not all going to get the same results. You won't see the exact same results twice.
2. Take ***small steps*** - AI can (and will) write whole novels if you let it. Don’t.
3. If the solution is bad, ***try again*** - Roll the dice and hit that refresh button!
4. If the solution is very/still bad, ***adjust your prompt*** - Sometimes you’ll realize that the AI needs more/better prompting. Either do so inline so that it has context for what went wrong, or summarize first and then start a new convo from that summary and a new improved prompt.
5. Beware of ***context bloat*** - The longer the conversation, the slower and worse the results. LLMs can only have full attention within a given context window. Outside of that they will start to lose context and/or misrepresent prior context within that conversation. Keep your conversations short. Summarizing is an important tool in this regard.
6. Beware of ***error loops or doom cycles*** - Sometimes the code assistant will get stuck, either trying to figure out what it needs to do to complete a task, or flip flopping from one error state to another. Sometimes the best course of action is to stop the conversation, summarize it and then figure out a better approach (better prompt, smaller steps, etc).
7. Beware of the ***commands Copilot wants to run*** - I’ve never experienced Copilot running commands without asking my permission first. However, I *have* seen it ask to run commands that were either wrong or downright harmful. Always read a command before you run it. You can also change the command first and then run it if you like.

### 3. Start with research

### 4. Ask AI to plan and wait for your approval before writing code

### 5. Save conversations

### 6. Save design decisions

### 7. Save plans

### 8. Working with persistent prompts (i.e. TODO.md)

### 9. Capture repeated instructions (i.e. instructions/rules)
