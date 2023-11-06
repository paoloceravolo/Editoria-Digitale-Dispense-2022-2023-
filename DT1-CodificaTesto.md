# Codifica del Testo

## Codifica

La **codifica** è quel processo che ci permette di:

> *esprimere informazioni e messaggi mediante le regole e i simboli di un sistema convenzionale (il codice) stabilito concordemente dall’emettitore e dal ricevitore dei messaggi allo scopo di trasmettere o elaborare automaticamente le informazioni* - **Treccani**

Nei calcolatori il **testo è memorizzato come sequenza binaria,** la codifica del testo si occupa di **definire** la **corrispondenza** tra una sequenza binaria e il corrispondente carattere alfanumerico.

Prendiamo ad esempio la codifica *Windows-1252*, Il carattere “é” è salvato in memoria usando la sequela binaria che in esadecimale corrisponde al valore “E9”, mentre per la codifica DOS latin-1 il valore “E9” corrisponde al carattere “Ú”

La difficoltà è quindi duplice:

- È necessario **scegliere** con cura, a seconda dell'applicazione di destinazione, la **codifica da utilizzare** quando si salva un testo 
- Quando è il momento di visualizzare un testo, è necessario **poter determinare la codifica utilizzata**

## Codifica ASCII 

**Quantità di informazione da rappresentare** (considerando l’alfabeto inglese): 

- 26 lettere

+ 26 lettere maiuscole
+ 10 cifre decimali
+ 30 caratteri circa di uso comune (., *, %, etc.) 
+ alcuni caratteri di controllo (spazi, interruzione di riga) 

in totale sono circa **120 caratteri**, per rappresentarli sono sufficienti **7 bit,** poiché 27 = 128 > 120 
Su questa base è stato creato il codice ASCII, basato appunto sull’uso di 7 bit per ogni carattere.

Esempio:

- A diventa 1000001
- B diventa 1000010 
- a diventa 1100000

![ASCII Code Chart](img/1920px-ASCII_Code_Chart.png)

### Limiti di ASCII 

La globalizzazione di Internet ha proposto il problema di rendere correttamente gli alfabeti di migliaia di lingue nel mondo.

Poiché i 7 bit usati da ASCII consentono di rappresentare solo 128 caratteri diversi, sono stati definiti nel tempo altri codici per consentire la rappresentazione di più caratteri

**ASCII esteso**: usa 8 bit (un BYTE) per carattere. Consente quindi di rappresentare anche caratteri accentati e lingue diverse dall’inglese.

### Altre codifiche storiche 

#### EBCDIC

**Extended Binary Characters for Digital Interchange Code**, codifica proprietaria IBM del 1965 a 8 bit. IBM è molto sicura della superiorità dei suoi chip e si azzarda fin dagli anni cinquanta ad usare tutti e 8 i bit del byte

#### ISO 646

Una **codifica ISO del 1991** che permettere l'uso di caratteri nazionali europei in un contesto sostanzialmente ASCII. Sono lasciati 12 codici liberi per le versioni nazionali dei vari linguaggi europei. Ogni versione nazionale li sostituisce con caratteri propri. I caratteri sacrificati sono: # $ @ \ ¬ ` { | } ~

#### ISO 8859/1

più comunemente **ISO Latin 1** è un estensione standard dell’ASCII che comprende un certo numero di caratteri degli alfabeti europei. È compatibile all’indietro con ASCII: estende i soli caratteri >127

## UNICODE

Lo standard Unicode definisce tre codifiche che consentono a uno stesso dato di essere trasferito utilizzando un vocabolario basato su 1, 2 o 4 byte: UTF-8, UTF-16, UTF-32. Queste tre codifiche descrivono gli stessi caratteri e possono essere trasformate efficientemente una nell'altra.

### Caratteristiche

- **Composizione dinamica**. Alcuni caratteri (in arabo, in cinese, ma anche, banalmente, le lettere accentate o con modificatori degli alfabeti europei) sono composizioni di codifiche indipendenti. In certi casi ricorrere ad un doppio codice per un carattere composto è eccessivo. Per i simboli di uso frequente esiste un singolo carattere equivalente

- **Semantica**. Ogni carattere possiede un suo significato preciso (la ß tedesca è diversa dalla ß greca) nonché proprietà come direzione, esigenze di spaziatura, capacità di combinazione

- **Convertibilità**. Esiste un meccanismo di conversione tra Unicode e altre codifiche precedenti, in modo da garantire compatibilità all’indietro

### Codifiche

#### UTF-8

I caratteri più frequenti sono codificati con **1 byte**, poi 2, 3 e 4 per i meno frequenti. Usato molto nel WEB. Ha il vantaggio che il set di caratteri ASCII mantiene la stessa codifica, può quindi essere usato su vecchie applicazioni. Ma non si accede direttamente a una codifica prima si deve codificare come raggruppare i byte

#### UTF-32

Ogni carattere è codificato da **4 byte**. Usato quando non si ritiene di avere problemi di memoria oppure se si fa uso di vocabolari poco frequenti

#### UTF-16

Caratteri codificati **da copie di byte**, 2 copie per i meno frequenti. Usato per situazioni dove si vuole bilanciare l'uso di memoria con la velocità di accesso ai dati

![UTF](img/UTF.png)



## Problemi di codifica

Se UNICODE è uno standard universale, in grado di rappresentare i caratteri di tutti gli alfabeti, perché ci sono ancora problemi di codifica?

Il **Byte Order Mark** (**BOM**) è una sequenza di byte UNICODE non stampabili posta all'inizio di un testo UNICODE per facilitarne l'interpretazione. BOM non è né standard né obbligatorio, ma rende più facile per le applicazioni compatibili determinare il sottotipo del formato Unicode e definire la direzione di lettura dei byte. Questo spesso causa problemi di compatibilità perché non tutte le applicazioni sanno come gestire BOM. Per le applicazioni non compatibili, questa sequenza di byte viene decodificata in ASCII esteso.

## Determinare codifica di un file

**Indipendentemente dall'origine di un file**, può essere utile verificare con assoluta certezza il suo formato e mostrare l'eventuale tag BOM.

Se all'inizio del file è presente un tag BOM, si tratta di un testo in formato Unicode:

- UTF-8 = EF BB BF 
- UTF-16 Big Endian = FE FF 
- UTF-16 Little Endian = FF FE 
- UTF-32 Big Endian = 00 00 FE FF  
- UTF-32 Little Endian = FF FE 00 00

premere [qui](https://validator.w3.org/i18n-checker/) per accedere al validatore di W3.org

L’assenza del BOM non consente di stabilire che il file non sia codificato in UNICODE, a volte rimuoverlo può aumentare la compatibilità con alcune applicazioni.

