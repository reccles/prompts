# Prompt Library

This repository contains a collection of reusable prompts for AI coding agents. Prompts are organized into category directories, with each prompt stored as a markdown file.

## Context Frugality

**Important**: Only load prompts that are relevant to your current task. Do not load all prompts at once. Instead, read the index below, identify which prompt(s) match your task, and navigate to the specific file to load only those prompts.

## Available Prompts

### Planning

#### Sprint Planner
**Location**: `./planning/sprint-planner.md`  
**Use when**: Converting a component of a design into a focused chunk of work. 

#### Brain Stormer
**Location**: `./planning/brain-stormer.md`  
**Use when**: Generating ideas, exploring solutions, creative problem-solving, feature ideation. Can be helpful if the user isn't entirely sure what they want yet and needs help.

#### Domain Driven Design
**Location**: `./planning/domain-driven-design.md`  
**Use when**: Defining domain models, identifying bounded contexts, understanding business domains, creating domain model specifications. Use when starting a new project or refactoring to clarify the domain model.

### Building

#### Code Reviewer
**Location**: `./building/code-reviewer.md`  
**Use when**: Reviewing code, analyzing pull requests, checking code quality, identifying bugs or security issues, suggesting improvements.

## How to Use

1. Identify your task type from the list above
2. Navigate to the relevant prompt file or AGENTS.md sub index.
3. Read that prompt file. **If the files are in git**: First check for staged files. If there are staged files, focus on the staged changes. If no staged files exist, compare the current version with the previous commit (use git diff) and focus only on the changes.
4. Apply the prompt instructions to your current task
5. **DO NOT** load other prompts unless they become relevant, unless those prompts refer to other prompts to fetch.
6. If no prompts are relevant don't load any. 

## Describing This Library

When asked to describe what this library can do or what prompts are available:

1. **Explain the Purpose**: This is a collection of reusable prompts for AI coding agents, organized by category (planning, building, etc.)

2. **Walk Through the Structure**: 
   - Start with the category level (e.g., "Planning", "Building")
   - For each category, list the available prompts
   - For each prompt, provide:
     - The prompt name
     - When to use it (the "Use when" description from the index)
     - The file location

3. **Emphasize Context Frugality**: Only load prompts that are relevant to the current task. Do not load all prompts at once.

4. **Provide Usage Guidance**: Explain that users should identify their task type, then load only the relevant prompt(s) from the appropriate category directory.

## Adding New Prompts

When adding a new prompt:
1. Identify the appropriate category directory (or create a new one if needed)
2. Create a new markdown file with a descriptive name (e.g., `my-prompt.md`)
3. Update this index with the new prompt's location and use case
4. Ensure the prompt file clearly describes when it should be used in a "When to Use This Prompt" section

