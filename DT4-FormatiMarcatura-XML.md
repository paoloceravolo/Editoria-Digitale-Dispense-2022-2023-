# XML (Extended Markup Language)
Raccomandazione del W3C dal 1998
- pensato originariamente come sostituto di HTML per il Web
- inizialmente si insisteva sulla sua capacità di descrivere la semantica dei dati, proponendo molti esempi in ambiente distribuito
- fu subito accolto con entusiasmo ed ebbe una rapida diffusione

## Il ruolo di XML
In realtà si è imposto come formato di interscambio tra applicazioni
- interoperabilità
- portabilità
- semantica dei dati
Nelle applicazioni distribuite è oggi spesso sostituito da JSON
- Migliore integrazione nel codice
- Minore leggibilità per l’uomo

## Javascript Object Notation
JavaScript Object Notation (JSON) è un formato standard di testo per la rappresentazione di dati strutturati basato sulla sintassi degli oggetti JavaScript.

Viene comunemente utilizzato per la trasmissione di dati nelle applicazioni distribuite (ad esempio, l'invio di alcuni dati dal server al client, in modo che possano essere visualizzati su una pagina web, o viceversa).

JSON è una stringa il cui formato assomiglia molto al formato degli oggetti JavaScript. All'interno di JSON si possono includere gli stessi tipi di dati di base presenti in un oggetto JavaScript standard: stringhe, numeri, array, booleani e altri letterali di oggetti.

***Esempio JSON***
Questo permette di costruire una gerarchia di dati, come ad esempio:

```json
{
 "book": [
 {
 "id":"01",
 "language": "Java",
 "edition": "third",
 "author": [“Herbert Schildt”, “John Doe”]
 },
 {
 "id":"07",
 "language": "C++",
 "edition": "second",
 "author": "E.Balagurusamy"
 }
 ]
}
```

## Marcatura estensibile
XML è un linguaggio di marcatura ispirato da SGML
- ha una minore complessità
- utilizza le URI per lo spazio dei nomi degli elementi

È stato progettato per descrivere dati, prescindendo completamente dalla loro presentazione.

È estensibile, i tag non sono predefiniti, ed è quindi generico Un documento XML quando è associato ad un DTD o uno Schema è progettato per essere auto-descrittivo

Nel mondo reale diversi sistemi contengono dati in formato non uniforme era quindi necessario uno standard per i formati di interscambio.

**XML è uno strumento per trasmettere informazioni, indipendente dalla piattaforma, dal software e dall’hardware**

## Differenze con HTML
- Linguaggio di markup per la presentazione
- Progettato per la visualizzazione di un ipertesto
- Elementi predefiniti nella DTD HTML
- Blandamente definito e interpretato
- Linguaggio di markup per i contenuti
- Progettato per lo scambio di dati fra applicazioni software
- Consente elementi definiti da utente
- Strettamente definito e interpretato

### Esempi di applicazioni
** Modelli B2B (Business-to-Business) **, ovvero interazioni tra sistemi di diversi operatori economici, non interazioni con clienti finali sono. Uno dei settori maggiormente
interessato ad XML

**EAI (Enterprise Application Integration)**, ovvero l’integrazione tra applicazioni all’interno di un’azienda 

![SLIDE 12](img/DT4-FormatiMarcatura-XML/)

Con XML semplici file di testo possono essere usati per condividere dati o per configurare applicazioni (leggibilità per macchina e utente): RSS, Calendar, Apache

**TEI (Text Encoding Initiative)**, per codifica di testi letterari .

## Multicanale
![SLIDE 13](img/DT4-FormatiMarcatura-XML/)

### Web 2.0
![SLIDE 14](img/DT4-FormatiMarcatura-XML/)
Ora sostituito da JSON

## Inforset XML
XML Infoset è un modello astratto dei dati XML
- descrive le relazioni valide tra gli elementi di un XML
- è un modo alternativo di definire la sintassi che risulta più adeguato all’uso di applicazioni come parser, strumenti di query, API di vari linguaggi

![SLIDE 14](img/DT4-FormatiMarcatura-XML/)

[](https://www.ukoln.ac.uk/metadata/dcmi/dc-elem-prop/)

## Sintassi

### Documenti ben formati

### Documenti validi

### Dichiarazione

### Nodi di un DTD

#### Elementi

#### Attributi

##### Tipi di attributo

#### Entità

***Esempio di entità***

***Esempio di entità***

# XML schema

## Cos'è uno schema XML

## XML schema vs DTD

## Supporto dei tipi di dati

## Estendibilità

***Esempio: documento XML***

***Esempio: DTD***

***Esempio: XSD***

## L'elemento schema

### Spazio dei nomi

### Elementi di XSD

### Elemento semplice

### Tipi di dati comuni

### Valori di default e fissi

## Restrizioni sul contenuto

### Insiemi di valori: lista

### Pattern

### Restrizioni sulla lunghezza

## Attributi

### Definire un attributo

#### Tipi complessi

***Esempi***

## Indicatori

### Indicatori d'ordine

### Indicatori di occorrenza

#### Complextype

#### Riferire un complextype

***Esempio XSD***

### Indicatori di gruppo

#### Attributi di gruppo

***Esempio***

## Validatori per XML schema

## Tecnologie XML


