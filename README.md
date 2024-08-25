## Project

notes - Manage notes with ease from the command-line using your `$EDITOR`.

## Description

Notes is a powerful and efficient command-line application for managing notes.
Designed for developers and command-line enthusiasts, it offers a range of
features to create, search, and organize your notes seamlessly.

## Features

- Create named or scratch notes fast
- Search and filter notes and pipe the results elsewhere
- Create notes from templates (i.e. forms)
- Use inclusion/exclusion terms to search notes and open them
- Create and execute saved searches
- Support for Zettelkasten personal knowledge management
- Support for backlinking

## Example
You have notes that you want to create and edit with your `$EDITOR` and keep
organized at the command-line.
1. Create a directory for your notes:
   ```bash
   mkdir journal
   ```
2. Change the directory:
   ```bash
   cd journal
   ```
3. Initialize a new Notes project:
   ```bash
   notes init
   ```
4. Create a new note:
   ```bash
   notes new
   ```
5. List the notes created so far:
   ```bash
   notes list
   ```

## Installation
1. Clone the repository:
   ```bash
   git clone /path/to/notes.git
   ```
2. Make the script executable:
   ```bash
   chmod +x notes/notes
   ```
3. Add the directory to the `PATH` environment variable:
   ```bash
   PATH="$PATH:$PWD/notes"
   ```

## Usage

The following are common usage examples:

### Back Command
Find backlinks for the PATH provided.
```bash
notes back PATH
```
Example:
```bash
notes back /path/to/notes/file.txt
```

### Base Command
Change the notes base (i.e. the base path).
```bash
notes base PATH
```
Example:
```bash
notes base /path/to/notes
```

### Conf Command
Print the environment variables.
```bash
notes conf
```
Examples:
```bash
notes conf
```

### Edit Command
Open filtered list of files based on the filter EXPR provided.
```bash
notes edit EXPR
```
Examples:
```bash
notes edit home
notes edit release
```

### Exec Command
Execute a function handler using the NAME provided.
```bash
notes exec NAME
```
Example:
```bash
notes exec archive
```

### File Command
Create a new note and print the filename. Optionally providing a filename.
```bash
notes file [NAME]
```
Examples:
```bash
notes file
notes file todo
```

### Find Command
Find notes matching the terms provided and print the filename(s).
```bash
notes find TERM [TERM, ...]
```
Examples:
```bash
notes find release
notes find release 0.0.1
```

### For Command
Create a new note using the FORM provided. Optionally providing a filename.
```bash
notes for FORM [NAME]
```
Examples:
```bash
notes for release
notes for release release-0.0.1
```

### Form Command
Create a note form (i.e. template) using the NAME provided.
```bash
notes form NAME
```
Example:
```bash
notes form release
```

### Func Command
Create a function handler using the NAME provided.
```bash
notes func NAME
```
Example:
```bash
notes func archive
```

### Grep Command
Find notes matching the terms provided and print matches using grep.
```bash
notes grep TERM [TERM, ...]
```
Examples:
```bash
notes grep release
notes grep release 0.0.1
```

### Hook Command
Create a runtime hook using the NAME provided.
```bash
notes hook NAME
```
Example:
```bash
notes hook vars
```

### Init Command
Initialize the notes repository.
```bash
notes init
```
Examples:
```bash
notes init
```

### Link Command
Print relative file path for the FILE provided.
```bash
notes link PATH
```
Example:
```bash
notes link /path/to/notes/file.txt
```

### List Command
List all notes and forms (i.e. templates). Optionally providing a filter EXPR.
```bash
notes list [EXPR]
```
Examples:
```bash
notes list
notes list release
```

### Main Command
Edit your default note.
```bash
notes main
```
Example:
```bash
notes main
```

### New Command
Create a new note and launch the EDITOR. Optionally providing a filename.
```bash
notes new [NAME]
```
Examples:
```bash
notes new
notes new todo
```

### Open Command
Find notes matching the terms provided and open the file(s) in the EDITOR.
```bash
notes open TERM [TERM, ...]
```
Examples:
```bash
notes open release
notes open release 0.0.1
```

### Path Command
Change the notes path for notes.
```bash
notes path PATH
```
Example:
```bash
notes path /path/to/notes/.notes
```

### Rand Command
Open a single random note. Optionally providing a filter EXPR.
```bash
notes rand [EXPR]
```
Examples:
```bash
notes rand
notes rand release
```

### Root Command
Change the notes root path name (i.e. under the base).
```bash
notes root NAME
```
Example:
```bash
notes root .notes
```

### Search Command
Find notes matching the terms provided and print the results and filename(s).
```bash
notes search TERM [TERM, ...]
```
Examples:
```bash
notes search release
notes search release 0.0.1
```

### Type Command
Change the notes type (i.e. the file suffix).
```bash
notes type NAME
```
Example:
```bash
notes type md
```

### View Command
Create and execute saved searches using the NAME provided.
```bash
notes view NAME [TERM, ...]
```
Examples:
```bash
notes view releases
notes view releases release 0.0.1
```

### With Command
Find backlinks for the PATH provided and open the file(s) in the EDITOR.
```bash
notes with PATH
```
Example:
```bash
notes with /path/to/notes/file.txt
```

## Searching

This application supports searching through notes using inclusion and exclusion
terms. Use of inclusion and exclusion terms are supported by `find`, `open`,
`search`, and `view` commands.

### Implicit inclusion
By default, any term provided, not prefixed, will be treated as an inclusion term.

Example:
```bash
notes search release
```

### Explicit inclusion
Any term provided that is prefixed with a `+` symbol, will be treated as an
inclusion term. Notes containing the term will be included in the results.

Example:
```bash
notes search +release
```

### Explicit exclusion
Any term provided that is prefixed with a `-` symbol, will be treated as an
exclusion term. Notes containing the term will be excluded from the results.

Example:
```bash
notes search -release
```

## Environment Variables

The following are overridable environment variables:

#### NOTES_BASE

The `NOTES_BASE` variable is the filepath for the parent directory of the notes
folder where all notes will be stored, and defaults to `$PWD`.

Example:
```bash
export NOTES_BASE=$HOME
```

#### NOTES_INIT

The `NOTES_INIT` variable is the fully-qualified filepath for the initial (or bootstrapping) notes
directory, and defaults to `$PWD/.notes`. This directory is checked for
pre-processing hooks before executing the program.

Example:
```bash
export NOTES_INIT=$PWD/.notes
```

#### NOTES_MAIN

The `NOTES_MAIN` variable is the filename of the "main" note used by the `notes
main` command, and defaults to `main`.

Example:
```bash
export NOTES_MAIN=index
```

#### NOTES_PATH

The `NOTES_PATH` variable is the fully-qualified filepath for the notes
directory, and defaults to `$NOTES_BASE/$NOTES_ROOT`.

Example:
```bash
export NOTES_PATH=$HOME/notes
```

#### NOTES_ROOT

The `NOTES_ROOT` variable is the directory name of the notes folder, and
defaults to `.notes`.

Example:
```bash
export NOTES_ROOT=notes
```

#### NOTES_TYPE

The `NOTES_TYPE` variable is the file suffix used when operating on notes, and
defaults to `txt`.

Example:
```bash
export NOTES_TYPE=md
```

## Contributing
Contributions are welcome! Please fork the repository and submit a pull request.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

---

Manage your notes with ease using `notes`.
