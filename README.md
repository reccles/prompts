# Prompt Library

This repository contains a collection of reusable prompts for AI coding agents. These prompts guide AI assistants in performing specific tasks like code review, sprint planning, and brainstorming.

## Why Use This Library

Instead of crafting prompts from scratch, you can reference these tested prompts designed to work effectively with AI coding agents. This library helps you:

- Use proven prompt patterns for common development tasks
- Maintain consistency in how you interact with AI assistants
- Save time by not reinventing prompt structures
- Access the latest versions of prompts as they evolve

## How to Use

Reference the root `AGENTS.md` file directly in your prompt by URL. This ensures you always get the latest version of the prompt library. The library will use staged files to review or your last commit diff. 

**Example prompt:**

```
Read the prompt library index at https://github.com/username/prompts/blob/main/AGENTS.md and identify which prompts are relevant to my task. Then load and apply those specific prompts.
```

Replace the URL with your repository's actual URL. The `AGENTS.md` file serves as an index that lists all available prompts, their locations, and when to use each one. I tend to clone the directory as walking the directory is a bit faster. 

## Discovering Available Prompts

To see what prompts are available and what they can do, ask your AI assistant:

```
Read the prompt library index at https://github.com/username/prompts/blob/main/AGENTS.md and describe what prompts are available and when to use each one. Walk through the structure to help me understand what this library can do.
```

The `AGENTS.md` file contains instructions for how to describe the library and navigate its structure, so your AI assistant will be able to provide you with a helpful overview.
