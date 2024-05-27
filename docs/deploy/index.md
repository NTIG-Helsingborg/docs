# Deploy
En framtida tanke är att ha en egen server för TE4 som vi kan använda för att deploya våra tjänster. Denna server kommer att ha en egen domän som vi kan använda för att exponera våra tjänster till internet.

<!-- ## Cloudflare Tunnels
Då en deploy av detta vore svårt under ett skolnät då vi inte har möjlighet att öppna portar i skolans router så kommer vi att använda oss av [Cloudflare Tunnels](./cloudflare-tunnels.md) för att exponera våra tjänster. Detta gör att vi kan köra våra tjänster på en lokal dator och exponera dem till internet utan att behöva öppna portar i vår router.

## Docker
För att underlätta deploy av våra tjänster kommer vi att använda oss av [Docker](./docker.md). Detta gör att vi kan skapa en container som innehåller allt som behövs för att köra vår tjänst. Detta gör att vi kan köra vår tjänst på vilken dator som helst som har Docker installerat. -->

## Backend
En bra ide inför deploying av backend är att använda sig av docker för att skapa en container som innehåller allt som behövs för att köra vår tjänst. Detta gör att vi kan köra vår tjänst på vilken dator som helst som har Docker installerat men även att olika tjänster inte krockar med varandra.

För att exponera vår tjänst till internet utan att behöva öppna portar i vår router kan vi använda oss av [Cloudflare Tunnels](./backend/cloudflare-tunnels.md). Ett annat alternativ är att använda sig av en molntjänst som t.ex. Heroku eller AWS. Men dessa kan ha större kostnader än att köra en egen server på t.ex en Raspberry Pi.

## Frontend
För att deploya frontend kan vi använda oss av [Vercel](https://vercel.com/). Detta är en molntjänst som gör det enkelt att deploya frontend. Det enda som behövs är att länka sitt GitHub konto och välja vilket repo som ska deployas. Vercel kommer då att bygga och deploya frontend automatiskt vid varje push till master branchen.

Ett annat alternativ är att deploya frontenden på en egen server. Detta kan göras genom att använda sig av Docker och Cloudflare Tunnels på samma sätt som för backend men även att använda sig av en webbserver som t.ex. Nginx eller Caddy.

## Länkar

- [Cloudflare Tunnels](./backend/cloudflare-tunnels.md)
- [Docker](./backend/docker.md)
