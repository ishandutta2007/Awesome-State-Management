# Awesome-State-Management

# Awesome-State-Management

## Top State Management Tools Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Predictable State Transitions, Atomic Reactivity & Framework-Native Integration*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **State Management**. These tools help applications manage shared state across components — from centralized Redux stores with strict unidirectional data flow to atomic primitives and reactive proxies that update UI granularly. The choice shapes bundle size, re-render behavior, and developer experience.

**Examples** include Redux Toolkit, MobX, Zustand, Recoil, Jotai, XState, Rematch, Pinia, Vuex, and NgRx (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, framework-native integration, and transparent reactivity models — ideal for frontend teams prioritizing predictable state transitions, minimal re-renders, and long-term maintainability.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **Redux DevTools (Browser Extension)** — While Redux is open-source, the browser extension ecosystem around it is maintained as a separate distribution. The core debugging capability (time-travel, action replay, state inspection) is free and open-source, but commercial integration with platforms like Sentry and LogRocket adds hosted error tracking and session replay alongside state debugging.

- **MobX-State-Tree Commercial Support** — MST is MIT-licensed, but commercial support and consulting are available through the maintainers for enterprises needing guaranteed response times and architecture guidance.

- **NgRx Enterprise Support** — NgRx is Apache 2.0 licensed, with enterprise support available through Angular consulting partners and Nx (formerly Nrwl) for large-scale Angular applications.

- **XState Commercial (Stately)** — XState core is MIT-licensed, but **Stately** provides a managed visual editor, deployment platform, and AI-assisted state machine generation as a commercial service.

## Open-Source GitHub Projects

- **[Redux Toolkit](https://github.com/reduxjs/redux-toolkit)**  
  **The standard way to write Redux logic** — 10,900+ GitHub stars, MIT licensed. **RTK 2.0** modernized the package with **true ESM publishing** (primary artifact `dist/redux-toolkit.modern.mjs`), ES2020 syntax targeting, and dropped UMD builds in favor of `redux-toolkit.browser.mjs` for CDN usage. **`createSlice`** auto-generates action creators and reducers, **`configureStore`** sets up sensible defaults including thunk and DevTools, and **RTK Query** provides data fetching and caching. A 2026 benchmark found that Redux Toolkit with `React.memo` produces **zero surplus re-renders** when unrelated state changes — equivalent to Zustand, Jotai, MobX, and Valtio — while adding **+10 KB** bundle overhead. **The convention-rich choice for large teams** needing DevTools workflows and a mature ecosystem.

- **[Zustand](https://github.com/pmndrs/zustand)**  
  **The minimal API surface champion** — 48,000+ GitHub stars, MIT licensed. **v5** requires React 18+, drops default exports, and makes `use-sync-external-store` a peer dependency for `createWithEqualityFn`. **Selector outputs must be stable references** — v5 matches React's default behavior, so returning new references causes infinite loops unless wrapped in `useShallow`. **+2 KB bundle overhead** — the smallest of the benchmarked libraries. Benchmarks confirm **zero surplus re-renders** with `React.memo`. **The default choice for teams wanting Redux-like predictability without the ceremony.**

- **[Jotai](https://github.com/pmndrs/jotai)**  
  **Atomic state management for React** — 19,000+ GitHub stars, MIT licensed. **Primitive and derived atoms** compose naturally, with **atom families** enabling per-row subscriptions that reduce re-renders under high-frequency updates. **+5 KB bundle overhead**. Benchmarks show **zero surplus re-renders** with `React.memo`. **The migration target for Recoil users** — multiple projects (Kubetail, AWS Graph Explorer) have migrated from the archived Recoil to Jotai for React 19 compatibility. **Best for complex derived state and fine-grained reactivity.**

- **[MobX](https://github.com/mobxjs/mobx)**  
  **Simple, scalable state management through transparent reactive programming** — 28,000+ GitHub stars, MIT licensed. **Observable state, computed values, and reactions** automatically track dependencies and update UI granularly. Benchmarks confirm **zero surplus re-renders** with `React.memo`. **Critical compatibility note**: the **React Compiler silently over-memoizes proxy-based libraries (MobX, Valtio), suppressing required re-renders** — an incompatibility invisible to production monitoring. **Best for teams wanting reactive state without explicit selectors.**

- **[XState](https://github.com/statelyai/xstate)**  
  **State machines and statecharts for complex application logic** — 27,000+ GitHub stars, MIT licensed. **v5** renamed `interpret()` to `createActor()`, requires **event objects instead of strings**, and renamed `schema` to `types`. The **`setup()` API** provides better type safety and organization. **Final state `output`** replaces `data`, and **`reenter`** replaces `external`. **Best for workflows where state transitions must be explicit, testable, and visualizable.**

- **[Pinia](https://github.com/vuejs/pinia)**  
  **The official Vue store** — 13,000+ GitHub stars, MIT licensed. **Vuex is maintenance-only and should not be reached for in new code**. **v3 dropped Vue 2** (Vue 3 only) and removed the `defineStore({ id })` object syntax in favor of `defineStore('counter', ...)`. **v4 (July 2026)** is ESM-only, requires Vue 3.5.11+ and TypeScript 5.6+, and needs `@vue/devtools-api` 8.x installed separately. **Setup stores** use Composition API patterns (`ref`, `computed`) with full TypeScript inference. **No mutations** — actions can contain synchronous and asynchronous logic directly. **The clear default for new Vue 3 projects.**

- **[NgRx](https://github.com/ngrx/platform)**  
  **Reactive state management for Angular** — 8,000+ GitHub stars, MIT licensed. Built on **RxJS** with **Effects** for side effects, **Selectors** for derived state, and **Store** for centralized state. **Deeply integrated with Angular's dependency injection and change detection**. **The framework-native choice for Angular enterprise applications** — the steepest learning curve but the strongest alignment with Angular's architecture.

- **[Rematch](https://github.com/rematch/rematch)**  
  **Redux framework with reduced boilerplate** — 8,400+ GitHub stars, MIT licensed, TypeScript-based. **No action types or action creators** — reducers dispatch actions directly. **Built-in effects** for async logic without thunk middleware. **The middle ground between Redux's power and Zustand's simplicity** for teams wanting Redux patterns with less ceremony.

- **[Vuex](https://github.com/vuejs/vuex)**  
  **The legacy Vue state management library** — 28,000+ GitHub stars, MIT licensed. **Maintenance-only** — Vue's official documentation directs new projects to Pinia. **Mutations, modules, and mapState/mapActions** define the Vuex pattern. **Still relevant for existing Vue 2/3 codebases** but not for new development.

- **[Valtio](https://github.com/pmndrs/valtio)**  
  **Proxy-based state management** — 8,000+ GitHub stars, MIT licensed. **Mutable state updates** trigger re-renders through proxy tracking. Benchmarks confirm **zero surplus re-renders** with `React.memo`. **Same React Compiler incompatibility as MobX** — over-memoization suppresses required re-renders.

- **[Recoil](https://github.com/facebookexperimental/Recoil)**  
  **Archived React state management from Meta** — 19,000+ GitHub stars. **No longer maintained** and **blocking React 19 upgrades**. **Migration targets**: Jotai (most API-aligned) or Zustand. **Do not start new projects on Recoil.**

### Additional Strong Open-Source Options

- **Redux (Core)** — The original Redux library. RTK is the recommended way to write Redux logic, but core Redux remains MIT licensed and maintained.
- **Akita** — State management for Angular with entity stores and query patterns.
- **Effector** — Reactive state manager with no React dependencies and strong TypeScript support.
- **Nanostores** — Tiny state manager (less than 1 KB) for React, Vue, Svelte, Solid, and vanilla JS.
- **Signals (TC39)** — Emerging web standard for reactive state with framework-agnostic semantics.

**Frameworks for building custom systems**: Combine **Redux Toolkit** for large-team conventions and DevTools workflows, **Zustand** for minimal API surface with predictable selectors, **Jotai** for atomic derived state and fine-grained subscriptions, **MobX** for transparent reactive programming (disable React Compiler for store consumers), **XState** for explicit state machines in complex workflows, and **Pinia** or **NgRx** for framework-native Vue and Angular integration — to build a state architecture tailored to your framework, team size, and performance requirements.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- State management libraries differ significantly in re-render behavior, bundle overhead, and framework alignment. **A 2026 controlled benchmark found that selector-based libraries (Redux Toolkit, Zustand, Jotai, MobX, Valtio) produce zero surplus re-renders when combined with `React.memo`** — equivalent performance despite different internals. **The React Compiler silently over-memoizes proxy-based libraries (MobX, Valtio), suppressing required re-renders** — this incompatibility is invisible to production monitoring and should be verified before adopting either library with the compiler. **Zustand v5 requires stable selector outputs** — returning new references causes infinite loops unless wrapped in `useShallow`. **Pinia v4 is ESM-only** and requires Vue 3.5.11+, TypeScript 5.6+, and `@vue/devtools-api` 8.x. **Recoil is archived** and blocks React 19 upgrades — migrate to Jotai or Zustand. **Not every application needs a state management library** — Vue 3's `ref` and `provide/inject` handle many use cases, and React Context is sufficient for infrequent, global updates.
- Self-hosted open-source solutions require proper bundle analysis, re-render profiling, and migration planning for existing state architectures.

---

**Made for frontend developers, React engineers, Vue and Angular teams, and developers building predictable application state architectures.**  
Let's make state management more open, performant, and framework-native.
