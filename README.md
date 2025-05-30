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

## Actvities

### Introduction

- [1. Introduction to copilot in VS Code](#1-introduction-to-copilot-in-vs-code)
- [2. Caveats](#2-caveats)

### Exploring A Workflow

- [3. Start with research](#3-start-with-research)
- [4. Save design decisions](#4-save-design-decisions)
- [5. Save conversations](#5-save-conversations)
- [6. Working through a plan in small steps](#6-working-through-a-plan-in-small-steps)
- [7. Working with persistent prompts (i.e. TODO.md)](#7-working-with-persistent-prompts-ie-todomd)
- [8. Capture repeated instructions (i.e. instructions/rules)](#8-capture-repeated-instructions-ie-instructionsrules)

## Introduction

### 1. Using copilot in VS Code

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

## Exploring a Workflow

Copilot is always eager to write code for you. Given a broad or vague enough prompt it can start to build whole apps and infrastructure for you, complete with documentation. We can absolutely take that approach if we want to, but the more we delegate to the LLM, the worse our resulting code and implementation will be. Leaving the design, code and implementation decisions up to the LLM and having it generated everything from scratch, is known as "vibe coding".

Any request to an LLM to generate code and associated materials is essentially a wish. We are not really in control of the output anymore than we would be than if we asked a genie with infinite knowledge of software development to build us an application based on a single wish. We're going to have to word that wish _very_ carefully and comprehensively in order to get what we want.

Luckily, with LLMs we get infinite* wishes (*not really).

In the rest of this workshop we'll take a look at a workflow that we've been experimenting with that gives us much more control (within the context of LLMs being non-deterministic by nature) over how Copilot will assist us to get our work done.

### 3. Start with research

Rather than diving in and getting Copilot to start writing code for us, we'll first ask it to come up with a plan of action we can follow. Try the following prompt (or construct one of your own) and have Copilot generate a plan and a recommendation for how we should proceed.

#### Example prompt

```markdown
I need an application that I can use to help me to track my progress towards my goals. I want to be able to add goals by giving them a name, a proposed start date and a frequency for how often I need to make progress (i.e. daily, weekly, on the nth of month). I also want to be able to mark goals as pending, active, completed or abandonned. I'd like to use a web interface on my laptop and an app on my iPhone to access and use the application. Ideally, most of the code would be shared between these two user interfaces so that I don't have so much maintenance to do.

You are a senior software engineer that I have engaged to help me build this application. I want you to start by coming up with a plan for how think you should tackle this build. List the choices that we have for the tech stack, the deploy stack and any other pertinent information, making clear recommendations for the direction you think we should take. I also want you to list any security considerations alongside any regulatory information I would need in order to use this application in the United Kingdom. I want to deploy this to some kind of cloud or SaaS service so that I don't have to host my own hardware.

DO NOT start writing any code yet. I just want you to generate the plan and recommendations for me. I'll work with you to refine the plan and let you know when I'm ready to move onto next steps.
```

### 4. Save design decisions

As we work with Copliot we may want to save various design decisons we make for later reference or to share out with the rest of our team and the client. Once we've gotten to a high-level plan we're happy with from our previous conversation, lets use the following prompt (or a variation thereof) to save our conversation and the outcome we reached.

#### Example prompt

```markdown
Summarize our conversation so far using the following format:
1. A short, single-paragraph description of our final decision.
2. A detailed description of the agreed plan.
3. A list of key choices that were made, highlighting whether these align with your recommendations or not. When they do not align, provide the reason that we went away from your recommendation

Provide your response as markdown.
```

Once we're happy with the output from Copilot, we can ask it to save out the file for us.

> ❗ **NOTE**: remember to switch to Agent mode so that Copilot will write the file for us!

#### Example prompt

```markdown
Save the final version of the markdown you showed me, without making any changes to it, in the file "docs/decisions/initial_agreed_plan.md".
```

### 5. Save conversations

We've been working for a while now in the one conversation (unless you already hit issues and had to skip to this section 😁), let's get a summary of what we've done so far so that we can continue in a new conversation. There are two potential audiences for the summarized and saved conversation: the LLM, so that it has context to continue the conversation or to refer to it later, our team and client, so they have context on how we got to where we got to.

So far, I've been experimenting with the following approach, but this is something that a team should agree upon in a way that works best for them.

1. If I want to save a conversation, or part of a conversation, for context around architecture, code decisions, or technical direction, I will store the resulting file in the **docs/decisions** folder.
2. If I want to use the summary as context for a continuing conversation with the LLM, I will store the file in **docs/prompts** in a file called **CONVO_CONTEXT.md**, overwriting any previous version, and use it as context for starting the next conversation.
3. If I want to save a whole conversation because it has some utility or useful context I want to share with others on the team, I'll store the resulting file in the **docs/convos** folder. This is intended to be temorary context sharing for handover or discussion and should be able to be regularly pruned to remove anything that has now served its purpose.

We covered option 1 in the previous step, so let's try option 2 first...

Use the following prompt to have the LLM summarize the conversation so far for us.

```markdown
Add a markdown document to docs/convos with a summary of this conversation. Name the file with the current timestamp, e.g. if it's 11:05:22 on the 1st January 2025 the file should be called 20250101110522.md
```

Now let's try option 3...

Use the following prompt to have the LLM summarize the conversation so far for us.

```markdown
Add a markdown document to docs/prompts/CONVO_CONTEXT.md with a summary of this conversation in a way that helps you (the AI) pick up from this point in a new conversation.
```

### 6. Working through a plan in small steps

Now we can use our CONVO_CONTEXT.md as starting context for our next conversation with Copilot.

Our plan as it stands is too high level. We need something that we can use to help us start building. Start a new conversation using the **New Conversation** <!-- TODO: add button image --> button in the top right of the Copilot panel.

Let's open the plan we stored in **docs/decisions/initial_agreed_plan.md** so we can use it as our current file context. If you don't have a version of this file yourself, you can copy the one from [example/docs/decisions/initial_agreed_plan.md](./example/docs/decisions/initial_agreed_plan.md).

Now let's add the saved summary from our previous conversation as additional context. We can add specific context we want the LLM to use in a conversation using the **Add Context** button <!-- TODO: add button image --> in the top left of the Copilot chat input.
Find **docs/prompts/CONVO_CONTEXT.md** or copy [example/docs/prompts/CONVO_CONTEXT.md](./example/docs/prompts/CONVO_CONTEXT.md) and use that.

> ❗**NOTE**: if you're swapping back to this README file to view the instructions as you're working with Copilot, this file will become the current file in our context rather than the plan. Copilot will likely find the plan on its own anyway, but to be on the safe side you could manually add the plan to the context using the same method you used to add the CONVO_CONTEXT.md file. There are no side effects that I'm aware of if you include the same file twice in the context.

Now we can use a prompt like the following to have Copilot build a step-by-step plan for the first feature from our plan we want to work on.

#### Example prompt

```markdown
Looking at the plan we agreed, I'd like to start implementing it in a step-by-step approach. Let's start with the React Native front-end. Build me a todo list in docs/prompts/TODO.md with step-by-step instructions for getting set up.

DO NOT start implementing the plan until I've had a chance to review it and make any adjustments I'd like to make.
```

It is likely that the first pass of this prompt is going to create a very detailed and long todo list that is going to suggest we build too much. It is our job as engineers at this point to figure out what to do next. Usually at this point I will take one of the following approaches:
1. Adjust my prompt so that it more specifically asks for what I'm looking for.
2. Abandon the LLM and write my own TODO.md file.

I'll typically use the latter approach if I know what I want to do and the former if I'm not sure or want a starter for ten. Just because we have access to Copilot, doesn't mean that we always have to use it. Often in software development it is not the writing of the code that takes the time, it is the knowing what to write.

