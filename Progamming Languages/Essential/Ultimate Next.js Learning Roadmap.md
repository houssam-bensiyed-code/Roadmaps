# ⚡ Next.js Mastery Roadmap — Phase 2: Full-Stack Architectural Thinking

> Picks up exactly where the TypeScript Foundations Roadmap (Phase 1) ended.
> Adapted from Phase 2 of the Software Engineering Mastery Roadmap for
> the full-stack Next.js industry — covering both server and client concerns.
> **Estimated Duration: 6–9 months**

---

## Prerequisites (Completed in Phase 1)
> ✅ TypeScript Mastery (Advanced types, generics, conditional types, mapped types, Zod)
> ✅ Node.js Internals (V8, event loop, libuv, memory, async patterns)
> ✅ Async Programming (Promises, async/await, streams, RxJS awareness)
> ✅ OOP + Functional Programming in TypeScript
> ✅ SOLID, Design Patterns, Clean Code
> ✅ SQL, Kysely/Drizzle/Prisma, Redis basics
> ✅ Git, pnpm, Vitest, CI/CD basics
> ✅ Docker, Docker Compose, Linux, Networking essentials
> ✅ Kubernetes concepts (awareness)

---
---

## 🟤 PHASE 0: React & Web Platform Foundations
> **Goal:** Deeply understand React's mental model, rendering, and the browser platform — so you know exactly what Next.js abstracts away.
> **Duration:** ~3–4 weeks

---

### 📦 Module 0.1: How the Modern Web Works (Full-Stack Perspective)
- Client-Server Model in Web Applications
- The Browser as a Runtime
  - HTML Parsing → DOM Construction → CSSOM → Render Tree → Layout → Paint → Composite
  - Critical Rendering Path (Why It Matters for Performance)
  - JavaScript Execution and Main Thread Blocking
- Web Rendering Strategies — The Landscape
  - **CSR (Client-Side Rendering):** Browser Downloads Empty HTML + JS → JS Renders Everything
    - Pros: Rich Interactivity, Simple Hosting
    - Cons: Slow First Paint, Poor SEO, Large JS Bundle
  - **SSR (Server-Side Rendering):** Server Generates Full HTML Per Request → Browser Hydrates
    - Pros: Fast First Paint, SEO, Dynamic Data
    - Cons: Server Load, TTFB Latency, Hydration Cost
  - **SSG (Static Site Generation):** HTML Pre-Built at Build Time → Served from CDN
    - Pros: Fastest Delivery, Cheapest Hosting, Perfect SEO
    - Cons: Stale Data, Build Time Scaling
  - **ISR (Incremental Static Regeneration):** SSG + Background Revalidation
    - Pros: SSG Speed + Fresh Data
    - Cons: Eventual Consistency, Complexity
  - **Streaming SSR:** Server Sends HTML in Chunks as Ready
    - Pros: Faster Time to First Byte, Progressive Rendering
    - Cons: Complexity, Client Must Handle Partial HTML
  - **Why Next.js Exists:** Unifies All These Strategies Per Route, Per Component
- The Journey of a Web Request
  - DNS → TCP → TLS → HTTP Request → Server Processing → HTTP Response → Browser Rendering → Hydration → Interactive
- CDNs, Edge Networks, and Where Code Runs
  - Origin Server (Traditional — Your Node.js Server)
  - CDN Edge (Static Assets, Cached Pages)
  - Edge Runtime (Run Code at CDN Edge — Cloudflare Workers, Vercel Edge)
  - Why Edge Matters for Next.js

### 📦 Module 0.2: React Fundamentals — Deep Understanding
- **React's Mental Model**
  - UI as a Function of State (`UI = f(state)`)
  - Declarative Programming (Describe What, Not How)
  - Component Tree (Hierarchical Composition)
  - Unidirectional Data Flow (Props Down, Events Up)
- **JSX and TypeScript**
  - JSX Compilation (JSX → `React.createElement()` → Virtual DOM Objects)
  - TypeScript with JSX (`.tsx`, JSX Types, `React.FC`, `React.ReactNode`, `React.ComponentProps`)
  - Type-Safe Props (Interfaces for Component Props)
  - Children Typing (`React.PropsWithChildren`, `React.ReactNode`)
  - Generic Components (`<T>` in Component Props)
- **Components**
  - Function Components (The Only Pattern That Matters Now)
  - Props (Read-Only Inputs)
  - Composition vs Inheritance (React Strongly Favors Composition)
  - Component Patterns
    - Container / Presentational (Separation of Logic and UI)
    - Compound Components (Components That Work Together — `<Select>`, `<Select.Option>`)
    - Render Props (Awareness — Mostly Replaced by Hooks)
    - Higher-Order Components (Awareness — Mostly Replaced by Hooks)
- **Hooks — The Core Runtime**
  - `useState` (Local Component State)
  - `useEffect` (Side Effects — Data Fetching, Subscriptions, DOM Manipulation)
    - Dependency Array (When to Re-Run)
    - Cleanup Function (Teardown)
    - Common Pitfalls (Infinite Loops, Stale Closures, Race Conditions)
  - `useRef` (Mutable Reference That Persists Across Renders)
  - `useMemo` (Memoize Expensive Computation)
  - `useCallback` (Memoize Function Reference)
  - `useReducer` (Complex State Logic — Reducer Pattern)
  - `useContext` (Global State Without Prop Drilling)
  - `useId` (Stable IDs for SSR Hydration)
  - `useTransition` (Non-Blocking State Updates)
  - `useOptimistic` (Optimistic UI Updates)
  - `useActionState` (Form Action State Management)
  - `use` (Unwrap Promises and Context — React 19)
- **Custom Hooks**
  - Extracting Reusable Logic into Hooks
  - Hook Naming Convention (`use` Prefix)
  - Hook Rules (Only Call at Top Level, Only in Components/Hooks)
  - Examples: `useFetch`, `useDebounce`, `useLocalStorage`, `useMediaQuery`
- **React Rendering Deep Dive**
  - Virtual DOM and Reconciliation (Diffing Algorithm)
  - Rendering vs Committing (Two Phases)
  - Re-Render Triggers (State Change, Parent Re-Render, Context Change)
  - Avoiding Unnecessary Re-Renders (Memoization, State Colocation)
  - `React.memo()` (Memoize Component by Props)
  - Key Prop and List Rendering (Why Keys Must Be Stable and Unique)

### 📦 Module 0.3: React Advanced Patterns
- **React Context API (Deep)**
  - `createContext`, `Provider`, `useContext`
  - Context Splitting (Multiple Contexts for Different Concerns)
  - Performance Issues with Context (Re-Render All Consumers on Value Change)
  - Context + Reducer Pattern (Mini State Management)
- **Error Boundaries**
  - `ErrorBoundary` Component (Class-Based — Only Way in React)
  - `react-error-boundary` Library (Functional Wrapper)
  - Error Recovery (Reset, Retry)
  - Error Boundary Placement Strategy
- **Suspense**
  - `<Suspense>` and `fallback` (Show Loading While Child Loads)
  - Suspense for Data Fetching (React 18+ — `use()` Hook)
  - Suspense for Code Splitting (`React.lazy()` + `<Suspense>`)
  - Nested Suspense Boundaries (Granular Loading States)
  - **💡 Next.js `loading.tsx` is Suspense. `error.tsx` is Error Boundary. Understanding these React primitives is critical.**
- **Concurrent Features (React 18/19)**
  - `useTransition` (Mark Updates as Non-Urgent)
  - `useDeferredValue` (Defer Rendering of Expensive Components)
  - `startTransition` (Non-Blocking State Transitions)
  - Streaming and Selective Hydration
  - **💡 These power Next.js Streaming SSR and Server Components**
- **Forms in React**
  - Controlled Components (State-Managed Inputs)
  - Uncontrolled Components (`useRef` Based)
  - Form Actions (React 19 — `<form action={serverAction}>`)
  - `useActionState` (Form Submission State)
  - `useFormStatus` (Pending State in Form)
  - **💡 Next.js Server Actions build directly on React Form Actions**

### 📦 Module 0.4: React Server Components — The Paradigm Shift
- **What Are React Server Components (RSC)**
  - Components That Run ONLY on the Server
  - Never Ship JavaScript to the Browser (Zero Client Bundle Impact)
  - Can Directly Access Databases, File Systems, APIs (No API Layer Needed)
  - Can `await` in Component Body (Async Components)
  - Cannot Use Hooks, Browser APIs, or Event Handlers
- **Server Components vs Client Components**
  - Server Components: Default in Next.js App Router
  - Client Components: Marked with `'use client'` Directive
  - Composability (Server Components Can Render Client Components as Children)
  - Client Components CANNOT Import Server Components Directly
  - Serialization Boundary (Props Passed from Server → Client Must Be Serializable)
- **When to Use Which**
  - Server Components: Data Fetching, Database Access, Heavy Computation, Secret Keys, Large Dependencies
  - Client Components: Interactivity, Event Handlers, State, Browser APIs, Custom Hooks with State/Effects
  - Decision Matrix (Default to Server, Opt-In to Client)
- **How RSC Works Under the Hood**
  - RSC Payload (Serialized Component Tree — Not HTML, Not JSON)
  - RSC Wire Format (Streaming the Component Tree)
  - Client-Side RSC Runtime (Reconciles RSC Payload with Client Components)
  - Flight Protocol (The Streaming Format Between Server and Client)
  - **💡 Understanding RSC deeply is what separates Next.js developers from Next.js beginners**

### 📦 Module 0.5: Styling & UI Foundations
- **CSS Approaches in React/Next.js**
  - CSS Modules (Scoped CSS — Next.js Built-In, Recommended for Most Cases)
  - Tailwind CSS (Utility-First — Industry Standard for Next.js)
    - JIT Compiler, Responsive Design, Dark Mode, Custom Config
    - `tailwind.config.ts`, `@apply`, Custom Utilities
    - `tailwind-merge`, `clsx` / `cn()` for Conditional Classes
  - CSS-in-JS (Styled-Components, Emotion — Awareness, RSC Compatibility Issues)
  - Global CSS (For CSS Resets, Fonts, Variables)
  - CSS Variables for Theming
- **Component Libraries (Awareness — Choose One)**
  - Shadcn/ui (Copy-Paste Components Built on Radix — Most Popular for Next.js)
  - Radix UI (Unstyled, Accessible Primitives)
  - Headless UI (Tailwind Labs)
  - MUI, Ant Design, Mantine (Full UI Libraries — Heavier)
- **Responsive Design and Accessibility**
  - Mobile-First Design
  - Semantic HTML
  - ARIA Attributes
  - Keyboard Navigation
  - Screen Reader Considerations
  - `eslint-plugin-jsx-a11y`

### 📦 Module 0.6: Understanding What Next.js Replaces
> **Connecting raw React to Next.js.**

- **Manual Routing → Next.js File-System Router**
  - `react-router-dom` → `app/` Directory Convention
  - Layout Wrapping → `layout.tsx` (Nested Layouts)
  - 404 Pages → `not-found.tsx`
  - Loading States → `loading.tsx` (Suspense Boundary)
  - Error States → `error.tsx` (Error Boundary)
- **Manual SSR Setup → Next.js Built-In**
  - Custom Express + `ReactDOMServer.renderToString()` → Next.js Handles Everything
  - Hydration Management → Next.js Handles Automatically
  - Streaming SSR → Next.js Handles with Suspense
- **Manual Data Fetching → Server Components + Server Actions**
  - `useEffect` + `fetch` on Client → `async` Server Component with Direct DB Access
  - API Routes for Mutations → Server Actions (`'use server'`)
- **Manual Build/Bundle → Next.js Turbopack/Webpack**
  - Webpack/Vite Config → `next.config.ts` (Minimal Config)
  - Code Splitting → Automatic Per-Route and Per-Component
  - Image Optimization → `next/image`
  - Font Optimization → `next/font`
- **Mapping Table**

  | Manual React / Express | Next.js Equivalent |
  |---|---|
  | `react-router-dom` | File-system routing (`app/` directory) |
  | `<Route path="/users/:id">` | `app/users/[id]/page.tsx` |
  | `<Layout>` wrapper component | `layout.tsx` (automatic nesting) |
  | `<Suspense fallback={<Spinner/>}>` | `loading.tsx` |
  | `<ErrorBoundary>` | `error.tsx` |
  | 404 component + catch-all | `not-found.tsx` |
  | `useEffect` + `fetch` for data | `async` Server Component with `await` |
  | Express API route + controller | Route Handler (`app/api/route.ts`) |
  | Express POST handler | Server Action (`'use server'`) |
  | Manual `ReactDOMServer.renderToString()` | Automatic SSR |
  | Custom Webpack config | `next.config.ts` |
  | Manual code splitting | Automatic per-route splitting |
  | `<img>` tag | `<Image>` (automatic optimization) |
  | Google Fonts `<link>` | `next/font` (zero layout shift) |
  | Express middleware | `middleware.ts` (Edge Middleware) |
  | `helmet` for headers | `next.config.ts` `headers()` |
  | Manual environment variables | `.env.local` + `NEXT_PUBLIC_` prefix |

> ### 🛠 Phase 0 Milestone Project: **React Application Without Next.js**
> Build a multi-page React application without Next.js to feel the pain:
> - Vite + React + TypeScript + React Router setup
> - Multiple pages with nested layouts (manually managed)
> - Client-side data fetching with `useEffect` + `fetch` (loading states, error states, race conditions)
> - Express.js backend API (separate server)
> - Manual SSR with `ReactDOMServer` and Express (serve pre-rendered HTML + hydrate)
> - Authentication flow (JWT stored in cookies — manual refresh)
> - Manual code splitting with `React.lazy()` + `Suspense`
> - Feel every pain point: manual routing, manual SSR, manual API layer, manual optimization
> - Then throw it all away and start Phase 1 with Next.js
>
> **Why:** You'll deeply understand file-system routing, Server Components, `loading.tsx`, `error.tsx`, Server Actions, and automatic optimization — because you built crude versions yourself.

---

### ✅ After Phase 0 — You Understand:
- Web rendering strategies (CSR, SSR, SSG, ISR, Streaming) and trade-offs
- React's mental model, hooks, rendering, and concurrent features deeply
- React Server Components — the paradigm shift and serialization boundary
- The mapping between manual React patterns and Next.js conventions
- Why Next.js exists and what problems it solves at each layer
- **You're not learning Next.js — you're learning what Next.js automated**

---
---

## 🟢 PHASE 1: Next.js Core
> **Goal:** Master Next.js App Router, Server Components, data fetching, caching, and the full request lifecycle.
> **Duration:** ~4–5 weeks

---

### 📦 Module 1.1: Next.js Fundamentals
- What Next.js Solves (Routing, Rendering, Data Fetching, Optimization — One Framework)
- Next.js Architecture Stack (React + Node.js + Rust Compiler + Edge Runtime)
- Installation and Project Setup (`create-next-app`)
- Project Structure
  - `app/` Directory (App Router — The Standard)
  - `public/` (Static Assets)
  - `next.config.ts` (Configuration)
  - `middleware.ts` (Edge Middleware)
  - `instrumentation.ts` (Observability Hooks)
- Runtimes
  - Node.js Runtime (Default — Full Node.js API Access)
  - Edge Runtime (Lightweight — V8 Isolates, Limited API, Faster Cold Start)
  - Choosing Runtime Per Route (`export const runtime = 'edge'`)
- `next.config.ts` Essentials
  - `images` (Allowed Domains, Formats)
  - `redirects` and `rewrites`
  - `headers` (Security Headers)
  - `env` (Build-Time Environment Variables)
  - `experimental` Features
  - Turbopack Configuration

### 📦 Module 1.2: App Router — File-System Routing
- **Route Conventions**
  - `page.tsx` (Page Component — Makes Folder a Route)
  - `layout.tsx` (Shared Layout — Wraps Page and Children, Persists Across Navigation)
  - `loading.tsx` (Suspense Boundary — Shows While Page/Layout Loads)
  - `error.tsx` (Error Boundary — Catches Errors in Segment)
  - `not-found.tsx` (404 Page for Segment)
  - `template.tsx` (Like Layout But Re-Mounts on Navigation — Rare)
  - `default.tsx` (Fallback for Parallel Routes)
  - `global-error.tsx` (Root Error Boundary)
  - `route.ts` (API Route Handler — No UI)
- **Dynamic Routes**
  - `[param]` (Single Dynamic Segment — `/users/[id]`)
  - `[...slug]` (Catch-All — `/docs/[...slug]`)
  - `[[...slug]]` (Optional Catch-All — Including Root)
  - `params` Prop (Accessing Dynamic Segments)
  - `generateStaticParams()` (Pre-Generate Dynamic Pages at Build)
- **Route Groups**
  - `(groupName)` (Organize Without Affecting URL)
  - Use Cases: Separate Layouts (`(marketing)`, `(dashboard)`), Organize by Feature
- **Parallel Routes**
  - `@slotName` (Render Multiple Pages Simultaneously)
  - Use Cases: Dashboards, Split Views, Modals
  - `default.tsx` (Fallback When Slot Has No Match)
- **Intercepting Routes**
  - `(.)`, `(..)`, `(..)(..)`, `(...)` (Intercept Route at Different Levels)
  - Use Cases: Modals That Overlay Current Page (Instagram-Style Photo Modal)
  - Soft Navigation (Modal) vs Hard Navigation (Full Page)
- **Nested Layouts**
  - Root Layout (`app/layout.tsx` — Required, `<html>`, `<body>`)
  - Nested Layouts (Each Folder Can Have Its Own Layout)
  - Layout Persistence (Layouts Don't Re-Render on Child Navigation)
  - Shared State in Layouts
- **Navigation**
  - `<Link>` Component (Client-Side Navigation, Prefetching)
  - `useRouter()` (Programmatic Navigation)
  - `usePathname()` (Current Path)
  - `useSearchParams()` (Query Parameters)
  - `useParams()` (Dynamic Route Parameters)
  - `redirect()` (Server-Side Redirect — In Server Components/Actions)
  - `permanentRedirect()` (301 Redirect)
  - `notFound()` (Trigger 404)
  - Active Link Patterns (Comparing `pathname`)

### 📦 Module 1.3: Server Components & Client Components in Practice
- **Server Components (Default)**
  - `async` Component Functions (Await Data Directly)
  - Access Database, File System, Secrets (Never Exposed to Client)
  - Import Server-Only Packages (Large Libraries Stay on Server)
  - `server-only` Package (Enforce Server-Only Imports)
  - Zero Client JavaScript for Pure Server Components
- **Client Components**
  - `'use client'` Directive (At Top of File)
  - All Hooks Work Here (`useState`, `useEffect`, etc.)
  - Event Handlers (`onClick`, `onChange`, etc.)
  - Browser APIs (`window`, `document`, `localStorage`)
  - Still Pre-Rendered on Server (SSR), Then Hydrated on Client
- **Composition Patterns**
  - Server Component Renders Client Component (Pass Props)
  - Server Component Passes Children to Client Component (Composition Pattern)
  - Client Component Cannot Import Server Component (Serialization Boundary)
  - Interleaving (Server → Client → Server Children)
  - Moving Client Boundary Down (Keep as Much as Possible on Server)
- **`'use server'` Directive**
  - Marks Functions as Server Actions
  - Can Be Called from Client Components
  - Secure Server-Side Execution
- **Third-Party Libraries**
  - Libraries With `useState`/`useEffect` Must Be in Client Components
  - Wrapping Client-Only Libraries (Create Client Component Wrapper)
  - `next/dynamic` (Dynamic Import with `ssr: false` for Client-Only)

### 📦 Module 1.4: Data Fetching
- **Server Component Data Fetching**
  - `async` Components with `await` (Direct Database/API Calls)
  - `fetch()` in Server Components (Extended by Next.js — Caching, Revalidation)
  - Multiple Parallel Fetches (`Promise.all()` — Avoid Waterfalls)
  - Sequential Fetches (When Order Matters)
  - Data Fetching in Layouts vs Pages (Layout Data Persists)
- **Caching — The Core Mental Model**
  - **Request Memoization** (Same `fetch` in Same Render → Deduplicated)
    - React `cache()` Function (Memoize Non-Fetch Async Functions)
  - **Data Cache** (Server-Side Cache — Persists Across Requests)
    - `fetch` Cache Options
      - `force-cache` (Default in Next.js 14 — Cache Indefinitely)
      - `no-store` (Never Cache — Always Fresh)
      - `next.revalidate` (Time-Based Revalidation — ISR)
  - **Full Route Cache** (Pre-Rendered HTML + RSC Payload Cached)
    - Static Rendering (Cached at Build Time)
    - Dynamic Rendering (Rendered Per Request)
  - **Router Cache** (Client-Side Cache of Visited Routes)
    - Prefetching (Automatic for `<Link>` in Viewport)
    - Cache Duration (30s for Dynamic, 5min for Static)
    - `router.refresh()` (Invalidate Router Cache)
- **Revalidation Strategies**
  - Time-Based (`revalidate: 60` — ISR)
  - On-Demand (`revalidatePath()`, `revalidateTag()`)
  - Tag-Based Caching (`fetch` with `tags: ['products']` → `revalidateTag('products')`)
- **Dynamic Functions (Opt Out of Static Rendering)**
  - `cookies()`, `headers()`, `searchParams` (Make Route Dynamic)
  - `connection()` (Signal Dynamic Rendering — Next.js 15)
  - `unstable_noStore()` / `noStore()` (Opt Out of Data Cache)
- **Streaming**
  - `loading.tsx` (Route-Level Streaming)
  - `<Suspense>` in Server Components (Component-Level Streaming)
  - Sequential vs Parallel Data Fetching with Suspense
  - Progressive Rendering (Show Parts of Page as They Become Ready)

### 📦 Module 1.5: Server Actions & Mutations
- **Server Actions**
  - `'use server'` Directive (File-Level or Function-Level)
  - Calling from Client Components (`<form action={serverAction}>`)
  - Calling from Event Handlers (`onClick` → Server Action via `startTransition`)
  - Inline Server Actions (Defined Inside Server Components)
  - Module-Level Server Actions (Defined in Separate `actions.ts` Files)
- **Form Handling**
  - `<form action={action}>` (Progressive Enhancement — Works Without JS)
  - `FormData` Parameter (Server Action Receives `FormData`)
  - `useActionState` (Track Pending State, Return Values, Errors)
  - `useFormStatus` (Pending State Inside Form — For Submit Buttons)
  - `useOptimistic` (Optimistic UI Updates Before Server Response)
- **Validation**
  - Zod Schema Validation in Server Actions
  - Return Validation Errors to Client (Structured Error Response)
  - Field-Level Error Display
- **Revalidation After Mutation**
  - `revalidatePath()` (Revalidate Specific Route)
  - `revalidateTag()` (Revalidate by Cache Tag)
  - `redirect()` After Mutation (Post-Redirect-Get Pattern)
- **Server Actions vs Route Handlers**
  - Server Actions: Form Mutations, State Updates, Revalidation
  - Route Handlers: Webhooks, External API Consumption, Non-UI Endpoints
  - When to Use Which

### 📦 Module 1.6: Route Handlers (API Routes)
- `app/api/*/route.ts` Convention
- HTTP Method Exports (`GET`, `POST`, `PUT`, `PATCH`, `DELETE`, `HEAD`, `OPTIONS`)
- `NextRequest` and `NextResponse` (Extended `Request`/`Response`)
- Request Parsing (Body, Query Params, Headers, Cookies)
- Response Helpers (`NextResponse.json()`, `NextResponse.redirect()`)
- Dynamic Route Handlers (`/api/users/[id]/route.ts`)
- Route Handler Caching (GET Handlers Can Be Cached)
- Streaming Responses (SSE, Large Data)
- CORS Configuration in Route Handlers
- Webhook Handlers (Signature Verification)

### 📦 Module 1.7: Middleware
- `middleware.ts` (Root-Level — Runs Before Every Request)
- `NextRequest` and `NextResponse` in Middleware
- Middleware Matching (`config.matcher` — Route Patterns)
- Middleware Use Cases
  - Authentication Checks (Redirect Unauthenticated Users)
  - URL Rewriting (A/B Testing, Feature Flags)
  - Request/Response Header Modification
  - Geolocation-Based Routing
  - Rate Limiting (Lightweight — Edge Compatible)
  - Logging and Analytics
  - Internationalization (i18n) Routing
- Middleware Runs on Edge Runtime (Limitations — No Node.js APIs)
- Middleware Chaining (Composing Multiple Middleware Functions)
- Middleware vs Guards vs Server Action Checks (When to Use What)

### 📦 Module 1.8: Metadata & SEO
- `metadata` Export (Static Metadata)
- `generateMetadata()` (Dynamic Metadata — Async)
- Open Graph, Twitter Card Metadata
- `robots.txt` (`app/robots.ts`)
- `sitemap.xml` (`app/sitemap.ts`)
- `opengraph-image.tsx` (Dynamic OG Image Generation)
- JSON-LD Structured Data
- Canonical URLs
- `<head>` Management

### 📦 Module 1.9: Optimization
- `next/image` (Automatic Image Optimization — Lazy Loading, Responsive, WebP/AVIF)
- `next/font` (Zero Layout Shift Font Loading — Google Fonts and Local Fonts)
- `next/script` (Script Loading Strategy — `beforeInteractive`, `afterInteractive`, `lazyOnload`)
- `next/link` (Prefetching — Automatic for Visible Links)
- Bundle Analysis (`@next/bundle-analyzer`)
- Dynamic Imports (`next/dynamic` — Code Splitting on Demand)
- Static Assets and `public/` Directory
- Environment Variables (`NEXT_PUBLIC_` for Client, Plain for Server)

> ### 🛠 Phase 1 Milestone Project: **Content Management Dashboard**
> Full-featured content management system with:
> - App Router with nested layouts (public site layout, dashboard layout, settings layout)
> - Dynamic routes for content pages (`/posts/[slug]`, `/categories/[id]`)
> - Parallel routes for dashboard (sidebar + main content)
> - Intercepting routes for content preview modals
> - Server Components for all data display (zero unnecessary client JS)
> - Client Components only where interactivity needed (forms, filters, dropdowns)
> - Server Actions for all CRUD mutations with Zod validation
> - `useActionState` + `useOptimistic` for form submissions
> - Revalidation strategy (tag-based for content, time-based for analytics)
> - Route Handlers for webhook endpoints (external CMS sync)
> - Middleware for auth redirect and role-based route protection
> - Dynamic metadata and OG images for SEO
> - `next/image`, `next/font`, bundle optimization

---

## 🔵 PHASE 2: Data Access & State Management
> **Goal:** Master database access, ORM integration, caching layers, and client/server state management.

---

### 📦 Module 2.1: Database Access in Next.js
- **The Server Component Advantage (Direct DB Access — No API Layer)**
  - Server Components Can Call Database Directly
  - No REST/GraphQL API Needed for Read Operations
  - Connection Management in Serverless (Cold Starts, Connection Limits)
- **Prisma with Next.js**
  - Prisma Client Singleton Pattern (Avoid Multiple Instances in Dev — `globalThis`)
  - Schema Design and Migrations
  - Prisma in Server Components (Async Queries)
  - Prisma in Server Actions (Mutations)
  - Edge Compatibility (`@prisma/adapter-*` for Edge Runtime)
  - Prisma Accelerate (Connection Pooling for Serverless)
- **Drizzle ORM with Next.js**
  - Drizzle Client Setup
  - Type-Safe Queries in Server Components
  - Drizzle Kit for Migrations
  - Edge-Compatible (Runs on Edge Runtime)
  - Drizzle vs Prisma for Next.js (Trade-offs)
- **Connection Pooling in Serverless**
  - The Problem (Every Serverless Invocation Opens New Connection)
  - Prisma Accelerate / Prisma Data Proxy
  - Neon Serverless Driver (WebSocket-Based — Edge Compatible)
  - PgBouncer (External Pooler)
  - Supabase Connection Pooler
- **Database Branching (Modern Workflow)**
  - Neon (Database Branching Like Git — Preview Environments)
  - PlanetScale (Database Branching — MySQL)
  - One Branch Per Pull Request

### 📦 Module 2.2: Caching Architecture (Deep Dive)
- **Next.js Four-Layer Cache (Revisited with Mastery)**
  - Request Memoization → Data Cache → Full Route Cache → Router Cache
  - How They Interact (Decision Tree)
  - When Each Layer Applies and How to Opt Out
- **React `cache()` Function**
  - Memoize Database Queries Across Components in Same Render
  - Prevents Waterfall Re-Fetching
  - Request-Scoped (Fresh Per Request)
- **`unstable_cache()` / `cacheLife()` / `cacheTag()` (Next.js 15)**
  - Cache Database Queries Across Requests (Beyond `fetch`)
  - Tag-Based Invalidation for Non-Fetch Data
  - Cache Profiles (`cacheLife('minutes')`, `cacheLife('hours')`)
- **External Caching (Redis)**
  - Redis for Application-Level Caching
  - `ioredis` or `@upstash/redis` (Serverless-Friendly)
  - Cache-Aside Pattern in Server Components
  - Session Storage in Redis
  - Rate Limiting State in Redis
- **CDN Caching**
  - Vercel Edge Cache
  - `Cache-Control` Headers for Route Handlers
  - `s-maxage` and `stale-while-revalidate`
  - ISR as CDN Cache Invalidation

### 📦 Module 2.3: Client-Side State Management
- **When You Need Client State (Server Components Reduce This Dramatically)**
  - UI State (Modals, Tabs, Dropdowns, Filters)
  - Optimistic Updates (Client Holds Pending State)
  - Real-Time Data (WebSocket/Polling State)
  - Form State (Multi-Step Forms, Wizard)
- **URL as State (Preferred for Shareable State)**
  - `searchParams` in Server Components
  - `useSearchParams()` + `useRouter()` in Client Components
  - `nuqs` Library (Type-Safe URL State Management)
  - Filtering, Sorting, Pagination via URL
- **React Context (Simple Global State)**
  - Context Provider in Layout (Wrap Client Subtree)
  - Theme, Locale, User Preferences
- **Zustand (Lightweight State Management — Preferred for Next.js)**
  - Store Creation (Outside Components)
  - Selectors (Granular Re-Renders)
  - Persist Middleware (localStorage Sync)
  - Server-Side Hydration Considerations
- **Jotai (Atomic State — Alternative)**
  - Atoms (Smallest Unit of State)
  - Derived Atoms (Computed State)
  - SSR Compatibility
- **TanStack Query (React Query) — Server State on Client**
  - When Needed in Next.js (Polling, Real-Time, Optimistic Updates, Infinite Scroll)
  - Query Keys and Stale Time
  - Mutations with Optimistic Updates
  - Prefetching (Hydrate from Server Component)
  - `dehydrate` / `HydrationBoundary` (Pass Server Data to Client Cache)
  - Why You Often DON'T Need React Query in Next.js (Server Components Replace Most Use Cases)

### 📦 Module 2.4: Database Migrations & Schema Management
- Migration Strategies
  - Prisma Migrate (`prisma migrate dev`, `prisma migrate deploy`)
  - Drizzle Kit (`drizzle-kit generate`, `drizzle-kit migrate`)
- Zero-Downtime Migrations (Expand/Contract Pattern)
- Data Migrations
- Running Migrations in CI/CD
- Preview Environment Databases (Neon Branching, PlanetScale Branching)
- Seed Scripts for Development and Testing

### 📦 Module 2.5: Full-Text Search & External Data
- **Search Solutions**
  - PostgreSQL Full-Text Search (`tsvector`, `tsquery` via Prisma/Drizzle)
  - Meilisearch (Fast, Self-Hosted — Awareness)
  - Algolia (Managed Search — Awareness)
  - Elasticsearch (Enterprise — Awareness)
- **External API Integration**
  - Server Components as API Consumers (Fetch External APIs)
  - Error Handling and Fallbacks
  - Caching External API Responses
  - Rate Limiting External API Calls
- **CMS Integration (Headless CMS)**
  - Sanity, Contentful, Strapi, Payload CMS (Awareness)
  - Content Preview (Draft Mode in Next.js)
  - Webhook-Triggered Revalidation
  - CMS Data in Server Components

> ### 🛠 Phase 2 Milestone Project: **E-Commerce Product Catalog**
> Product catalog with categories, tags, variants, reviews, and search:
> - Prisma or Drizzle with PostgreSQL (complex relationships)
> - Server Components for all product listing and detail pages (zero client JS for reads)
> - React `cache()` for deduplicating database queries across components
> - Tag-based caching with on-demand revalidation after admin updates
> - Redis caching (`@upstash/redis`) for hot product data and category counts
> - URL-based state for filtering, sorting, pagination (`nuqs`)
> - Client-side optimistic cart updates with Zustand
> - Full-text search with PostgreSQL `tsvector`
> - Database migrations, seed data, preview environment branching with Neon

---

## 🟡 PHASE 3: Authentication & Security
> **Goal:** Implement production-grade authentication, authorization, and application hardening for Next.js.

---

### 📦 Module 3.1: Authentication Architecture in Next.js
- **Authentication Layers in Next.js**
  - Middleware (Edge — First Check, Redirect Unauthenticated)
  - Server Components (Verify Session, Render Based on Auth)
  - Server Actions (Verify Before Mutation)
  - Route Handlers (Verify for API Endpoints)
  - Client Components (Show/Hide UI Based on Auth State)
- **Session Strategies**
  - Cookie-Based Sessions (Stateful — Session ID in Cookie, Data in DB/Redis)
  - JWT-Based Sessions (Stateless — Token in Cookie, Data in Token)
  - Cookie-Based JWT (Secure: `HttpOnly`, `Secure`, `SameSite`, `Path`)
  - When JWT vs Session-Based (Trade-offs for Next.js)

### 📦 Module 3.2: Auth.js (NextAuth v5)
- **Auth.js Core**
  - `auth()` Function (Get Session in Server Components)
  - `signIn()`, `signOut()` (Server Actions)
  - `auth.ts` Configuration (Providers, Callbacks, Session Strategy)
  - `middleware.ts` Integration (Protect Routes)
- **Providers**
  - OAuth Providers (Google, GitHub, Discord, Apple, Microsoft)
  - Credentials Provider (Email/Password — Custom Logic)
  - Email Provider (Magic Links)
  - Multiple Providers Simultaneously
- **Session Management**
  - JWT Strategy (Default — Stateless)
  - Database Strategy (Stateful — Session Table)
  - Session Callbacks (Modify Session/Token Content)
  - Extending Session Types (Add Custom Fields)
- **Database Adapters**
  - Prisma Adapter (`@auth/prisma-adapter`)
  - Drizzle Adapter (`@auth/drizzle-adapter`)
  - Custom Adapter
  - User, Account, Session, VerificationToken Tables
- **Callbacks Deep Dive**
  - `jwt` Callback (Modify JWT on Sign-In)
  - `session` Callback (Modify Session Object)
  - `signIn` Callback (Control Who Can Sign In)
  - `redirect` Callback (Control Redirect After Auth)
- **Advanced Auth.js**
  - Account Linking (Multiple Providers per User)
  - Custom Sign-In Pages
  - Role-Based Session Data (Add `role` to JWT/Session)
  - Refresh Token Rotation for OAuth

### 📦 Module 3.3: Custom Authentication (Build Your Own)
- **When to Build Custom Auth (Beyond Auth.js)**
  - Complex Business Requirements
  - Multi-Tenant Authentication
  - Organization-Based Access Control
  - Custom Session Management
- **Custom JWT Authentication**
  - `jose` Library (JWT Sign, Verify — Edge Compatible)
  - Login Server Action (Verify Credentials, Set JWT Cookie)
  - Middleware (Verify JWT, Redirect If Invalid)
  - Server Component Session Access (Read/Verify Cookie)
  - Refresh Token Strategy (Rotation, Revocation with Redis)
- **External Auth Providers**
  - Clerk (Managed Auth — Excellent Next.js Integration)
  - Lucia Auth (Lightweight, DIY-Friendly)
  - Kinde (Modern Auth Platform)
  - Supabase Auth
  - Keycloak (Self-Hosted Enterprise)

### 📦 Module 3.4: Authorization Patterns
- **RBAC (Role-Based Access Control)**
  - Roles in Session/JWT
  - Middleware-Level Route Protection (By Role)
  - Server Component Conditional Rendering (By Role)
  - Server Action Authorization Checks (By Role)
- **ABAC (Attribute-Based Access Control)**
  - Policy-Based Authorization
  - CASL Integration (`@casl/ability`)
  - Attribute-Based Rendering in Server Components
- **Resource-Level Authorization**
  - Ownership Checks in Server Actions and Server Components
  - Data-Level Security (Filter Queries by User ID)
  - Organization/Tenant Scoping
- **Row-Level Security (Database-Level)**
  - PostgreSQL RLS Policies
  - Supabase RLS (Awareness)
  - Database-Enforced Authorization

### 📦 Module 3.5: Application Security Hardening
- **OWASP Top 10 for Next.js**
  - XSS Prevention
    - React Auto-Escapes JSX (Safe by Default)
    - `dangerouslySetInnerHTML` (Escape Hatch — Sanitize with `DOMPurify`)
    - Server Actions Receive Untrusted Input (Validate Everything)
  - CSRF Protection
    - Same-Site Cookies (Next.js Default)
    - Server Actions Use POST + Origin Check (Built-In CSRF Protection)
    - Custom CSRF Tokens for Route Handlers (When Needed)
  - Injection Prevention
    - SQL Injection (ORM Parameterizes — Safe by Default)
    - Server Action Input Validation (Zod Schemas — Always Validate)
    - Command Injection (Don't `exec` User Input)
  - Insecure Direct Object References (IDOR)
    - Always Verify Ownership in Server Actions/Components
    - Don't Trust Client-Provided IDs Without Auth Check
- **Security Headers**
  - `next.config.ts` `headers()` (CSP, HSTS, X-Frame-Options, etc.)
  - Content Security Policy (CSP) — Nonce-Based for Inline Scripts
  - Strict Transport Security (HSTS)
  - Permissions Policy
- **CORS**
  - Route Handler CORS (`NextResponse` with CORS Headers)
  - `next.config.ts` for API Proxy (Avoid CORS Entirely)
- **Rate Limiting**
  - Middleware-Based (Edge — `@upstash/ratelimit`)
  - Route Handler-Based
  - Per-IP, Per-User, Per-Endpoint
- **Environment Variable Security**
  - `NEXT_PUBLIC_*` (Exposed to Client — Never Put Secrets Here)
  - Server-Only Variables (Only in Server Components/Actions/Route Handlers)
  - `server-only` Package (Prevent Accidental Client Import of Secret-Using Code)
- **Dependency Scanning**
  - `npm audit` / `pnpm audit`
  - Snyk, Socket.dev
  - Dependabot for Automated Updates

> ### 🛠 Phase 3 Milestone Project: **Secure Multi-Tenant SaaS Dashboard**
> Multi-tenant dashboard with:
> - Auth.js with Google OAuth + Credentials provider + Prisma adapter
> - JWT session strategy with custom roles and tenant ID
> - Middleware route protection (public pages vs authenticated vs admin)
> - RBAC (`admin`, `manager`, `member`) with role-based UI rendering in Server Components
> - Resource-level authorization (users only see their tenant's data)
> - Server Action authorization checks with Zod validation
> - Row-level security concepts (filter all queries by tenant)
> - Rate limiting with `@upstash/ratelimit` in middleware
> - Security headers via `next.config.ts` (CSP with nonce)
> - CSRF-safe Server Actions
> - Full security test suite

---

## 🟠 PHASE 4: Architecture & Design Patterns
> **Goal:** Apply architectural styles, modular design, and domain patterns within Next.js full-stack applications.

---

### 📦 Module 4.1: Next.js Application Architecture
- **Architectural Decision: How Much Backend in Next.js?**
  - Full-Stack Next.js (Database Direct, Server Actions, Route Handlers — Everything)
  - Next.js Frontend + Separate Backend API (NestJS/FastAPI/Spring Boot — Enterprise)
  - Next.js BFF (Backend-for-Frontend — Proxies to Microservices)
  - Choosing Based on Team Size, Complexity, Scale
- **Feature-Based Architecture**
  - Feature Folders (`features/products/`, `features/orders/`, `features/users/`)
  - Each Feature Contains: Components, Actions, Queries, Schemas, Types, Tests
  - Shared Code (`shared/`, `lib/`, `components/ui/`)
  - Clear Import Rules (Features Don't Import From Other Features Directly)
- **Colocation Principle**
  - Keep Related Code Together (Component + Test + Styles + Types)
  - App Router Colocation (Non-`page.tsx` Files in Route Folders Are Not Routes)
  - Private Folders (`_components/`, `_lib/` — Convention)

### 📦 Module 4.2: Layered Architecture in Next.js
- **Presentation Layer (Routes, Pages, Components)**
  - `app/` Directory (Route Handlers, Pages, Layouts)
  - UI Components (`components/ui/` — Reusable, Stateless)
  - Feature Components (`features/*/components/` — Feature-Specific)
- **Application Layer (Server Actions, Use Cases)**
  - Server Actions as Use Cases (Each Action = One Business Operation)
  - Action Files (`features/*/actions/`)
  - Input Validation (Zod Schemas)
  - Authorization Checks
  - Orchestrating Domain Logic
- **Domain Layer (Business Logic, Validation)**
  - Pure TypeScript Functions and Types (No Next.js/React Dependencies)
  - Business Rules, Calculations, Validations
  - Domain Types and Value Objects
  - Can Be Shared Between Client and Server
- **Data Access Layer (Repositories, Database Queries)**
  - Query Functions (`features/*/queries/` — Server-Only)
  - Repository Pattern (Abstract Database Access Behind Interface)
  - Data Mappers (Database Model → Domain Model)
  - `server-only` Package (Enforce Server-Only Data Access)
- **Why This Matters**
  - Testability (Each Layer Testable in Isolation)
  - Replaceability (Swap Database Without Touching UI)
  - Clarity (Where Does This Code Go?)

### 📦 Module 4.3: Server Action Patterns
- **Action Organization**
  - One Action Per File vs Grouped Actions
  - Action Naming Conventions (`createOrder`, `updateProduct`, `deleteUser`)
  - Shared Action Utilities (Auth Check, Validation Wrapper)
- **Safe Action Pattern**
  - `next-safe-action` Library (Type-Safe, Validated Server Actions)
    - Schema Validation (Zod)
    - Middleware Chains (Auth, Logging, Rate Limiting)
    - Type-Safe Return Values
    - Error Handling
  - Custom Safe Action Wrapper (Build Your Own)
    - Action Function → Validate Input → Check Auth → Execute → Return Result
    - Typed Response (`{ success: true, data } | { success: false, error }`)
- **Optimistic Update Patterns**
  - `useOptimistic` for Instant UI Feedback
  - Rollback on Server Error
  - Revalidation After Server Confirmation
- **Progressive Enhancement**
  - Actions Work Without JavaScript (Form Submission)
  - Enhanced With JavaScript (Optimistic Updates, Loading States)
  - Graceful Degradation Strategy

### 📦 Module 4.4: Hexagonal Architecture in Next.js
- **Ports & Adapters for Full-Stack**
  - Domain Layer (Pure TypeScript — No Framework Dependencies)
    - Entities, Value Objects, Domain Services
    - Business Rules as Pure Functions
  - Application Layer (Use Cases)
    - Port Interfaces (Repository Interfaces, Service Interfaces)
    - Use Case Functions (Orchestrate Domain)
  - Infrastructure Layer (Adapters)
    - Prisma/Drizzle Repository Implementations
    - External API Clients
    - Email Service Adapters
  - Presentation Layer (Next.js-Specific)
    - Pages and Layouts (Server Components Calling Use Cases)
    - Server Actions (Calling Use Cases)
    - Route Handlers (Calling Use Cases)
- **Practical Structure**
  - `src/domain/` (Zero Dependencies)
  - `src/application/` (Depends Only on Domain)
  - `src/infrastructure/` (Implements Ports — Depends on Domain + External)
  - `src/app/` (Next.js Routes — Depends on Application)
- **Trade-offs in Next.js Context**
  - When Hexagonal Makes Sense (Large Teams, Complex Domain, Backend-Heavy)
  - When It's Overkill (Small Apps, Content Sites, CRUD)

### 📦 Module 4.5: Strategic DDD
- Ubiquitous Language
- Domain Discovery (Event Storming)
- Bounded Contexts
  - Mapping to Next.js Feature Modules
  - When Bounded Context Becomes Separate Service
- Context Mapping Patterns
  - Shared Kernel, Customer-Supplier, Conformist
  - Anti-Corruption Layer, Open Host Service
  - Partnership, Separate Ways
- Subdomain Classification (Core, Supporting, Generic)

### 📦 Module 4.6: Tactical DDD in Next.js
- Entities and Value Objects (Plain TypeScript Classes)
- Aggregates (Consistency Boundaries)
- Domain Events (In-Process Event Bus)
- Repositories (Interface in Domain, Prisma/Drizzle Implementation)
- Domain Services (Stateless Cross-Aggregate Logic)
- Application Services / Use Cases
- Specifications Pattern
- Mapping Between Domain Models and Database Models

### 📦 Module 4.7: Architecture Decision Records
- ADR Structure (Title, Status, Context, Decision, Consequences)
- When to Write an ADR
- ADR Templates
- Connecting ADRs to Code

> ### 🛠 Phase 4 Milestone Project: **Order Management System (DDD + Layered Architecture)**
> Order management system with:
> - Feature-based architecture (Orders, Inventory, Payments, Notifications)
> - Layered architecture (Presentation → Application → Domain → Infrastructure)
> - Domain layer with zero framework dependencies (entities, value objects, business rules)
> - Repository pattern with Prisma adapters behind interfaces
> - Server Actions as use cases (validated with Zod, authorized, typed responses)
> - `next-safe-action` for action middleware chain
> - Domain events via in-process event emitter
> - Anti-Corruption Layer for external payment provider
> - ADRs for all major decisions
> - Event Storming artifacts documented

---

## 🔴 PHASE 5: Full-Stack Integration & Real-Time
> **Goal:** Master advanced Next.js patterns, third-party integrations, real-time features, and external API design.

---

### 📦 Module 5.1: API Design with Next.js
- **Route Handlers as API**
  - RESTful Route Handler Design
  - Request Validation (Zod for Body, Params, Query)
  - Response Standardization (Consistent Error/Success Format)
  - API Versioning (`/api/v1/`, `/api/v2/`)
  - OpenAPI Generation from Route Handlers (`next-swagger-doc`, `next-openapi`)
- **tRPC with Next.js (Type-Safe API Layer)**
  - tRPC Architecture (Type-Safe RPC — No API Layer Needed)
  - Router Definition (Procedures: Query, Mutation, Subscription)
  - Input Validation (Zod Integration)
  - Context (Auth, Database Session)
  - Middleware (Auth, Logging, Error Handling)
  - Client Integration (React Query Under the Hood)
  - tRPC vs Server Actions vs REST Route Handlers (Decision Framework)
- **GraphQL with Next.js**
  - Apollo Server in Route Handlers
  - Relay / Apollo Client with Server Components
  - GraphQL Yoga (Awareness)
  - When GraphQL in Next.js (Complex Data Requirements, Multiple Clients)

### 📦 Module 5.2: Real-Time Features
- **Server-Sent Events (SSE)**
  - Route Handler Streaming (`ReadableStream`)
  - Client-Side `EventSource` API
  - Use Cases: Live Notifications, Activity Feeds
- **WebSockets**
  - WebSocket Limitations in Serverless (No Persistent Connections)
  - Solutions
    - Separate WebSocket Server (Node.js/Fastify — Long-Lived Process)
    - Ably / Pusher (Managed Real-Time Infrastructure)
    - Socket.IO with Custom Server
    - Supabase Realtime
    - Partykit / Cloudflare Durable Objects (Edge-Native)
  - Client-Side WebSocket Integration
- **Polling**
  - TanStack Query with Polling (`refetchInterval`)
  - When Polling Is the Simplest Correct Answer
- **Optimistic UI**
  - `useOptimistic` for Instant Feedback
  - Revalidation After Confirmation
  - Conflict Resolution (Server State vs Client State)

### 📦 Module 5.3: Background Jobs & Async Processing
- **The Serverless Challenge (No Long-Running Processes)**
- **Solutions for Background Work**
  - Vercel Cron Jobs (`vercel.json` Crons + Route Handlers)
  - Inngest (Event-Driven Background Jobs — Excellent Next.js Integration)
    - Functions, Events, Steps
    - Retries, Scheduling, Fan-Out
    - Long-Running Jobs with Steps
  - Trigger.dev (Background Jobs for Next.js)
  - QStash (`@upstash/qstash` — Serverless Message Queue)
  - BullMQ with Separate Worker Process (Traditional)
- **Email Sending**
  - Resend (Modern Email API — React Email Templates)
  - Nodemailer (Traditional — Awareness)
  - Email in Server Actions (Trigger After Mutation)
  - Email via Background Job (Better — Non-Blocking)
- **File Upload & Storage**
  - `@vercel/blob` (Vercel Blob Storage)
  - UploadThing (Full-Stack File Upload)
  - AWS S3 / Cloudflare R2 (Presigned URLs)
  - Upload in Server Actions vs Route Handlers vs Client Direct-to-Storage
  - Image Processing (Sharp — Server-Side Resize/Optimize)

### 📦 Module 5.4: Payment Integration
- **Stripe with Next.js**
  - Stripe Checkout (Hosted Payment Page — Simplest)
  - Stripe Elements (Embedded Payment Form)
  - Server Action for Payment Intent Creation
  - Webhook Handler (Route Handler for `stripe.webhooks.constructEvent`)
  - Subscription Management
  - Idempotency Keys
  - Testing with Stripe CLI (`stripe listen --forward-to`)
- **Payment Security**
  - PCI Compliance (Stripe Handles Card Data — You Handle Webhook Verification)
  - Webhook Signature Verification
  - Idempotent Webhook Processing (Store Processed Event IDs)

### 📦 Module 5.5: Internationalization (i18n)
- Routing Strategies
  - Sub-Path (`/en/about`, `/fr/about`)
  - Domain-Based (`en.example.com`, `fr.example.com`)
- `next-intl` Library (Preferred for App Router)
  - Message Files (JSON per Locale)
  - Server Components Translation
  - Client Components Translation
  - Middleware Locale Detection
  - `generateStaticParams` for Localized Routes
- Content Translation Strategies
- RTL Support (Awareness)
- Date, Number, Currency Formatting (`Intl` API)

### 📦 Module 5.6: Multi-Tenancy
- **Tenant Isolation Strategies**
  - Shared Database with Tenant Column (Simple, Most Common)
  - Schema-Per-Tenant (PostgreSQL Schemas)
  - Database-Per-Tenant (Maximum Isolation — Expensive)
- **Tenant Resolution**
  - Subdomain-Based (`tenant.example.com` — Middleware Resolves)
  - Path-Based (`/tenant/dashboard` — Route Group)
  - Custom Domain (CNAME — `next.config.ts` Rewrites)
- **Tenant Context Propagation**
  - Middleware Sets Tenant ID
  - Server Components/Actions Access Tenant Context
  - Database Queries Scoped by Tenant
- **Tenant-Aware Caching**
  - Cache Keys Include Tenant ID
  - Separate Cache Per Tenant (When Needed)

> ### 🛠 Phase 5 Milestone Project: **Multi-Tenant SaaS Platform**
> Full SaaS platform with:
> - Multi-tenancy with subdomain resolution (middleware)
> - tRPC API layer for complex data operations
> - Stripe integration for subscription management (Checkout + Webhooks)
> - Real-time notifications via SSE
> - Background jobs with Inngest (welcome email, report generation, webhook processing)
> - File upload with UploadThing or Vercel Blob
> - Internationalization with `next-intl` (English + one other language)
> - Tenant-scoped data access (all queries filtered by tenant)
> - Admin dashboard for tenant management

---

## 🟣 PHASE 6: Performance & Optimization
> **Goal:** Master Next.js performance — rendering strategies, bundle optimization, Core Web Vitals, and scalability.

---

### 📦 Module 6.1: Rendering Strategy Optimization
- **Static vs Dynamic Per Route**
  - Identifying Static Routes (Content Pages, Marketing, Documentation)
  - Identifying Dynamic Routes (Dashboards, User-Specific Pages)
  - Partial Prerendering (PPR — Static Shell + Dynamic Holes — Experimental)
  - `generateStaticParams()` for Static Dynamic Routes
- **Streaming Optimization**
  - Strategic `<Suspense>` Boundary Placement
  - Avoiding Waterfalls (Parallel Data Fetching)
  - Progressive Rendering (Critical Content First, Secondary Later)
  - Skeleton Screens and Loading States
- **Edge vs Node.js Runtime Per Route**
  - Edge: Simple Logic, Low Latency, No Heavy Dependencies
  - Node.js: Complex Logic, Database Libraries, Full API Access
  - Choosing Per Route Segment

### 📦 Module 6.2: Core Web Vitals
- **LCP (Largest Contentful Paint)**
  - Optimize Hero Images (`next/image`, `priority` Prop)
  - Font Loading (`next/font` — Zero Layout Shift)
  - Server Component Rendering (Fast Time to Content)
  - Reduce Server Response Time (Edge, Caching, Connection Pooling)
- **INP (Interaction to Next Paint)**
  - Minimize Client JavaScript (Server Components Default)
  - `useTransition` for Non-Blocking Updates
  - Lazy Load Non-Critical Client Components (`next/dynamic`)
  - Avoid Long Tasks on Main Thread
  - Web Workers for CPU-Heavy Operations
- **CLS (Cumulative Layout Shift)**
  - Image Dimensions (`next/image` Handles Automatically)
  - Font Loading (`next/font` Prevents FOIT/FOUT)
  - Dynamic Content (Reserve Space for Async Content)
  - Avoid Injecting Content Above Existing Content
- **Measurement**
  - Lighthouse (Lab Data)
  - Chrome User Experience Report — CrUX (Field Data)
  - Vercel Analytics / Speed Insights (Real User Monitoring)
  - `web-vitals` Library (Custom Reporting)
  - `useReportWebVitals` (Next.js Built-In)

### 📦 Module 6.3: Bundle Optimization
- **Analyzing Bundles**
  - `@next/bundle-analyzer` (Visual Bundle Map)
  - Import Cost VS Code Extension
  - `next build` Output Analysis (Route Sizes, First Load JS)
- **Reducing Bundle Size**
  - Server Components (Eliminate Client JS for Data Display)
  - Dynamic Imports (`next/dynamic`, `React.lazy()`)
  - Tree Shaking (Import Specific Functions, Not Entire Libraries)
  - Barrel File Anti-Pattern (Barrel Files Break Tree Shaking — Avoid)
  - Alternative Smaller Libraries (`date-fns` vs `moment`, `clsx` vs `classnames`)
  - `optimizePackageImports` in `next.config.ts`
- **Code Splitting Strategies**
  - Route-Based Splitting (Automatic in Next.js)
  - Component-Based Splitting (`next/dynamic`)
  - Library-Based Splitting (Heavy Libraries Only When Needed)

### 📦 Module 6.4: Image & Media Optimization
- `next/image` Deep Dive
  - Responsive Images (`sizes` Prop)
  - `fill` Mode (Object-Fit for Dynamic Size Containers)
  - Priority Loading for Above-the-Fold Images
  - Remote Image Configuration (`remotePatterns` in `next.config.ts`)
  - Custom Image Loaders (Cloudinary, Imgix)
  - AVIF and WebP Format Negotiation
  - Placeholder Blur (Blur Hash, Base64 Placeholder)
- Video Optimization Strategy
  - Lazy Loading Video
  - Video CDN (Mux, Cloudflare Stream — Awareness)
  - Adaptive Bitrate Streaming (HLS)

### 📦 Module 6.5: Scalability & Edge
- **Edge Rendering**
  - Edge Runtime for Route Handlers and Middleware
  - Edge-Compatible Database Drivers (Neon, PlanetScale, Turso)
  - Edge-Compatible Auth (JWT Verification with `jose`)
  - Limitations (No `fs`, Limited `node:` APIs)
- **ISR at Scale**
  - On-Demand Revalidation (Webhook → `revalidatePath()`/`revalidateTag()`)
  - Stale-While-Revalidate Pattern
  - Tag-Based Invalidation Strategy
- **Multi-Region Deployment**
  - Vercel (Automatic Global CDN, Edge Functions)
  - Self-Hosted Multi-Region (Kubernetes + CDN)
  - Database Proximity (Read Replicas Near Edge)
  - Data Consistency Across Regions

> ### 🛠 Phase 6 Milestone Project: **Performance Audit & Optimization**
> Take the Phase 5 SaaS platform and optimize:
> - Core Web Vitals all green (LCP < 2.5s, INP < 200ms, CLS < 0.1)
> - Bundle analysis and reduction (reduce client JS by 40%+)
> - Strategic rendering (static for marketing pages, dynamic for dashboard, streaming for data-heavy pages)
> - Image optimization with `next/image` (responsive, AVIF, blur placeholders)
> - Edge middleware for auth and rate limiting
> - ISR with on-demand revalidation for content pages
> - Vercel Analytics / Speed Insights monitoring
> - Performance budget defined and enforced in CI
> - Lighthouse CI integration (fail build if score drops)

---

## ⚫ PHASE 7: Testing at Scale
> **Goal:** Master every layer of testing for Next.js — from unit to E2E to visual.

---

### 📦 Module 7.1: Unit Testing
- **Vitest Configuration for Next.js**
  - `vitest.config.ts` with Next.js Plugin (`@vitejs/plugin-react`)
  - Path Aliases Matching `tsconfig.json`
  - Server vs Client Test Environments
- **Testing React Components**
  - React Testing Library (`@testing-library/react`)
    - `render`, `screen`, `fireEvent`, `waitFor`
    - `userEvent` (Realistic User Interactions)
    - Accessibility Queries (`getByRole`, `getByLabelText`)
    - Async Testing (`findBy*`, `waitFor`)
  - Testing Server Components (Render Directly — They're Just Functions)
  - Testing Client Components (Standard React Testing Library)
  - Mocking `next/navigation` (`useRouter`, `usePathname`, `useSearchParams`)
  - Mocking `next/image`, `next/link`
- **Testing Server Actions**
  - Call Directly as Functions (They're Just Async Functions)
  - Mock Database/External Dependencies
  - Verify Side Effects (Revalidation, Redirect)
  - Test Validation Errors
- **Testing Hooks**
  - `renderHook` from React Testing Library
  - Testing Custom Hooks in Isolation
- **Testing Utilities**
  - Test Factories (Generate Test Data)
  - MSW (Mock Service Worker — Mock API Calls)

### 📦 Module 7.2: Integration Testing
- **Testing with Real Database**
  - Testcontainers (PostgreSQL for Integration Tests)
  - Prisma Test Environment (Migrations + Seed)
  - Transaction Rollback Between Tests
- **Testing Route Handlers**
  - Call Route Handler Functions Directly
  - Validate Request/Response
  - Test Error Cases
- **Testing Middleware**
  - Mock `NextRequest` and `NextResponse`
  - Verify Redirects, Rewrites, Header Modifications
- **API Testing**
  - End-to-End API Tests (Spin Up Next.js Dev Server)
  - `supertest` or `fetch` Against Local Server

### 📦 Module 7.3: End-to-End Testing
- **Playwright (Preferred for Next.js)**
  - Setup and Configuration (`playwright.config.ts`)
  - Page Object Model (Organize Test Helpers)
  - Navigation, Forms, Assertions
  - Testing Authentication Flows (Login, Protected Routes)
  - Testing Server Actions (Form Submission, Verification)
  - Visual Testing (Screenshot Comparison)
  - API Testing with Playwright (`request` Context)
  - Multi-Browser Testing (Chromium, Firefox, WebKit)
  - Mobile Viewport Testing
  - Parallel Execution
  - CI Integration (GitHub Actions + Playwright)
- **Cypress (Alternative — Awareness)**
  - Component Testing
  - E2E Testing
  - When Cypress vs Playwright

### 📦 Module 7.4: Architecture & Visual Testing
- **Architecture Testing**
  - `dependency-cruiser` (Enforce Import Rules)
    - Domain Must Not Import Infrastructure
    - Features Must Not Cross-Import
  - `eslint-plugin-boundaries` (Module Boundary Rules)
- **Visual Regression Testing**
  - Playwright Visual Comparisons (Built-In)
  - Chromatic (Storybook Visual Testing — Awareness)
  - Percy (Awareness)
- **Accessibility Testing**
  - `axe-core` Integration (Playwright + axe)
  - `jest-axe` for Component-Level
  - Lighthouse Accessibility Audit in CI

### 📦 Module 7.5: Performance & Load Testing
- **Lighthouse CI**
  - `@lhci/cli` (Run Lighthouse in CI)
  - Performance Budgets (Fail Build on Regression)
  - Assertions (LCP, INP, CLS Thresholds)
- **Load Testing Route Handlers**
  - k6 for API Load Testing
  - Autocannon for Quick Benchmarks
- **Bundle Size Monitoring**
  - `next build` Output Tracking
  - `bundlewatch` (Fail on Bundle Size Increase)

### 📦 Module 7.6: Testing Strategy
- Test Pyramid for Next.js
  - Unit (Components, Actions, Hooks, Utils) — Most Tests
  - Integration (Routes + Database, Route Handlers + Auth) — Medium
  - E2E (Critical User Flows — Login, Purchase, CRUD) — Fewest
- Testing What Matters (Don't Test Framework Code, Test Your Logic)
- Test Data Management
- CI/CD Integration (Run Tests Before Deploy)

> ### 🛠 Phase 7 Milestone Project: **Comprehensive Test Suite for SaaS Platform**
> Retrofit the SaaS platform with:
> - Unit tests (Vitest + React Testing Library) for all components, Server Actions, hooks
> - Integration tests with Testcontainers (PostgreSQL) for data access layer
> - Route Handler tests with mocked auth
> - Playwright E2E tests for critical flows (auth, CRUD, payment, tenant switching)
> - Visual regression tests with Playwright screenshots
> - Accessibility tests with axe-core integration
> - Architecture tests with `dependency-cruiser` (layer rules)
> - Lighthouse CI with performance budgets
> - Bundle size monitoring with `bundlewatch`
> - All tests in GitHub Actions CI pipeline (unit → integration → E2E → Lighthouse)
> - Greater than 80% meaningful coverage

---

## 🔶 PHASE 8: DevOps, Observability & Production Readiness
> **Goal:** Deploy, monitor, and operate Next.js applications in production with confidence.

---

### 📦 Module 8.1: Deployment Strategies
- **Vercel (First-Class Next.js Hosting)**
  - Git Push → Build → Deploy (Zero Config)
  - Preview Deployments (Every PR Gets a URL)
  - Serverless Functions (Server Components, Route Handlers, Server Actions)
  - Edge Functions (Middleware, Edge-Runtime Routes)
  - Vercel KV (Redis), Vercel Postgres, Vercel Blob
  - Domain Configuration, Environment Variables
  - Deployment Protection (Password, Vercel Auth)
  - Spend Management and Budget Alerts
- **Self-Hosted (Docker + Node.js)**
  - `next build` → `next start` (Standalone Node.js Server)
  - `output: 'standalone'` (Minimal Production Build)
  - Multi-Stage Dockerfile for Next.js
    - Stage 1: Install Dependencies
    - Stage 2: Build (`next build`)
    - Stage 3: Production Image (`standalone` Output + `public/` + `.next/static/`)
  - Docker Compose (Next.js + PostgreSQL + Redis)
  - Sharp for Image Optimization in Docker (`next/image`)
  - Health Check Endpoint
- **Self-Hosted (Kubernetes)**
  - Deployment, Service, Ingress
  - Horizontal Pod Autoscaler
  - Readiness/Liveness Probes (Health Endpoint)
  - ConfigMaps and Secrets
  - Helm Charts
  - CDN in Front (CloudFront, Cloudflare)
- **Other Platforms**
  - AWS Amplify (Managed Next.js Hosting)
  - Cloudflare Pages (Edge-First — `@cloudflare/next-on-pages`)
  - Netlify (Awareness)
  - Coolify, SST (Self-Hosted Alternatives)
- **Static Export (`output: 'export'`)**
  - When to Use (No Server Needed — CDN-Only)
  - Limitations (No Server Components, No Middleware, No ISR)
  - S3 + CloudFront Deployment

### 📦 Module 8.2: CI/CD Pipeline Design
- **CI Pipeline (GitHub Actions)**
  - Lint (ESLint) → Type Check (`tsc --noEmit`) → Unit Test → Integration Test (Testcontainers) → Build (`next build`) → Bundle Size Check → Lighthouse CI → E2E Test (Playwright) → Docker Build → Push
  - Caching (`node_modules`, `.next/cache`, Playwright Browsers)
  - Parallel Jobs (Unit/Integration Tests Parallel with Lint/Type Check)
  - Preview Deployment per PR (Vercel Auto or Manual)
- **CD Pipeline**
  - Vercel: Automatic (Git Push = Deploy)
  - Self-Hosted: Docker Build → Push to Registry → Deploy to Kubernetes
  - Blue/Green Deployments
  - Canary Releases
  - Feature Flags
    - Vercel Edge Config
    - LaunchDarkly / Unleash
    - Custom with Redis + Middleware
    - Server Component Conditional Rendering by Feature Flag
  - Database Migrations as Pipeline Step (Before Deploy)
- **GitOps for Self-Hosted**
  - ArgoCD (Kubernetes Deployments from Git)
  - Sync Policies, Rollback

### 📦 Module 8.3: Infrastructure as Code
- Terraform for Next.js Infrastructure
  - AWS (ECS/EKS, RDS, ElastiCache, CloudFront, S3)
  - Vercel Provider (Terraform Vercel Provider — Projects, Domains, Env Vars)
- Database Infrastructure
  - Neon (Serverless PostgreSQL — Branching)
  - Supabase
  - PlanetScale
  - Self-Managed (RDS, Aurora)

### 📦 Module 8.4: Observability
- **Logging**
  - `pino` (Structured JSON Logging — Preferred for Node.js)
  - Logging in Server Components, Server Actions, Route Handlers
  - Request Context (Correlation IDs via Middleware Headers)
  - `instrumentation.ts` (Next.js Instrumentation Hook — Setup Logging/Tracing at Startup)
  - Log Aggregation (Vercel Logs, Axiom, Datadog, Loki)
  - What to Log (Errors, Auth Events, Mutations, Performance) vs What Not to Log (PII)
- **Metrics**
  - Vercel Analytics (Web Vitals, Traffic, Speed Insights)
  - Custom Metrics
    - Prometheus Client (`prom-client`) in Route Handlers
    - `/metrics` Endpoint
  - Business Metrics (Signups, Conversions, Feature Usage)
  - Grafana Dashboards
  - SLIs, SLOs, Error Budgets
- **Distributed Tracing**
  - OpenTelemetry for Next.js
    - `@vercel/otel` (Vercel OpenTelemetry — Simplified)
    - `@opentelemetry/sdk-node` (Standard)
    - `instrumentation.ts` (Next.js Hook for OTel Initialization)
    - Auto-Instrumentation (HTTP, `fetch`, Database)
    - Custom Spans (Server Components, Server Actions)
    - Trace Context Propagation
  - Trace Backends (Jaeger, Grafana Tempo, Honeycomb, Axiom)
  - Correlating Logs + Traces (Trace ID in Log Entries)
- **Error Monitoring**
  - Sentry for Next.js (`@sentry/nextjs`)
    - Automatic Error Capture (Server, Client, Edge)
    - Source Maps Upload (Stack Traces in Original TypeScript)
    - Performance Monitoring (Transaction Traces)
    - User Feedback Widget
    - Release Tracking
  - Custom Error Reporting (Error Boundary + Route Handler)
- **Real User Monitoring (RUM)**
  - Vercel Speed Insights
  - `useReportWebVitals` (Custom RUM Endpoint)
  - Core Web Vitals Monitoring Over Time
- **Alerting**
  - Vercel Alerts (Deployment Failure, Spending)
  - Sentry Alerts (Error Spike, New Issue)
  - Custom Alerts (Prometheus Alertmanager)
  - PagerDuty / Opsgenie Integration (Awareness)

### 📦 Module 8.5: Production Readiness Checklist
- Security Headers Configured (`next.config.ts`)
- CSRF Protection (Server Actions — Built-In)
- Rate Limiting (Middleware or Route-Level)
- Authentication on All Protected Routes
- Input Validation on All Server Actions (Zod)
- Error Boundaries on All Route Segments (`error.tsx`)
- Health Check Endpoint (`/api/health`)
- Structured Logging with Correlation IDs
- Error Monitoring (Sentry)
- Web Vitals Monitoring
- OpenTelemetry Tracing
- Database Migrations Automated in CI/CD
- Environment Variables Secured (No Secrets in `NEXT_PUBLIC_*`)
- Image Optimization Configured (`next/image`)
- Font Optimization (`next/font`)
- Bundle Size Under Budget
- Lighthouse Scores Above Threshold
- E2E Tests Passing
- Preview Deployments for PRs
- Rollback Strategy Defined
- Caching Strategy Documented
- On-Call Runbooks Written

> ### 🛠 Phase 8 Milestone Project: **Production-Ready Deployment**
> Take the SaaS platform and make it production-ready:
> - Deployed to Vercel (primary) AND self-hosted Docker + Kubernetes (alternative)
> - Multi-stage Dockerfile with `standalone` output
> - Helm chart for Kubernetes deployment
> - Full CI/CD pipeline (GitHub Actions: lint → type-check → test → build → bundle-check → lighthouse → E2E → deploy)
> - GitOps with ArgoCD (self-hosted track)
> - Terraform for infrastructure (Vercel project config or AWS resources)
> - Sentry error monitoring with source maps
> - OpenTelemetry tracing via `instrumentation.ts`
> - Structured logging with `pino` → Axiom/Loki
> - Vercel Analytics + custom Prometheus metrics
> - Feature flags with Edge Config or Redis
> - Preview deployments for every PR
> - Production readiness checklist verified

---
---

## 🏗️ CAPSTONE PROJECT: Full-Stack E-Commerce Platform
> **This is the Phase 2 capstone — it ties everything together.**
>
> Build a production-grade e-commerce platform with Next.js:
>
> - **App Router architecture** with nested layouts (storefront, dashboard, checkout, admin)
> - **Server Components** for all product browsing, catalog, and content pages (minimal client JS)
> - **Feature-based architecture** (Catalog, Cart, Orders, Payments, Users, Admin) with enforced module boundaries
> - **Layered architecture** (Presentation → Application → Domain → Infrastructure) with domain layer having zero framework dependencies
> - **DDD tactical patterns** (Aggregates, Value Objects, Domain Events via in-process event bus, Repositories behind interfaces with Prisma adapters)
> - **Server Actions** for all mutations with `next-safe-action` (validation, auth, typed responses)
> - **CQRS** for product catalog (write to PostgreSQL via Server Actions, read-optimized with Redis cache + full-text search)
> - **Prisma** with PostgreSQL, connection pooling for serverless, database branching with Neon for preview environments
> - **Redis caching** (`@upstash/redis`) with tag-based invalidation
> - **Auth.js** with Google OAuth + Credentials + JWT session with roles and tenant ID
> - **RBAC** (admin, manager, customer) enforced at middleware, Server Component, and Server Action levels
> - **Stripe** integration (Checkout for payments, Webhooks for order fulfillment, Subscription for premium)
> - **Real-time** order tracking via SSE, real-time inventory via `useOptimistic`
> - **Background jobs** with Inngest (order confirmation email, invoice generation, inventory sync)
> - **Internationalization** with `next-intl` (English + Spanish)
> - **Multi-tenancy** (admin manages multiple storefronts via subdomain)
> - **Performance optimized** — Core Web Vitals all green, bundle analyzed, strategic rendering (SSG for catalog, dynamic for dashboard, streaming for search results)
> - **tRPC** for admin dashboard complex data operations
> - **Comprehensive test suite** — Vitest unit tests, Testcontainers integration tests, Playwright E2E for critical flows, visual regression, accessibility tests, Lighthouse CI
> - **Full CI/CD** (GitHub Actions → Vercel preview + production deploy)
> - **Observability** — Sentry error monitoring, OpenTelemetry tracing, structured logging with `pino`, Vercel Analytics
> - **Architecture Decision Records (ADRs)** and **C4 diagrams**
> - **Production readiness** checklist verified
>
> **Why:** Covers full-stack architecture, DDD, rendering strategies, authentication, payment integration, real-time features, performance optimization, testing, DevOps, and observability in one cohesive Next.js project.

---

## ✅ After Completing This Roadmap — You Can:
- Understand React Server Components, streaming, and the rendering paradigm deeply
- Build production-grade Next.js applications with the App Router mastered
- Choose and justify rendering strategies per route (SSG, SSR, ISR, streaming, edge)
- Design layered and feature-based architectures for Next.js
- Model domains using DDD patterns in a full-stack TypeScript context
- Implement type-safe data access with Prisma/Drizzle and caching with Redis
- Build secure applications with Auth.js, OAuth2, JWT, RBAC, ABAC
- Design excellent API layers (Server Actions, Route Handlers, tRPC, GraphQL)
- Integrate payments, file uploads, email, background jobs
- Optimize Core Web Vitals and bundle size systematically
- Write comprehensive tests at every layer (unit, integration, E2E, visual, performance)
- Deploy to Vercel and self-hosted (Docker, Kubernetes) with CI/CD
- Build full observability (logging, metrics, tracing, error monitoring)
- Make and document architectural decisions (ADRs)
- **You are ready for Phase 3: Cloud-Native Mastery & Leadership**

---

## 📋 Quick Reference Summary

```
Phase  0  ➜  React & Web Platform Foundations           🟤
Phase  1  ➜  Next.js Core (App Router, RSC, Caching)    🟢
Phase  2  ➜  Data Access & State Management              🔵
Phase  3  ➜  Authentication & Security                   🟡
Phase  4  ➜  Architecture & Design Patterns              🟠
Phase  5  ➜  Full-Stack Integration & Real-Time          🔴
Phase  6  ➜  Performance & Optimization                  🟣
Phase  7  ➜  Testing at Scale                            ⚫
Phase  8  ➜  DevOps, Observability & Production          🔶
       🏗️  ➜  CAPSTONE: E-Commerce Platform
```

> **⏱ Estimated Timeline:** 6–9 months (with consistent daily practice)
> **💡 Pro Tip:** Next.js makes the simple things trivial and the complex things possible. Your job is knowing which rendering strategy, which caching layer, which data pattern — for THIS specific page, THIS specific component, THIS specific use case. There is no one-size-fits-all.
> **⚡ Key Principle:** Server Components changed everything. Default to the server. Move to the client only when you need interactivity. This isn't just a performance tip — it's an architectural paradigm shift. The less JavaScript you ship, the faster your app, the happier your users.
```

---

## How This Maps to the SE Roadmap Phase 2

| SE Roadmap Phase 2 Module | Adapted For Next.js In |
|---|---|
| 2.1 Architectural Styles (Monolith, Modular, Hexagonal, Clean, CQRS) | Phase 4 (Modules 4.1–4.6) |
| 2.2 Distributed Systems (Caching, Scalability, Resilience, Edge) | Phase 1 (Module 1.4 Caching), Phase 6 (Scalability, Edge), Phase 5 (Background Jobs) |
| 2.3 API Design & Integration (REST, GraphQL, tRPC, Webhooks, Real-Time) | Phase 5 (Modules 5.1–5.4), Phase 1 (Modules 1.5, 1.6) |
| 2.4 Security Architecture (OWASP, OAuth2, JWT, Auth, RBAC, ABAC) | Phase 3 |
| 2.5 DevOps & CI/CD (Pipelines, Deployments, IaC, Observability) | Phase 8 |
| 2.6 Domain-Driven Design (Strategic + Tactical DDD) | Phase 4 (Modules 4.5, 4.6) |
| Phase 2 Project: E-Commerce Platform | Capstone Project |
| **Additional for Next.js Industry** | |
| Rendering Strategies (CSR, SSR, SSG, ISR, Streaming, PPR) | Phase 1 (Module 1.4), Phase 6 (Module 6.1) |
| React Server Components & Server Actions | Phase 0 (Module 0.4), Phase 1 (Modules 1.3, 1.5) |
| Core Web Vitals & Performance | Phase 6 |
| Full-Stack Patterns (Payments, i18n, Multi-Tenancy, Real-Time) | Phase 5 |
| Client State Management (Zustand, TanStack Query, URL State) | Phase 2 (Module 2.3) |

**Every topic from Phase 2 of the SE Roadmap is adapted for the Next.js full-stack industry. Plus Next.js-specific concerns that any production app needs.**