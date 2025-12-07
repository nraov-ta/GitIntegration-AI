# Code Standards

## Java Code Standards

### Package Naming
- Root package: `com.example.{projectname}`
- Subpackages:
  - `model`: Entity classes
  - `dto`: Data Transfer Objects
  - `service`: Business logic
  - `controller`: REST endpoints
  - `repository`: Data access
  - `validator`: Validation logic
  - `exception`: Custom exceptions
  - `config`: Configuration classes

### Naming Conventions
- Classes: PascalCase (e.g., `ContactService`)
- Methods: camelCase (e.g., `createContact()`)
- Constants: UPPER_SNAKE_CASE (e.g., `MAX_PAGE_SIZE`)
- Variables: camelCase
- Access modifiers: Always explicit
- Interfaces: PrefixWithI (e.g., `IContactService`) or suffix with Impl

### Documentation
- All public classes and methods: JavaDoc
- Include @param, @return, @throws tags
- Provide examples in complex methods

### Error Handling
- Custom exceptions extending RuntimeException
- Meaningful error messages with context
- Never catch and ignore exceptions silently
- Log at appropriate level before throwing

### Best Practices
- Dependency injection via constructor
- Use Spring annotations (@Service, @Repository, @Controller)
- Implement proper transaction management
- Use @Transactional for atomic operations
- Validation at DTO level
- Use @Valid annotation on controller parameters

## React Code Standards

### Component Naming
- Components: PascalCase (e.g., `ContactList.jsx`)
- Hooks: camelCase starting with 'use' (e.g., `useContacts.js`)
- Utilities: camelCase (e.g., `apiService.js`)

### File Organization
- Components in `src/components/`
- Pages in `src/pages/`
- Custom hooks in `src/hooks/`
- API services in `src/services/`
- Utilities in `src/utils/`
- Tests alongside files (`.test.jsx`)

### Component Structure
- Import statements at top
- Component definition
- PropTypes or TypeScript interfaces
- Export at end
- Functional components preferred

### Props Validation
- Use PropTypes for runtime validation
- Define required props explicitly
- Use defaultProps for optional props

### Documentation
- JSDoc comments for components
- Describe props, state, effects
- Include usage examples

### Best Practices
- Lift state up when needed
- Use custom hooks for logic
- Implement error boundaries
- Handle loading and error states
- Use React Router for navigation
- Implement proper form validation
- Use axios with interceptors for API calls

## Testing Standards

### Backend (JUnit 5 + Mockito)
- Test file naming: `{Class}Test.java` in `src/test/java`
- Tests per class: minimum 10-15 test methods
- Use @DisplayName for clear test descriptions
- Mock dependencies with @Mock
- Arrange-Act-Assert pattern

### Frontend (Vitest + React Testing Library)
- Test file naming: `{Component}.test.jsx` in `__tests__/`
- Query elements by role or label (not test ID)
- Test user interactions, not implementation
- Coverage target: >80%

## General Standards

### Version Control
- One logical change per commit
- Clear, descriptive commit messages
- Reference user stories/issues

### Code Review
- Address all comments before merge
- Maintain test coverage
- Follow naming conventions
- No magic numbers/strings (use constants)

### Performance
- Profile before optimizing
- Use appropriate data structures
- Implement caching for expensive operations
- Pagination for large datasets

### Security
- Validate all user inputs
- Use parameterized queries
- Implement proper authentication/authorization
- Never log sensitive data
- Use HTTPS in production
