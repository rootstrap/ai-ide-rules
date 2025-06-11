# node rules

This file has useful rules meant for a Node project.

- These rules are IDE agnostic (Cursor, Windsurf, etc).
- You can prompt your preferred AI with the rules to adapt them.
- Edit the rules if required.

## Writing rules best practices

- Keep rules simple, concise, and specific. Rules that are too long or vague may confuse the AI.
- There’s no need to add generic rules (e.g. “write good code”), as these are already baked into the AI's training data.
- Format your rules using bullet points, numbered lists, and markdown. These are easier for the AI to follow compared to a long paragraph. For example:

```md
# Coding Guidelines

- My project's programming language is python
- Use early returns when possible
- Always add documentation when creating new functions and classes
  XML tags can be an effective way to communicate and group similar rules together. For example:
```

- XML tags can be an effective way to communicate and group similar rules together. For example:

```xml
<coding_guidelines>
- My project's programming language is python
- Use early returns when possible
- Always add documentation when creating new functions and classes
</coding_guidelines>
```

## Why we use rules?

- Encode domain-specific knowledge about your codebase
- Automate project-specific workflows or templates
- Standardize style or architecture decisions

## Rules

<tech_stack>

- Node.js v22.12.0
- NestJS framework
- PostgreSQL database
- TypeORM ORM
- Docker for containerization
- Docker Compose for orchestration
- Jest for testing
- ESLint for code quality
  </tech_stack>

<files_structure>

- controllers/
- services/
- repositories/
- entities/
- models/
  - dto/
  - constants/
- guards/
- decorators/
  </files_structure>

<coding_practices>

- Follow ESLint rules (eslint.config.mjs)
- Avoid using `any` type in DTOs and services to maintain type safety
- Use bcrypt for password hashing to ensure secure password storage
- Use structured logging instead of `console.log` statements
- Implement proper error handling in async functions using try/catch blocks
- Use `Promise.all()` for concurrent operations when possible
- Keep controllers thin by moving business logic to service layer
- Use `Map` instead of arrays for key-value pair operations
- Organize related functionality into classes following SOLID principles

  </coding_practices>

<testing_practices>

- Keep tests focused and simple (one assertion per test)
- Use single `expect` statement per test for clarity
- Name tests following Given/When/Then pattern for clarity
- Use `beforeEach`/`afterEach` hooks for consistent test setup and cleanup
- Define mocks in `beforeAll` or `beforeEach` hooks to avoid repetition
- Extract complex mocks into separate files for reusability
- Maintain minimum 90% code coverage for unit tests

</testing_practices>

<documentation_practices>

- Document API endpoints using Swagger/OpenAPI decorators
- Use `@ApiTags`, `@ApiOperation`, and `@ApiResponse` for comprehensive API documentation
- Add JSDoc comments with examples for complex functions
- Include request/response examples in Swagger documentation

</documentation_practices>
