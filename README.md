# switch-vssubscription-to-own-tenant

Company's offer their employees Visual Studio subscriptions for using wide range of tools, software, services, and resources to support application development, testing, and deployment across multiple platforms. Along with this Visual Studio subscription one also gets a $50 Azure credit for creating Azure resources. As part of creating Azure resources employees may also create a Service Principal. Service Principal is created at a root tenant level, and also requires App Registration at the root tenant level. But organisations can have security policies in place that prevents users from creating App Registrations.

To circumvent this issue, the Visual Studio subscription can be transferred to the user's individual tenant, where the individual has full rights on their own tenant. This allows users to create Service Principal with App Registration without having any issues.

## Steps to Switch VS Subscritpion to User's Own Entra ID Tenant

1. Create user's own Entra ID tenant. This Entra ID tenant will have:
   - Tenant ID: `xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`
   - Primary Domain: `username.onmicrosoft.com`
2. Go to your Visual Studio subscription in Azure portal, and click on `Change Directory` to switch to your user's personal Entra ID tenant
   ![image](https://github.com/user-attachments/assets/69b6a520-431c-4eb6-bd6c-cdbc7a58559c)

3. Go to user's own Entra ID tenant, by clicking on the user icon in the top right in the Azure Portal, and click on Switch Directory to switch the Azure portal view to user's own Entra ID tenant
4. Invite user's company account as an external user to user's own Entra ID tenant
   - Go to user's own Entra ID view in Azure portal
   - Under `Manage -> Users` blade, click on `Add -> User -> Invite External User`
   - Enter user's company id, for example `firstname.lastname@contoso.com`
   - User should be added in user's own Entra ID as: `firstname.lastname_contoso.com#EXT#@username.onmicrosoft.com`
5. To login to user's own Entra ID using az CLI:
   - `az login --tenant <hexadecimal-tenant-id>`
   
