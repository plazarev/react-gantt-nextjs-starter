# DHTMLX React Gantt with Next.js (App Router)
 
A quick-start demo of **DHTMLX React Gantt** integrated into a **Next.js** application using the **App Router**. Built with React 19, TypeScript, and Tailwind CSS — shows the correct `'use client'` pattern for mounting a browser-only Gantt chart inside a server-rendered Next.js page.
 
A companion tutorial walks through the integration step by step: [Next.js integration guide](https://docs.dhtmlx.com/gantt/integrations/react/nextjs/)

## What is DHTMLX React Gantt with Next.js Starter
 
This starter shows how to embed DHTMLX React Gantt inside a Next.js App Router application. DHTMLX Gantt is a browser-only component: it accesses the DOM on initialization and cannot run during server-side rendering. The demo solves this by placing the Gantt chart in a dedicated Client Component marked with `'use client'`, which tells Next.js to render it only on the client while the page itself remains a Server Component.
 
The Gantt component receives tasks, links, and configuration as props from the page, keeping the component stateless and reusable. Data is loaded from a static seed file with tasks, task dependencies (links), and time scale configuration, giving you a working project timeline with day, month, and year zoom levels and drag-and-drop task management out of the box.
 
## When to Use
 
- Use this demo when building a Next.js App Router application that needs a Gantt chart for project planning or task scheduling.
- Use this when you need a working reference for the `'use client'` pattern that correctly isolates DHTMLX Gantt from Next.js server-side rendering.
- Use this as a minimal starting point before adding state management (Zustand), a real data source, or API routes for task persistence.
- Use this when you want to understand the props-driven Gantt component pattern before extending it with callbacks and mutations.

## Quick Start
 
```bash
git clone https://github.com/DHTMLX/react-gantt-nextjs-starter
cd react-gantt-nextjs-starter
npm install
npm run dev
```
 
Open [http://localhost:3000](http://localhost:3000) in your browser.
 
### Production Build
 
```bash
npm run build
npm start
```
 
## Architecture
 
```
├── app/
│   ├── page.tsx              # Server Component — loads seed data, renders Gantt
│   ├── layout.tsx            # Root layout with global styles
│   └── globals.css           # Global styles and Tailwind configuration
├── components/
│   └── Gantt/
│       └── Gantt.tsx         # 'use client' component wrapping ReactGantt
├── data/
│   └── demoData.ts           # Seed tasks, links, and zoom configuration
├── next.config.ts            # Next.js configuration
└── postcss.config.mjs        # PostCSS / Tailwind configuration
```
 
`page.tsx` is a Server Component that loads task and link data and passes it as props to `Gantt.tsx`. `Gantt.tsx` is a Client Component that handles all browser-specific Gantt initialization. This split keeps the server component clean while ensuring Gantt only runs in the browser.
 
## Key Patterns
 
- **`'use client'` boundary** — `Gantt.tsx` is marked as a Client Component, which is the correct Next.js App Router mechanism for keeping browser-only libraries out of SSR. Without this directive, Next.js will attempt to render Gantt on the server and throw DOM-related errors.
- **Props-driven Gantt component** — tasks, links, and zoom configuration are all passed as props from the Server Component page. The Gantt component holds no internal state, making it straightforward to replace the seed data with a real data fetch.
- **Tasks and links as separate props** — unlike a simple event list, DHTMLX Gantt requires both a tasks array and a links array (dependency arrows between tasks). The seed data in `demoData.ts` provides both, showing the expected data shape.
- **Time scale configuration in seed data** — zoom levels (day, month, year) are defined in `demoData.ts` alongside the tasks and links, so all initial Gantt configuration is co-located and easy to find.

## Features
 
| Feature | Details |
|---|---|
| Next.js App Router | Uses the current App Router architecture, not Pages Router |
| SSR-safe integration | `'use client'` directive isolates Gantt from server rendering |
| Tasks and links | Seed data includes both tasks and dependency links |
| Time scales | Day, month, and year zoom levels configured from seed data |
| Drag-and-drop | Task rescheduling and reordering |
| Props-driven config | Tasks, links, and zoom passed as props from the Server Component |
| TypeScript | Full type coverage for tasks, links, and Gantt config |
| Tailwind CSS | Utility-first styling via PostCSS |
| React 19 | Built on the latest React release |
| Next.js 16 | Uses current Next.js App Router architecture |
 
## Production Notes
 
This demo is a starter, not a production-ready application. Before going to production:
 
- **Replace static data** — `demoData.ts` is a seed file. Load real tasks and links in the page's Server Component using `fetch` or an ORM query, then pass them as props to the Gantt component. Consider adding Next.js API routes for task CRUD operations.
- **Add state management** — the demo has no mutation handling. See the [Zustand starter](https://github.com/DHTMLX/react-gantt-zustand-starter) for a pattern that routes Gantt mutations through a centralized store, or use the Zustand + TanStack Query progression for full server-backed state.
- **Add error boundaries and loading states** — wrap the Gantt Client Component in a `<Suspense>` boundary with a loading fallback for data fetching scenarios.
- **Gantt license** — DHTMLX React Gantt requires a valid commercial license for production use (see License section below).

## Related Resources
 
- [Next.js integration tutorial (official guide)](https://dhtmlx.com/blog/why-use-dhtmlx-gantt-for-react-with-next-js-in-project-management-apps/)
- [DHTMLX React Gantt product page](https://dhtmlx.com/docs/products/dhtmlxGantt-for-React/)
- [DHTMLX Gantt product page](https://dhtmlx.com/docs/products/dhtmlxGantt/)
- [DHTMLX Gantt documentation](https://docs.dhtmlx.com/gantt/)
- [React Gantt integration guide](https://docs.dhtmlx.com/gantt/web__react.html)
- [Gantt + Zustand starter (state management)](https://github.com/DHTMLX/react-gantt-zustand-starter)
- [Gantt + TanStack Query starter (server-backed state)](https://github.com/dhtmlx/react-gantt-tanstack-query-starter)
- [Next.js App Router documentation](https://nextjs.org/docs/app)
- [Community forum](https://forum.dhtmlx.com/)
- [Report an issue](https://github.com/DHTMLX/react-gantt-nextjs-starter/issues)

## License
 
The source code in this repository is released under the **MIT License**.
 
**Commercial License**
Required for proprietary or commercial applications. Includes access to PRO features, dedicated technical support, and long-term maintenance.
[Learn more →](https://dhtmlx.com/docs/products/dhtmlxGantt-for-React/#licensing)
 
**Try before you buy**
A free evaluation of DHTMLX React Gantt is available — no credit card required.
[Start your evaluation →](https://dhtmlx.com/docs/products/dhtmlxGantt-for-React/download.shtml)
