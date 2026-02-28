# Procedura che ho seguito per leggere la eeprom del modem campione

> Utilizzo di un computer Windows solo perché ho trovato i programmi per lui :( [🔵](https://github.com/R0mb0/Modem_Fastweb_NEXXT_Downgrade/tree/main/01_Procedura_lettura_eeprom/01_Driver) [🔴](https://github.com/R0mb0/Modem_Fastweb_NEXXT_Downgrade/tree/main/01_Procedura_lettura_eeprom/02_Software) 

## Strumenti utilizzati

### -> CH341A mini programmer (BLACK) <-
  
![CH341A](https://github.com/R0mb0/Modem_Fastweb_NEXXT_Downgrade/blob/main/01_Procedura_lettura_eeprom/00_Immagini/CH341A.jpeg)

#### ⚠️ Fare attenzione che il CH341A con la scheda nera ha un problema di progettazione che alimenta la eeprom con 5V e ciò potrebbe danneggiare la circuiteria vicina alla eeprom
  
### -> SOP8 Clip <-
  
![SOP8](https://github.com/R0mb0/Modem_Fastweb_NEXXT_Downgrade/blob/main/01_Procedura_lettura_eeprom/00_Immagini/SOP8%20Clip.jpeg)

## Software utilizzato

### Driver

- Il driver per installare su windows la scheda CH341A è diposonibile a [questo link](https://github.com/R0mb0/Modem_Fastweb_NEXXT_Downgrade/tree/main/01_Procedura_lettura_eeprom/01_Driver)

### Programma

- Il programma usato per interagire cone la scheda CH341A è disponibile a [questo link](https://github.com/R0mb0/Modem_Fastweb_NEXXT_Downgrade/tree/main/01_Procedura_lettura_eeprom/02_Software)

#### Il nome del programma e `NeoProgrammer`

## Chip bersaglio 

### -> FM25Q16A <-

- ![Immagine_grande](https://github.com/R0mb0/Modem_Fastweb_NEXXT_Downgrade/blob/main/00_Smontaggio_modem/00_Immagini/0017.jpg)
- ![Microscopio](https://github.com/R0mb0/Modem_Fastweb_NEXXT_Downgrade/blob/main/01_Procedura_lettura_eeprom/00_Immagini/Microscopio.jpeg)
- ![Dettaglio](https://github.com/R0mb0/Modem_Fastweb_NEXXT_Downgrade/blob/main/01_Procedura_lettura_eeprom/00_Immagini/eeprom.png)

### ⚠️ Il microchip `FM25Q16A` è della serie 25 (BIOS 25 SPI)

## Posizionamento della pinza sul CH341A

### ⚠️ Il pin 1, che sarebbe il filo rosso della pinza è semrpe sul lato della levetta 

![Posizione pinza](https://github.com/R0mb0/Modem_Fastweb_NEXXT_Downgrade/blob/main/01_Procedura_lettura_eeprom/00_Immagini/CH341A%2BSOP8.jpeg)

# Procedura estrazione della eeprom

1. Componi la scheda con gli accessori.
2. Collega la scheda `CH341A` al pc (consiglio con l'uso di una piccola prolunga USB) e poi installare il driver.
3. Aprire `NeoProgrammer` e pinzare la scehda del modem.

   ![Scheda_Pinzata](https://github.com/R0mb0/Modem_Fastweb_NEXXT_Downgrade/blob/main/01_Procedura_lettura_eeprom/00_Immagini/Scheda_Pinzata.jpeg)
4. Premere su `Detect` poi sul pulsante per la lettura della eeprom e infine salvare il risultato.

   ![NeoProgrammer](https://github.com/R0mb0/Modem_Fastweb_NEXXT_Downgrade/blob/main/01_Procedura_lettura_eeprom/00_Immagini/Programma.png)

# Perché estrarre la eeprom? 

- _Estrarre la eeprom serve per capire (facendo i confronti tra le varie eeprom formate dei vari aggiornamenti) come è formato il boorloader e di conseguenza serve per capire come creare un aggiornamento per fare il downgrade._
