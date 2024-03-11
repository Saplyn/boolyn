# Basics

## Git Repository

Git repository is a collection of files and folders that are tracked by Git. It
is a directory that contains the `.git` directory. The `.git` directory is where
Git stores the metadata and object database for the project.

```sh
# Create a new repository
git init
```

A newly created repository looks like this:

```txt
.
└── .git
    ├── branches
    ├── config
    ├── description
    ├── HEAD
    ├── hooks
    │   ├── applypatch-msg.sample
    │   ├── commit-msg.sample
    │   ├── fsmonitor-watchman.sample
    │   ├── post-update.sample
    │   ├── pre-applypatch.sample
    │   ├── pre-commit.sample
    │   ├── pre-merge-commit.sample
    │   ├── prepare-commit-msg.sample
    │   ├── pre-push.sample
    │   ├── pre-rebase.sample
    │   ├── pre-receive.sample
    │   ├── push-to-checkout.sample
    │   └── update.sample
    ├── info
    │   └── exclude
    ├── objects
    │   ├── info
    │   └── pack
    └── refs
        ├── heads
        └── tags
```

## Recording Changes

Each file in the working directory can be `tracked` or `untracked`, and tracked
files can be `unmodified`, `modified`, or `staged`. The staged files can be
`committed` to the repository.

```sh
# Check the status of the working directory
git status

# Add a file to the staging area
git add <file>

# Commit the staged changes
git commit -m "commit message"

# Show the changes between the working directory and the staging area
git diff

# View the commit history
git log
```

It is possible to tell git to ignore files by creating a `.gitignore` file. Its
syntax is simple: each line contains a pattern for files to ignore.

```txt
# https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository
# ignore a file named `ignore-me.txt`
ignore-me.txt

# ignore all `.a` files
*.a

# but do track `lib.a`, even though you're ignoring `.a` files above
!lib.a

# only ignore the `TODO` file in the current directory, not `sub-dir/TODO`
/TODO

# ignore all files in any directory named `build/`
build/

# ignore `doc/notes.txt`, but not `doc/server/arch.txt`
doc/*.txt

# ignore all `.pdf` files in the `doc/` directory and any of its subdirectories
doc/**/*.pdf
```

We can also explicitly remove a file from the staging area or tracked files,
or discard changes in the working directory.

```sh
# Restore a file from the staged area
# https://stackoverflow.com/a/65434709
git restore --staged <file>
git rm --cached

# Remove files from the working tree (tracked files)
git rm <file>

# Discard changes in the working directory
git restore <file>

# Move or rename a file
git mv <old-file> <new-file>
```
