# CLAUDE.md - AI Assistant Guide for ccw-app

This document provides comprehensive guidance for AI assistants working on the `ccw-app` repository. It covers codebase structure, development workflows, and key conventions.

## Table of Contents
- [Repository Overview](#repository-overview)
- [Codebase Structure](#codebase-structure)
- [Development Workflow](#development-workflow)
- [Git Conventions](#git-conventions)
- [Code Conventions](#code-conventions)
- [Testing Guidelines](#testing-guidelines)
- [AI Assistant Guidelines](#ai-assistant-guidelines)

## Repository Overview

**Repository:** wico216/ccw-app
**Project Name:** CCW App (Collectible Card Wizard)
**Status:** Planning & Documentation Phase
**Purpose:** Web-based Progressive Web App for managing Magic: The Gathering card collections, building decks, and tracking card values

### Project Description

CCW App is a personal collection management tool inspired by Manabox. It provides:
- Card collection tracking and organization
- Deck building and analysis
- Price tracking and collection valuation
- Offline-capable Progressive Web App
- No subscription fees - complete data ownership

### Key Information
- **Tech Stack**: React + TypeScript, Supabase, Tailwind CSS
- **Data Source**: Scryfall API for MTG card data
- **Development follows feature branch workflow**
- **All AI assistant work should be done on designated `claude/*` branches**
- **See PROJECT_SPEC.md for detailed technical specifications**
- **See MANABOX_RESEARCH.md for competitive analysis**

## Codebase Structure

### Current State
The repository is in the planning phase with comprehensive documentation completed:

```
ccw-app/
├── .git/                    # Git repository metadata
├── CLAUDE.md                # This file - AI assistant guide
├── MANABOX_RESEARCH.md      # Research on Manabox app features
├── PROJECT_SPEC.md          # Detailed technical specification
├── README.md                # Project documentation (to be created)
├── frontend/                # React web app (to be created)
│   ├── src/
│   │   ├── components/      # UI components
│   │   ├── pages/           # Page components
│   │   ├── services/        # API services (Scryfall, Supabase)
│   │   ├── hooks/           # Custom React hooks
│   │   ├── types/           # TypeScript type definitions
│   │   ├── lib/             # Utility libraries
│   │   └── utils/           # Helper functions
│   ├── public/              # Static assets
│   └── package.json         # Frontend dependencies
└── docs/                    # Additional documentation
```

### Recommended Structure
As you build out the project, follow these organizational principles:

1. **Source Code Organization**
   - Keep source code in `src/` directory
   - Use clear, descriptive directory names
   - Group related functionality together
   - Separate concerns (UI, business logic, data access, etc.)

2. **Configuration Files**
   - Keep configuration files in project root
   - Use environment-specific configs when needed
   - Document all configuration options

3. **Documentation**
   - Maintain README.md for project overview
   - Use inline comments for complex logic
   - Keep API documentation up to date
   - Update CLAUDE.md when conventions change

## Development Workflow

### Branch Strategy

**Main Branch:** `main` or `master` (to be established)
**Feature Branches:** `claude/claude-md-*` pattern for AI assistant work

#### Branch Naming Convention
- **Feature branches:** `feature/descriptive-name`
- **Bug fixes:** `fix/descriptive-name`
- **AI assistant branches:** `claude/claude-md-{session-id}`
- **Hotfixes:** `hotfix/descriptive-name`

### Workflow Steps

1. **Starting New Work**
   ```bash
   # Ensure you're on the correct branch
   git checkout -b claude/claude-md-{session-id}

   # Fetch latest changes
   git fetch origin
   ```

2. **During Development**
   - Make incremental commits with clear messages
   - Test changes before committing
   - Keep commits focused and atomic
   - Update documentation as you code

3. **Completing Work**
   ```bash
   # Stage changes
   git add .

   # Commit with descriptive message
   git commit -m "Brief description of changes"

   # Push to remote (with retry logic for network issues)
   git push -u origin {branch-name}
   ```

4. **Creating Pull Requests**
   - Provide clear title and description
   - Reference any related issues
   - Include test plan
   - Request appropriate reviewers

## Git Conventions

### Commit Messages

Follow conventional commit format:

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Examples:**
```
feat(auth): add user authentication system

Implement JWT-based authentication with login/logout functionality.
Includes password hashing and token refresh mechanism.

Closes #123
```

```
fix(api): handle null response in user endpoint

Added null check to prevent crashes when API returns empty response.
```

### Git Best Practices

1. **Commits**
   - Keep commits small and focused
   - Write clear, descriptive commit messages
   - Commit working code (tests should pass)
   - Don't commit sensitive data (.env files, credentials)

2. **Branches**
   - Create new branch for each feature/fix
   - Keep branches up to date with main
   - Delete branches after merging
   - Use descriptive branch names

3. **Push Operations**
   - Always use `git push -u origin <branch-name>`
   - Branch must start with `claude/` for AI assistant work
   - Retry on network failures (up to 4 times with exponential backoff: 2s, 4s, 8s, 16s)

4. **Pull Operations**
   - Fetch specific branches: `git fetch origin <branch-name>`
   - Pull with: `git pull origin <branch-name>`
   - Same retry logic as push for network failures

## Code Conventions

### General Principles

1. **Code Quality**
   - Write clean, readable code
   - Follow DRY (Don't Repeat Yourself)
   - Use meaningful variable and function names
   - Keep functions small and focused
   - Add comments for complex logic

2. **Security**
   - Never commit credentials or secrets
   - Validate all user inputs
   - Prevent common vulnerabilities (XSS, SQL injection, CSRF, etc.)
   - Follow OWASP Top 10 guidelines
   - Use parameterized queries for database access

3. **Error Handling**
   - Handle errors gracefully
   - Provide meaningful error messages
   - Log errors appropriately
   - Don't expose sensitive info in errors

4. **Performance**
   - Optimize for readability first, then performance
   - Avoid premature optimization
   - Profile before optimizing
   - Document performance-critical code

### Language-Specific Conventions

#### JavaScript/TypeScript
```javascript
// Use const by default, let when reassignment needed
const MAX_RETRIES = 3;
let attemptCount = 0;

// Use arrow functions for callbacks
items.map(item => item.value);

// Use async/await over promises when possible
async function fetchData() {
  try {
    const response = await api.getData();
    return response;
  } catch (error) {
    console.error('Failed to fetch data:', error);
    throw error;
  }
}

// Use descriptive names
function calculateUserAge(birthDate) {
  // Implementation
}
```

#### Python
```python
# Follow PEP 8 style guide
# Use snake_case for functions and variables
def calculate_user_age(birth_date):
    """Calculate user's age from birth date."""
    # Implementation
    pass

# Use type hints
def process_data(data: list[dict]) -> dict:
    """Process list of data dictionaries."""
    return {}

# Use context managers for resources
with open('file.txt', 'r') as f:
    content = f.read()
```

## Testing Guidelines

### Test Strategy

1. **Unit Tests**
   - Test individual functions/methods
   - Mock external dependencies
   - Aim for high code coverage
   - Keep tests fast and isolated

2. **Integration Tests**
   - Test component interactions
   - Use realistic test data
   - Test error scenarios
   - Verify edge cases

3. **Test Organization**
   ```
   tests/
   ├── unit/           # Unit tests
   ├── integration/    # Integration tests
   ├── e2e/           # End-to-end tests
   └── fixtures/      # Test data and fixtures
   ```

### Writing Tests

```javascript
// Example test structure
describe('UserService', () => {
  describe('createUser', () => {
    it('should create user with valid data', async () => {
      // Arrange
      const userData = { name: 'Test', email: 'test@example.com' };

      // Act
      const result = await userService.createUser(userData);

      // Assert
      expect(result).toBeDefined();
      expect(result.name).toBe('Test');
    });

    it('should throw error with invalid email', async () => {
      // Arrange
      const userData = { name: 'Test', email: 'invalid' };

      // Act & Assert
      await expect(userService.createUser(userData))
        .rejects.toThrow('Invalid email');
    });
  });
});
```

## AI Assistant Guidelines

### General Workflow

1. **Understanding Tasks**
   - Read task description carefully
   - Ask clarifying questions if needed
   - Break down complex tasks into steps
   - Use TodoWrite tool to track progress

2. **Code Exploration**
   - Use Task tool with Explore subagent for codebase exploration
   - Use Read tool for specific files
   - Use Grep for code searches
   - Don't make assumptions - verify by reading code

3. **Making Changes**
   - Always read files before editing
   - Prefer Edit tool over Write for existing files
   - Make incremental changes
   - Test after each change
   - Update documentation

4. **Communication**
   - Be concise and clear
   - Use technical accuracy over validation
   - Reference code with `file_path:line_number` format
   - Avoid emojis unless requested
   - Output text directly, don't use echo/comments

### Tool Usage Best Practices

1. **File Operations**
   - Use Read (not cat/head/tail)
   - Use Edit (not sed/awk)
   - Use Write (not echo >/cat <<EOF)
   - Use Glob for file pattern matching
   - Use Grep for content search

2. **Task Management**
   - Use TodoWrite for multi-step tasks
   - Mark todos in_progress before starting
   - Complete todos immediately when done
   - Only one task in_progress at a time
   - Update todos in real-time

3. **Parallel Operations**
   - Run independent commands in parallel
   - Use single message with multiple tool calls
   - Don't parallelize dependent operations
   - Never use placeholders

4. **Git Operations**
   - Commit only when explicitly asked
   - Never skip hooks (--no-verify)
   - Avoid --amend unless explicitly requested
   - Check authorship before amending
   - Never force push to main/master

### Security Considerations

1. **Code Security**
   - Validate all inputs
   - Prevent injection attacks
   - Use parameterized queries
   - Sanitize user data
   - Follow OWASP guidelines

2. **Secrets Management**
   - Never commit credentials
   - Use environment variables
   - Don't log sensitive data
   - Warn before committing .env files

3. **Dependencies**
   - Keep dependencies updated
   - Review security advisories
   - Use lock files
   - Audit packages regularly

### Code Review Checklist

Before completing work, verify:

- [ ] Code follows project conventions
- [ ] Security vulnerabilities addressed
- [ ] Tests pass
- [ ] Documentation updated
- [ ] No secrets committed
- [ ] Error handling implemented
- [ ] Code is readable and maintainable
- [ ] Edge cases handled
- [ ] Performance considered
- [ ] Commits are atomic and well-described

### Common Patterns

1. **Error Handling**
   ```javascript
   try {
     const result = await operation();
     return result;
   } catch (error) {
     console.error('Operation failed:', error);
     // Handle specific error types
     if (error instanceof ValidationError) {
       throw new BadRequestError(error.message);
     }
     throw error;
   }
   ```

2. **Input Validation**
   ```javascript
   function validateEmail(email) {
     if (!email || typeof email !== 'string') {
       throw new Error('Email is required');
     }
     const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
     if (!emailRegex.test(email)) {
       throw new Error('Invalid email format');
     }
     return email.trim().toLowerCase();
   }
   ```

3. **Retry Logic**
   ```javascript
   async function withRetry(fn, maxRetries = 4) {
     for (let i = 0; i < maxRetries; i++) {
       try {
         return await fn();
       } catch (error) {
         if (i === maxRetries - 1) throw error;
         const delay = Math.pow(2, i) * 1000; // 1s, 2s, 4s, 8s
         await new Promise(resolve => setTimeout(resolve, delay));
       }
     }
   }
   ```

## Project-Specific Notes

### Current Status
- **Stage:** Planning & Documentation Complete
- **Phase:** Ready to begin implementation
- **Next Steps:**
  - Initialize Vite + React + TypeScript project
  - Set up Tailwind CSS + shadcn/ui
  - Create Supabase project and database schema
  - Implement Scryfall API integration
  - Begin Phase 1 (MVP) development

### Technology Stack

**Frontend:**
- React 18 with TypeScript
- Vite (build tool)
- Tailwind CSS + shadcn/ui (styling)
- React Router v6 (routing)
- Zustand (state management)
- React Query/TanStack Query (data fetching)
- Dexie.js (IndexedDB for offline)

**Backend:**
- Supabase (BaaS platform)
- PostgreSQL (database)
- Supabase Auth (authentication)
- Supabase Storage (file storage)

**External APIs:**
- Scryfall API (MTG card data)
- Scryfall CDN (card images)

**Deployment:**
- Vercel (frontend hosting)
- Supabase Cloud (backend)

### External Dependencies

**Data Sources:**
- **Scryfall API**: https://api.scryfall.com - Free MTG card database
  - Rate limit: Respectful use (100ms between requests)
  - No API key required
  - Comprehensive card data including prices, rulings, images

**Key npm Packages:**
- `@supabase/supabase-js` - Supabase client
- `@tanstack/react-query` - Data fetching and caching
- `react-router-dom` - Routing
- `zustand` - State management
- `dexie` - IndexedDB wrapper
- `zod` - Schema validation
- `react-hook-form` - Form handling
- `recharts` - Data visualization

### Project Conventions

**File Naming:**
- Components: PascalCase (e.g., `CardSearch.tsx`)
- Utilities: camelCase (e.g., `formatPrice.ts`)
- Types: PascalCase (e.g., `Card.types.ts`)
- Services: camelCase with .service suffix (e.g., `scryfall.service.ts`)

**Component Structure:**
```typescript
// components/CardSearch/CardSearch.tsx
import { useState } from 'react';
import { Button } from '@/components/ui/button';
import { scryfallService } from '@/services/scryfall.service';
import type { Card } from '@/types/card.types';

export function CardSearch() {
  // Component logic
}
```

**Service Pattern:**
```typescript
// services/scryfall.service.ts
class ScryfallService {
  private baseURL = 'https://api.scryfall.com';

  async searchCards(query: string) {
    // Implementation
  }
}

export const scryfallService = new ScryfallService();
```

**Type Definitions:**
```typescript
// types/card.types.ts
export interface Card {
  id: string;
  name: string;
  mana_cost?: string;
  type_line: string;
  oracle_text?: string;
  // ...
}
```

### API Integration Notes

**Scryfall API Best Practices:**
- Cache responses to minimize API calls
- Respect rate limits (100ms between requests)
- Use bulk data endpoints when possible
- Handle 404s gracefully (card not found)
- Parse card symbols for mana cost display

**Supabase Best Practices:**
- Use Row Level Security (RLS) policies
- Leverage realtime subscriptions for live updates
- Use parameterized queries to prevent injection
- Implement proper error handling
- Use TypeScript types generated from schema

### Known Issues
- None yet (project in planning phase)
- Will be documented as development progresses

### Development Phases

**Phase 1 (Weeks 1-3):** MVP - Card Search & Collection
**Phase 2 (Weeks 4-5):** Organization - Binders & Lists
**Phase 3 (Weeks 6-8):** Deck Building
**Phase 4 (Weeks 9-12):** Advanced Features

See PROJECT_SPEC.md for detailed phase breakdown.

## Resources

### Project Documentation
- **PROJECT_SPEC.md**: Comprehensive technical specification and implementation plan
- **MANABOX_RESEARCH.md**: Competitive analysis and feature research
- **CLAUDE.md**: This file - AI assistant guide

### External Documentation
- **React**: https://react.dev/
- **TypeScript**: https://www.typescriptlang.org/docs/
- **Vite**: https://vitejs.dev/
- **Tailwind CSS**: https://tailwindcss.com/docs
- **shadcn/ui**: https://ui.shadcn.com/
- **Supabase**: https://supabase.com/docs
- **React Query**: https://tanstack.com/query/latest
- **Scryfall API**: https://scryfall.com/docs/api
- **Git Documentation**: https://git-scm.com/doc
- **Conventional Commits**: https://www.conventionalcommits.org/
- **OWASP Top 10**: https://owasp.org/www-project-top-ten/

### Tools
- **Version Control**: Git/GitHub
- **Package Manager**: npm
- **Build Tool**: Vite
- **Testing**: Vitest, React Testing Library, Playwright
- **Code Quality**: ESLint, Prettier, TypeScript
- **Deployment**: Vercel
- **Backend**: Supabase

### Learning Resources
- **React Tutorial**: https://react.dev/learn
- **TypeScript Handbook**: https://www.typescriptlang.org/docs/handbook/
- **Supabase Getting Started**: https://supabase.com/docs/guides/getting-started
- **PWA Guide**: https://web.dev/progressive-web-apps/
- **MTG API Guide**: https://scryfall.com/docs/api-overview

## Maintenance

### Updating This Document

This document should be updated when:
- Project structure changes significantly
- New conventions are established
- Technology stack changes
- Important patterns emerge
- Workflows are modified

Keep this document current and accurate to ensure AI assistants have the best context for working on the project.

---

**Last Updated:** 2025-11-15
**Version:** 2.0.0
**Maintained by:** Project contributors

**Changelog:**
- v2.0.0 (2025-11-15): Updated with CCW App project details, tech stack, and conventions
- v1.0.0 (2025-11-15): Initial AI assistant guide template
