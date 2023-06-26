# Git Mastery

## Configuration (Global and Project Scope)
Git allows configuration options at both global and project scopes.

### Global Git Configuration:

- Create `~/.gitconfig` or `~/.config/git/config`.
- Add the following content:

```
[user]
  email = your_email@example.com
  name = Your Name
[core]
  autocrlf = input
  excludesfile = ~/.gitignore
```

Replace `your_email@example.com` and Your Name with your own information.

#### Repository Git Configuration:

- Open the repository.
- `Use git config --local` to set repository-specific configurations:
```
git config --local user.email your_email@example.com
```

### Gitignore:
#### Global Gitignore File:

- Create `~/.gitignore`.
- Add patterns to ignore:
```
.directory
.Trash-*
.DS_Store
```

### Gitignore Templates:

#### Use the following resources:
- `gitignore.io`: Generate `.gitignore` files based on selected technologies.
- GitHub gitignore: Find templates for various languages and frameworks at github.com/github/gitignore.
With these guidelines, you can configure Git globally and per repository, as well as manage `.gitignore` files effectively.
