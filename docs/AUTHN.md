## Alternative Authentication Methods
 
 If using OpenID Connect is not feasible for your scenario, you can also authenticate using one of the following methods:
 
    - **Service Principal with Client Secret**: Create a service principal in Azure AD and use its client ID and client secret to authenticate. Store these values as GitHub secrets and reference them in your workflow.

``` yaml
    jobs:
      sign:
        runs-on: windows-latest

        steps:

          - name: Artifact Signing
            uses: azure/artifact-signing-action@v1
            with:
              azure-tenant-id: ${{ secrets.AZURE_TENANT_ID }}
              azure-client-id: ${{ secrets.AZURE_CLIENT_ID }}
              azure-client-secret: ${{ secrets.AZURE_CLIENT_SECRET }}
              ...
              exclude-environment-credential: true
              exclude-workload-identity-credential: true
              exclude-managed-identity-credential: true
              exclude-shared-token-cache-credential: true
              exclude-visual-studio-credential: true
              exclude-visual-studio-code-credential: true
              exclude-azure-cli-credential: false
              exclude-azure-powershell-credential: true
              exclude-azure-developer-cli-credential: true
              exclude-interactive-browser-credential: true
```
