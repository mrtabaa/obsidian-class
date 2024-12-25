 [Website](https://pnpm.io/installation)

NOTE: 
Do NOT use `pnpm` to install `@angular/cli`. Use `pmpm` **only** for creating/managing Angular projects. 

##### Installation
1. Install `pnpm`
```bash
npm install -g pnpm
```
2. Replace `npm` with `pnpm` for Angular CLI
```bash
ng config -g cli.packageManager pnpm
```
3. Now `ng` will use `pnpm`. e.g.
```bash
ng new client
ng update
```
##### Replace `npm` with `pnpm` in your Angular project
1. `cd` to your project
```bash 
cd client
```
2. Remove `node_modules` folder and `package-lock.json` manually or by this command:
```bash
rm -rf node_modules package-lock.json
```
3. Install `node_modules`
```bash
pnpm install	
```
4. Now you see `pnpm-lock.yaml` in your project.
##### `pnpm` use cases
```bash
pnpm i @angular/material
pnpm i ng2-file-upload
```