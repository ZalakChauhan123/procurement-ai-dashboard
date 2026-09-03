# AGENTS.md — Procurement AI Dashboard

This document provides project-specific guidance for AI coding agents working on **Procurement AI Dashboard**.

The project is an enterprise-style procurement management application built with Next.js, React, TypeScript, Tailwind CSS, and reusable component-based UI architecture.

The product combines UX/UI design, frontend engineering, procurement workflows, data visualization, and AI-assisted functionality.

---

## 1. Project Overview

**Project:** Procurement AI Dashboard

**Purpose:** Provide an enterprise-style interface for managing procurement activities and exploring AI-assisted procurement workflows.

### Main product areas

* Procurement dashboard
* Purchase requests
* Suppliers
* Contracts
* Approval workflows
* Procurement analytics
* AI assistant
* AI-agent workflows

The project should prioritize:

* Usability
* Clear information architecture
* Consistent design
* Reusable components
* Responsive behavior
* Maintainable code
* Reliable functionality

---

## 2. Technology Stack

* Next.js 16.3
* React 19
* TypeScript 7
* Tailwind CSS v4
* shadcn/ui
* Base UI
* SWR
* Recharts
* lucide-react
* @iconify/react
* Tiptap
* Framer Motion
* pnpm

Use the existing dependencies before introducing new ones.

---

## 3. Repository Structure

```text
app/
├── api/                       # Next.js Route Handlers
├── auth/                      # Authentication pages
├── (dashboard-layout)/        # Main dashboard application
├── components/                # Application-level components
├── context/                   # React contexts
├── hooks/                     # Reusable hooks
├── lib/                       # Utilities
└── css/                       # Page-specific CSS

components/
├── ui/                        # Reusable UI primitives
└── ...

public/                        # Static assets

CLAUDE.md                      # Claude Code project instructions
AGENTS.md                      # Shared AI coding-agent instructions
```

---

## 4. Before Making Changes

AI agents must inspect the relevant existing implementation before modifying it.

For a new feature:

1. Identify the relevant route.
2. Inspect related components.
3. Inspect existing API patterns.
4. Check for reusable UI components.
5. Check existing hooks/context.
6. Follow established conventions.
7. Only then implement the change.

Do not recreate functionality that already exists elsewhere in the project.

---

## 5. Component Architecture

Prefer reusable components.

Use:

```text
components/ui/
```

for generic reusable UI primitives.

Use feature-specific directories for components that contain business logic.

Examples:

```text
components/procurement/
components/suppliers/
components/contracts/
components/approvals/
components/ai-assistant/
```

Generic UI components should not contain procurement-specific business logic.

---

## 6. Design System

Maintain a consistent component-based design system.

Before creating a new component, check whether an existing component can be reused or extended.

Maintain consistency across:

* Typography
* Spacing
* Buttons
* Inputs
* Cards
* Tables
* Dialogs
* Forms
* Navigation
* Status indicators
* Charts
* Empty states
* Error states

Do not introduce a new visual pattern when an existing project pattern can be reused.

---

## 7. UX Principles

Design and implementation decisions should consider the complete user workflow.

For every major feature consider:

```text
User Goal
    ↓
Information Required
    ↓
Interaction
    ↓
System Feedback
    ↓
Successful Completion
```

Features should account for:

* Loading
* Empty states
* Errors
* Success feedback
* Validation
* Accessibility
* Responsive layouts

Avoid adding UI elements that do not contribute to the user's task.

---

## 8. Responsive Design

All user-facing interfaces should work across:

* Desktop
* Tablet
* Mobile

Use the existing Tailwind responsive utilities.

Avoid fixed dimensions that unnecessarily prevent responsive behavior.

---

## 9. API Architecture

The application uses real Next.js Route Handlers.

API endpoints belong under:

```text
app/api/
```

Follow this pattern:

```text
Component
    ↓
Hook / Context
    ↓
SWR
    ↓
Route Handler
    ↓
Data Layer
```

Do not introduce mocked API behavior when a real application Route Handler is appropriate.

Handle:

* Loading
* Errors
* Empty responses
* Invalid requests
* Server errors

appropriately.

---

## 10. Data Fetching

Use SWR where the existing architecture uses client-side data fetching.

Before creating a new fetcher:

1. Check `app/api/global-fetcher.ts`.
2. Check existing feature patterns.
3. Reuse shared fetcher conventions.
4. Avoid duplicating API request logic.

---

## 11. Forms

Reuse existing form components and patterns.

Forms should provide:

* Clear labels
* Validation
* Error messages
* Loading states
* Success feedback
* Accessible controls

Do not create custom form controls when an appropriate reusable component already exists.

---

## 12. Tables

Use the existing table abstractions.

Where applicable:

* Reuse DataTable components.
* Reuse sorting.
* Reuse filtering.
* Reuse pagination.
* Keep table columns typed.
* Provide empty states.
* Ensure tables remain usable on smaller screens.

---

## 13. Charts

Use Recharts for application charts.

Charts should communicate meaningful information.

Examples:

* Spending trends
* Supplier metrics
* Purchase requests
* Approval activity
* Contract expiration
* Procurement categories

Do not add charts purely for decoration.

---

## 14. AI Features

AI functionality is part of the product direction.

Possible AI features include:

* Procurement assistant
* Natural-language search
* Purchase request assistance
* Supplier analysis
* Contract information retrieval
* Workflow assistance
* AI-agent actions

AI-generated results must be validated before being used for consequential operations.

For actions that modify data or trigger business workflows:

```text
AI Suggestion
      ↓
Validation
      ↓
User Confirmation
      ↓
Action
```

Do not allow an AI model to silently perform consequential actions without appropriate safeguards.

Never expose:

* API keys
* Secrets
* Private credentials
* Server-only environment variables

to client-side code.

---

## 15. AI Coding Agent Rules

AI coding agents may assist with:

* Implementation
* Debugging
* Refactoring
* Documentation
* Testing
* Code exploration
* UI development

However, generated code must be reviewed.

Follow:

```text
Inspect
  ↓
Plan
  ↓
Implement
  ↓
Review
  ↓
Test
  ↓
Fix
```

Do not blindly trust generated code.

Do not make broad unrelated changes because an AI agent identifies them as possible improvements.

---

## 16. TypeScript

Use TypeScript throughout the project.

Avoid unnecessary:

```typescript
any
```

Prefer:

* Explicit interfaces
* Type aliases
* Typed API responses
* Typed component props
* Typed form data
* Typed domain models

Do not silence TypeScript errors merely to make the build pass.

---

## 17. Styling

Use Tailwind CSS v4.

Use:

```typescript
cn(...)
```

from the shared utility when conditional class composition is required.

Avoid manually concatenating complex class strings.

Follow existing project styling patterns.

---

## 18. Icons

Use `lucide-react` for new icons unless an existing component already follows another icon system.

Do not introduce a new icon library without a clear reason.

---

## 19. Performance

Avoid unnecessary:

* Client components
* Re-renders
* API requests
* Large dependencies
* Bundle growth
* Data fetching
* DOM complexity

Prefer Next.js server capabilities where appropriate.

Do not introduce complex optimizations without a measurable reason.

---

## 20. Accessibility

New UI should consider:

* Keyboard navigation
* Semantic HTML
* Labels
* Focus states
* Accessible names
* Appropriate ARIA attributes
* Color-independent status indicators

Do not sacrifice accessibility for visual appearance.

---

## 21. Testing & Verification

Before considering a change complete, run:

```bash
pnpm lint
```

For larger changes or before release:

```bash
pnpm build
```

Verify:

* TypeScript
* ESLint
* Runtime behavior
* Responsive behavior
* Error states
* Loading states
* Empty states
* Accessibility
* Existing functionality

If validation fails, investigate the actual cause rather than disabling the check.

---

## 22. Package Management

Use pnpm.

```bash
pnpm install
pnpm dev
pnpm lint
pnpm build
pnpm start
```

Do not use npm or yarn for project dependency management unless specifically required.

---

## 23. Change Scope

Keep changes focused.

Do not:

* Rewrite unrelated files.
* Perform unnecessary refactoring.
* Replace working libraries without a reason.
* Add dependencies unnecessarily.
* Change existing behavior outside the requested scope.
* Delete working code simply because it could be implemented differently.

If a larger architectural change is necessary, explain why before proceeding.

---

## 24. Security

Never commit:

```text
.env
.env.local
API keys
access tokens
private credentials
database credentials
```

Use environment variables for secrets.

Never expose server-side secrets through client components.

---

## 25. Definition of Done

A feature is considered complete when:

* The requested functionality works.
* The implementation follows existing architecture.
* Components are reusable where appropriate.
* UX states are handled.
* Responsive behavior works.
* TypeScript passes.
* Lint passes.
* No unnecessary dependencies were introduced.
* No secrets were exposed.
* Existing functionality remains intact.

---

## 26. General Agent Principle

Prefer:

**Understand → Reuse → Implement → Validate**

over:

**Generate → Replace → Hope**

The AI coding agent is an implementation assistant. Final responsibility for product behavior, architecture, security, UX, and code quality remains with the developer.
