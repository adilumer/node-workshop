# Node.js Workshop - Getting Ready

## Tools

- [Node.js Workshop - Getting Ready](#nodejs-workshop---getting-ready)
  - [Tools](#tools)
    - [The IDE](#the-ide)
    - [Node.js \& package manager](#nodejs--package-manager)
    - [The Database Engine(s)](#the-database-engines)
    - [What else?](#what-else)
  - [Next Steps](#next-steps)

### The IDE

- [Visual Studio Code](https://code.visualstudio.com/) is going to be our defacto editor and micro IDE for this workshop. You can however use any tool of your choice, if you are more comfortable with it: [NetBeans](https://netbeans.apache.org/front/main/index.html), [Emacs](https://www.gnu.org/software/emacs/download.html), [WebStorm](https://www.jetbrains.com/webstorm/). Or even Vi, nano or the default notepad in your os.

- If you happen to install [Visual Studio Code](https://code.visualstudio.com/), these are the extensions I have installed, in context of this workshop, that might seem handy:
  - [ritwickdey.LiveServer](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
  - [mgmcdermott.vscode-language-babel](https://marketplace.visualstudio.com/items?itemName=mgmcdermott.vscode-language-babel)
  - [ldd-vs-code.better-package-json](https://marketplace.visualstudio.com/items?itemName=ldd-vs-code.better-package-json)
  - [esbenp.prettier-vscode](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
  - [christian-kohler.path-intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)
  - [christian-kohler.npm-intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.npm-intellisense)
  - [Angular.ng-template](https://marketplace.visualstudio.com/items?itemName=Angular.ng-template)
  - [cyrilletuzi.angular-schematics](https://marketplace.visualstudio.com/items?itemName=cyrilletuzi.angular-schematics)

### Node.js & package manager

```Node.js``` is the JavaScript runtime environment we would be using as our main tool. It comes in with a built-in package manager called ```npm```.

You can install Node.js using pre-built installers for your OS from [here](https://nodejs.org/en/download/prebuilt-installer). This would also install npm. You don't need to install any additional tools that are offered in the installer (like Chocolatey) but feel free if you want to explore.

The current LTS version would be fine. After following the instructions on the installer, make sure that installation was successful by going to your terminal:

- Type ```node -v```. It is expected to produce an ouput similar to ```v20.10.0``` (the SemVer representation of installed node version.)
- Do the same for npm: ```npm -v```, expecting a similar output, e.g. ```10.6.0```

You can move on to the next tool now.

### The Database Engine(s)

- [PostgreSQL](https://www.postgresql.org/download/) will be used as the default database system in this workshop. It is recommended that it installed locally. Just like Node.js, its prebuilt installer can be found [here](https://www.postgresql.org/download/).
- [REDIS](https://redis.io/) will be used for some practiacal examples. If you are using MacOS or linux, the installation is quite simple, but for MS Windows users, [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) would be necessary, as the newer version is not supported on Windows. You don't need this at the start, and should ask for the mentor's help if it is proving hard to figure out.

### What else?

You would need a web browser, that your computer probably already has. You would be fine with any modern browser.

## [Next Steps](./2-js-101.md)

[Next Step: How much should I already know?](./2-js-101.md)
