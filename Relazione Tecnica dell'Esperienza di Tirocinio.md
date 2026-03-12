**Relazione Tecnica dell'Esperienza di Tirocinio**

## **1\. Sviluppo Software e Interoperabilità**

L'esperienza di stage è iniziata con una fase intensiva dedicata allo sviluppo software cross-platform. Il workflow ha previsto inizialmente la programmazione in ambiente **Windows nativo**, utilizzando **Python** sia come linguaggio interpretato che compilato (in formato .exe).

* **Sviluppo Cross-Platform:** Successivamente, il codice è stato portato in ambiente **WSL (Windows Subsystem for Linux)**. Questa transizione ha presentato sfide tecniche significative, in particolare nella gestione degli input da tastiera: è stato necessario adattare il codice implementando librerie specifiche (come getch) per garantire la corretta intercettazione dei comandi utente sui due diversi sistemi operativi.  
* **Progetto Cardine:** Sviluppo di un convertitore di temperatura interattivo (Celsius/Fahrenheit).  
* **Logica e UI da Terminale:** Oltre alla logica di calcolo, è stata curata l'interazione utente mappando input da tastiera specifici, come la pressione dei tasti *Esc* per l'uscita e *Invio* per la conferma.  
* **Distribuzione:** Per garantire la massima portabilità senza richiedere l'installazione dell'interprete Python sulle macchine host, il software è stato compilato in eseguibili stand-alone utilizzando **PyInstaller**.  
  * *Comando usato:* pyinstaller \--onefile eslin.py

## **2\. Versioning e Collaborazione con Git**

Per garantire il monitoraggio della cronologia delle modifiche e facilitare il lavoro di squadra, è stato adottato un flusso di lavoro rigoroso basato su **Git**.

* **Sicurezza e Autenticazione:** Configurazione delle postazioni di lavoro tramite la generazione di chiavi crittografiche **SSH**, garantendo un'autenticazione sicura e *passwordless* verso i server GitHub.  
  * *Comandi usati:* ssh-keygen, ssh-add .ssh/ciro  
* **Gestione del Repository:** Utilizzo dei comandi standard per l'inizializzazione, il tracciamento dei file e la pubblicazione remota del codice sorgente.  
  * *Comandi usati:* git init, git add ., git commit \-m "first commit", git push \-u origin main  
* **Gestione Revisioni e Merge:** Impiego di git checkout per navigare in modo flessibile tra i rami e i vecchi commit, e git merge per integrare nel ramo principale gli aggiornamenti sviluppati sul branch di stage.  
* **Tool Grafici per il Debugging del Codice:** Per un monitoraggio avanzato dell'albero dei commit e per la risoluzione visiva di eventuali conflitti di merge, sono stati impiegati software come **gitk** e **meld**.

## **3\. Infrastrutture Web e Dockerizzazione**

Una parte cruciale del tirocinio ha riguardato la gestione e lo sviluppo di applicativi su stack tecnologici profondamente differenti, passando da architetture legacy ad ambienti moderni basati su container.

* **Ambiente Windows (IIS):** Per il mantenimento dei servizi web legati alla mensa aziendale, è stata configurata l'infrastruttura nativa su Windows. L'attività ha compreso l'installazione e la configurazione di **IIS (Internet Information Services)** per il deployment di applicativi **ASPX**. Sono state affrontate tematiche quali la gestione degli *Application Pools*, l'impostazione dei permessi sulle directory locali e il troubleshooting della pubblicazione dei siti sulla rete locale.  
* **Dockerizzazione (Progetto Acubens):** Per il progetto principale, basato su stack LAMP in ambiente WSL, l'obiettivo è stato standardizzare l'ambiente di sviluppo per l'intero team. È stato redatto un **Dockerfile** dedicato per isolare le dipendenze (Apache, PHP, estensioni di sistema) all'interno di un container Linux immutabile.  
* **Orchestrazione:** L'interazione tra i microservizi (Web Server e Database) è stata orchestrata tramite **Docker Compose**. Sono state definite reti virtuali interne e configurati **volumi persistenti** per evitare la perdita di dati allo spegnimento delle macchine.  
  * *Comando usato:* docker compose build  
* **Evoluzione del Database:** È stata modificata la struttura relazionale del database **MySQL** introducendo una nuova colonna alias nella tabella family. L'aggiornamento è stato applicato tramite script SQL versionati e successivamente integrato nella logica di backend (PHP) e di visualizzazione frontend.  
  * *Comando usato:* git add 06-alter.family.sql  
* **Manutenzione del Sistema:** Sono state apprese le procedure per garantire un ambiente di sviluppo sempre pulito ed esente da conflitti, testando la reale persistenza dei volumi configurati.  
  * *Comandi usati:* docker system prune (per pulire cache e immagini orfane), docker compose down \-v (per simulare una distruzione totale e ricreazione dell'ambiente).

## **4\. Analisi Logica e Problem Solving (Progetto Acubens)**

Durante lo sviluppo e il refactoring del progetto Acubens, l'implementazione di funzionalità legate alla gestione dei pacchetti software ha richiesto una metodologia di analisi strutturata per superare blocchi logici nel codice PHP.

* **Analisi del Codice Preesistente:** Per operare in sicurezza su script complessi e stratificati nel tempo (come change\_ben\_debug.php, add\_package.php e package.php), sono stati utilizzati strumenti di reverse engineering sul versioning. Tramite git blame e l'uso intensivo di grep, è stata analizzata la paternità e lo scopo originario delle porzioni di codice interessate.  
* **Schematizzazione Logica:** Di fronte a un'intricata serie di controlli condizionali per verificare l'appartenenza dei dispositivi a specifici pacchetti (con conseguenti rimozioni dal Database o aggiornamenti di file JSON), la scrittura del codice è stata temporaneamente sospesa a favore dell'analisi visiva.  
* **Sviluppo guidato da Flowchart:** È stato redatto un diagramma di flusso dettagliato per mappare tutte le casistiche e i flussi (If/Else) del processo di *Controllo Pubblicazioni*. Questo approccio analitico ha fornito una mappa mentale chiara che ha permesso di sbloccare la fase di programmazione e implementare una soluzione pulita e funzionante.

*\!\[Diagramma di flusso realizzato per la risoluzione logica del sistema di pubblicazione e gestione pacchetti\](FlowChartContrPub.jpg)*

## **5\. Quality Assurance e Automazione**

Per garantire l'affidabilità del software Acubens a ogni rilascio, è stata implementata un'infrastruttura di test automatizzati, coprendo sia le logiche di sistema che l'interfaccia utente.

* **Testing E2E con Puppeteer:** È stato configurato un ambiente di test *End-to-End* in JavaScript utilizzando **Node.js** e **Puppeteer**. Questo strumento ha permesso di instanziare un browser *headless* (senza interfaccia grafica) per simulare l'interazione umana con le pagine web, verificando flussi complessi come il login e la navigazione.  
  * *Dipendenze e Installazione:* npm i puppeteer, configurazione e installazione di librerie di sistema per il rendering grafico in WSL (come libgbm-dev).  
* **Test Unitari e Integrazione:** Creazione di script per testare le funzionalità core da riga di comando utilizzando **BATS** (Bash Automated Testing System). Il processo di esecuzione delle suite di test è stato ottimizzato centralizzandolo all'interno di file **Makefile**.  
  * *Comandi usati:* make test, make test-puppeteer, bats login.bats

## **6\. Documentazione Tecnica e Debugging**

La stesura di documentazione chiara e l'implementazione di strumenti di ausilio allo sviluppo sono state trattate come parti integranti del ciclo di vita del software.

* **Generazione Documentazione Automatica:** Scrittura dei manuali tecnici in formato **Markdown**. Per la distribuzione ufficiale, la documentazione è stata convertita in formato PDF formattato avvalendosi del software **htmldoc**, gestito tramite script bash di automazione personalizzati (genera.sh).  
* **Normalizzazione dei File:** Lavorando in un ecosistema misto Windows/Linux, sono stati impiegati tool come dos2unix per bonificare e uniformare i caratteri di fine riga (CRLF vs LF) nei file testuali, prevenendo errori in fase di esecuzione degli script.  
* **Tool di Debugging nell'UI:** Al fine di facilitare i test quotidiani, l'interfaccia utente del software è stata arricchita con pulsanti di debug dedicati e checkbox per il filtraggio condizionale dei dati visualizzati a schermo (ad esempio, distinguendo tra dispositivi *legacy* e dispositivi *orion*).

## **7\. Esperienze Hardware e Sistemistiche**

L'esperienza sistemistica non si è limitata ai servizi virtuali, ma ha abbracciato anche la gestione di hardware fisico e dispositivi IoT.

* **Provisioning Schede Wi-Fi IoT:** È stato analizzato e riprodotto l'intero ciclo di configurazione industriale delle schede di rete:  
  * Identificazione univoca tramite lettura ottica del **codice QR**.  
  * Interrogazione del database e recupero dati dall'**anagrafica di produzione**.  
  * Collegamento diretto alla scheda sfruttandola in modalità **Access Point**.  
  * Accesso all'interfaccia web embedded e configurazione dei parametri di rete tramite **DHCP**.  
* **Ottimizzazione Raspberry Pi 1B:** Recupero e messa in opera di un hardware dalle risorse estremamente limitate. È stato installato il sistema operativo ultraleggero **DietPi** e configurato l'accesso remoto via **SSH** con scambio di chiavi asimmetriche.  
* **Interfacciamento Inverter:** Apprendimento delle logiche di interazione con hardware di potenza industriale, comprendente il collegamento fisico al sistema e l'esecuzione delle routine di aggiornamento firmware (*update*).  
* **Gestione File System di Rete:** Studio e implementazione dei protocolli di condivisione di rete operando su Linux per accedere a risorse Windows.  
  * *Comando usato:* sudo mount \-t cifs //10.21.39.232/Public /mnt/public \-o guest,vers=3.0 (montaggio tramite protocollo **CIFS**).

## **8\. Innovazione e IA Generativa**

Durante tutto il tirocinio, è stata incoraggiata l'esplorazione e l'integrazione di strumenti basati su **Intelligenza Artificiale Generativa** (come *GitHub Copilot* e *Gemini*). Queste tecnologie sono state impiegate quotidianamente come supporto operativo per suggerire ottimizzazioni algoritmiche (refactoring), generare *boilerplate code* per l'infrastruttura Docker, velocizzare il troubleshooting degli errori in console e assistere nella revisione linguistica della documentazione tecnica.

