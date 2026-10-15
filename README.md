READMI

# 1-Beschrijving

Dit project is een paython web application voor het regestereren en beheren van storingen . De appliactie gebruikt Flask en PostgreSQL en wordt met docker Compose uitgevoerd .


de aplicatie en data base drain in een afzonderlijk conteiners . de database gegecvens worden opgeslagen in een persistent Docker volume , zodat ze behouden blijven waneer de conteiners opnieuw worden gestart 


# 2-Technologieen 
- python
- PostgreSQL
- Docker 
- Docker compose 
- git hub container regestery 

# 3-Veriesten 

installeer : 
docker desktop 
Git

controleer of docker werkt na het installatie :

shell :docker --version 
moet de versie uit geven
shell :docker compose version 
versie uit gaven anders het is nog niet geinsteleerd of werkt niet !!

# 4-installatie vanaf null

stap 1 repository ophalen 
clone de repository
git clone : https://github.com/A-H-studies/cloud-computing
shwll : cd cloud-computing (licatie van de repository ) 


Stap 2 : omgeving variable installeren 

Maak een locale .env aan op basis van het voorbeeldbestand 

shell : copy-item .env.example .env 

open de .env en vull de versie waarden in 

POSTGRES_USER=
POSTGRES_PASSWORD=
POSTGRES_DB=

gebruik een sterke database wachtwoord 


stap 3 : applicatie starten 

docker compose up --build -d 

controleer de status : 

docker compose  ps 

bekijk de applicatie indien nodig : 

docker compose logs --tail=50 web 

(je ziet de de laatste 50 log lijnen van de web ) 

stap 4 : applicatie openen 


open devolgende URL :
http://localhost:8000

# 5-Beheercomandos : 

de container stoppen 
shell : docker compose stop 

de container opnieuw starten 
shell : docker compose start 

de container stoppen en verwijderen 

shell : docker compose down

de logs bekijken : 

shell : docker compose logs -f 

de applicatie opnieuw bouwen en starten :

shell : docker compose up --build -d 


# 6-Database en pemanente opslag 

POstgreSQL gebruikt het Docker-volume db-data om databasegegevens te bewaren. Daardoor blijven de gegevens beschikbaar nadat conteiners zijn gestopt , verwijder of opnieuw aangemakt , zolang het volume behouden blijft . 

gebruik bij het normale stoppen : 
docker compose down 

verwijder het database volume niet als de opslagegeven behouden moeten blijven . het commando docker compose down -v kan de gegevens verwijderen .


# 7-configuratie en beveliging 

de volgende bestanden worden gebruikt 

dockerfile : bout de python applicatie image 
compose.yaml : configureert de applicatie en de PostgreSQL .
.env : bevat de geheim gegevens (password , user , etc ) de password moet aleen latters en cijfers zijn 
.env.example : toont de vereiste omgevingsvriable zonder geheime gegevens 
gitignore : voorkomt dat locale bestande en .env aan Git worden toegevoegd 
.dockerignore : voorkomt dat onnodige bestanden en geheime gegevens in de Docker-buildcontext terechtkomt 



# 8-problemen en opsossing 

als de applicatie niet beschikbaar is dan controller de status door  : 

shell : docker compose ps 

die toont de status van uw container 

de logs bekijken :

shell : docker compose logs --tail=100 web 
voor de logs van de web 
shell : docker compose logs --tail=100 db
voor de logs van de data base 


controleer daar in als de omgevingsvriable correct zijn (user en password ) en of de database gezond is .

als poort 8000 al door een andere applicatie wordt gebrukt , controleer dan de poortenconfiguratie in compose.yaml .

# 9-Stoppen 

stop en verwijder de conteiners met :
shell :docker compose down 

de datagegevens blijven bewaard zolang je de bijbehornde docker volume niet wordt verwijdert 