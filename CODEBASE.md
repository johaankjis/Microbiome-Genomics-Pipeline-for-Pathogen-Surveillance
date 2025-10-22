# Microbiome Genomics Pipeline Codebase Overview

## Project Summary
This repository implements a Next.js 15 dashboard for orchestrating and monitoring a microbiome genomics pipeline used in pathogen surveillance. A shared root layout wires up site-wide fonts, analytics, and styling tokens, while individual route groups deliver dedicated workflow screens for dashboards, data management, pipeline execution, and analysis results.【F:app/layout.tsx†L1-L28】【F:app/page.tsx†L17-L194】【F:app/data/page.tsx†L28-L200】【F:app/pipeline/page.tsx†L16-L200】【F:app/results/page.tsx†L18-L200】

## Tech Stack at a Glance
- **Framework:** Next.js 15 with the App Router and React 19.【F:package.json†L6-L55】
- **Styling:** Tailwind CSS 4 with custom OKLCH design tokens and animation utilities declared in the global stylesheet.【F:app/globals.css†L1-L127】
- **UI Kit:** A local shadcn-inspired component library backed by Radix UI primitives (buttons, cards, forms, overlays, navigation).【F:package.json†L11-L61】【F:components/ui/card.tsx†L1-L92】
- **Data Viz:** Recharts-based charts power taxonomic distributions, quality metrics, pathogen detection, and temporal trends.【F:components/taxonomy-chart.tsx†L1-L40】【F:components/quality-metrics-chart.tsx†L1-L43】【F:components/pathogen-detection-chart.tsx†L1-L101】【F:components/abundance-timeline.tsx†L1-L78】
- **Forms & Validation:** React Hook Form, Zod, and Radix inputs support configurable pipeline steps and dataset management tools.【F:package.json†L11-L61】【F:app/pipeline/page.tsx†L120-L200】【F:app/data/page.tsx†L97-L199】

## Directory Guide
- **`app/`** – App Router entry points for the dashboard, data, pipeline, and results flows. Each page composes the shared sidebar navigation and header shell around route-specific content blocks.【F:app/page.tsx†L17-L194】【F:app/data/page.tsx†L80-L199】【F:app/pipeline/page.tsx†L103-L200】【F:app/results/page.tsx†L21-L200】
- **`components/`** – Feature-specific building blocks such as the sidebar navigation, global header, diversity metrics, pathogen detection listings, and other data visualizations.【F:components/sidebar-nav.tsx†L1-L123】【F:components/header.tsx†L1-L46】【F:components/diversity-metrics.tsx†L1-L66】【F:components/pathogen-detection-chart.tsx†L1-L101】
- **`components/ui/`** – Reusable primitives (cards, buttons, tables, dialogs, etc.) that wrap Radix UI behaviors with the project’s design tokens.【F:components/ui/card.tsx†L1-L92】
- **`hooks/`** – Client hooks for toast notifications and responsive breakpoints, used to deliver interactive feedback and mobile-aware layouts.【F:hooks/use-toast.ts†L1-L191】【F:hooks/use-mobile.ts†L1-L19】
- **`lib/`** – Utility helpers such as the `cn` className merger shared across UI components.【F:lib/utils.ts†L1-L6】
- **`styles/`** & **`app/globals.css`** – Tailwind setup plus theme variables that define the dashboard’s scientific look in light and dark modes.【F:app/globals.css†L1-L127】

## Feature Highlights
### Dashboard Insight Hub (`/`)
The landing dashboard surfaces KPI cards, recent pipeline runs, tool availability, and system notifications within the shared chrome, offering a bird’s-eye view of surveillance operations.【F:app/page.tsx†L30-L188】

### Dataset Management (`/data`)
Researchers can upload new sequencing data, filter and search existing datasets, and review ingest status through tables augmented with contextual actions.【F:app/data/page.tsx†L92-L199】

### Pipeline Execution Center (`/pipeline`)
Users configure pipeline runs by selecting datasets, toggling bioinformatics tools (FastQC, Bowtie2, GATK, Kraken2, BLAST), adjusting parameters, and tracking live progress across tabs for configuration, monitoring, and history.【F:app/pipeline/page.tsx†L115-L200】

### Analysis Results (`/results`)
Completed runs expose exportable summaries, high-risk pathogen alerts, species diversity metrics, and interactive Recharts visualizations for taxonomy, abundance, and detection trends.【F:app/results/page.tsx†L33-L195】【F:components/pathogen-detection-chart.tsx†L45-L101】【F:components/diversity-metrics.tsx†L37-L66】【F:components/abundance-timeline.tsx†L15-L78】

## Styling & Layout
- Global CSS establishes OKLCH color palettes, sidebar-specific tokens, and responsive radii, ensuring scientific branding across light and dark themes.【F:app/globals.css†L6-L127】
- The sidebar navigation enumerates primary routes and auxiliary settings/help links, while displaying live system status messaging.【F:components/sidebar-nav.tsx†L8-L123】
- A persistent header provides search, notifications, and account controls for authenticated operators.【F:components/header.tsx†L1-L46】

## State & Interaction Utilities
- Toast utilities centralize enqueue/dismiss logic with an internal reducer to coordinate ephemeral notifications across the app.【F:hooks/use-toast.ts†L8-L191】
- The `useIsMobile` hook watches viewport width to adapt responsive layouts where needed.【F:hooks/use-mobile.ts†L3-L19】

## Development Workflow
Package scripts mirror the standard Next.js toolchain for local development, production builds, linting, and deployment start-up.【F:package.json†L5-L10】 Install dependencies with your preferred package manager (pnpm, npm, or yarn) before running `next dev` for iterative work or `next build && next start` to preview production output.【F:package.json†L5-L10】

