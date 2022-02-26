# fitbit-cli-pnpm-setup
How to setup the Fitbit CLI on `Windows` using nvm and pnpm
## 📝 Disclaimer:
I only use node for a few projects and my upgrade went without issues,
if you have a more complex setup, things could go wrong.
### 💾 Backups
It may be important to make a backup of your files or `node_modules`
> Don't blame me for data loss :)


### Old Setup
My old setup contained the following:
- Node js
- Npm
- A few global packages
### New Setup
- [nvm-windows](https://github.com/coreybutler/nvm-windows)
- [pnpm](https://pnpm.io)
- Latest version of node
- Node 14.19.0 (a random version I picked that still works with Fitbit CLI)

# [Uninstalling current setup](https://stackoverflow.com/questions/20711240/how-to-completely-remove-node-js-from-windows/20711410#20711410)
1) Run `npm cache clean --force`
2) Use control panel to uninstall node
3) Restart your computer
4) Remove any of the following files if they exist:
- `C:\Program Files (x86)\Nodejs`
- `C:\Program Files\Nodejs`
- `C:\Users\{User}\AppData\Roaming\npm` (or %appdata%\npm)
- `C:\Users\{User}\AppData\Roaming\npm-cache` (or %appdata%\npm-cache)
- `C:\Users\{User}\.npmrc` (and possibly check for that without the . prefix too)
- `C:\Users\{User}\AppData\Local\Temp\npm-*`
5) Check `%PATH%` environment variable to ensure no references to Nodejs or npm exist.

# Setup nvm
1) Download the latest installer for [nvm-windows](https://github.com/coreybutler/nvm-windows)
2) Run the installer with the default setup
3) Run `nvm install <version>` to install node (this will also install npm)
4) Run `nvm use <version>` to use that specific version (you may need admin to use this command)
5) Run `npm install -g pnpm` to install pnpm (it's counterintuitive but it works for now)
6) Install any global packages you normally use by running `pnpm install -g <package>`

## Inside a Fitbit project
1) Install an older version of node that works with the Fitbit CLI (ex. 14.19.0) `nvm install <old-version>`
2) Switch to the older version when working with Fitbit by running `nvm use <old-version>`
3) Install pnpm using `npm install -g pnpm` (packages need to be reinstalled for each version of node)
4) Install the Fitbit CLI tools by running `pnpn add -D @fitbit/sdk` and `pnpn add -D @fitbit/sdk-cli`
5) At this point, setup is complete! when running build commands, pnpx is the same as npx.

### Clean Up
- Remove any unused files in your project
- Add `pnpm-lock.yaml` to `.gitignore` if needed

# Resources
Here is a list of helpful links:
- [Node.js](https://nodejs.org/en/)
- [nvm-windows](https://github.com/coreybutler/nvm-windows)
- [pnpm installation](https://pnpm.io/installation)
- [pnpm add](https://pnpm.io/cli/add)
- [Fitbit CLI Guide](https://dev.fitbit.com/build/guides/command-line-interface/)
- [Fitbit SDK Package](https://www.npmjs.com/package/@fitbit/sdk)
- [Fitbit SDK-CLI Package](https://www.npmjs.com/package/@fitbit/sdk-cli)
