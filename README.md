<div align="center">
  <img src="static/imgs/logo-removebg.png" alt="White Lace & Promises logo" width="180" />
  <h1>White Lace &amp; Promises</h1>
  <p><em>Where your story becomes something timeless.</em></p>
  <p>A cinematic digital experience for wedding and event styling.</p>
  <p>
    <img src="https://img.shields.io/badge/Svelte-5-FF3E00?style=flat-square&logo=svelte&logoColor=white" alt="Svelte 5" />
    <img src="https://img.shields.io/badge/SvelteKit-2-FF3E00?style=flat-square&logo=svelte&logoColor=white" alt="SvelteKit 2" />
    <img src="https://img.shields.io/badge/TypeScript-6-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript 6" />
    <img src="https://img.shields.io/badge/GSAP-3-88CE02?style=flat-square&logo=gsap&logoColor=black" alt="GSAP 3" />
    <img src="https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white" alt="Tailwind CSS 4" />
    <img src="https://img.shields.io/badge/PostgreSQL-Database-4169E1?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  </p>
  <p><a href="#overview">Overview</a> · <a href="#the-experience">Experience</a> · <a href="#technology-stack">Technology</a> · <a href="#getting-started">Installation</a> · <a href="#development-status">Status</a></p>
</div>

---

## Overview

**White Lace & Promises** is a web application designed to translate the identity of a Brisbane-based wedding and event styling studio into an immersive digital experience. It combines editorial composition, cinematic motion, event photography and thoughtful interactions to communicate the studio's approach to planning, consulting, design and event execution.

Rather than treating the website as a conventional service catalogue, the project approaches the interface as a visual narrative: from the opening brand sequence to the presentation of real celebration imagery and the dedicated event enquiry page.

The technical foundation is built with SvelteKit and TypeScript, with a component-driven interface, GSAP-powered animations and a server-side foundation for future data-driven functionality.

## The Experience

| Feature | Description |
| --- | --- |
| Cinematic entrance | A choreographed brand introduction featuring animated framing lines, logo and typography reveals, metallic gold accents and a circular iris transition. |
| Video-driven hero | Full-screen background footage with staggered text reveals, animated calls to action and scroll-linked parallax. |
| Editorial storytelling | A brand story presented through expressive serif typography, layered photography and carefully composed layouts. |
| Event discovery | Visual presentation of weddings, corporate events, social celebrations and special occasions. |
| Continuous gallery | A looping photographic gallery with lazy-loaded images and scroll-responsive animation speed. |
| Couples showcase | Interactive image selection through thumbnails and an alternative layout for mobile devices. |
| Ambient soundtrack | Optional audio playback with gradual volume transitions, a mute control and visibility-aware behaviour. |
| Custom cursor | A decorative pointer with a fading particle trail, disabled for touch devices and reduced-motion preferences. |
| Event enquiry | A structured form interface covering contact information, event logistics, styling services and additional requirements. |
| Responsive navigation | A scroll-aware navigation bar, mobile menu and direct contact links. |

### Visual identity

The interface draws on the visual language of luxury editorial design. A restrained palette, expressive typography and choreographed motion create a consistent brand experience across the landing page and enquiry interface.

| Design element | Specification |
| --- | --- |
| Primary accent | Gold — `#C9A347` |
| Main background | Near black — `#0A0A0A` |
| Light foreground | Off-white — `#F5F5F0` |
| Enquiry background | Warm ivory — `#F6EED8` |
| Display typography | Cormorant Garamond |
| Body typography | Montserrat |
| Motion language | Staggered reveals, parallax, masking and orchestrated transitions |

The fonts are served locally. Shared design tokens live in [`src/routes/layout.css`](src/routes/layout.css), while component-specific styles encapsulate the visual behaviour of each section.

## Technology Stack

Versions below reflect the dependency ranges declared in [`package.json`](package.json).

| Layer | Technology | Purpose |
| --- | --- | --- |
| Application framework | SvelteKit 2 | File-based routing and server-side application infrastructure |
| UI framework | Svelte 5 | Reactive components and runes-based state management |
| Programming language | TypeScript 6 | Static typing and maintainable application code |
| Styling | Tailwind CSS 4 + CSS | Utility styling, design tokens and custom component layouts |
| Motion | GSAP 3 + ScrollTrigger | Animation timelines, scroll-driven effects and transitions |
| Build tooling | Vite 8 | Development server and production bundling |
| Database | PostgreSQL | Relational persistence foundation |
| Data access | Drizzle ORM / Drizzle Kit + postgres.js | Typed schema, database access and schema management |
| Authentication | Better Auth | Server-side email/password authentication configuration and session handling |
| Local infrastructure | Docker Compose | Local PostgreSQL service |
| Code quality | ESLint, Prettier, svelte-check | Linting, formatting and static diagnostics |

## Architecture

The application separates the public experience, reusable UI components, shared configuration and server-only infrastructure. SvelteKit provides the route and server lifecycle; GSAP and browser APIs handle the motion and interactive presentation.

```mermaid
flowchart TD
    A[Visitor] --> B[SvelteKit application]
    B --> C[Landing page]
    B --> D[Event enquiry page]
    C --> E[Reusable Svelte components]
    D --> E
    E --> F[GSAP and browser APIs]
    E --> G[Local media and design tokens]
    B --> H[Server hook]
    H --> I[Better Auth]
    I --> J[Drizzle ORM]
    J --> K[(PostgreSQL)]
```

The database and authentication layers are configured, but the enquiry form is not currently connected to them. The diagram therefore does not imply an implemented enquiry submission workflow.

### Project structure

```text
While-Lace-Promises/
├── src/
│   ├── lib/
│   │   ├── assets/                 # Application branding and favicon
│   │   ├── components/             # Reusable presentation components
│   │   │   ├── GrandEntrance.svelte
│   │   │   ├── Hero.svelte
│   │   │   ├── Nav.svelte
│   │   │   ├── About.svelte
│   │   │   ├── Explore.svelte
│   │   │   ├── Gallery.svelte
│   │   │   ├── Customers.svelte
│   │   │   ├── Contact.svelte
│   │   │   ├── Footer.svelte
│   │   │   ├── Ornament.svelte
│   │   │   ├── AmbientMusic.svelte
│   │   │   └── CustomCursor.svelte
│   │   ├── server/
│   │   │   ├── auth.ts              # Better Auth configuration
│   │   │   └── db/
│   │   │       ├── index.ts          # PostgreSQL client and ORM
│   │   │       ├── schema.ts         # Database schema
│   │   │       └── auth.schema.ts    # Authentication schema
│   │   └── contact.ts              # Shared contact information
│   ├── routes/
│   │   ├── +layout.svelte           # Shared layout and metadata
│   │   ├── +page.svelte             # Main landing page
│   │   ├── enquiry/
│   │   │   └── +page.svelte         # Event enquiry interface
│   │   └── layout.css               # Global styles and design tokens
│   └── hooks.server.ts              # Server-side session handling
├── static/
│   ├── fonts/                       # Locally hosted typography
│   ├── imgs/                        # Event and brand photography
│   ├── music/                       # Ambient audio
│   └── videos/                      # Cinematic video assets
├── .env.example                     # Environment configuration template
├── compose.yaml                     # Local database service
├── drizzle.config.ts                # Drizzle configuration
├── vite.config.ts                   # Vite and SvelteKit configuration
├── package.json
└── README.md
```

## Getting Started

### Prerequisites

- Node.js 24 (recommended) and npm
- Git
- Docker with Docker Compose, or an accessible PostgreSQL instance

### 1. Clone the repository

```bash
git clone https://github.com/DavidJosueP2/While-Lace-Promises.git
cd While-Lace-Promises
```

### 2. Install dependencies

```bash
npm ci
```

The repository includes a `package-lock.json` file for reproducible dependency installation.

### 3. Configure environment variables

Copy the supplied template into a local `.env` file.

```bash
cp .env.example .env
```

On Windows PowerShell:

```powershell
Copy-Item .env.example .env
```

Configure the following variables:

```dotenv
DATABASE_URL="postgres://root:mysecretpassword@localhost:5432/local"
ORIGIN="http://localhost:5173"
BETTER_AUTH_SECRET="replace-with-a-strong-generated-secret"
```

| Variable | Description |
| --- | --- |
| `DATABASE_URL` | PostgreSQL connection string. The example matches the local Docker Compose service. |
| `ORIGIN` | Public base URL used by Better Auth. Set it to the actual deployment origin in production. |
| `BETTER_AUTH_SECRET` | Private authentication secret. Use a high-entropy generated value of at least 32 characters. |

Generate a suitable secret with Node.js:

```bash
node -e "console.log(require('node:crypto').randomBytes(32).toString('hex'))"
```

Never commit `.env` or production credentials. The supplied database credentials are intended only for local development.

### 4. Start PostgreSQL

```bash
docker compose up -d
```

The local database listens on port `5432` and uses a named Docker volume for persistence. If you use an existing PostgreSQL instance instead, update `DATABASE_URL` accordingly.

### 5. Initialise the database schema

The current Drizzle configuration reads `DATABASE_URL` from the process environment. Make sure the variable is exported before running database commands, even if it is already present in `.env`.

For Bash:

```bash
export DATABASE_URL="postgres://root:mysecretpassword@localhost:5432/local"
npm run db:push
```

For Windows PowerShell:

```powershell
$env:DATABASE_URL = "postgres://root:mysecretpassword@localhost:5432/local"
npm run db:push
```

Use the connection string from your local configuration. `db:push` is appropriate for initialising a local development database; prefer reviewed migrations for production schema changes.

### 6. Start the application

```bash
npm run dev
```

Open **[http://localhost:5173](http://localhost:5173)** in your browser.

To open the browser automatically:

```bash
npm run dev -- --open
```

## Available Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Vite development server. |
| `npm run build` | Create a production build. |
| `npm run preview` | Preview the production build locally. |
| `npm run check` | Run Svelte and TypeScript diagnostics. |
| `npm run check:watch` | Run diagnostics in watch mode. |
| `npm run lint` | Check formatting and linting rules. |
| `npm run format` | Format the project with Prettier. |
| `npm run db:start` | Start the database with Docker Compose in the foreground. |
| `npm run db:push` | Apply the declared schema directly to the database. |
| `npm run db:generate` | Generate SQL migration files. |
| `npm run db:migrate` | Apply generated migrations. |
| `npm run db:studio` | Launch Drizzle Studio. |
| `npm run auth:schema` | Regenerate the Better Auth database schema. |

## Production Build & Deployment

Before deployment, run the available static checks and create a production build:

```bash
npm run check
npm run lint
npm run build
npm run preview
```

The project currently uses `@sveltejs/adapter-auto`. Choose an appropriate [SvelteKit adapter](https://svelte.dev/docs/kit/adapters) if your hosting environment requires an explicit deployment target.

The server environment must provide a reachable PostgreSQL instance, the public application origin and a securely generated authentication secret. The Docker Compose configuration is intended as a local database environment, not as a complete production deployment.

## Development Status

The repository contains an implemented landing page and event enquiry interface, with a foundational server-side configuration.

| Area | Current implementation |
| --- | --- |
| Landing page (`/`) | Implemented with branded sections and interactive animations |
| Enquiry page (`/enquiry`) | Implemented form interface with native required-field validation |
| Enquiry processing | Not yet implemented; submission is currently prevented in the browser |
| Authentication | Better Auth configuration and server hook present; dedicated sign-in/sign-up screens are not included |
| Data persistence | PostgreSQL and Drizzle configured; enquiry-specific persistence is not implemented |
| Additional pages | Navigation targets such as `/about`, `/events`, `/gallery` and individual event pages are referenced but not yet defined as routes |

### Future improvements

- Complete the standalone service and gallery pages.
- Connect the enquiry form to server-side validation, persistence and a delivery or notification workflow.
- Replace placeholder contact values with verified business information before release.
- Extend reduced-motion support and conduct accessibility, performance and cross-browser testing.
- Verify media usage rights and optimise video, audio and image delivery for production.

## Author

Developed by [David Barragán](https://github.com/DavidJosueP2).

Project repository: [DavidJosueP2/While-Lace-Promises](https://github.com/DavidJosueP2/While-Lace-Promises).

## Licensing & Assets

No project-wide license is currently included in the repository. Cormorant Garamond and Montserrat include their own license notices under `static/fonts/`. Brand assets, event photographs, videos and audio may be subject to separate ownership and usage conditions. Confirm permission before redistributing or reusing them.

---

<div align="center">
  <strong>White Lace &amp; Promises</strong><br />
  <em>Thoughtfully designed. Beautifully experienced.</em>
</div>
