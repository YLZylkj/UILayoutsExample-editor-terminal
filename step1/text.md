The Katacoda editor-terminal UI Layout combines an Editor with a Terminal. When changes are made to files using the editor, they are automatically sync'ed to the user's home directory.

# Index.json

The editor will display and interact with files relative to the uieditorpath you set in the index.json file for your scenario.

"environment": {
  "uilayout": "editor-terminal",
  "uieditorpath": "/root/example"
}
If not specified, the uieditorpath will default to the /root directory.

You can pre-open a set of files in the editor by defining a files array in the root of the index.json file.

"files": [
    "app.js", "index.js"
]
Files open in the editor window are updated as you make changes in the editor. If the files do not already exist, the tabs will still open for them, but they will not be created until you have updated the content in the editor window.

You can include a path with these filenames. Paths should be given relative to the uieditorpath. Only files under that path will be diplayed in the editor's directory tree.

The syntax highlighting for the editor is automatically inferred from the file extension. This can be enforced by adding a uisettings to your environment.

"environment": {
    "uilayout": "editor-terminal",
    "uieditorpath": "/root/example",
    "uisettings": "javascript"
},
# Helper Functionality

You can replace, prepend, append, and insert text into an open editor file.

Copy file to editor:

var http = require('http');
var requestListener = function (req, res) {
  res.writeHead(200);
  res.end('Hello, World!');
}

var server = http.createServer(requestListener);
server.listen(3000, function() { console.log("Listening on port 3000")});
The following snippet will prepend the contents of the editor:

console.log("Starting...")
Within the Markdown, include:

<pre class="file" data-filename="app.js" data-target="prepend">console.log("Starting...")
</pre>
The following snippet will append the contents of the editor:

console.log("Finishing...")
Within the Markdown, include:

<pre class="file" data-filename="app.js" data-target="append">console.log("Finishing...")
</pre>
The editor can copy to particular files based on the data-filename attribute:

console.log("Index.js here...")
Within the Markdown, include:

<pre class="file" data-filename="index.js" data-target="replace">console.log("Index.js here...")
</pre>
Using the data-target="insert" attribute you can instruct the editor to insert the text in a particular position marked by data-marker attribute.

#TODO-insert
<pre class="file" data-filename="app.js" data-target="insert" data-marker="#TODO-insert">
console.log("Inserted value using the data-marker attribute...")
</pre>
console.log("Inserted value using the data-marker attribute...")
## New Files

Added files in the uieditorpath will automatically be added to the tree in the editor. A markdown extension also makes it easy to open new files in the editor.

Create a new file via the CLI: touch newFile.js{{execute}}

The Markdown is:

`touch newFile.js`{{execute}}
This can then be opened: newFile.js{{open}}

The Markdown is:

`newFile.js`{{open}}