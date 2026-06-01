# XsltRunner

A simple project for running XSLT transformations in VS Code.

## About

This project uses [DeltaXignia's XSLT and XPath extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=deltaxml.xslt-xpath). The extension runs Saxon-HE under Java, and this repository already includes the Saxon JAR you need.

The setup below is adapted from the extension documentation:

- [Getting started](https://deltaxml.github.io/vscode-xslt-xpath/index.html)
- [Running XSLT tasks](https://deltaxml.github.io/vscode-xslt-xpath/run-xslt.html)

## Set up in VS Code

### 1. Install the extension

1. Open this repository as a folder in VS Code.
2. Open the **Extensions** view with `Ctrl+Shift+X`.
3. Search for `XSLT XPath`.
4. Install **XSLT/XPath for Visual Studio Code** by DeltaXignia.

### 2. Set up Saxon (Java)

1. Make sure Java 8 or later is installed and available on your machine.
2. Open **Preferences: Open User Settings** from the Command Palette if you want to configure it globally, or edit the workspace setting in `.vscode/settings.json`.
3. Search for `xslt`.
4. Set **XSLT › Tasks: Saxon Jar** to the Saxon JAR included in this repo:

   `Saxon\v12\SaxonHE12-7J\saxon-he-12.7.jar`

This repository already includes that file, so you do not need to download Saxon separately. It is also already configured for this workspace in `.vscode/settings.json`.

### 3. Configure the initial task

If you want to create the task from scratch, follow the extension's quick-start flow:

1. Open the Command Palette and run **Tasks: Run Build Task** (`Ctrl+Shift+B`).
2. If prompted, choose **Configure Build Task**.
3. Select the **Saxon** task type.
4. VS Code will create `.vscode/tasks.json` with a starter XSLT task.
5. Update the task label and any file settings to match the transform you want to run.
6. Save `tasks.json`, then run **Tasks: Run Build Task** again.

This repository already includes a starter task in `.vscode/tasks.json`:

- `type`: `xslt`
- `label`: `xslt: Saxon Transform (New)`
- `saxonJar`: `${config:XSLT.tasks.saxonJar}`
- `xsltFile`, `xmlSource`, and `resultPath` use the extension's file pickers

## Usage

Run the configured transform with `Ctrl+Shift+B` or **Tasks: Run Build Task** from the Command Palette. The task uses the bundled Saxon-HE 12.7 JAR and prompts you to choose the XSLT file, XML input, and result file.
