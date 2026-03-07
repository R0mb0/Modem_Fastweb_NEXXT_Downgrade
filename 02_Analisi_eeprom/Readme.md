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

### Modem vecchio

```
DECIMAL       HEXADECIMAL     ENTROPY
--------------------------------------------------------------------------------
0             0x0             Falling entropy edge (0.644521)
59392         0xE800          Falling entropy edge (0.822126)
75776         0x12800         Falling entropy edge (0.812222)
86016         0x15000         Rising entropy edge (0.955952)
89088         0x15C00         Falling entropy edge (0.641537)
124928        0x1E800         Falling entropy edge (0.807315)
148480        0x24400         Falling entropy edge (0.823436)
153600        0x25800         Falling entropy edge (0.835363)
155648        0x26000         Falling entropy edge (0.665379)
159744        0x27000         Falling entropy edge (0.819659)
176128        0x2B000         Falling entropy edge (0.832881)
182272        0x2C800         Falling entropy edge (0.704932)
194560        0x2F800         Rising entropy edge (0.963875)
197632        0x30400         Falling entropy edge (0.686690)
223232        0x36800         Falling entropy edge (0.736068)
268288        0x41800         Falling entropy edge (0.759784)
272384        0x42800         Falling entropy edge (0.839400)
297984        0x48C00         Rising entropy edge (0.955795)
301056        0x49800         Falling entropy edge (0.794650)
315392        0x4D000         Falling entropy edge (0.840631)
354304        0x56800         Falling entropy edge (0.825896)
359424        0x57C00         Falling entropy edge (0.825077)
366592        0x59800         Falling entropy edge (0.825051)
400384        0x61C00         Rising entropy edge (0.950146)
402432        0x62400         Rising entropy edge (0.972083)
403456        0x62800         Falling entropy edge (0.449113)
```

### Modem nuovo

```
DECIMAL       HEXADECIMAL     ENTROPY
--------------------------------------------------------------------------------
0             0x0             Falling entropy edge (0.680582)
54272         0xD400          Falling entropy edge (0.770339)
79872         0x13800         Falling entropy edge (0.833202)
83968         0x14800         Falling entropy edge (0.843346)
90112         0x16000         Falling entropy edge (0.815972)
138240        0x21C00         Rising entropy edge (0.964436)
141312        0x22800         Falling entropy edge (0.728882)
179200        0x2BC00         Falling entropy edge (0.838067)
200704        0x31000         Falling entropy edge (0.779826)
209920        0x33400         Falling entropy edge (0.798684)
214016        0x34400         Falling entropy edge (0.834188)
223232        0x36800         Falling entropy edge (0.807675)
239616        0x3A800         Rising entropy edge (0.959462)
244736        0x3BC00         Rising entropy edge (0.958925)
248832        0x3CC00         Rising entropy edge (0.964803)
252928        0x3DC00         Rising entropy edge (0.963928)
254976        0x3E400         Rising entropy edge (0.957781)
258048        0x3F000         Falling entropy edge (0.303144)
```

Livelli di entropia così alti mi fanno sospettare che le memorie siano cifrate