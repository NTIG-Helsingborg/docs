# Cloudflare Tunnels
[Cloudflare Tunnels](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/) är ett verktyg som gör det möjligt att exponera en lokal tjänst till internet utan att behöva öppna portar i din router. Detta görs genom att skapa en tunnel mellan din dator och Cloudflares nätverk.

För att kunna använda Cloudflare Tunnels krävs det att ditt domännamn är kopplat till Cloudflare. Om du inte redan har ett konto kan du skapa ett på [Cloudflare](https://dash.cloudflare.com/sign-up). Följ sedan [denna guide](https://developers.cloudflare.com/fundamentals/setup/manage-domains/add-site/) för att lägga till ditt domännamn.

Följ sedan deras [guide](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/get-started/create-local-tunnel/) som beskriver hur du sätter upp en tunnel med hjälp av deras CLI.

Eftersom att vi alltid vill att cloudflare tunnels ska köra så sätter vi upp det som en systemd service. Följ deras guide för detta [här](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/configure-tunnels/local-management/as-a-service/linux/). Detta kan kräva att du flyttar din config fil från `~/.cloudflared/config.yml` till `/etc/cloudflared/config.yml`.

## Sammanfattning
För att kunna använda Cloudflare Tunnels behövs följande:
1. DNS namnet måste finnas hos Cloudflare, behöver dock inte vara köpt där.
2. De hostnames som vi vill ska routas till vår tunnel måste vara configurerade i Cloudflare via `cloudflared tunnel route dns <UUID or NAME> <hostname>`.
3. Vi behöver en config fil för vår tunnel som innehåller information om var requesten ska routas till när den har anländit till vår dator. Viktigt är att komma ihåg att steg 2 måste göras innan vi kan använda hostnamet i vår config fil. Antingen via direkt nämning *(subdomain.example.com)* eller via en wildcard *(\*.example.com)*.

### Guider:
- [Lägg till domännamn i Cloudflare](https://developers.cloudflare.com/fundamentals/setup/manage-domains/add-site/)
- [Skapa en tunnel](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/get-started/create-local-tunnel/)
- [Konfigurera som systemd service](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/configure-tunnels/local-management/as-a-service/linux/)
- [Route hostnames till tunneln](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/configure-tunnels/local-management/configuration-file/#file-structure-for-public-hostnames). (Går även igenom hur routingen fungerar)
