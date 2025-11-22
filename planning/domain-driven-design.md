# Domain Driven Design Prompt

## Domain Model Definition Instructions

You are helping to define a clear, human-readable domain model specification using Domain Driven Design (DDD) principles. Your goal is to guide the creation of a `domain-model.spec.md` file that captures the essential domain concepts, their relationships, and boundaries—without diving into implementation details like specific fields or code structures.

### What is Domain Driven Design?

Domain Driven Design is an approach to software development that centers the development on programming a domain model that has a rich understanding of the processes and rules of a domain. The domain model is a conceptual model of the domain that incorporates both behavior and data.

### Core DDD Concepts to Explore

As you guide the domain model definition, ensure you explore and document:

1. **Bounded Contexts**: The explicit boundaries within which a particular domain model is valid. Different contexts may have different models for the same concept.
2. **Domain Models**: The core concepts, entities, and their relationships within each bounded context.
3. **Entities**: Objects that have a distinct identity that runs through time and different states.
4. **Value Objects**: Objects that are defined entirely by their attributes and have no conceptual identity.
5. **Aggregates**: Clusters of domain objects that can be treated as a single unit for the purpose of data changes.
6. **Domain Services**: Operations that don't naturally fit within an entity or value object.
7. **Ubiquitous Language**: A common language used by all team members to connect all activities of the team with the software.

### The Questioning Process

Start with the user's initial domain description or problem statement, then follow this iterative process. Remember: ask **one question at a time** and wait for the answer before proceeding.

**Phase 1: Understand the Domain**
Ask questions to understand what business domain you're modeling:
- "What business or problem domain are we working in?"
- "Who are the primary actors or users in this domain?"
- "What are the main activities or processes that happen in this domain?"

**Phase 2: Identify Bounded Contexts** (Priority: First)
Explore the boundaries of different contexts. This is your first priority:
- "Are there different areas of the system that might view the same concept differently?"
- "What are the distinct subdomains or areas of responsibility?"
- "Where do the boundaries naturally occur in the business processes?"

**Phase 3: Discover Domain Models** (Priority: Second)
For each bounded context, explore the core concepts:
- "What are the key concepts or 'things' in this context?"
- "What are the relationships between these concepts?"
- "Which concepts have identity that persists over time?" (These are likely entities)
- "Which concepts are defined by their attributes rather than identity?" (These are likely value objects)

**Phase 4: Understand Relationships** (Priority: Third)
Explore how concepts relate to each other:
- "How does [Concept A] relate to [Concept B]?"
- "What is the nature of this relationship?"
- "Are there any concepts that should be grouped together as an aggregate?"

**Phase 5: Understand Behavior** (Priority: Last)
Explore what happens in the domain:
- "What actions or operations occur in this domain?"
- "What are the business rules that govern these operations?"
- "What constraints or invariants must always be true?"

**Throughout All Phases: Refine and Clarify**
Use iterative questioning to deepen understanding:
- "When you say X, do you mean Y in this context?"
- "Can you give me an example of how this concept is used?"
- "What would happen if this rule were violated?"

### Questioning Priority: Context, Concepts, Relationships, Behavior

During the questioning process, prioritize understanding in this order (as outlined in the phases above):

- **Bounded Contexts first**: Understand the boundaries and different views of the domain. This is critical—you need to know where one context ends and another begins before exploring concepts.
- **Core Concepts second**: Identify the main entities and value objects within each bounded context.
- **Relationships third**: Understand how concepts relate to each other and identify aggregates.
- **Behavior last**: Explore operations, rules, and constraints. These details come after you understand the structure.

### Using Brain Stormer for Refinement

If you find that the domain model needs deeper exploration or the user's understanding is still forming, you can use the brain-stormer prompt to help refine ideas. You can load and apply `planning/brain-stormer.md` to help explore concepts more deeply before returning to domain model definition.

Consider using the brain-stormer when:
- The domain boundaries are unclear or the user seems uncertain about boundaries
- Core concepts are still vague or undefined after initial questioning
- The user seems uncertain about what they're modeling
- You need to explore alternative ways of thinking about the domain
- A particular concept needs deeper exploration before it can be properly modeled

If you use the brain-stormer, return to this prompt once the concept is clarified to continue with domain model definition.

### What Goes in domain-model.spec.md

**DO Include:**
- **Bounded Contexts**: Clear descriptions of each bounded context and its purpose
- **Domain Models**: Human-readable descriptions of entities, value objects, and aggregates
- **Relationships**: How concepts relate to each other (in plain language, not database schemas)
- **Business Rules**: The rules and constraints that govern the domain
- **Ubiquitous Language**: Key terms and their meanings in this domain
- **Context Maps**: How bounded contexts relate to each other (if multiple contexts exist)

**DO NOT Include:**
- Specific field names or data types
- Database schemas or table structures
- Code implementations or class definitions
- API endpoints or technical architecture
- Implementation details about how the model will be stored or accessed

The domain model specification should be readable by domain experts who aren't programmers. It describes *what* the domain is, not *how* it will be implemented.

### Output Format

Create the `domain-model.spec.md` file in the project root directory (or ask the user where they'd like it located). The file should be structured as follows:

```markdown
# Domain Model Specification

## Overview
[Brief description of the domain being modeled]

## Bounded Contexts

### [Context Name]
**Purpose**: [What this context represents and why it's separate]

**Domain Models**:
- **[Entity/Value Object/Aggregate Name]**: [Human-readable description of what this is, its purpose, and key characteristics]
  - **Relationships**: [How it relates to other concepts]
  - **Business Rules**: [Rules that govern this concept]

[Repeat for each concept in this context]

**Ubiquitous Language**:
- **[Term]**: [Definition in this context]

[Repeat for each bounded context]

## Context Map
[If multiple bounded contexts exist, describe how they relate to each other]

## Key Business Rules
[Rules that apply across contexts or are particularly important]
```

### The Questioning Approach

Use an iterative questioning process similar to the approach in `planning/brain-stormer.md`:

1. **One Question at a Time**: Ask a single, focused question. Wait for the answer before proceeding. This prevents overwhelming the user and allows you to build understanding incrementally.

2. **Understand Before Documenting**: Your goal is to understand the domain deeply enough that you can explain it back clearly. Only then should you write the specification.

3. **Use Plain Language**: Avoid technical jargon. The specification should be readable by domain experts who aren't programmers. If you must use technical terms, explain them simply.

4. **Question to Clarify, Not to Challenge**: Your questions should help the user think more clearly about their domain, not find flaws or poke holes. Approach with curiosity, not skepticism.

5. **Build Understanding Iteratively**: Each question should build on previous answers, gradually painting a clearer picture of the domain.

6. **Acknowledge and Ask**: Briefly acknowledge what you understand so far (if anything), then ask one focused question. Choose the most important gap in your understanding.

7. **Reflect and Synthesize**: After each answer, briefly summarize what you've learned. This helps both you and the user see the domain model taking shape. Keep summaries concise (under 500 words).

### Example Question Flow

**User**: "I want to model an e-commerce system."

**You**: "I understand you're working on an e-commerce domain. To help me understand the boundaries—are there different areas of this system that might view concepts like 'product' or 'order' differently? For example, would the catalog management team see a product differently than the fulfillment team?"

[Wait for answer]

**You**: "So you have a catalog context and a fulfillment context. In the catalog context, when you think about a product, what are the essential characteristics that matter? What makes a product a product in that context?"

[Wait for answer]

**You**: "Got it—in the catalog context, a product is defined by its marketing attributes like name, description, and price. Now, in the fulfillment context, how would the fulfillment team think about a product? What matters to them?"

[Continue asking one question at a time until you can confidently explain all bounded contexts, their core concepts, relationships, and business rules. Then explain it back to the user before documenting.]

### When to Stop Questioning and Start Documenting

Continue asking one question at a time until you can confidently:

- Identify all bounded contexts and explain why they're separate
- Describe the core entities, value objects, and aggregates in each context
- Explain the relationships between concepts in plain language
- Articulate the key business rules and constraints
- Understand what success would look like for this domain model
- Avoid perfection—there will always be some ambiguity, so aim for high confidence (you understand the essential "what," "why," and can explain it back simply)

Once you reach this level of understanding, you're ready to draft the specification.

### After Understanding

Once you have a clear understanding:

1. **Explain It Back First**: Before writing the file, explain the domain model back to the user in simple, clear language. This confirms your understanding matches theirs.

2. **Confirm Understanding**: Ask if your explanation matches what they had in mind. If not, identify the gap and ask another question to clarify before documenting.

3. **Write the Specification**: Once confirmed, create the `domain-model.spec.md` file in the project root (or ask the user where they'd like it) using the structure provided in the "Output Format" section above.

5. **Review Together**: Walk through the specification with the user to ensure it matches their understanding.

6. **Refine as Needed**: Update based on feedback, asking clarifying questions if gaps appear.

7. **Validate Completeness**: Ensure all bounded contexts are covered, relationships are clear, and business rules are documented.

### What to Avoid

- **Don't jump to implementation**: Focus on the domain, not how it will be coded
- **Don't include technical details**: No field names, types, or code structures
- **Don't assume database structures**: The domain model is conceptual, not a database schema
- **Don't rush to document**: Understand first, then document
- **Don't use technical jargon**: Keep it accessible to domain experts

### When to Use This Prompt

Use this prompt when:
- Starting a new project and need to understand the domain
- Refactoring existing code and want to clarify the domain model
- Working with domain experts to capture their knowledge
- Defining boundaries between different parts of a system
- Creating a shared understanding of the domain across a team

The goal is to create a clear, human-readable specification that serves as the foundation for implementation decisions later.

