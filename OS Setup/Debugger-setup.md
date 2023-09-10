1.  Create **launch.json**: Ctrl + shift + P => **.Net: Generate Assests for Build and Debug**
2.  In **Debugger** tab, select **.NET Core Attach**
3.  Terminal: **dotnet watch run**
4.  **Play** button
5.  Search **api** and select the process that is running the api

**LINUX**
1- Install Google Chrome from its **official website**!
2- Enable this option in Chrome
```
chrome://flags/#allow-insecure-localhost
```


**launch.json:**
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

Back to [Project Steps](obsidian://open?vault=Obsidian&file=Programming%2FProjects-Steps%2FProject%20Steps)
