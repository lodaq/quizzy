# Quizzy

![Status: Under development](https://img.shields.io/badge/status-under_development-orange)

A browser-local quiz builder and player. Create quizzes, practice with multiple-choice and true-or-false questions, and review scores and previous attempts.

## Current implementation

- Create, edit, duplicate, and delete quizzes.
- Browse sample and saved quizzes by category or search.
- Play quizzes, navigate questions, and review results and explanations.
- Store quizzes and attempt history in the current browser's `localStorage`.

The current app uses Next.js 13, React 18, TypeScript, Tailwind CSS, Radix/shadcn components, React Hook Form, and Zod. It has no implemented PostgreSQL/Prisma backend, account authentication, or remote quiz synchronization.

## Data and sharing limits

Quiz data belongs to this browser profile. Clearing site data removes it, and another device or browser does not receive it. A URL containing a quiz ID does not transfer a browser-local quiz to someone else. Public-library labels and sharing controls should be treated as prototype UI until remote persistence and access controls are implemented.

This project is under active development and uses an older framework version. Review dependencies and security before deploying it publicly.

## Run locally

```sh
git clone https://github.com/lodaq/quizzy.git
cd quizzy
npm ci
npm run dev
```

Use a Node.js version compatible with the dependencies in `package-lock.json`. Open http://localhost:3000. No database or API credentials are required by the current storage implementation.

## Development

```sh
npm run lint
npx tsc --noEmit
npm run build
```

No automated test script is currently defined.

- `app/`: home, browse, create, edit, play, results, and My Quizzes routes.
- `lib/storage.ts`: sample quizzes and browser-local persistence.
- `types/quiz.ts`: quiz, question, option, and attempt contracts.
- `components/`: quiz forms, player, cards, and shared interface controls.

The original backend, multiplayer, and account ideas are future work, not guarantees of the current implementation.

## Known verification blockers

As checked on 2026-11-06, type checking reports nullable question time limits passed to form inputs in the create and edit pages. The production build also rejects client pages that export `generateStaticParams`, starting with the results route. These existing issues must be resolved before claiming a working static export.
