#### API
1.  In **Debugger** tab, select **C#**
2. Select your project's name like `C#:api`
3. Start the debugger by **Play** button

#### Client
1.  Create `launch.json` file: `Ctrl + shift + P` => `.Net: Generate Assests for Build and Debug`
2. Add this code
	`launch.json`:
```json
"configurations": [
   {
		"name": ".NET Core Attach",
		"type": "coreclr",
		"request": "attach",
		"requireExactSource": false
	},
	{
		"name": "Angular Client",
		"request": "launch",
		"type": "chrome",
		"url": "https://localhost:4200/",
		"webRoot": "${workspaceFolder}/client",
	}
]
```
3.  **Play** button

Back to [[New-sln,-API]]
