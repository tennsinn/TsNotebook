# Git

Init the local repository.

	git init

## Config

Use `git config` to edit the configs.

List the related configs.

	git config --list

### Scope

The save path and apply scope will related to the notation added.

|     Notation      |   Save Path    | Apply Scope  |
| :---------------: | :------------: | :----------- |
|    `--system`     | /etc/gitconfig | all users    |
|    `--global`     |  ~/.gitconfig  | current user |
| `--local` or None |  .git/config   | current repo |

### User information

Set the local user information.

	git config [scope] user.name {user_name}
	git config [scope] user.email {user_email}

### Tools

Change the setting of tools like editor or merge tool.

	git config [scope] core.editor {editor_name}
	git config [scope] merge.tool {tool_name}

## Remote repository

Generate the SSH key.

	git ssh-keygen -t rsa -C {user_email}

Clone the remote repository to the local.

	git clone {repo_addr}

Connect to the remote repository.

	git remote add origin {repo_addr}
