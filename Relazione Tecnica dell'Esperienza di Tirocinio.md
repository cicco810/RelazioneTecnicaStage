# **Relazione Tecnica di Tirocinio**

## **1\. Sviluppo Software e Interoperabilità**

L'esperienza di stage è iniziata con una fase intensiva dedicata allo sviluppo software cross-platform in ambiente **WSL (Windows Subsystem for Linux)**. Utilizzando il linguaggio **Python**, è stata approfondita l'interoperabilità tra sistemi operativi per gestire un workflow fluido tra Windows e Linux.

* **Progetto Cardine:** Realizzazione di un convertitore di temperatura (Celsius/Fahrenheit).  
* **Logica e UI:** Oltre al calcolo, è stata curata l'interazione utente tramite la mappatura di input da tastiera, come i tasti *Esc* e *Invio*. Per la gestione degli input è stata utilizzata la libreria getch.  
* **Distribuzione:** Il software è stato compilato in eseguibili nativi per garantire la massima portabilità utilizzando PyInstaller.  
  * *Comando usato:* pyinstaller \--onefile eslin.py.

## **2\. Versioning e Collaborazione con Git**

È stato implementato un flusso di lavoro basato su **Git** per il monitoraggio della cronologia e la sicurezza del codice.

* **Sicurezza:** Configurazione delle postazioni tramite generazione di chiavi **SSH** per l'autenticazione sicura su GitHub.  
  * *Comandi usati:* ssh-keygen , ssh-add .ssh/ciro.  
* **Gestione Repository:** Utilizzo di comandi standard per il primo commit e la pubblicazione remota.  
  * *Comandi usati:* git init, git add ., git commit \-m "first commit", git push \-u origin main.  
* **Tool Grafici:** Per il monitoraggio avanzato della cronologia e dei conflitti sono stati impiegati **gitk** e **meld**.

## **3\. Infrastrutture Web e Dockerizzazione**

Il percorso è proseguito con interventi diretti su infrastrutture reali, operando su architetture **ASPX** per la gestione servizi mensa e sul progetto **Acubens**.

* **Dockerizzazione:** Passaggio cruciale per garantire la coerenza dell'ecosistema di sviluppo. Tramite un **Dockerfile** è stata definita un'immagine isolata con tutte le dipendenze.  
* **Orchestrazione:** Utilizzo di **Docker Compose** per gestire la complessità di database e backend, definendo volumi per la persistenza e reti virtuali.  
  * *Comando usato:* docker compose build.  
* **Stack LAMP:** Implementazione di una nuova colonna **"alias"** nel database relazionale **MySQL** sia a livello di backend che di frontend.  
  * *Comando usato:* git add 06-alter.family.sql.

## **4\. Esperienze Hardware e Sistemistiche**

Sono state condotte due attività hardware distinte e contemporanee.

## **4.1 Raspberry Pi 1B e DietPi**

L'attività sul Raspberry Pi 1B è stata focalizzata sulla gestione delle risorse limitate.

* **Sistema Operativo:** È stato effettuato un cambio verso **DietPi** per ottimizzare le prestazioni.  
* **Software:** Si è tentata l'installazione di browser leggeri come **Dillo** per far fronte ai vincoli hardware.  
* **Accesso Remoto:** Gestione del dispositivo tramite protocollo **SSH**.  
  * *Comando usato:* ssh-copy-id \-i .ssh/ciro.pub root@10.21.37.87.

## **4.2 Interfacciamento Inverter**

Sul fronte industriale, è stato analizzato il funzionamento di un **inverter**.

* **Operatività:** L'attività si è limitata al collegamento al sistema e all'esecuzione di un aggiornamento del dispositivo (*update*).

## **5\. Innovazione e IA**

È stata esplorata l'efficacia degli strumenti di **Intelligenza Artificiale Generativa** applicata al coding, come **GitHub Copilot** e **Gemini**, valutandone il supporto nell'ottimizzazione del flusso di lavoro quotidiano.

