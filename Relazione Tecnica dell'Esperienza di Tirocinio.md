# **Relazione Tecnica di Tirocinio**

## **1\. Sviluppo Software e Interoperabilità**

L'esperienza di stage è iniziata con una fase intensiva dedicata allo sviluppo software cross-platform. Il workflow ha previsto inizialmente lo sviluppo in ambiente **Windows native**, utilizzando **Python** sia come linguaggio interpretato che compilato in formato .exe.

* **Sviluppo Cross-Platform:** Successivamente, il codice è stato replicato in ambiente **WSL (Linux)**. Questa transizione ha presentato sfide tecniche significative, in particolare nella gestione della tastiera: è stato necessario adattare il codice utilizzando librerie diverse (come getch) per gestire correttamente l'input utente sui due diversi sistemi operativi.  
* **Progetto Cardine:** Realizzazione di un convertitore di temperatura (Celsius/Fahrenheit).  
* **Logica e UI:** È stata curata l'interazione utente tramite la mappatura di input da tastiera, come i tasti *Esc* e *Invio*.  
* **Distribuzione:** Il software è stato compilato in eseguibili nativi per garantire la massima portabilità utilizzando **PyInstaller**.  
  * *Comando usato:* pyinstaller \--onefile eslin.py.

## **2\. Versioning e Collaborazione con Git**

È stato implementato un flusso di lavoro basato su **Git** per il monitoraggio della cronologia e la sicurezza del codice.

* **Sicurezza:** Configurazione delle postazioni tramite generazione di chiavi **SSH** per l'autenticazione sicura su GitHub.  
  * *Comandi usati:* ssh-keygen, ssh-add .ssh/ciro.  
* **Gestione Repository:** Utilizzo di comandi standard per il primo commit e la pubblicazione remota.  
  * *Comandi usati:* git init, git add ., git commit \-m "first commit", git push \-u origin main.  
* **Gestione Revisioni:** Utilizzo di git checkout per navigare tra i commit e git merge per l'integrazione degli aggiornamenti dal branch di stage.  
* **Tool Grafici:** Per il monitoraggio avanzato della cronologia e dei conflitti sono stati impiegati **gitk** e **meld**.

## **3\. Infrastrutture Web, Dockerizzazione e Database**

Il lavoro ha riguardato la gestione di applicativi su stack tecnologici differenti:

* **Ambiente Windows (IIS):** Per i servizi mensa è stata configurata l'infrastruttura **ASPX** tramite **IIS (Internet Information Services)**. L'attività ha previsto la gestione dei *Application Pools*, l'impostazione dei permessi delle directory e il debug della pubblicazione dei siti web in ambiente Microsoft.  
* **Dockerizzazione (Progetto Acubens):** Per standardizzare l'ambiente di sviluppo su WSL, è stato creato un **Dockerfile** dedicato. Tramite **Docker Compose** è stata orchestrata l'interazione tra web server e database, definendo volumi per la persistenza dei dati.  
  * *Comando:* `docker compose build`.  
* **Database e Stack LAMP:** È stata modificata la struttura del database **MySQL** inserendo la colonna `alias` nella tabella `family`. La modifica è stata gestita tramite script SQL e integrata nel backend dell'applicativo.  
  * *Comando:* `git add 06-alter.family.sql`.  
* **Manutenzione:** Per verificare la stabilità dell'ambiente, sono stati eseguiti cicli di pulizia e rigenerazione dei container.  
  * *Comandi:* `docker system prune` e `docker compose down -v`.

## **4\. Quality Assurance e Automazione**

È stata implementata una suite di test automatizzati per verificare l'integrità del software **Acubens**.

* **Testing con Puppeteer:** Configurazione di un ambiente di test **E2E (End-to-End)** utilizzando **Node.js** e **Puppeteer** per simulare le azioni dell'utente nel browser.  
  * *Installazione dipendenze:* npm i puppeteer, installazione di librerie di sistema necessarie (come libgbm-dev).  
* **Test Unitari e Suite:** Esecuzione di test tramite **BATS (Bash Automated Testing System)** e Makefile dedicati.  
  * *Comandi usati:* make test, make test-puppeteer, bats login.bats.

## **5\. Documentazione Tecnica e Debugging**

È stata curata la documentazione del progetto e l'implementazione di strumenti di supporto allo sviluppo.

* **Generazione Documentazione:** Utilizzo di tool come htmldoc e script personalizzati (genera.sh) per convertire file Markdown in documentazione tecnica.  
* **Normalizzazione file:** Impiego di dos2unix per correggere i formati di fine linea nei file modificati in ambienti misti (Windows/Linux).  
* **Strumenti di Debug:** Aggiunta di un pulsante di debug nell'interfaccia e integrazione di checkbox per il filtraggio avanzato dei dati (es. visualizzazione dispositivi *legacy* vs *orion*).

## **6\. Esperienze Hardware e Sistemistiche**

Oltre alle attività sistemistiche, è stato analizzato il ciclo di vita hardware dei dispositivi.

* **Provisioning Schede Wi-Fi:** È stato studiato l'intero processo di configurazione delle schede, comprendente:  
  * Identificazione della scheda tramite scansione di **codici QR**.  
  * Recupero delle informazioni dall'**anagrafica di produzione**.  
  * Connessione alla scheda tramite **Access Point** dedicato.  
  * Configurazione dei parametri **DHCP** tramite interfaccia web.  
* **Raspberry Pi 1B e DietPi:** Ottimizzazione di hardware datato tramite **DietPi** e gestione via **SSH** con chiavi pubbliche.  
* **Interfacciamento Inverter:** Analisi del collegamento al sistema e aggiornamento (*update*) del firmware del dispositivo.  
* **Gestione di Rete:** Montaggio di cartelle condivise Windows su Linux tramite protocollo **CIFS**.  
  * *Comando usato:* sudo mount \-t cifs //10.21.39.232/Public /mnt/public.

## **7\. Innovazione e IA**

Esplorazione dell'efficacia degli strumenti di **IA Generativa** (GitHub Copilot, Gemini) per l'ottimizzazione del codice e la stesura della documentazione tecnica, velocizzando la risoluzione di bug e la configurazione degli ambienti Docker.

