# XsltRunner

A starter project for running XSLT transformations in VS Code.

## About

This project uses [DeltaXignia's XSLT and XPath extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=deltaxml.xslt-xpath). The extension runs Saxon-HE under Java, and this repository includes the Saxon JAR you can point VS Code to from your own workspace settings.

Use this repository as a starter project. Create a new Git repository for your actual work, copy this project into it, and then create your own VS Code settings and tasks there.

The setup below is adapted from the extension documentation:

- [Getting started](https://deltaxml.github.io/vscode-xslt-xpath/index.html)
- [Running XSLT tasks](https://deltaxml.github.io/vscode-xslt-xpath/run-xslt.html)

## Set up in VS Code

### 1. Install the extension

1. Open your new repository as a folder in VS Code.
2. Open the **Extensions** view with `Ctrl+Shift+X`.
3. Search for `XSLT XPath`.
4. Install **XSLT/XPath for Visual Studio Code** by DeltaXignia.

### 2. Set up Saxon (Java)

1. Make sure Java 8 or later is installed and available on your machine.
2. In your new repository, create a `.vscode/settings.json` file, or set the value in VS Code user settings if you prefer a global setup.
3. Set **XSLT › Tasks: Saxon Jar** to the Saxon JAR included in this starter project:

   `Saxon/v12/SaxonHE12-7J/saxon-he-12.7.jar`

Example `.vscode/settings.json`:

```json
{
  "XSLT.tasks.saxonJar": "Saxon/v12/SaxonHE12-7J/saxon-he-12.7.jar"
}
```

This starter project includes the Saxon JAR, so you do not need to download Saxon separately.

### 3. Configure the initial task

Create your own `.vscode/tasks.json` in the new repository. The starter project no longer includes default task files because `.vscode/` is ignored here.

You can create the initial task with the extension's quick-start flow:

1. Open the Command Palette and run **Tasks: Run Build Task** (`Ctrl+Shift+B`).
2. If prompted, choose **Configure Build Task**.
3. Select the **Saxon** task type.
4. VS Code will create `.vscode/tasks.json` with a starter XSLT task.
5. Update the task label and any file settings to match the transform you want to run.
6. Save `tasks.json`, then run **Tasks: Run Build Task** again.

Example starter task:

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "xslt: Saxon Transform",
      "type": "xslt",
      "saxonJar": "${config:XSLT.tasks.saxonJar}",
      "xsltFile": "${command:xslt-xpath.pickXsltFile}",
      "xmlSource": "${command:xslt-xpath.pickXmlSourceFile}",
      "resultPath": "${command:xslt-xpath.pickResultFile}",
      "problemMatcher": []
    }
  ]
}
```

## Sharing VS Code configuration

This repository ignores `.vscode/` on purpose:

- it keeps the starter project free of user-specific workspace files
- it lets each new project decide whether those files should stay local or be shared

If you want to commit `.vscode/settings.json` and `.vscode/tasks.json` in your new repository, remove `.vscode/` from `.gitignore` there before committing them.

## Usage

After creating `settings.json` and `tasks.json`, run the transform with `Ctrl+Shift+B` or **Tasks: Run Build Task** from the Command Palette. The task uses the bundled Saxon-HE 12.7 JAR and can prompt you to choose the XSLT file, XML input, and result file depending on how you configure it.
