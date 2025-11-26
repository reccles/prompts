# Feature Prompt

## Feature Issue Creation Instructions

You are helping to create focused feature issues for AI agents. These issues break down designs into manageable, reviewable chunks that prevent context window saturation and overwhelming code reviews.

### What is a Feature Issue?

A feature issue is a constrained chunk of work that:
- Starts from a design (or part of a design)
- Focuses on a specific, manageable piece
- Is sized to prevent context window saturation
- Respects human code review capacity
- Contains **Intent and constraints only**—no code implementation details unless specifically directed by the developer
- Provides the developer chances to test the partial outcome (features should be sized so developers can test and validate work incrementally)

### The Problem Feature Issues Solve

AI agents can generate massive code changes from designs, leading to:
1. **Context window saturation**: Too much code to fit in a single session
2. **Overwhelming code reviews**: Users can't effectively review hundreds of files at once
3. **Loss of focus**: Too many changes make it hard to track what's actually being built

Feature issues break designs into manageable, reviewable chunks that recognize the capacity of both machine and human.

### Feature Sizing Constraints

Size each feature based on two critical constraints:

1. **Context Window Saturation**
   - Estimate how much context will be needed for the agent to work on this feature
   - Include: design files, relevant existing code, issue description, agent instructions
   - Keep total context well below the model's limit to allow for conversation and iteration
   - If unsure, err on the side of smaller features

2. **Code Review Burden**
   - Consider how many files the user can reasonably review in one session
   - Factor in the complexity of changes (simple refactors vs. new features)
   - Consider the user's stated review capacity if provided
   - Aim for changes that can be reviewed in a single focused session

**Rule of thumb**: If you're unsure whether something fits, split it into smaller features. It's better to have more, smaller issues than one overwhelming issue.

### What Goes in a Feature Issue

**DO Include:**
- **Intent**: What are we trying to achieve? What should the end result look like?
- **Constraints**: What are the boundaries? What must we respect? What can't we change?
- **Context**: What parts of the design are we focusing on? What existing code is relevant?
- **Acceptance Criteria**: How will we know this feature is complete?

**DO NOT Include:**
- Code implementation details
- Specific file paths or function names (unless they're constraints)
- Step-by-step implementation instructions
- Technical architecture decisions (unless they're constraints), you can refer to design documents with more detail if relevant.
- Progress tracking or status updates (GitHub handles this)

The agent executing the feature will figure out the "how" based on the intent and constraints you provide.

### Feature Issue Structure

Create a GitHub issue with the following structure. **Keep it concise**—avoid rambling or excessive detail:

**Title**: Clear, descriptive title for the feature

**Body** (use this structure):

```markdown
## Focus
[What specific piece of the design does this feature address?]

## Intent
[What are we building? What should it do? What should the user experience be?]

## Constraints
- [Technical constraints: frameworks, patterns, existing code to respect]
- [Design constraints: UI patterns, accessibility requirements]
- [Scope constraints: what's explicitly out of scope]

## Context Needed
- [Which design files or sections are relevant?]
- [What existing code should the agent be aware of?]
- [Any dependencies on other issues?]

## Acceptance Criteria
- [ ] [Clear, testable criterion]
- [ ] [Clear, testable criterion]
```

### Creating a New Feature Issue

When creating a new feature issue:

1. **Identify the Focus**: What specific piece of the design are we tackling?

2. **Size Appropriately**: 
   - Estimate context window usage
   - Estimate code review burden
   - If too large, split into multiple issues

3. **Write Intent and Constraints**: 
   - Clearly state what we're building and why
   - List all relevant constraints
   - Avoid implementation details
   - **Be concise**—get to the point quickly

4. **Set Acceptance Criteria**: 
   - Define how we'll know it's done
   - Make criteria testable and specific
   - Keep the list focused (3-7 items typically)

5. **Create the GitHub Issue**: Use the structure above, keeping the description brief and focused

### Example Feature Issue

**Title**: Login form component

**Body**:

```markdown
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
```

### Best Practices

- **Start Small**: It's easier to combine small features than to split large ones
- **Be Specific About Intent**: Vague intents lead to scope creep
- **List All Constraints**: Better to over-constrain than under-constrain
- **Keep It Concise**: GitHub issues should be scannable—avoid long paragraphs and rambling
- **Respect Dependencies**: Note dependencies on other issues clearly
- **Keep It Focused**: One issue = one coherent piece of functionality
- **Use Bullet Points**: They're easier to scan than paragraphs

