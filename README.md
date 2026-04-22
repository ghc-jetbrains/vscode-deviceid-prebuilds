# vscode-deviceid-prebuilds

Prebuilt native addon binaries for [@vscode/deviceid](https://github.com/microsoft/vscode-deviceid) on Windows x64 and ARM64.

## Building Prebuilds

### How to Build

1. Go to the **Actions** tab
2. Select **Build DeviceId Prebuilds** workflow
3. Click **Run workflow**
4. Enter the parameters:
   - `version`: The @vscode/deviceid version to build (e.g., `0.1.4`)
   - `node_version`: Node.js version to use (must be >= 22, e.g., `22`)
5. Click **Run workflow**

### What Happens

The workflow will:

- Install the specified @vscode/deviceid version via npm on both Windows x64 and ARM64 runners
- Extract the `windows.node` native addon from each build
- Create a GitHub release named `v{version}`
- Upload the prebuilt binaries as:
  - `deviceid-v{version}-napi-v{napiVersion}-win32-x64.node`
  - `deviceid-v{version}-napi-v{napiVersion}-win32-arm64.node`

### Example

Running the workflow with version `0.1.4` and Node.js version `22` creates:

- Release: `v0.1.4`
- Tag: `v0.1.4-node22`
- Assets:
  - `deviceid-v0.1.4-napi-v{N}-win32-x64.node`
  - `deviceid-v0.1.4-napi-v{N}-win32-arm64.node`

## Using Prebuilt Binaries

Download the prebuilt binaries from the [Releases](https://github.com/ghc-jetbrains/vscode-deviceid-prebuilds/releases) page and place them in your project to avoid compilation.

## Requirements

- Node.js >= 22
- GitHub-hosted `windows-11-arm` runner (for ARM64 builds)
