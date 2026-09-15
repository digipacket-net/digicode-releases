# DigiCode — user guide

A native code editor for macOS, by [Digipacket](https://digipacket.net).
This page covers everything version 1.0.0 can do.

[Français](GUIDE.md) · **English**

Questions, bugs, ideas: <https://digipacket.net/contact>.

---

## Contents

1. [Installing](#installing)
2. [Getting started](#getting-started)
3. [The interface](#the-interface)
4. [Keyboard shortcuts](#keyboard-shortcuts)
5. [The command palette](#the-command-palette)
6. [Editing](#editing)
7. [File explorer](#file-explorer)
8. [Searching the project](#searching-the-project)
9. [Terminal](#terminal)
10. [Git](#git)
11. [Project Launcher](#project-launcher)
12. [Writing your own recipe](#writing-your-own-recipe)
13. [Local server](#local-server)
14. [WordPress plugins](#wordpress-plugins)
15. [Settings](#settings)
16. [Where DigiCode keeps its files](#where-digicode-keeps-its-files)
17. [Known limits](#known-limits)

---

## Installing

```sh
brew install --cask digipacket-net/tap/digicode
```

Or take the `.dmg` from
[Releases](https://github.com/digipacket-net/digicode-releases/releases) and
drag DigiCode into Applications.

**Requirements:** macOS 13 Ventura or later. The app is universal — native on
Apple Silicon and on Intel.

**Downloading by hand:** the first time, use **right click → Open** rather than
a double click. DigiCode is signed but not notarised by Apple, and macOS will
not open a downloaded app it has never seen. Once only; every launch after that
is normal. Installing through Homebrew skips this step.

**Uninstalling:** `brew uninstall --cask digicode`, or drag `DigiCode.app` to
the Trash. To remove its data as well — database, recipes, preferences —
`brew uninstall --zap --cask digicode`.

---

## Getting started

1. **Open a folder** — ⇧⌘O, or the button on the welcome screen, which also
   offers *Open File…*, *New File*, *New Project from Recipe* and the palette.
   This is what gives the explorer, search, Git and the server a project to
   work on.
2. **Open a file** — click it in the explorer, or press ⌘P to find it by name.
3. **Find any command** — ⇧⌘P, then type. Everything DigiCode can do is there.

No project yet? ⌃⌘N opens the **Project Launcher**, which creates one —
WordPress, Laravel, React, Vue, Next.js, Node, Python, PHP — in a click.

---

## The interface

```
┌──────────────────────────────────────────────────┐
│ ●●●              DigiCode                        │  title bar + tabs
├────┬─────────────┬───────────────────────────────┤
│ 📁 │             │  file path                    │  breadcrumb
│ 🔍 │  side       ├───────────────────────────────┤
│ ⑂  │  panel      │                               │
│ ▤  │             │  editor                       │
│ 🧩 │             │                               │
│    │             ├───────────────────────────────┤
│ ── │             │  TERMINAL · SERVER · …        │  bottom panel
│ ⌨  │             │                               │
│ 🔌 │             │                               │
│ ── │             │                               │
│ ⚙  │             │                               │
├────┴─────────────┴───────────────────────────────┤
│ branch ↑2↓0   Swift   UTF-8   Ln 12, Col 4       │  status bar
└──────────────────────────────────────────────────┘
```

**The rail on the left** has two groups separated by a hairline. The top five
icons switch the **side panel**: Explorer, Search, Source Control, Project
Launcher, Extensions. The two below open the **bottom panel**: Terminal and
Server. Clicking the icon that is already showing puts the panel away.

**The bottom panel** carries the Terminal, Server, Problems and Output tabs —
plus **Plugins** when the open project is a WordPress site.

**The status bar** shows the Git branch, how far ahead and behind the remote it
is, how many files have changed, then the file's language, its encoding, the
caret position, the length of the selection, and the number of cursors when
there is more than one.

The rail and the status bar can be hidden in the settings (⌘,).

---

## Keyboard shortcuts

### Files

| Shortcut | Action                 |
| -------- | ---------------------- |
| ⌘N       | New file               |
| ⌘O       | Open file              |
| ⇧⌘O      | Open a project folder  |
| ⌘S       | Save                   |
| ⇧⌘S      | Save as                |
| ⌘W       | Close tab              |
| ⌘P       | Quick open by name     |

### Editing and selection

| Shortcut | Action                       |
| -------- | ---------------------------- |
| ⌘F       | Find in file                 |
| ⌥⌘F      | Find and replace             |
| ⌘G       | Next match                   |
| ⇧⌘G      | Previous match               |
| ⎋        | Close the find bar           |
| ⌘D       | Add the next occurrence      |
| ⇧⌘L      | Select all occurrences       |
| ⌥⌘↑      | Add a cursor above           |
| ⌥⌘↓      | Add a cursor below           |
| ⌃Space   | Completions                  |

### Navigation and panels

| Shortcut | Action                   |
| -------- | ------------------------ |
| ⇧⌘P      | Command palette          |
| ⌘B       | Toggle the side panel    |
| ⌘J       | Toggle the bottom panel  |
| ⇧⌘E      | Explorer                 |
| ⇧⌘F      | Project search           |
| ⌃⇧G      | Source Control           |
| ⇧⌘N      | Project Launcher         |
| ⇧⌘X      | Extensions               |
| ⌃`       | Terminal                 |
| ⌃⇧`      | New terminal session     |
| ⌃⇧S      | Local server             |
| ⌥⌘Z      | Line wrapping            |
| ⌘,       | Settings                 |

### Project and Git

| Shortcut | Action                    |
| -------- | ------------------------- |
| ⌃⌘N      | New project (launcher)    |
| ⇧⌘R      | Refresh the Git status    |
| ⌘↵       | Commit what is staged     |

---

## The command palette

**⇧⌘P** opens the palette. It lists **55 commands**, filtered as you type:
typing `opf` finds "Open Folder…", initials are enough. Commands without a
shortcut are only reachable from here.

The categories: **File**, **View**, **Find**, **Selection**, **Editor**,
**Terminal**, **Git**, **Search**, **Project**, **Server**, **Plugins**.

**⌘P** opens a different palette: finding a file in the project by name.

---

## Editing

The editor is built on TextKit 2, the native macOS text layer.

**Syntax highlighting** by Tree-sitter — a real parse of the grammar, not
regular expressions — for **seven languages**: Swift, JavaScript, Python, PHP,
HTML, CSS, JSON. The language is recognised from the file extension and shown in
the status bar.

**Multiple cursors.** ⌘D adds the next occurrence of the selected word, ⇧⌘L
takes them all, ⌥⌘↑ and ⌥⌘↓ stack cursors. Every keystroke applies to all of
them at once, and one undo (⌘Z) takes back the lot. A click or an arrow key
collapses back to a single cursor.

**Find in file.** ⌘F opens the bar; ⌥⌘F adds the replace field. Three options:
match case, whole word, regular expression. The counter reads "3 of 12". ⌘G and
⇧⌘G move through the matches, ⎋ closes.

In regular expression mode the replacement expands capture groups (`$1`, `$2`).
In literal mode everything is taken at face value.

**Completions.** ⌃Space offers the words in the document and the language's
keywords. ↑ ↓ to choose, ↵ to insert, ⎋ to dismiss.

**Tabs.** One tab per open file, with a dot beside the name while there are
unsaved changes.

---

## File explorer

⇧⌘E. The tree of the open folder.

- A click opens a file; a click on a folder unfolds it.
- **Right click**: *New File…*, *New Folder…*, *Rename…*, *Move to Trash*,
  *Copy Path*, *Reveal in Finder*.
- **Drag and drop** to move a file; open tabs follow a file that is moved or
  renamed.
- A deleted file goes to the Trash rather than being erased. The confirmation
  can be turned off in the settings.
- The panel header carries three buttons: new file, new folder, refresh.

---

## Searching the project

⇧⌘F. Searches across files, not only the one that is open.

**Three scopes**, chosen with the three buttons under the field:

| Scope         | What gets read                                |
| ------------- | --------------------------------------------- |
| **Project**   | the whole open folder                         |
| **Open File** | the file in the active tab, and nothing else  |
| **Folder**    | a folder chosen anywhere on disk              |

The same three options as the find bar: case, whole word, regular expression.

**Filtering files** — the button to the right of the options opens two fields,
*include* and *exclude*, which take comma-separated patterns: `*.swift`,
`src/**`, `*.test.js`. These filters pick files out of a tree, so they do not
appear in the "Open File" scope.

Build and dependency folders are skipped by default, and a binary file is
detected by its first null byte rather than read.

**Replace everywhere** — the ✓ button beside the replace field rewrites every
file on disk. A confirmation says what is about to change. It cannot be undone
from the editor: do it on a project under Git.

---

## Terminal

⌃` opens the panel, ⌃⇧` starts another session. These are real shells — `zsh` by
default, changeable in the settings — started in the project's folder, with the
colour, keys and resizing a full-screen program like `vim` or `top` expects.

Several sessions live side by side; the panel's tab strip closes one. All of
them end when the application quits.

---

## Git

⌃⇧G. DigiCode drives the `git` installed on the machine — not a
reimplementation — so your configuration, your credentials and your hooks all
apply unchanged.

**What the panel shows:** the branch and how it stands against the remote, files
in conflict, files that are staged, files that are not. Clicking a file opens
its **diff** in the editor, line by line.

**What it does:**

- stage or unstage a file, or everything at once;
- **commit** — write the message in the field, then ⌘↵;
- **switch branch** or create one, from the branch menu;
- **fetch**, **pull**, **push**. The pull is fast-forward only (`--ff-only`): a
  diverged history is reported rather than merged behind your back.

⇧⌘R reads the repository state again.

---

## Project Launcher

⌃⌘N, or ⇧⌘N for the side panel. Creates a complete project — folder, files,
dependencies installed — in a click, then opens it.

**The ten recipes that ship:**

| Recipe             | What it produces                                    | Tools needed        |
| ------------------ | --------------------------------------------------- | ------------------- |
| **WordPress**      | the latest WordPress, ready for its own installer   | php, tar, git       |
| **Laravel**        | a Laravel application created by Composer           | php, composer, git  |
| **PHP**            | an empty PHP project served by PHP's own server     | php, git            |
| **React**          | a React application on Vite, with fast refresh      | node, npm           |
| **Vue**            | a Vue 3 application on Vite                         | node, npm           |
| **Next.js**        | a Next.js application with the app router           | node, npm, npx      |
| **Node · Express** | an Express HTTP server with a start script          | node, npm, git      |
| **Python**         | a virtual environment, a `requirements.txt`, a module | python3, git      |
| **Static Site**    | HTML, CSS and JavaScript, nothing to install        | git                 |
| **Empty Project**  | a folder, a README and a Git repository             | git                 |

**Common options:** most recipes offer "initialise a Git repository"; React and
Vue offer **TypeScript** and "install the dependencies"; Node offers to install
Express; Python offers the virtual environment. Uncheck what you do not want.

**Missing tools.** The panel shows, for each recipe, which tools it needs and
which are missing. DigiCode looks for executables on your login shell's `PATH`,
so Homebrew, nvm or Herd are found even when the app was launched from the
Finder. A recipe with a tool missing is not run: it says so before creating
anything.

**While it runs**, a progress bar and the command log scroll past. It can be
cancelled.

---

## Writing your own recipe

Recipes are **YAML** or **JSON** files dropped into:

```
~/Library/Application Support/DigiCode/Recipes
```

The "Open the Recipes Folder" command (palette) opens it, creating it if needed;
"Reload Project Recipes" reads the folder again. A recipe carrying the same `id`
as a built-in one replaces it.

### Skeleton

```yaml
recipes:
  - id: my-project
    name: My project
    summary: What the list shows under the name.
    category: Web
    symbol: shippingbox        # an SF Symbols name
    requires: [git, npm]       # tools needed beyond those the steps name
    next:                      # shown at the end, one line per entry
      - npm run dev

    options:
      - key: git
        title: Initialise a Git repository
        summary: Optional explanation
        default: true

    steps:
      - title: Create the public folder
        mkdir: public

      - title: Write the page
        write: public/index.html
        contents: |
          <!doctype html>
          <h1>{{name}}</h1>

      - title: Install the dependencies
        run: npm
        arguments: [install]

      - title: Initialise the repository
        run: git
        arguments: [init]
        when: git                # only if that option is ticked
```

### The actions

| Key        | What it does              | Keys that go with it        |
| ---------- | ------------------------- | --------------------------- |
| `run`      | runs an executable        | `arguments` (a list)        |
| `mkdir`    | creates a folder          |                             |
| `write`    | writes a file             | `contents`                  |
| `download` | downloads a URL           | `to`                        |
| `extract`  | unpacks an archive        | `to`, `strip`               |
| `move`     | moves a file              | `to`                        |
| `delete`   | deletes a file            |                             |

### Keys any step can carry

| Key        | Effect                                              |
| ---------- | --------------------------------------------------- |
| `title`    | what the log shows                                   |
| `in`       | the subfolder the step runs in                       |
| `when`     | run only if this option is ticked                    |
| `unless`   | run only if this option is **un**ticked              |
| `optional` | a failure does not stop the recipe                   |

### Variables

`{{name}}` the project's name, `{{path}}` its full path, `{{parent}}` the folder
that contains it.

### Two safety rules

A step runs an **executable and its arguments**, never a shell line: there is
nothing to escape and no injection to make. And every path is resolved inside
the project folder — a recipe that tries to write outside it is refused, both
when it is read and after the variables have been substituted.

---

## Local server

⌃⇧S. Runs a PHP site and a database, **with no Docker and nothing installed
system-wide**.

### Web

The **WEB** row serves the open project at `127.0.0.1:8000` through PHP's own
built-in server. The folder served is `public/` when it exists — Laravel's case
— and the project root otherwise, as with WordPress.

PHP is not downloaded: DigiCode uses the one on your machine (Herd, Homebrew or
the system) and shows `brew install php` when it finds none.

### Database

The **DATABASE** row installs MySQL in a click: roughly 180 MB downloaded once,
into the application's own folder. Nothing is placed on the system, and the
row's `…` menu can remove all of it.

- **Copy** puts the host, port, user and password on the clipboard, ready for
  TablePlus, Sequel Ace or DBeaver. The connection is `127.0.0.1`, port
  **33060**, user **digicode**.
- **The `…` menu** exports a database to a `.sql` file (`mysqldump`, in a single
  transaction) wherever you choose.

The server listens on the loopback interface only, `root` has a random password
reachable through the socket alone, and the credential files are `0600`.

### WordPress

When the open project is a WordPress site with no `wp-config.php`, a strip
offers **Set it up**: the database is created and the file written, with its
eight salts drawn at random. All that is left is to open the site and fill in
the installer.

### Finding your server again

What was running for a project is written down. **Reopening the folder starts
the database and the web server again, on the same port**, so the link you kept
still answers. A server you stopped on purpose stays stopped.

---

## WordPress plugins

When the open project is a WordPress site, a **Plugins** tab appears beside
Server. It lists the plugins Digipacket publishes and installs them into
`wp-content/plugins` in a click: Backup Toolkit, Login Security, Partner for
WooCommerce, Republish AI.

For a plugin already present the buttons become **Reinstall** and **Remove**,
and a badge shows the installed version. Reinstalling replaces; it does not
duplicate.

After installing, activate the plugin in the WordPress admin as usual.

---

## Settings

⌘, — five panes.

**Appearance:** colour theme, whether to show the activity rail and the status
bar.

**Editor:** font and size, line height, tab width (2, 4 or 8), spaces instead of
tabs, keeping the indentation on a new line, line numbers, current-line
highlight, line wrapping. A button restores the defaults.

**Terminal:** shell path, font size.

**Key Bindings:** the list of shortcuts in force. It can be read, not yet
changed.

**Extensions:** where DigiCode will look for them.

> **Settings are not kept between launches yet.** They return to their defaults
> every time the app starts. That is phase 9 of development.

---

## Where DigiCode keeps its files

Everything lives under `~/Library/Application Support/DigiCode/`:

| Path                      | What is in it                                  |
| ------------------------- | ---------------------------------------------- |
| `Servers/mysql/`          | MySQL, its data and its credentials             |
| `Recipes/`                | your own project recipes                        |
| `Extensions/`             | extensions, once they exist                     |
| `server-session.json`     | what was running for each project               |
| `plugin-catalogue.json`   | the plugin list, cached for an hour             |

Deleting that folder returns DigiCode to a fresh state without touching your
projects.

---

## Known limits

Stated rather than hidden.

- **Settings do not persist** between launches (phase 9).
- **The Extensions, Problems and Output panels** carry a `PREVIEW` badge: they
  show sample data. The extension registry will arrive with a published
  extension format.
- **No Apple notarisation.** The app is signed, but Apple has not
  countersigned it, for want of a paid certificate. Homebrew takes care of
  this; a manual download needs a right click → Open the first time.
- **MySQL rather than MariaDB.** MariaDB no longer publishes macOS binaries;
  MySQL Community speaks the same protocol and is what WordPress and Laravel
  connect to.
- **Fast-forward `pull` only.** A divergence is reported, not merged
  automatically.

---

## A question?

<https://digipacket.net/contact>

DigiCode is developed by **Digipacket**.
