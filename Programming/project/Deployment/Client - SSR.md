Exclude the pages that require API data on prerendering to prevent errors on `ng build --ssr`
[Learn here](https://stackoverflow.com/a/79731221/3944285)

Also make sure to add `ssr` under `prerender`, so it tells the Angular CLI where to find the file that contains the **server-side entry point** of your application.
```json
	"prerender": {  
		"discoverRoutes": false,  
		"routesFile": "routes.txt"  
	},  
	"ssr": {  
		"entry": "server.ts" 
	}
```
Then you can run `ng build --ssr`