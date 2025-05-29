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

### 3. Start with research

### 4. Ask AI to plan and wait for your approval before writing code

### 5. Save conversations

### 6. Save design decisions

### 7. Save plans

### 8. Working with persistent prompts (i.e. TODO.md)

### 9. Capture repeated instructions (i.e. instructions/rules)
