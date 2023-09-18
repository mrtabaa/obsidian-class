**It is necessary to use:**
Stops API processing and reading from DB if the user cancels their request by Closing the browser, leaving the page, hitting cancel button, etc.

If CancellationToken is not used, API will process the request disregarding the user's cancellation which is waste of resources.

NOTE: Do not use if you want to process the user entry no matter what. E.g. record the user entry to DB.

![[cancellation.jpg]]


Back to [Project Steps](obsidian://open?vault=obsidian-class&file=Programming%2F0%20-%20Project%20Steps)