This is a completely overkill Todo App.

# Structure
It consists of five (5) main parts:

## API 
A .NET 8 Minimal API secured with ASP.NET Identity and [OpenIddict](https://documentation.openiddict.com/).
The Database will be PostgreSql.
Hosted as a docker image in Azure Container Registry and deployed in Azure Container Apps with their built in Aspire Dashboard.

## Blazor App
A Razor Pages Application that is used to administer users, and a place to display any audit tracking. 
This will additionally have Redis Caching.

## Function
A .NET 8 Function using the Event Grid Trigger from a Blob Store to optimise user profile pictures.

## Worker
A .NET 8 Worker using Quartz.NET to schedule emails, it will use the Outbox pattern to ensure that notification emails are sent at least once.
It will additionally schedule emails for:
- overdue items
- items due the next day
- a weekly recap of a users activity.

## React App
A standard react SPA app that will be how the users interact with the API and actually add / edit / delete Todo items.
This would use [react-oidc-context](https://github.com/authts/react-oidc-context?tab=readme-ov-file)

## Next.JS App (Future)
A potential future other avenue for users to interact with the API and to add / edit / delete Todo items. 
This would use [authjs](https://authjs.dev/getting-started/authentication/oauth)

## Monitoring
All monitoring will use OpenTelemetry outputted to Azure Monitor
