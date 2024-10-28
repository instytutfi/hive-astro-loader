# Contribute to Hive Astro Loader

`@onhive.io/astro-loader` is an open-source project, and we welcome contributions of all kinds.
It is build with TypeScript and bundled with [Bun]((https://bun.sh/).

## Project Structure

- `src/index.ts`: The main entry point for the package.
- `src/adapters/`: Adapters between data from the Hive API and the export types of the package.
- `src/api/`: API callers for the Hive API.
- `src/loaders/`: Hive Loaders implementation. This is what is exposed to the Astro user.
- `src/schema/`: Types and Zod schemas.

## Development

Fork and clone the repository, install dependencies with `bun install` and run dev mode with `bun dev`.
You can write automated tests and run them with `bun test`. Optionally, use `npm link` to locally test your changes.

We've got some tools aiming to improve the development experience:

- [eslint](https://eslint.org/) for linting and code formatting.
- [prettier](https://prettier.io/) for code formatting.
- [husky](https://typicode.github.io/husky/#/) for pre-commit hooks.
- [lint-staged](https://github.com/okonet/lint-staged) for running linters and formatters on staged files.

## Submitting a Pull Request

- When you're ready to submit a pull request, create a new branch with a descriptive name (e.g., `feat/add-new-feature`).
- Make your changes and commit them with clear and descriptive commit messages.
- Write tests to cover your changes if applicable.
- Create a pull request to the `main` branch of the repository.
- Provide a clear and concise description of your changes in the pull request.
- If your changes are related to an open issue, reference it in the pull request.
- Wait for the project maintainers to review and merge your pull request.
