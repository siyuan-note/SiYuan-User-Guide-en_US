## Import

When we open the local folder or connect to WebDAV, SiYuan will convert the Markdown file (`.md`) in the path into a `.sy.md` file to complete the import.

When importing, SiYuan will automatically process the `[[link|text]]` in the original Markdown text and convert them into content block quotes. After the import is complete, SiYuan will not write the original Markdown file, and all new editing operations will be saved in the `.sy.md` file.

`.sy.md` is an extended syntax of Markdown. For details, please see ((20200924095851-u5jmzr3 "Storage format")).

## Export

Copy (Ctrl C) in the editor is ((20200924100600-knx7ub0 "formatted Markdown text")). If you need to export standard Markdown files, you can right-click on the file tree document and select "Export". If you need to export automatically during editing, please check "Auto Export" in `Settings - Export`.

Later we will provide batch export functions, such as packaging Markdown and its associated resource files through the TextBundle specification, which can provide better Markdown migration.
