# Sprint Planner Prompt

## Sprint Planning Instructions

You are helping to create AI-native sprints. These are focused work sessions designed to prevent AI agents from generating overwhelming amounts of work from a design. An AI-native sprint starts with a design and focuses on a specific piece of it, sized to fit within practical constraints.

### What is an AI-Native Sprint?

An AI-native sprint is a constrained chunk of work that:
- Unlike traditional sprints: not time-based (no 2-week assumption), no team structure assumed, no story point estimation required
- Starts from a design (or part of a design)
- Focuses on a specific, manageable piece
- Is sized to prevent context window saturation
- Respects human code review capacity
- Contains **Intent and constraints only**—no code implementation details unless specifically directed by the developer
- Tracks progress with status updates within the sprint plan itself
- Provides the developer chances to test the partial outcome (sprints should be sized so developers can test and validate work incrementally)

### The Problem AI-Native Sprints Solve

AI agents can generate massive code changes from designs, leading to:
1. **Context window saturation**: Too much code to fit in a single session
2. **Overwhelming code reviews**: Users can't effectively review hundreds of files at once
3. **Loss of focus**: Too many changes make it hard to track what's actually being built

AI-native sprints break designs into manageable, reviewable chunks that recognize the capacity of both machine and human.

### Sprint Sizing Constraints

Size each sprint based on two critical constraints:

1. **Context Window Saturation**
   - Estimate how much context will be needed for the agent to work on this sprint
   - Include: design files, relevant existing code, sprint plan, agent instructions
   - Keep total context well below the model's limit to allow for conversation and iteration
   - If unsure, err on the side of smaller sprints

2. **Code Review Burden**
   - Consider how many files the user can reasonably review in one session
   - Factor in the complexity of changes (simple refactors vs. new features)
   - Consider the user's stated review capacity if provided
   - Aim for changes that can be reviewed in a single focused session

**Rule of thumb**: If you're unsure whether something fits, split it into smaller sprints. It's better to have more, smaller sprints than one overwhelming sprint.

### What Goes in a Sprint Plan

**DO Include:**
- **Intent**: What are we trying to achieve? What should the end result look like?
- **Constraints**: What are the boundaries? What must we respect? What can't we change?
- **Context**: What parts of the design are we focusing on? What existing code is relevant?
- **Acceptance Criteria**: How will we know this sprint is complete?
- **Status**: Track progress within the sprint plan (see Status Tracking below)

**DO NOT Include:**
- Code implementation details
- Specific file paths or function names (unless they're constraints)
- Step-by-step implementation instructions
- Technical architecture decisions (unless they're constraints), you can refer to design documents with more detail if relevant.

The agent executing the sprint will figure out the "how" based on the intent and constraints you provide.

### Sprint Structure

Each sprint plan should contain:

1. **Sprint Name**: `<ISO_DATE>_<animal>.md` format (see Naming Convention below)

2. **Focus**: What specific piece of the design does this sprint address?

3. **Intent**: 
   - What are we building?
   - What should it do?
   - What should the user experience be?

4. **Constraints**:
   - Technical constraints (frameworks, patterns, existing code to respect)
   - Design constraints (UI patterns, accessibility requirements)
   - Scope constraints (what's explicitly out of scope for this sprint)

5. **Context Needed**:
   - Which design files or sections are relevant?
   - What existing code should the agent be aware of?
   - Any dependencies on other sprints?

6. **Acceptance Criteria**: Clear, testable criteria for completion

7. **Status**: Current state of the sprint (see Status Tracking below). Place this at the end of the sprint plan file.

### Status Tracking

Track progress directly in the sprint plan file. Update status as work progresses:

- **planned**: Sprint is planned but not started
- **in_progress**: Work has begun on this sprint
- **review**: Code is ready for user review
- **completed**: Sprint is done and accepted
- **blocked**: Something is preventing progress (note what)

When status changes, update it in the sprint plan and note any relevant context.

### Naming Convention

Sprint files follow this format: `<ISO_DATE>_<animal>.md`

- **ISO Date**: Use YYYY-MM-DD format (e.g., `2024-01-15`)
- **Animal Name**: Progress through the alphabet sequentially, using the next letter after the highest letter already used
  - Check existing sprint files in the directory
  - Extract the first letter of each animal name from existing sprint files
  - Find the highest letter already used, then use the next letter in the alphabet
    - Example: If you see "aardvark" (a), "bear" (b), "cat" (c), the highest is "c", so next is "d" for "dog"
    - Example: If you see "aardvark" (a), "cat" (c), "elephant" (e), the highest is "e", so next is "f" for "fox"
    - Example: If you see all letters a-z used, wrap back to 'a' and use a different 'a' animal (e.g., "antelope" if "aardvark" exists)
  - Examples: `a` = aardvark, `b` = bear, `c` = cat, `d` = dog, `e` = elephant, `f` = fox, etc.
  - If wrapping back to a letter that's already used, pick a different animal name starting with that letter

**Completed Sprints**: When a sprint is completed, rename the file to add `completed_` prefix:
- Original: `2024-01-15_cat.md`
- Completed: `completed_2024-01-15_cat.md`

This helps filter out past sprints when scanning what new work is planned.

### Creating a New Sprint

When creating a new sprint:

1. **Identify the Focus**: What specific piece of the design are we tackling?

2. **Check Existing Sprints**: 
   - Look at existing sprint files in the directory (excluding `completed_` prefixed files for letter determination)
   - Determine the next available animal letter (see Naming Convention above)
   - Check for dependencies on incomplete sprints (sprints without `completed_` prefix)

3. **Size Appropriately**: 
   - Estimate context window usage
   - Estimate code review burden
   - If too large, split into multiple sprints

4. **Write Intent and Constraints**: 
   - Clearly state what we're building and why
   - List all relevant constraints
   - Avoid implementation details

5. **Set Acceptance Criteria**: 
   - Define how we'll know it's done
   - Make criteria testable and specific

6. **Name the File**: Use `<ISO_DATE>_<animal>.md` format

7. **Set Initial Status**: Start with `status: planned`

### Example Sprint Structure

```markdown
# 2024-01-15_cat.md

## Focus
User authentication flow - login form component

## Intent
Create a login form that allows users to sign in with email and password. The form should validate input, show clear error messages, and match the design system's button and input styles.

## Constraints
- Must use existing design system components (Button, Input, Form)
- Must integrate with existing auth API endpoint `/api/auth/login`
- Must follow accessibility guidelines (WCAG 2.1 AA)
- Must match design mockup `designs/auth/login.png`
- Do not implement "remember me" or password reset (out of scope)

## Context Needed
- Design file: `designs/auth/login.png`
- Existing components: `src/components/Button.tsx`, `src/components/Input.tsx`
- Auth API: `src/api/auth.ts`

## Acceptance Criteria
- [ ] Login form renders with email and password fields
- [ ] Form validates email format and required fields
- [ ] Error messages display clearly for invalid inputs
- [ ] Successful login redirects to dashboard
- [ ] Form matches design mockup visually
- [ ] Form is keyboard navigable and screen-reader accessible

## Status
planned
```

### Best Practices

- **Start Small**: It's easier to combine small sprints than to split large ones
- **Be Specific About Intent**: Vague intents lead to scope creep
- **List All Constraints**: Better to over-constrain than under-constrain
- **Update Status Regularly**: Keep the sprint plan as the source of truth
- **Respect Dependencies**: Don't start a sprint that depends on incomplete work
- **Keep It Focused**: One sprint = one coherent piece of functionality
