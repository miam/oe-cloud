# OE Azure gyakorlat
## Bevezető
Ezen a gyakorlaton a Microsoft publikus felhőjének használatába nyertek betekintést néhány feladat elvégzésével.

## Belépés
Böngészőben nyisd meg az Azure Portal-t: https://portal.azure.com/

Belépéshez használd az egyik devops user-t, ami az órán kerül kiosztásra.
Ilyen formátumban add meg:
devopsXX@aztechnaccoutlook.onmicrosoft.com

A felhasználóhoz tartozó jelszó szintén az órán kerül kiosztásra.

## Az erőforrások létrehozásáról általában
A portálon számos módon eljuthatunk egy-egy Azure resource kezelésehez.
Legegyszerűbb a kereső portált használni, fent középen a böngészősor alatt vagy a g+/ billentyő kombóval.

## Resource Group létrehozása
Az RG-ket az erőforrások egyszerű csoportosítasára használjuk.
Bővebb info itt: https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-setup-guide/organize-resources

Hozd létre a belépési névnek megfelelő RG-t: devopsXX
A Region legyen: (Europe) West Europe

Akár itt: https://portal.azure.com/#create/Microsoft.ResourceGroup

**Nagyon figyelj, hogy innentől a megfelelő Resource Groupba hozd létre a resource-okat és service-ket!**

## Egy sima App Service létrehozása: nginx dockerben
A főmenűből App Service, link: https://portal.azure.com/#create/Microsoft.WebSite
- RG: devopsXX
- Name: unique név - devopsXX vagy ha foglalt devopsXXabcdstb
- Publish: Docker Container
- OS: Linux
- Region: Germany West Central
- SKU and size: vegyuk kissebre -> ki lehet választani a Dev/Test-ből B1-et (100 ACU, 1,75 GB memory)
- Többi lehet default

Ha létrejött, akkor devopsXX App Service overview nézetében elérhető az URL. Előfordulhat, hogy csak North Europe-ban lesz erőforrás.

Nézd meg, hogy tényleg fut-e! Pl: https://devops51.azurewebsites.net/

## Container csere az App Serviceben, latest ngnix-re
Az adott App Service/Deployment Center/Settings alatt:
- Registry settings
- Repository access: Public
- Full Image Name and Tag: nginx:latest
- Save (A változások érvényesülésére türelemmel kell várni.)
- Az URL alatt már a módosított image kell elérhető legyen.

## Alkalmazás és adatbázis: WordPress deploy
A keresőből elérhető: wordpress
- Válaszd ki a Marketplace-ből
- RG: devopsXX
- Region: North Europe
- Ismét Azure globally unique Name szükséges. Pl.: devopsXXwp
- Hosting plan: Change plan basic-re
- Wordpress setup
   Véletlenszerű jelszó pl.: Password+1234
   Create (Hosszabb várakozás szükséges)
- Ellenőrizd az URL-t! Pl: https://devops51wp.azurewebsites.net/

## Extra feladat
https://github.com/Azure-Samples/ms-identity-python-webapp

## Végső takarítás
Az összes komponens kitörlődik, ha letöröljük a Resource Group-ot.
