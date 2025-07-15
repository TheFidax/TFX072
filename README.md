# Scheda di Illuminazione Digitale per vetture [ACME](http://acmetreni.it/index.php/it/) [Gran Confort Revamping IC901](https://scalaenne.wordpress.com/2016/01/09/gran-sconfort-progetto-ic-901-ic-300-ic-270/) in Scala H0
Questa scheda e' pensata per illuminare in maniera digitale le vetture ACME Gran Confort sottoposte a *Revamping IC901 / IC300 / IC270*, in scala H0.</br>
E' stata progettata espressamente sugli ingombri stutturali della carrozza per massimizzare il realismo luminoso garantendo **tutte** le zone illuminate in maniera indipendente: 
- Ambiente Salone 
- Vestiboli
- Ritirate
- Predisposizione per le *Luci di Coda Rosse* 

**Codice Identificativo Progetto: TFX072**

**Ultima Revisione HardWare: 1.21a**

**Ultima Revisione FirmWare: 019**

*NOTA:* Dalla revisione Hardware 1.00a e' possibile conoscere il *Seriale Progressivo* della scheda tramite lo spazio ad esso dedicato:
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/progressivo_seriale.jpg" width="1280">

## Indice
* [Immagini Dimostrative](#immagini-dimostrative)
* [Video Presentazione del Progetto](#video-presentazione-del-progetto)
* [Manuali Scheda](#manuali-scheda)
* [FirmWare](#firmware)
* [HardWare](#hardware)
* [Caratteristiche della Scheda](#caratteristiche-della-scheda)
* [Contattami](#Contattami)

------------

## Immagini Dimostrative

- Carrozza in condizioni luminose *Diurne*

<img src="https://github.com/TheFidax/TFX072/blob/main/Images/diurna.jpg" width="1280">

- Carrozza in condizioni luminose *Notturne*

<img src="https://github.com/TheFidax/TFX072/blob/main/Images/notturna.jpg" width="1280">

- Scheda nella sua posizione appoggiata sopra gli interni:

<img src="https://github.com/TheFidax/TFX072/blob/main/Images/scheda_posizionata.jpg" width="1280"></br>

------------

## Video Presentazione del Progetto
[![Video Presentazione](https://img.youtube.com/vi/xxxx/0.jpg)](http://www.youtube.com/watch?v=xxxx)

------------

## Manuali Scheda
I manuali della scheda sono [disponibile qui](https://github.com/TheFidax/TFX072/tree/main/Manuali).

------------

## FirmWare
Il Firmware dedicato e' presente sotto la cartella [FirmWare](https://github.com/TheFidax/TFX072/tree/main/FirmWare), per poterlo caricare è necessario un programmatore AVR ISP con adattatore all'interfaccia JST SH6.</br>
Le cifre finali del file .HEX identificano la versione del FirmWare.

*NOTA*: Nella cartella e' presente una sotto cartella contenente dei FirmWare di Debug.</br>

**NOTA: Per conoscere la versione del Firmware presente a bordo e' sufficiente *Leggere la CV 7*.**

------------

## HardWare
Il progetto di questa scheda e' disponibile qui: https://workspace.circuitmaker.com/Projects/Details/luca-fidanza/TFX072 .</br>
**Viene rilasciato con la seguente Licenza**: https://creativecommons.org/licenses/by-nc-nd/4.0/ .</br>
I **File Gerber**, il **BOM** e il file **Pick and Place** sono nel file **.Zip** disponibile sotto la cartella [HardWare](https://github.com/TheFidax/TFX072/tree/main/HardWare).</br> 

**NOTA**: Lo spessore *consigliato* del PCB per questa scheda è di: **1mm**

------------

## Caratteristiche della Scheda
Di seguito sono riportate le caratteristiche della scheda, poi spiegate in dettaglio nei vari paragrafi dedicati.
- [Ponte di Diodi Schottky](#ponte-di-diodi-schottky)
- [Filtro Pi](#Filtro-Pi)  
- [Chip Step Down Buck MCP16331](#chip-step-down-buck-mcp16331)
- [Condensatori PowerPack](#condensatori-powerpack)
- [Dcc Reader e Sistema ACK](#Dcc-reader-e-sistema-ack)
- [Sistema BiDirezionale RCN217](#sistema-bidirezionale-RCN217)
- [Microchip ATmega128A](#microchip-atmega128a)
- [Porta di Programmazione ISP](#porta-di-programmazione-isp)
- [Ambiente Salone](#Ambiente-Salone)
- [Vestiboli](#illuminazione-Vestiboli)
- [Ritirate](#illuminazione-Ritirate)
- [Luci di Coda Rosse](#luci-di-coda-rosse)
- [Altoparlante](#altoparlante)
- [Decoder PluX](#interfaccia-plux)
- [Porta SUSI](#porta-susi)
- MINIMUM CLEARANCE: 6mil

------------

### Ponte di Diodi Schottky
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/rectifier.jpg" width="1280">

Il circuito di alimentazione e' realizzato meadiante 4 diodi Schottky in configurazione [Ponte di Graetz](https://it.wikipedia.org/wiki/Raddrizzatore#Ponte_di_Graetz).</br>
Tale configurazione permette di *raddrizzare* la tensione captata dalle prese di corrente in Conrente Continua a prescindere del sistema di alimentazione:
- Corrente Continua Analogica (fornisce sempre gli stessi poli in uscita)
- Corrente PWM (raddrizza l'onda quadra fornendo una tensione simil continua)
- Corrente Alternata Analogica (raddrizza l'onda sinusoidale fornendo una tensione simil continua)
- Digitale (raddrizza l'onda quadra fornendo una tensione simil continua)

------------

### Filtro Pi
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/pi_filter.jpg" width="1280">

Quando e' attivo il *RailCom cutout* in aggiunta a particolari combinazioni di Alimentatori / Centrali Digitali e' possibile che il regolatore di tensione generi un ronzio anomalo, per prevenire un suo funzionamento non corretto dalla revisione Hardware 1.30a e' presente un [Filtro Pi](https://electronicsreference.com/analog/pi_filter/) di supporto prima del chip MCP16331.

------------

### Chip Step Down Buck MCP16331
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/mcp16331.jpg" width="1280">

L'alimentazione a 5 volt e' fornita dal chip [Microchip MCP16331](https://www.microchip.com/wwwproducts/en/MCP16331), un regolatore di tensione di tipo [Step Down Buck](https://it.wikipedia.org/wiki/Convertitore_buck) in gradi di ricevere in ingresso tensioni fino a 50 volt e di fornire in uscita una tensione stabile a 5 volt con sviluppo di calore minimo.</br>

------------

### Condensatori PowerPack
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/powerpack.jpg" width="1280">

Per sopperire a problemi di captazione di corrente e' previsto un sistema *powerpack* formato da 4 condensatori al Tantalio da 100uF con tensione **massima** di 35 volt.</br>
I condensatori sono separati dal circuito di alimentazione da un Diodo ed un Resistore che rappresentano *il sistema di ricarica lenta*, come protezione dalle sovratensioni e' presente un diodo Zener da 27v.</br>

Compatibilmente con lo spazio e' possibile aggiungere altri condensatori, *e' necessario che siano anche essi da 35v* per permettere il corretto funzionamento del sistema di protezione, tramite le piazzole ad essi dedicate.</br>

<img src="https://github.com/TheFidax/TFX072/blob/main/Images/external_powerpack.jpg" width="1280">

------------

### Dcc Reader e Sistema ACK
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/dcc_ack.jpg" width="1280">

Il segnale digitale e' letto mediante resistore per la protezione del pin di input, l'impulso ACK, necessario per il binario di programmazione, viene fornito mediante resistore da 120Ω.</br>
La scheda **e' compatibile con il DCC e con il Motorola**, programmazione **solo** sotto DCC.

------------

### Sistema BiDirezionale RCN217
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/rcn217.jpg" width="1280">

**NOTA: FUNZIONALITA' ANCORA NON IMPLEMENTATA LATO FIRMWARE.**</br>
Dalla revisione HardWare 1.00a e' disponibile il sistema di comunicazione bidirezionale [Rcn217](http://normen.railcommunity.de/RCN-217.pdf), utile per la lettura delle CVs in modalita' POM e per conoscere la posizione del rotabile sul tracciato.</br>
**NOTA**: E' necessario una centrale digitale che supporti il protocollo RCN217.</br>

------------

### Microchip ATmega128A
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/atmega.jpg" width="1280">

Il *cervello* della scheda e' un microcontrollore [ATmega128A](https://www.microchip.com/wwwproducts/en/ATmega128A) a 64 pin operante a 5 volt con frequenza di 16MHz tramite cristallo esterno.</br>
Il microcontrollore comanda *in maniera indipendente* tutti (leggere NOTA) i LED, in modo tale da garantire la massima flessibilita' di funzionamento.</br>

*NOTA*: Il salone e' progettato con *8 segmenti* da 3 led ognuno mentre i vestiboli sono illuminati da due led in parallelo; il microcontrollore comanda il segmento e **non** il singolo LED.

Il chip e' programmabile **anche** utilizzando l'**Arduino IDE** (mediante *programmatore ISP*) tramite il [MegaCore](https://github.com/MCUdude/MegaCore).</br>

I valori dei **FUSE** sono i seguenti: 
- LOW: 0x3F
- High: 0xC7
- Extended: 0xFF
- LOCKBITS: 0xFF

Il microcontrollore **non può** essere dotato di *bootloader*: non e' presente una porta Seriale.

------------

### Porta di Programmazione ISP
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/isp.jpg" width="1280">

Per programmare il microcontrollore e' presente *una porta di programmazione ISP* con connettore JST SH6 per prevenire connessioni invertite.</br>
I collegamenti della **Porta ISP** sono riportati nel seguente schema:</br>

<img src="https://github.com/TheFidax/TFX072/blob/main/Images/isp_schematic.jpg" width="1280">

------------

### Ambiente Salone
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/luci_salone.jpg" width="1280">

L'ambiente salone e' illuminato mediante 8 segmenti da 3 led l'uno, ogni segmento e' indipendente dagli altri.</br>
A differenza del prototipo reale, ove l'illuminazione e' centrale ed illumina in maniera diffusa, sulla scheda si e' optato per due file di led cosi' da illuminare in maniera piu' uniforme l'ambiente viaggiatori.</br>

------------

### Illuminazione Vestiboli
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/luci_vestiboli.jpg" width="1280">

La zona dei vestiboli, su entrambi i lati della carrozza, sono illuminati grazie a 3 led che coprono anche la zona di accesso all'ambiente salone; le zone contrapposte sono indipendenti.

------------

### Illuminazione Ritirate
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/luci_ritirate.jpg" width="1280">

La scheda e' progettata con LED per illuminare gli spazi delle riitirate, anche essi sono indipendenti.

------------

### Luci di Coda Rosse
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/luci_coda_pad.jpg" width="1280">
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/luci_coda_npn.jpg" width="1280">

Su entrambi i lati sono presenti le connessioni per delle **Luci di Coda Rosse**.</br>
Le connessioni prevedere un *polo positivo* collegato alla linea a **5 volt** e un *polo negativo* pilotato dal micro tramite transistor.

------------

### Altoparlante
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/speaker.jpg" width="1280">

La scheda ha lo spazio, e connessioni, per un altoparlante da *rotondo* da 20 millimetri.</br>
*Consigliato 8 Ohm e 2 Watt*.

------------

### Interfaccia PluX
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/plux.jpg" width="1280">

E' presente un **connettore PluX** per poter utilizzare decoder commerciali.</br>
Durante il funzionamento con Decoder, la scheda di illuminazione diventa un [Modulo SUSI](https://github.com/TheFidax/Rcn600), questa configurazione diventa necessario se e' richiesto un protocollo *proprietario* non decodifcicabile dalla scheda.</br>
Protocolli come:
- [MFX/M4](https://en.wikipedia.org/wiki/M%C3%A4rklin_Digital)
- [RailCom Plus](http://www.esu.eu/en/support/white-papers/railcomplusr/) 

Il connettore PluX fornisce il collegamento alle rotaie (per portare i comandi al Decoder), il [Bus SUSI](https://dccwiki.com/SUSI) (per utilizzare la scheda come modulo SUSI) e il collegamento per un altoparlante (in caso di decoder sonori: es. [ESU LokSound v5 FX](http://www.esu.eu/en/products/loksound/loksound-5-fx/)).

**ATTENZIONE! Non è previsto un "motore fittizio" pertanto in caso di decoder "per locomotive" la *Lettura/Scrittura* delle CVs e' permessa soltanto tramite *PoM!***

------------

### Porta SUSI
<img src="https://github.com/TheFidax/TFX072/blob/main/Images/susi.jpg" width="1280">

Per garantire la massima personalizzazione, e' presente anche **una porta SUSI** per eventuali moduli SUSI esterni.

------------

## Contattami
Per curiosita' o ulteriori informazioni puoi contattarmi al seguente indirizzo email: TheFidaxContacts@gmail.com</br>
Oppure sulla pagina Instagram: [The_Fidax_Modellismo](https://www.instagram.com/the_fidax_modellismo/).</br>
Alcuni pezzi in esubero possono anche essere trovati sul mio profilo **Ebay***: https://www.ebay.it/sch/the_fidax/m.html</br>