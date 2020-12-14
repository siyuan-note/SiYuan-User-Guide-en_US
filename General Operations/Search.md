## Search function

Search mainly involves three functional points:

* Global text search, trigger the search box via <kbd>Ctrl P</kbd> / <kbd>⌘ P</kbd>
* Content block reference/embedded search, in the editor document by typing `((keyword` to trigger
* Relation graph search, filter nodes and connections based on keywords in the relation graph

## Type filtering

If the search keyword starts with the following characters, type filtering is enabled.

* `d` Document block
* `#` Heading block
* `*` List block (including ordered list block, unordered list block and task list block)
* `-` List item block
* `` ` `` Code block
* `>` Blockquote block
* `$` Mathematical formula block
* `{` Super block
* `p` Paragraph block

For example, if you want to search for all heading blocks that contain `Markdown`, you can use `#Markdown` as the search criteria. If the beginning character of the keyword to be searched is in the above list, you need to use `\` to escape. For example, if you want to search for the keyword `doc`, `d` will hit the document block filter, so that the keyword actually searched is `oc`, which needs to be escaped by `\doc`.

## For geeks...
{: id="20201117103851-gx21lz6"}

Global text search support:

* Regular expression
* SQL

For SQL search, use the built-in SQLite database (system temporary folder/siyuan/siyuan.db).

* Edit changes will be automatically synchronized to the database, please do not write to the database
* The database is created temporarily and only exists when the kernel is running
* The data is written asynchronously 7 seconds after editing the document, not real-time

### `blocks` table

This table is used to store content block data.

|    Field | Type | Description                                             |
| -------: | :--: | ------------------------------------------------------- |
|       id | text | Self-incrementing primary key                           |
| block_id | text | Content block ID                                        |
|      box | text | Notebook name                                           |
|     path | text | Path of the document where the content block is located |
|  tree_id | text | Abstract Syntax Tree ID, as the same as root node ID    |
|  content | text | Content block Markdown                                  |
|     type | text | Content block type                                      |

Example:

```sql
SELECT * FROM blocks WHERE content LIKE '%content block%'
```

List of `type` content block type values:

* `NodeDocument` Document block
* `NodeHeading` Heading block
* `NodeParagraph` Paragraph block
* `NodeList` List block
* `NodeListItem` List item block
* `NodeMathBlock` Mathematical formula block
* `NodeCodeBlock` Code block
* `NodeBlockquote` Blockquote block
* `NodeTable` Table block
* `NodeSuperBlock` Super block

### Default query conditions

* If you do not specify the `type` column, the default will add `type = NodeParagraph`, that is, only query paragraph blocks
* If `LIMIT` is not specified, only the first 32 results will be returned at most


{: id="20200924100839-5oe1j4n" type="doc"}