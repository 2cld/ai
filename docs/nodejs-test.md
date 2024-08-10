[edit]()

# nodejs-test
- setup simple nodejs based web testing
- on windows
- on linux
- on wsl
- follow through network routes to test windows firewall, wsl routes, linux routes, external firewalls, docker port mappings... etc

## install nodejs windows 
- powershell node install [https://nodejs.org/en/download/package-manager](https://nodejs.org/en/download/package-manager)
```
# installs fnm (Fast Node Manager)
winget install Schniz.fnm

# configure fnm environment
fnm env --use-on-cd | Out-String | Invoke-Expression

# download and install Node.js
fnm use --install-if-missing 20

# verifies the right Node.js version is in the environment
node -v # should print `v20.16.0`

# verifies the right npm version is in the environment
npm -v # should print `10.8.1`
```
- simple website test [https://www.computerhope.com/issues/ch002070.htm](https://www.computerhope.com/issues/ch002070.htm)
- ps npm install global
```
npm install -g npm
```
- express install
```
npm install -g express-generator
```
- Set execution policy to run express gen
```
PS C:\WINDOWS\system32> Get-ExecutionPolicy -Scope CurrentUser
Undefined
PS C:\WINDOWS\system32> Get-ExecutionPolicy -List

        Scope ExecutionPolicy
        ----- ---------------
MachinePolicy       Undefined
   UserPolicy       Undefined
      Process       Undefined
  CurrentUser       Undefined
 LocalMachine       Undefined


PS C:\WINDOWS\system32> Set-ExecutionPolicy RemoteSigned -Scope CurrentUser

Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution policy might expose
you to the security risks described in the about_Execution_Policies help topic at
https:/go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): A
```
- Create and launch test web
```
PS C:\Users\ghadmin\code> cd ~\code\webtest\
PS C:\Users\ghadmin\code\webtest> express myapp --view="pug"

   create : myapp\
   create : myapp\public\
   create : myapp\public\javascripts\
   create : myapp\public\images\
   create : myapp\public\stylesheets\
   create : myapp\public\stylesheets\style.css
   create : myapp\routes\
   create : myapp\routes\index.js
   create : myapp\routes\users.js
   create : myapp\views\
   create : myapp\views\error.pug
   create : myapp\views\index.pug
   create : myapp\views\layout.pug
   create : myapp\app.js
   create : myapp\package.json
   create : myapp\bin\
   create : myapp\bin\www

   change directory:
     > cd myapp

   install dependencies:
     > npm install

   run the app:
     > SET DEBUG=myapp:* & npm start

PS C:\Users\ghadmin\code\webtest> cd myapp
PS C:\Users\ghadmin\code\webtest\myapp> npm install
npm warn deprecated core-js@2.6.12: core-js@<3.23.3 is no longer maintained and not recommended for usage due to the number of issues. Because of the V8 engine whims, feature detection in old core-js versions could cause a slowdown up to 100x even if nothing is polyfilled. Some versions have web compatibility issues. Please, upgrade your dependencies to the actual version of core-js.

added 131 packages, and audited 132 packages in 8s

13 packages are looking for funding
  run `npm fund` for details

7 vulnerabilities (2 low, 5 high)

To address issues that do not require attention, run:
  npm audit fix

To address all issues, run:
  npm audit fix --force

Run `npm audit` for details.
PS C:\Users\ghadmin\code\webtest\myapp> SET DEBUG=myapp:*
PS C:\Users\ghadmin\code\webtest\myapp> npm start

> myapp@0.0.0 start
> node ./bin/www

GET / 200 6337.573 ms - 170
GET /stylesheets/style.css 200 7.633 ms - 111
```
- approve windows firewall modification for node.js
- see node.js in firewall rules any inbound any port
- Test localhost [http://localhost:3000/](http://localhost:3000/)
```
tbdcmdline
```
- tbd [tbdlink]()
```
tbdcmdline
```
---
## install nodejs Linux
- npm install global  [https://nodejs.org/en/download/package-manager](https://nodejs.org/en/download/package-manager)
```
sudo npm install -g npm
```
- express install
```
sudo npm install -g express-generator
```
