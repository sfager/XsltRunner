# XsltRunner
A simple project for running XSL Transformations using VS Code

# About
This project is a guide to help me run XSLT transformations in VS Code. It uses [DeltaXignia's XSLT and XPath extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=deltaxml.xslt-xpath) . 
The extension provides a simple way to run XSLT transformations and view the results directly in the editor. The extension uses Saxon-HE as the XSLT processor, which is a powerful and widely used XSLT processor. Java is required to run Saxon-HE, so make sure you have Java installed on your system. The project include Saxon-HE jar file, so you don't need to download it separately.

For more information about setting up the extension and running XSLT transformations, refer to the [extension documentation](https://deltaxml.github.io/vscode-xslt-xpath/run-xslt.html)

# Usage
The project includes default task for running XSLT transformations. You can run the task by pressing `Ctrl+Shift+B` or by selecting `Run Build Task` from the Command Palette. The task will use the `saxon-he-12.7.jar` file included in the project to run the transformation.
