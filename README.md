# NextHMI · rilasci

Pacchetti di installazione di **NextHMI**, il programma operatore delle pesatrici NEMESIS. Qui ci sono solo i pacchetti pronti; il codice non è pubblico.

## Scaricare

L'ultima versione è sempre in [Releases › Latest](https://github.com/Blicks-srl/nexthmi-releases/releases/latest). Ogni versione ha questi file:

| File | Per |
|---|---|
| `nexthmi-<versione>-windows-amd64.exe` | PC e tablet Windows (10 o successivo, 64 bit): si installa con un doppio clic |
| `nexthmi-<versione>-windows-amd64.zip` | Lo stesso pacchetto Windows, da estrarre a mano |
| `nexthmi-<versione>-linux-arm64.run` | PC Linux ARM a 64 bit, per esempio Raspberry: si installa senza estrarre |
| `nexthmi-<versione>-linux-amd64.run` | PC Linux Intel o AMD a 64 bit: si installa senza estrarre |
| `nexthmi-<versione>-linux-*.tar.gz` | Gli stessi pacchetti Linux, da estrarre a mano |
| `nexthmi-<versione>.sha256` | Le somme SHA-256 di tutti i file sopra |
| `latest.json` | Versione, data, indirizzo e SHA-256 dei pacchetti, per le macchine che cercano gli aggiornamenti |

L'ultima versione ha anche un indirizzo fisso, `https://github.com/Blicks-srl/nexthmi-releases/releases/latest/download/<file>`, per esempio [latest.json](https://github.com/Blicks-srl/nexthmi-releases/releases/latest/download/latest.json).

## Controllare il file scaricato

Windows, in PowerShell, nella cartella dei file scaricati:

```powershell
Get-FileHash .\nexthmi-2.0.0.1-windows-amd64.exe -Algorithm SHA256
```

Il valore deve essere uguale a quello sulla riga del file nel `.sha256`. Linux, con il `.sha256` nella stessa cartella:

```sh
sha256sum -c --ignore-missing nexthmi-2.0.0.1.sha256
```

## Aggiornare una macchina

Si aggiorna **a macchina ferma**: l'aggiornamento ferma le pagine e l'acquisizione per qualche minuto, fa prima una copia di sicurezza dei dati e riparte con la versione nuova. Se un passo non riesce, torna alla versione di prima.

- **Windows, da internet** (dalla versione 2.0.1.0): in **Diagnostica › Aggiornamento software** premere **Cerca aggiornamenti**; se c'è una versione più nuova, **Scarica** la porta sul PC e ne controlla firma e SHA-256, poi si tocca la versione e si preme **Aggiorna**. Il PC deve raggiungere `github.com`.
- **Windows, da chiavetta:** copiare il file `.exe` nella cartella principale di una chiavetta USB, inserirla nel PC della macchina, aprire **Diagnostica › Aggiornamento software**, toccare la versione e premere **Aggiorna**.
- **Windows, sul PC:** doppio clic sul file `.exe`. Chiede i diritti di amministratore, installa su un PC nuovo e aggiorna dove NextHMI c'è già.
- **Linux:** copiare sul PC il `.run` giusto, poi:

  ```sh
  sudo sh nexthmi-<versione>-linux-arm64.run aggiorna -macchina-ferma
  ```

## Prima installazione

Windows: doppio clic sul file `.exe`. Linux: `sudo sh nexthmi-<versione>-linux-arm64.run -prova` mostra i passi senza cambiare niente, poi lo stesso comando senza `-prova` installa. Ogni pacchetto contiene `INSTALL.md`, la guida completa: opzioni, copie di sicurezza, ritorno alla versione di prima.
