---
name: react-coding-preferences
description: Personal React and TypeScript preferences for client-rendered single-page apps. Use alongside vercel-react-best-practices and library skills when writing, refactoring, or reviewing React or TypeScript code.
---

# React coding preferences

Apply these preferences as an overlay to `vercel-react-best-practices`, `vercel-composition-patterns` and the library skills. Where they conflict, this overlay wins. A repository's own conventions, such as its frontend README or `AGENTS.md`, win over both.

## Stack mapping

The target is a client-rendered single-page app: Vite, React 19 with React Compiler, TanStack Router and TanStack Query. Read Vercel's rules through this table:

| Vercel rules | Here |
| --- | --- |
| `server-*`, `async-api-routes`, `rendering-hydration-*` | Out of scope: nothing renders on a server. |
| `client-swr-dedup` | TanStack Query deduplicates and caches requests. Load data through query options in route loaders, as the `router-query` skill describes. |
| `rerender-memo`, `rerender-memo-with-default-value`, `rerender-simple-expression-in-memo`, `rendering-hoist-jsx` | React Compiler memoises. Write plain components, values and handlers. Add `memo`, `useMemo` or `useCallback` only where the compiler reports that it skipped a component, or a profile shows a hot path. |
| `advanced-event-handler-refs`, `advanced-use-latest` | When an effect must read the latest props or handlers without re-running, wrap that logic in `useEffectEvent`. Its functions have no stable identity, so they stay out of effect dependencies. |
| `bundle-dynamic-imports` (`next/dynamic`) | Split code by route with TanStack Router's lazy route files, and with `React.lazy` for a heavy component inside a route. |
| `client-localstorage-schema`, `js-cache-storage` | Hold personal data in memory only: the query cache runs without a persister and is cleared on sign-out. Browser storage (`localStorage`, `sessionStorage`, IndexedDB) holds none of it. |

## TypeScript

Before writing or reviewing TypeScript, read `typescript-best-practices` and the two principles it builds on, `principle-type-system-discipline` and `principle-boundary-discipline`. They also mention other principle skills that are not installed; skip those references.

When a project generates its API client from a schema, that client is the boundary: trust its types inside the app, and add a runtime schema only where data enters from anywhere else.
