# Codewind Che Testing

## Steps to deploy a custom Theia VSIX file
### Prerequisites

1. Clone the VSCode extension repository (VSCode and Che share the same extension).
```bash
git clone git@github.com:eclipse/codewind-vscode.git
```

2. Clone this repository as you'll want to change the `yaml` files.
```bash
git clone git@github.com:james-wallis/codewind-che-testing.git
```

3. Install `vsix` which is used to package the VSCode extension.

### Setup
1. In the `codewind-vscode` directory (cloned in the prerequisites) build a Theia VSIX file.
    * This is different to the VSCode extension as there are some commands that are not available in Theia.
```bash
# Change into the 'dev' directory
cd dev

# Create a new package.json which does not contain the unsupported commands
./prebuild.js theia

# Create the vscode package
# Note the output of this command, it will tell you the path of the generated .vsix file
# E.g. "Packaged: /codewind-vscode/dev/codewind-0.7.0.vsix"
vsce package

# Reset the package.json
git restore package.json
```

2. Move the created `.vsix` file into the `codewind-che-testing` directory.
```bash
# Use the path outputted in the previous step
# For example
mv /codewind-vscode/dev/codewind-0.7.0.vsix /codewind-che-testing/vscode-plugin/codewind-theia.vsix
```



