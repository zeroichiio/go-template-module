# template
GO mod template

This is my standard **module** template that I use for new modules, this normally goes inside a GO **workspace**

### 1.0 GO workspace
if you are using multiple modules (using multiple packages) 

- create base folder for workspace
 
```
go work init <name of workspace>
```

### 2.0 GO module (template)

- clone 
- initalize
- add gitub requirements
### 2.1 git clone
```
git clone https://github.com/zeroichiio/template.git
```
- rename the folder
```
cd <new name> 
```
go mod init <module name>

### 2.2 .git/config additions
For signing github commits and so on (public/private) repositories:

**.git/config**

```
[user]
        email = <your github assigned email>
        name = <your github username>
        signingkey = A69E641C4115DFB5 <your signing key in this form>
[commit]
        gpgsign = true <default to signing commits> 
```

### 2.3 Use module in workspace
```
go work use ./<module name>
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

rinse and repeat cloning github in 2.1 through to 2.3

