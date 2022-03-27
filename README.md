# template
GO mod template

This is my general **module** template that I use for new GO modules, this also can go inside a GO **workspace** as of GO 1.18

I use the workspace when there are mutliple modules (with or without multiple packages) that are **loosely linked together** for things like microservices or grpc that use a common module

The idea is the go workspace is the base folder in the Go development folder, and that is where the GO workspace is created in 1.0 (below).

Next inside the workspace this repo is cloned to make the nessecary new modules, and each module has its own github repo to allow for independant tagging and release of each module in the workspace, as I use VScode with "add folder to VS Code workspace", this works for me for both GO, GOPLS, VSCODE, Intellisense and Independant Github versioning) Your millage might vary.

This folder structure is based on the following community contributed structure:
https://github.com/golang-standards/project-layout

### 1.0 GO workspace
if you are using multiple modules (using multiple packages) 

- create base folder for workspace
 
```
mkdir <my workspace name>
cd <my workspace name>
go work init <name of workspace>
```

### 2.0 GO module (template)

- clone 
- initialize 
- add gitub requirements
### 2.1 git clone
```
git clone https://github.com/zeroichiio/go-template-module.git
```
- rename the folder *go-template-module to <module one name>

### 2.2 initialize 
use go mod init to make the go.mod file
```
cd <module one name> 
go mod init <module one name>
```

### 2.3 .git/config additions
For signing github commits and so on (public/private) repositories:

**.git/config**

```
[remote "origin"]
	url = https://github.com/zeroichiio/<module one name>.git
[user]
        email = <your github assigned email>
        name = <your github username>
        signingkey = A69E641C4115DFB5 <== your signing key in this form
[commit]
        gpgsign = true <== default to signing commits
```

### 2.4 Use module in workspace
```
go work use ./<module one name>
```
alternatively edit go.work file to include module folder

**go.work**
```
go 1.18

use (
  ./<module one name>
  ./<module two name>
)
```
        
### 3.0 add additional modules to workspace

rinse and repeat cloning github in 2.1 through to 2.4

