# CLAUDE.md

This project is **Procurement AI Dashboard**, a Next.js 16.3 (App Router) + React 19 + TypeScript 7 enterprise-style procurement management dashboard.

The application is being developed as a product-oriented frontend project combining **UX/UI design, reusable component architecture, procurement workflows, data visualization, and AI-assisted functionality**.

It uses real Next.js Route Handlers under `app/api` as its backend layer rather than relying on a mocked SPA architecture.

## Project Goals

The application is designed to provide an enterprise procurement experience covering:

* Procurement overview and analytics
* Purchase request management
* Supplier management
* Contract management
* Approval workflows
* Data visualization
* AI-assisted procurement workflows
* AI assistant / agent functionality

Prioritize customer-facing functionality, usability, maintainability, and consistency over unnecessary visual complexity.

---

## Technology Stack

* **Framework:** Next.js 16.3 App Router
* **Frontend:** React 19
* **Language:** TypeScript 7
* **Styling:** Tailwind CSS v4
* **UI Components:** Component-based UI primitives using shadcn/ui and Base UI
* **Data Fetching:** SWR
* **Backend:** Next.js Route Handlers under `app/api`
* **Charts:** Recharts
* **Icons:** lucide-react and @iconify/react
* **Rich Text:** Tiptap
* **Animations:** Framer Motion
* **Forms:** React state + reusable UI form components
* **Package Manager:** pnpm

The application should remain a standard Next.js application and should not be converted into a mocked SPA architecture.

---

## Project Structure

```text
/app
├── layout.tsx
├── globals.css
├── not-found.tsx
│
├── api/
│   ├── global-fetcher.ts
│   └── <feature>/
│       └── route.ts
│
├── auth/
│   ├── auth2/
│   ├── authforms/
│   ├── error/
│   └── maintenance/
│
├── (dashboard-layout)/
│   ├── layout.tsx
│   ├── page.tsx
│   ├── apps/
│   ├── pages/
│   ├── layout/
│   ├── icons/
│   └── types/
│
├── components/
│   ├── dashboards/
│   ├── procurement/
│   ├── suppliers/
│   ├── contracts/
│   ├── approvals/
│   ├── ai-assistant/
│   ├── tables/
│   ├── shared/
│   └── ui/
│
├── context/
├── hooks/
├── lib/
└── css/
```

### Directory Responsibilities

* `app/(dashboard-layout)/` — Main authenticated application and dashboard routes.
* `app/auth/` — Authentication and standalone system pages.
* `app/api/` — Backend Route Handlers and API endpoints.
* `app/components/` — Feature-specific and application-level components.
* `components/ui/` — Reusable UI primitives.
* `context/` — Feature-specific React context providers.
* `hooks/` — Reusable React hooks.
* `lib/` — Shared utilities and helpers.
* `css/` — Page-specific styling.

---

## Routing

Use the Next.js App Router and file-based routing.

### Dashboard routes

Dashboard pages belong under:

```text
app/(dashboard-layout)/
```

The dashboard layout provides the common application shell, including navigation and header components.

### Authentication routes

Authentication-related pages belong under:

```text
app/auth/
```

These routes should remain outside the dashboard shell.

### Adding a new page

To add a dashboard page:

```text
app/(dashboard-layout)/<feature>/page.tsx
```

If the page needs a navigation entry, update the appropriate sidebar configuration.

Do not introduce a separate client-side routing system.

---

## Data & API Architecture

The application uses real Next.js Route Handlers.

Feature APIs should follow this pattern:

```text
UI Component
     ↓
Context / Hook
     ↓
SWR
     ↓
app/api/<feature>/route.ts
     ↓
Data / Service Layer
```

When implementing a new feature:

1. Create the appropriate Route Handler.
2. Create or update the required data-fetching logic.
3. Use SWR for client-side fetching where appropriate.
4. Keep API and UI responsibilities separate.
5. Handle loading, error, and empty states.
6. Avoid introducing mock APIs when a real Route Handler is appropriate.

---

## UI & Design System

The project follows a reusable component-based UI architecture.

Prefer existing components before creating new ones.

Reusable components should be placed in:

```text
components/ui/
```

or in an appropriate feature-specific component directory.

### Design principles

* User-centered design
* Clear information hierarchy
* Consistent interaction patterns
* Responsive layouts
* Accessibility
* Reusable components
* Consistent spacing and typography
* Appropriate information density for enterprise applications

### Component rules

* Prefer composition over duplication.
* Do not duplicate an existing component unnecessarily.
* Extend reusable components when the behavior should be shared.
* Keep feature-specific behavior outside generic UI primitives.
* Do not modify global UI primitives for a feature-specific requirement unless the change is intentionally global.

---

## Styling

Use Tailwind CSS v4.

Use the shared `cn()` utility from:

```text
lib/utils.ts
```

for conditional class composition.

Prefer:

```typescript
cn(...)
```

instead of manually concatenating class strings.

Follow the existing project's spacing, typography, responsive breakpoints, and component patterns before introducing new styling conventions.

---

## Icons

Prefer:

```text
lucide-react
```

for new icons.

`@iconify/react` is also present in existing components.

When modifying an existing component, follow the icon library already used by that component unless there is a strong reason to change it.

---

## Forms

Use the existing form patterns and reusable UI components.

Before creating a new form component:

1. Check existing forms.
2. Reuse existing input and selection components.
3. Maintain consistent validation and error states.
4. Keep form behavior accessible.
5. Avoid unnecessary third-party form libraries when existing patterns are sufficient.

---

## Tables

Use the existing table abstractions and TanStack Table patterns where applicable.

Before creating a new data table:

* Check existing table components.
* Reuse sorting behavior.
* Reuse filtering behavior.
* Reuse pagination patterns.
* Maintain responsive behavior.
* Provide useful empty and loading states.

---

## Charts

Use:

```text
recharts
```

for data visualization.

Charts should communicate useful procurement information rather than being added only for visual decoration.

Examples include:

* Procurement spending
* Purchase request trends
* Supplier performance
* Approval statistics
* Contract expiration
* Category-level spending

---

## AI Features

AI functionality is an important part of the product.

Potential AI capabilities include:

* Procurement assistant
* Natural-language data queries
* Purchase request assistance
* Supplier information retrieval
* Contract information retrieval
* Workflow assistance
* AI-agent tool execution

AI-generated output must be treated as untrusted until validated.

When implementing AI functionality:

1. Clearly define the AI capability.
2. Keep business rules outside the model where possible.
3. Validate structured AI output.
4. Handle failures and unavailable services.
5. Never expose API keys or secrets to the client.
6. Keep user confirmation for consequential actions.
7. Make it clear when an action is AI-assisted.

AI should support the product workflow rather than replace necessary human decisions.

---

## AI-Assisted Development

AI coding tools may be used during development, including:

* Claude Code
* OpenAI Codex
* ChatGPT
* Other coding agents

AI-generated code must be reviewed before being accepted.

When using an AI coding agent:

```text
Understand
    ↓
Plan
    ↓
Implement
    ↓
Review
    ↓
Test
    ↓
Refine
```

Do not blindly accept generated code.

The developer remains responsible for:

* Architecture
* Security
* Correctness
* Accessibility
* Performance
* Maintainability
* User experience
* Final implementation decisions

---

## UX & Usability

Product decisions should be evaluated from the user's perspective.

When implementing a new feature, consider:

* Who uses the feature?
* What task are they trying to complete?
* What information do they need?
* What can cause confusion?
* What happens when data is missing?
* What happens when an action fails?
* Can the workflow be completed efficiently?

Where appropriate, usability testing and A/B testing may be used to evaluate alternative designs.

---

## Performance

Avoid unnecessary client-side rendering.

Prefer server-side capabilities of Next.js where appropriate.

Consider:

* Component rendering cost
* Data-fetching strategy
* Bundle size
* Image optimization
* API response size
* Unnecessary re-renders
* Loading states
* Caching opportunities

Do not optimize prematurely; measure or identify a meaningful performance problem before introducing complexity.

---

## TypeScript

Use TypeScript consistently.

Avoid:

```typescript
any
```

unless there is a clear and documented reason.

Prefer explicit types for:

* API responses
* Component props
* Form data
* Domain models
* AI structured responses

Keep types close to the domain they represent when appropriate.

---

## Verification

Before considering a frontend change complete, run:

```bash
pnpm lint
```

For production/build verification:

```bash
pnpm build
```

The build must pass TypeScript checking.

When adding or modifying functionality, verify:

* TypeScript errors
* ESLint errors
* Runtime behavior
* Responsive behavior
* Loading states
* Error states
* Empty states
* Accessibility
* Existing functionality

Do not consider a change complete solely because the development server starts successfully.

---

## Package Management

Use:

```bash
pnpm
```

for package management.

Examples:

```bash
pnpm install
pnpm dev
pnpm lint
pnpm build
pnpm start
```

Do not introduce a different package manager unless there is a specific project requirement.

---

## Git & Changes

Keep changes focused.

Before modifying code:

1. Understand the existing implementation.
2. Identify reusable components.
3. Avoid unnecessary refactoring.
4. Avoid introducing dependencies when existing dependencies can solve the problem.
5. Keep unrelated changes out of the commit.

When a task can be solved with a small change, prefer the small change.

---

## Important Rules for AI Coding Agents

1. Read the relevant existing files before making changes.
2. Follow existing project conventions.
3. Reuse components whenever possible.
4. Do not invent APIs or dependencies without checking the repository.
5. Do not replace working architecture unnecessarily.
6. Keep changes scoped to the requested feature.
7. Validate changes with lint/build where appropriate.
8. Review AI-generated code before considering it complete.
9. Protect secrets and environment variables.
10. Prioritize product functionality and usability over unnecessary visual complexity.
