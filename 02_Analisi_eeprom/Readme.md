# Analisi delle eeprom

## Programmi utilizzati 

<details>
  <summary>

  ## Installare `chocolatey` su windows
    
  </summary>

```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

</details>

<details>
  <summary>

  ## -> WinMerge <-
    
  </summary>

```
choco install winmerge
```

</details>

<details>
  <summary>

  ## -> HxD <-
    
  </summary>

```
choco install hxd
```

</details>

## Risultati ottenuti fino a questo punto 

1. Usando `WinMerge` ho controllato se ci fossero stati degli errori di lettura con lo strumento `CH341A` ottenendo che non ci sono stati problemi di lettura, siccome per ogni eeprom scaricata sono state fatte due prove di lettura ed entrambe erano identiche.

2. Sempre usando `WinMerge` ho provato a vedere se tra le due eeprom ci fossero dei settori comuni, ma non ne ho trovati.

3. Usando `HxD` ho provato a vedere se ci fossero dei campi in chiaro e noti, come ad esempio un MAC address, ma non ho trovato niente.

4. Sospetto quindi che la memoria sia stata cifrata.

## Uso di `binwalk` per comprendere quale è il livello di entropia

<details>
<summary>

### Installazione

</summary>

- Attivare l'ambiente di linux in Windows   
`wsl --install`

- Installazione dello strumento  
`sudo apt update && sudo apt install binwalk`

- Esempio della esecuzione del comando   
`binwalk firmware.bin`

</details>

## Il risultato 

Per entrambe le eeprom ho riscontrato dei livelli molto alti di entropia: