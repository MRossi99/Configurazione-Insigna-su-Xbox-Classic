Guida per configurare **Insignia** sulla prima Xbox e giocare online ai titoli supportati usando il menu **Xbox Live**.

Ormai la Xbox Classic ha parecchi anni sulle spalle e i vecchi servizi Xbox Live non sono più disponibili. Grazie a **Insignia**, un progetto gratuito gestito dalla community, possiamo tornare a utilizzare le funzionalità online dei giochi supportati e giocare nuovamente insieme. <br>
<br>
In questa guida partiamo da una **Xbox già modificata**, capace di avviare applicazioni homebrew e collegarsi al PC tramite FTP.

> [!IMPORTANT]
> La modifica deve consentire le connessioni Xbox Live e la **HDD key non deve essere tutta zero**. Se uno di questi requisiti manca, la sola configurazione di rete non basta. Non cambiare la chiave del disco senza una procedura dedicata e un backup.

📥 Prima di procedere ecco tutto il necessario:

| Nome | Link | Note |
| :--- | :--- | :--- |
| **Insignia Setup Assistant** | [Download](https://github.com/insignia-live/setup-assistant-release/releases/latest) | Scarica `default.xbe` per console modificate |
| **FileZilla Client** | [Download](https://filezilla-project.org/) | Per trasferire il programma sulla Xbox |
| **Insignia** | [Sito ufficiale](https://insignia.live/) | Per richiedere gratuitamente il codice di registrazione |
| **WinSCP** | [Download](https://winscp.net/eng/download.php) | Alternativa a FileZilla |

**1. Controllare la dashboard Microsoft**

- Accendi la Xbox e apri **MS Dashboard** dalla dashboard modificata.
- Vai su **Impostazioni → Informazioni di sistema** e attendi la versione indicata nella tabella.

> Se manca, gli [Extras Disc di Rocky5](https://github.com/Rocky5/Xbox-Softmodding-Tool) includono l'installazione della dashboard Microsoft. Sulla console con modchip verifica il riconoscimento **hardmodded**, poi usa **Dashboards → MS Dashboards → Install**. Prima salva C: ed E: sul PC, come spiegato al punto 2: questa installazione modifica file su C:. Leggi le conferme e scegli soltanto la funzione dedicata alla dashboard Microsoft.

**2. Collegare la Xbox al PC**

- Collega la Xbox al router con un **cavo Ethernet**.
- Collega anche il PC alla stessa rete; sul PC puoi usare Ethernet oppure Wi-Fi.
- Nelle impostazioni della dashboard modificata abilita il server **FTP** e annota l'indirizzo IP della Xbox.
- Apri **FileZilla Client** sul PC e inserisci i dati della console:

| Campo | Cosa inserire |
| :--- | :--- |
| Host | Indirizzo IP locale della Xbox |
| Nome utente | Utente FTP configurato nella dashboard |
| Password | Password FTP configurata nella dashboard |
| Porta | `21` |

- Premi **Connessione rapida**. Nel pannello remoto dovresti vedere le partizioni della console, tra cui **C:** ed **E:**.
- Per conservare una copia dei tuoi dati, crea sul PC una cartella di backup e trascinaci il contenuto di C: ed E:. Attendi che i trasferimenti siano terminati.

> Se FileZilla non si collega, ricontrolla IP, credenziali e server FTP. Lascia aperta la dashboard modificata mentre trasferisci i file: passando a un'altra applicazione il suo server FTP potrebbe chiudersi.

**3. Inserire Insignia Setup Assistant nella Xbox**

- Scarica il file **`default.xbe`** dal link nella tabella iniziale.
- In FileZilla apri la partizione **E:** della console.
- Entra nella cartella **Apps**, oppure creala se non esiste.
- Al suo interno crea una cartella chiamata **Insignia**.
- Copia `default.xbe` dentro questa cartella. Il percorso finale deve essere:

```text
E:\Apps\Insignia\default.xbe
```

- Attendi il completamento del trasferimento.
- Sulla Xbox apri il file manager della dashboard, raggiungi quel percorso e avvia **default.xbe**.

> Non è necessario che Insignia compaia automaticamente nel menu Applicazioni: puoi avviarlo direttamente dal file manager.

**4. Registrare la console e impostare i DNS**

- Nell'Assistant seleziona **Register Xbox**. In caso di errore usa **Troubleshoot**.
- Torna alla dashboard Microsoft e apri le impostazioni di rete Xbox Live.
- Imposta i **DNS manuali**:

| Campo | Valore |
| :--- | :--- |
| DNS primario | `46.101.64.175` |
| DNS secondario | `8.8.8.8` |

- Se necessario, inseriscili anche nella dashboard modificata.
- Salva ed esegui il **test della connessione**.

> [!NOTE]
> Se tornando alla dashboard modificata i DNS cambiano, controlla che questa non sovrascriva le impostazioni Microsoft. Rocky5 propone anche **UnleashX Network Patched**, che conserva la configurazione di rete Microsoft.

**5. Creare il Gamertag** <br>
*Ora creiamo l'account per giocare online.*

- Registra la tua email sul [sito Insignia](https://insignia.live/) e recupera il codice ricevuto.
- Nella dashboard Microsoft avvia la registrazione Xbox Live, scegli paese e Gamertag e inserisci il codice.
- Usa **la stessa email** della richiesta.
- Se vengono chiesti dati di pagamento, usa dati fittizi e il numero di prova `4111 1111 1111 1111`, indicato da Insignia. **Non inserire una carta reale.**
- Completa l'attivazione e imposta il PIN.

**6. Entrare in partita**

- Cerca il tuo titolo nell'[elenco dei giochi supportati](https://insignia.live/games).
- Apri la sua scheda e controlla eventuali indicazioni su aggiornamenti e contenuti necessari.
- Avvia il gioco e seleziona **Xbox Live** dal suo menu.
- Accedi con il Gamertag appena creato.
- Cerca una partita oppure creane una e organizza una sessione con altri giocatori.

> [!TIP]
> Se non trovi partite, non significa necessariamente che la connessione sia sbagliata: potrebbero non esserci giocatori su quel titolo in quel momento. Il sito Insignia mostra l'attività dei giochi; puoi anche usare la community collegata dal sito per organizzarti.

Ora avrai terminato la configurazione: scegli un gioco supportato e goditi nuovamente il multiplayer sulla tua Xbox! <br>

**Se la connessione funziona ma non riesci a giocare.**

- Controlla il **NAT** seguendo la [guida ufficiale](https://insignia.live/guide/nat). Molte partite collegano direttamente le console tra loro: riuscire ad accedere al servizio non garantisce di poter raggiungere tutti i giocatori.
- Con una sola Xbox, Insignia indica l'inoltro della porta **UDP 3074** verso l'IP locale della console. Se lo imposti, assegna alla Xbox una prenotazione DHCP sul router per mantenere stabile quell'indirizzo.
- Se **Halo 2** segnala un errore nell'aggiornamento dei file del matchmaking, apri l'Insignia Assistant e usa **Empty Ticket Cache**, come spiegato nella [guida alla cache](https://insignia.live/guide/cache).
- Per giocare a **Phantasy Star Online Episode 1&2** bisogna selezionare il server nella pagina ufficiale di Insigna [Qui](https://insignia.live/games/4d53004a).
