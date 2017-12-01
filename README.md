# Campfire

### Excutes firebase realtime db queries from a vscode text buffer

## Usage

* To execute the current file or the selection press `F8` or use the command `Execute Firebase query`
* To cancel a running process press `F9`

## Configuration

Clear output before execution

````json
{
  "campfire.clearOutput": true
}
````

Show start and end info

````json
{
  "campfire.showInfo": true
}
````

Show stdout and stderr

````json
{
  "campfire.showStdout": true,
  "campfire.showStderr": true
}
````

If `miramac.node.legacyMode` is `true` (default) the extention will not use new features and options. Because of some strange problems I can't reproduce, the extension remains in legacy mode. To use the following options simply set this option to `false`

````json
{
  "campfire.legacyMode": false
}
````


Change the node binary for execution (default to node binary from PATH if unset)

````json
{
  "campfire.nodeBin": "/path/to/some/bin/node-7.0"
}
````

## How it works

The selected code or if nothing is selected, the active file, is written in a temporarily file (something like `node_<random-sring>.tmp`). You don't have to save the file for execution.
This file will be executed by your installed version of node.js. Therefore `node` has to be in the PATH.

```javascript
require('child_process').spawn('node', options,[tmpFile, args])
```

Any data from `stdout` or `stderr` will be printed to an OutputChannel. Unfortunately console colors won't work.

## Credits
Based on [https://github.com/Miramac/vscode-exec-node](https://github.com/Miramac/vscode-exec-node)

**Enjoy!**
