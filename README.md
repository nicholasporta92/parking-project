# Parking Project – Backend

Backend del sistema di prenotazione parcheggi sviluppato in Java Spring Boot con persistenza su MongoDB.
Il progetto è containerizzato tramite Docker ed è dotato di pipeline CI/CD GitLab.

## Tecnologie utilizzate

- Java 17
- Spring Boot
- Spring Security
- MongoDB
- Docker
- GitLab CI/CD
- SonarQube

## Funzionalità

- API REST per la gestione dei parcheggi
- Gestione dei posti veicolo
- Gestione delle prenotazioni
- Report e statistiche
- Architettura Controller / Service / Repository
- Utilizzo di DTO
- Gestione accessi tramite ruoli USER e ADMIN

## Documentazione

Il codice è completamente documentato tramite Javadoc.

Controller, Service, Model e DTO includono commenti Javadoc
per descrivere responsabilità, parametri, valori di ritorno ed eccezioni,
al fine di migliorare la leggibilità e la manutenibilità del progetto.

## Swagger / OpenAPI

Il progetto include Swagger (OpenAPI) per la documentazione e il test delle API REST.

Una volta avviata l’applicazione, l’interfaccia Swagger è disponibile all’indirizzo:
http://localhost:8090/swagger-ui.html

Swagger viene utilizzato per verificare e testare gli endpoint esposti dal backend.

## Autenticazione di test (Demo)

Per scopi dimostrativi e di test tramite Swagger, è configurato un
UserDetailsService in memoria.

Sono disponibili i seguenti utenti:

- Amministratore
  - username: admin
  - password: adminpass
  - ruolo: AMMINISTRATORE

- Utente standard
  - username: user
  - password: userpass
  - ruolo: UTENTE

Questa configurazione consente di testare correttamente gli endpoint
protetti da @PreAuthorize tramite Swagger.

Gli utenti in memoria sono presenti esclusivamente a scopo dimostrativo
e non sono destinati a un utilizzo in produzione.


## Gestione ruoli

La registrazione standard crea un utente con ruolo USER.

La registrazione come ADMIN è possibile solo fornendo un codice amministratore,
configurato nel file application.yml.

## Docker

Build immagine Docker:
docker build -t parking-backend .

Avvio container:
docker run -p 8090:8090 parking-backend

Backend disponibile su:
http://localhost:8090

## CI/CD

Il progetto include una pipeline GitLab (.gitlab-ci.yml) che prevede:
- build del progetto
- esecuzione dei test
- build dell’immagine Docker
- push su Docker Hub solo in caso di tag

Rilascio versione:
git tag v1.0.0
git push origin v1.0.0

## Avvio in locale

Prerequisiti:
- Java 17
- MongoDB attivo

## Configurazione MongoDB

Il file application.yml contiene entrambe le configurazioni per MongoDB.

Di default l’applicazione è configurata per l’esecuzione su server
(Docker / ambiente remoto) utilizzando il servizio MongoDB chiamato "mongodb".

Per eseguire l’applicazione in locale è sufficiente commentare la configurazione server
e decommentare quella con localhost.

Configurazioni presenti:
- Server: mongodb://mongodb:27017/parkingdb
- Locale: mongodb://localhost:27017/parkingdb

Avvio applicazione:
mvn clean spring-boot:run

Backend disponibile su:
http://localhost:8090

## Stato del progetto

Backend completo e funzionante.
Frontend da completare

## Autore

Nicholas Porta
https://github.com/nicholasporta92
