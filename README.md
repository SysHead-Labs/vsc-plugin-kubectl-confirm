# Kubectl Confirm

Kubectl Confirm is a VS Code extension focused on safer Kubernetes operations.

Instead of executing `kubectl` commands immediately from the editor, the extension adds validation, context visibility, confirmation prompts, and delayed execution safeguards to help prevent mistakes against the wrong cluster or namespace.

![Overview](https://raw.githubusercontent.com/SysHead-Labs/vsc-plugin-kubectl-confirm/refs/heads/master/images/confirm-apply.png)

## Core Functionality

- Execute Kubernetes operations directly from VS Code explorer context menus.
- Display the active Kubernetes context before running destructive commands.
- Show the exact `kubectl` command before execution.
- Require explicit user confirmation for `apply` and `delete` actions.
- Add a cancellable 5 second safety countdown before execution.
- Validate selected resource types before running commands.
- Sync local manifests from live Kubernetes resources.
- Support both standard manifests and Kustomize workflows.

![Right-click menu](https://raw.githubusercontent.com/SysHead-Labs/vsc-plugin-kubectl-confirm/refs/heads/master/images/right-click-menu.png)

## Available Commands

| Command | Description | Shortcut |
| :--- | :--- | :--- |
| `K8S: Apply` | Confirm context and execute `kubectl apply -f` after a safety countdown |  |
| `K8S: Delete` | Confirm context and execute `kubectl delete -f` after a safety countdown |  |
| `K8S: Diff` | Run `kubectl diff -f` against a file or directory | `ctrl+shift+alt+d / ctrl+shift+cmd+d` |
| `K8S: Apply kustomize` | Confirm context and execute `kubectl apply -k` after a safety countdown |  |
| `K8S: Diff kustomize` | Run `kubectl diff -k` against a directory |  |
| `K8S: Sync Container` | Update only the container section from the live Kubernetes resource | `ctrl+shift+alt+s / ctrl+shift+cmd+s` |
| `K8S: Sync` | Update the selected local manifest from the live Kubernetes resource |  |
| `DIR: cd` | Open a terminal in the selected directory |  |

## Safety Features

The extension was built around preventing accidental Kubernetes changes during daily operations.

For `apply` and `delete` actions, the extension:

1. Detects and displays the active Kubernetes context.
2. Shows the exact command that will be executed.
3. Requires manual confirmation inside VS Code.
4. Starts a visible 5 second cancellable countdown.

![Confirm Dialog](https://raw.githubusercontent.com/SysHead-Labs/vsc-plugin-kubectl-confirm/refs/heads/master/images/cancel-apply.png)

5. Sends the command to the currently active terminal only after confirmation.

## Requirements

- VS Code
- A configured `kubectl` installation
- Access to a Kubernetes cluster
- An active VS Code terminal session

## Project Information

This project is an independently maintained fork inspired by:
https://github.com/bagechashu/vsc-plugin-kubeapply

The extension has been expanded with additional Kubernetes safety and validation functionality, updated workflows, and modernized command handling.

## Credits

- [shaimendel](https://github.com/shaimendel/vscode-plugin-cicd-github-actions)
- [bagechashu](https://github.com/bagechashu/vsc-plugin-kubeapply)