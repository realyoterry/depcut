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

### `getFiles(dir: string): string[]`
> Recursively retrieves JavaScript and TypeScript files from the given directory.
- **Arguments:**
  - `dir` → Type: `string` → The directory path to scan.
- **Returns:** An array of file paths that match the supported extensions.
- **Type:** Utility function

Example usage:
```javascript
const files = getFiles('./src');
console.log(files); // List of JS/TS files in the project
```

---

### `dependencyUsed(dependency: string): boolean`
> Checks if a dependency is imported in any project file.
- **Arguments:**
  - `dependency` → Type: `string` → The dependency name to check.
- **Returns:** `true` if the dependency is found in the code, otherwise `false`.
- **Type:** Utility function

Example usage:
```javascript
if (dependencyUsed('lodash')) {
  console.log('lodash is used in the project');
}
```

---

### `scriptUsed(dependency: string): boolean`
> Checks if a dependency is used inside `package.json` scripts.
- **Arguments:**
  - `dependency` → Type: `string` → The dependency name to check.
- **Returns:** `true` if the dependency is found in scripts, otherwise `false`.
- **Type:** Utility function

Example usage:
```javascript
if (scriptUsed('nodemon')) {
  console.log('nodemon is used in scripts');
}
```

---

### `getGlobal(): string[]`
> Retrieves a list of globally installed npm packages.
- **Arguments:** `None`
- **Returns:** An array of globally installed package names.
- **Type:** Utility function

Example usage:
```javascript
const globalPackages = getGlobal();
console.log(globalPackages); // List of globally installed packages
```

---

### `remove(dependencies: string[], global?: boolean): void`
> Uninstalls the given list of dependencies. If `global` is `true`, removes global packages.
- **Arguments:**
  - `dependencies` → Type: `string[]` → An array of dependency names to remove.
  - `global` (optional) → Type: `boolean` → Set to `true` to remove global packages.
- **Returns:** `void`
- **Type:** CLI function

Example usage:
```javascript
remove(['lodash', 'chalk']); // Remove dependencies locally
remove(['typescript'], true); // Remove a global dependency
```

---

### `main(): void`
> Runs the main program, scans dependencies, and prompts the user for removal.
- **Arguments:** `None`
- **Returns:** `void`
- **Type:** Entry function

Example usage:
```javascript
main(); // Starts the dependency cleanup process
```

---

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/realyoterry/depcut/blob/main/LICENSE) file for details.
