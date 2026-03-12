# 

# **Relazione Tecnica di Tirocinio**

## **1\. Sviluppo Software e Interoperabilità**

L'esperienza di stage è iniziata con una fase intensiva dedicata allo sviluppo software cross-platform in ambiente **WSL (Windows Subsystem for Linux)**. Utilizzando il linguaggio **Python**, è stata approfondita l'interoperabilità tra sistemi operativi per gestire un workflow fluido tra Windows e Linux.

* **Progetto Cardine:** Realizzazione di un convertitore di temperatura (Celsius/Fahrenheit).  
* **Logica e UI:** Oltre al calcolo, è stata curata l'interazione utente tramite la mappatura di input da tastiera, come i tasti *Esc* e *Invio*. Per la gestione degli input è stata utilizzata la libreria getch.  
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

Il percorso è proseguito con interventi diretti su infrastrutture reali, operando su architetture **ASPX** per la gestione servizi mensa e sul progetto **Acubens**.

* **Dockerizzazione:** Passaggio cruciale per garantire la coerenza dell'ecosistema di sviluppo. Tramite un **Dockerfile** è stata definita un'immagine isolata con tutte le dipendenze.  
* **Orchestrazione:** Utilizzo di **Docker Compose** per gestire la complessità di database e backend, definendo volumi per la persistenza e reti virtuali.  
  * *Comando usato:* docker compose build.  
* **Stack LAMP & Database:** Implementazione di una nuova colonna **"alias"** nel database relazionale **MySQL** sia a livello di backend che di frontend.  
  * *Comando usato:* git add 06-alter.family.sql.  
* **Manutenzione:** Pulizia del sistema tramite docker system prune e rigenerazione dei volumi con docker compose down \-v per testare la persistenza dei dati.

## **4\. Quality Assurance e Automazione (Novità)**

Una parte significativa del lavoro recente ha riguardato l'implementazione di test automatizzati per verificare l'integrità del software **Acubens**.

* **Testing con Puppeteer:** È stato configurato un ambiente di test E2E (End-to-End) utilizzando **Node.js** e **Puppeteer** per simulare le azioni dell'utente nel browser.  
  * *Installazione dipendenze:* npm i puppeteer, installazione di librerie di sistema necessarie (come libgbm-dev).  
* **Test Unitari e Suite:** Esecuzione di test tramite **BATS** (Bash Automated Testing System) e Makefile dedicati.  
  * *Comandi usati:* make test, make test-puppeteer, bats login.bats.

## **5\. Documentazione Tecnica e Debugging (Novità)**

È stata curata la documentazione del progetto e l'implementazione di strumenti di supporto allo sviluppo.

* **Generazione Documentazione:** Utilizzo di tool come htmldoc e script personalizzati (genera.sh) per convertire file Markdown in documentazione tecnica fruibile.  
* **Normalizzazione file:** Impiego di dos2unix per correggere i formati di fine linea nei file di documentazione modificati in ambienti misti.  
* **Strumenti di Debug:** Aggiunta di un pulsante di debug nell'interfaccia e integrazione di checkbox per il filtraggio avanzato dei dati (es. visualizzazione dispositivi *legacy* vs *orion*).

## **6\. Esperienze Hardware e Sistemistiche**

Sono state condotte attività hardware e di gestione remota.

* **Raspberry Pi 1B e DietPi:** Ottimizzazione di un hardware datato tramite **DietPi** e gestione via **SSH** con scambio di chiavi pubbliche per accesso passwordless.  
* **Interfacciamento Inverter:** Analisi del collegamento al sistema e aggiornamento firmware del dispositivo.  
* **Gestione di Rete:** Montaggio di cartelle condivise Windows su Linux tramite protocollo **CIFS**.  
  * *Comando usato:* sudo mount \-t cifs //10.21.39.232/Public /mnt/public.

## **7\. Innovazione e IA**

Esplorazione dell'efficacia degli strumenti di **IA Generativa** (GitHub Copilot, Gemini) per l'ottimizzazione del codice e la stesura della documentazione tecnica, accelerando la risoluzione di bug complessi e la configurazione degli ambienti Docker.

