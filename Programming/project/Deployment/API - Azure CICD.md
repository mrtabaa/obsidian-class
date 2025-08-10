1. Create the Web App without deployment
2. Under `Deployment` tab connect the GitHub repo.
	1. Under `Authentication settings` select `User-assigned identity`
3. Under `Microsoft Entra ID` => `Manage` => `App registrations`
	1. Add an app by `New registration`
	2. Name it like, `wa-arshia-api-school-github-actions
	3. Leave everything else as-is and hit `Register`. 
	4. Under `Manage` => `Certificates & secrets` => `Federated credentials` => `Add credential`
		1. Select `GitHub Actions`
		2. Fill in organization and repo names
		3. `Entity type` => `Branch` => `main`
		4. Pick a name and `Add`
4. In the Web App project
	1. `Access control (IAM)` => `Add role assignment`
	2. Search for `Website contributer`
	3. `Select members` and search for `wa-arshia-api-school-github-actions`
	4. Select the member and hit `Review + assign`
5. Replace the `yml` following items with the new Azure generated `yml` file 
```yml
with:
  client-id: ${{ secrets.AZUREAPPSERVICE_CLIENTID_032917DF3B07488FA446A37DE1C9A28E }}
  tenant-id: ${{ secrets.AZUREAPPSERVICE_TENANTID_250FA19C80D64DA69821A2A1C72E6446 }}
  subscription-id: ${{ secrets.AZUREAPPSERVICE_SUBSCRIPTIONID_1F5E4BCD74334236B7A5CCF299960165 }}
```
6. Make sure the `yml` code includes `permissions` like this
```yml
  deploy:
    runs-on: ubuntu-latest
    needs: build
    permissions:
      id-token: write # <--- IMPORTANT: Required for requesting the JWT for OIDC login
      contents: read # Required for actions/checkout (implicitly used by download-artifact)
```
	