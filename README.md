# Microbiome Genomics Pipeline for Pathogen Surveillance

A Next.js 15 dashboard that simulates orchestrating and monitoring a microbiome genomics pipeline for pathogen surveillance labs. The application combines configurable pipeline controls, dataset management tools, and analysis dashboards to help researchers track sequencing runs from ingestion through actionable insights.

## Features
- **Operational dashboard** with KPI cards, recent pipeline run summaries, and tool status highlights for a quick health check of ongoing sequencing operations.【F:app/page.tsx†L17-L188】
- **Dataset management workspace** that lists uploaded sequencing cohorts, supports filtering and inline actions, and surfaces ingest metadata for each dataset.【F:app/data/page.tsx†L28-L199】
- **Pipeline execution center** where analysts toggle bioinformatics tools (FastQC, Bowtie2, GATK, Kraken2, BLAST), tune parameters, and follow live progress across configuration, monitoring, and history tabs.【F:app/pipeline/page.tsx†L16-L200】
- **Analysis results hub** featuring pathogen alerts, species diversity summaries, and interactive Recharts visualizations for taxonomy, abundance, and detection trends.【F:app/results/page.tsx†L18-L200】【F:components/pathogen-detection-chart.tsx†L1-L101】【F:components/abundance-timeline.tsx†L1-L78】
- **Reusable UI primitives** built atop Radix UI, offering cards, dialogs, tables, and toast notifications styled with Tailwind CSS 4 design tokens.【F:components/ui/card.tsx†L1-L92】【F:hooks/use-toast.ts†L8-L191】【F:app/globals.css†L1-L127】

## Project Structure
```
.
├── app/                # App Router pages, layouts, and route groups
├── components/         # Feature components plus shadcn-inspired UI primitives
├── hooks/              # Shared hooks for toast state and responsive helpers
├── lib/                # Utility helpers (e.g., className combiner)
├── public/             # Static assets
├── styles/             # Tailwind configuration entry points
└── CODEBASE.md         # Deep-dive architectural guide
```

## Tech Stack
- **Framework:** Next.js 15 (App Router) with React 19 and TypeScript.【F:package.json†L1-L59】
- **Styling:** Tailwind CSS 4, custom OKLCH design tokens, and Radix UI primitives.【F:app/globals.css†L1-L127】【F:components/ui/card.tsx†L1-L92】
- **Data Visualization:** Recharts charts for taxonomy distributions, quality metrics, and pathogen detection timelines.【F:components/taxonomy-chart.tsx†L1-L40】【F:components/quality-metrics-chart.tsx†L1-L43】【F:components/pathogen-detection-chart.tsx†L1-L101】【F:components/abundance-timeline.tsx†L1-L78】
- **Forms & Validation:** React Hook Form with Zod schemas for configurable pipeline steps and data entry flows.【F:app/pipeline/page.tsx†L120-L200】【F:app/data/page.tsx†L97-L199】

## Getting Started
1. **Install dependencies** using your preferred package manager (examples shown for pnpm):
   ```bash
   pnpm install
   ```
2. **Run the development server:**
   ```bash
   pnpm dev
   ```
3. **Visit** `http://localhost:3000` to explore the dashboard.

Available scripts align with the standard Next.js toolchain:

| Command      | Description                |
| ------------ | -------------------------- |
| `pnpm dev`   | Start the development app. |
| `pnpm build` | Generate an optimized build. |
| `pnpm start` | Serve the production build. |
| `pnpm lint`  | Run ESLint checks. |

## Additional Resources
- Consult [`CODEBASE.md`](./CODEBASE.md) for a deeper architectural walkthrough and feature-by-feature overview.【F:CODEBASE.md†L1-L56】

