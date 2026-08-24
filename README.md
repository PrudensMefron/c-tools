# c-tools

Small Bash tooling for bootstrapping C and C++ projects with the author's preferred Allman++ formatting setup.

The `c-setup` CLI can create either:

- a traditional C/C++ project; or
- a desktop WebView project using [Saucer](https://github.com/saucer/saucer) with a Vite frontend.

## Traditional projects

Interactive setup supports:

- Meson + Ninja
- CMake + Ninja
- Zig
- Makefile
- optional Git initialization
- Allman++ `.clang-format`
- `.clang-tidy`
- local Zed settings

When Zig is selected, the generated `build.zig` provides:

```bash
zig build
zig build run
zig build clean
zig build release
zig build release-run
zig build release-clean
```

The Zig template targets Zig 0.16.x and compiles C/C++ directly through the Zig toolchain.

## Desktop WebView with Saucer

The Saucer template uses C++23 and asks for one of these build setups:

- CMake + Ninja
- Zig + CMake + Ninja

It also asks which frontend package manager/runtime should be used:

- Bun
- pnpm
- npm
- Yarn

The setup creates `frontend/tools/dev.mjs`, but deliberately leaves the Vite framework choice to you. After setup, initialize the Vite project inside `frontend/` using the selected package manager. Because `frontend/tools/` already exists, create-vite may warn that the directory is not empty; keep/ignore the existing files instead of deleting `tools/`.

For Zig + CMake + Ninja, the generated build exposes:

```bash
# Build frontend, embed it, compile a Debug native build
zig build

# Start Vite and run the Debug native application
zig build dev

# Embedded Debug build + run
zig build run

# Optimized embedded build
zig build release

# Optimized embedded build + run
zig build release-run

# Remove only release output
zig build release-clean

# Remove dev/debug/release output and frontend dist
zig build clean

# Also remove node_modules, .zig-cache and other reconstructible caches
zig build clean-all
```

## Installation

Requirements for the base script:

- Git
- Bash

Clone the repository and make the script executable:

```bash
git clone https://github.com/PrudensMefron/c-tools.git c-tools
cd c-tools
chmod +x c-setup
```

Create a symlink somewhere on your `PATH`, for example:

```bash
sudo ln -s "$(pwd)/c-setup" /usr/bin/c-setup
```

Then create a project with:

```bash
c-setup my-project-name
```

Additional tools are required according to the selected project template, such as Zig, CMake, Ninja, Saucer's Linux development dependencies, and the selected JavaScript package manager/runtime.

## Uninstallation

Remove the symlink:

```bash
sudo unlink /usr/bin/c-setup
```

Then delete the cloned repository if desired.

## Contributions

Issues and pull requests are welcome.
