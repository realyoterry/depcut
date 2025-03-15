# depcut

A CLI-based unused dependency remover.

## How It Works
- Checks for `dependencies` or `devDependencies` objects inside `package.json`.
- Checks for global packages by using `npm ls -g`.
- Check JS/TS files and `scripts` object in `package.json` to ensure the dependencies are unused.
- Prompts the user to remove unused dependencies.

## Usage

Start off by running with `npx`:

```sh
npx depcut
```

or manually installing:

```sh
npm install depcut
```

## API Reference

#### `getFiles(dir: string): string[]`
🔹Recursively retrieves JavaScript and TypeScript files from the given directory.

#### `dependencyUsed(dependency: string): boolean`
🔹Checks if a dependency is imported in any project file.

#### `scriptUsed(dependency: string): boolean`
🔹Checks if a dependency is used inside package.json scripts.

#### `getGlobal(): string[]`
🔹Retrieves a list of globally installed npm packages.

#### `remove(dependencies: string[], global?: boolean): void`
🔹Uninstalls the given list of dependencies. If `global` is `true`, removes global packages.

#### `main(): void`
🔹Main function to run all listed functions.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/realyoterry/depcut/blob/main/LICENSE) file for details.
