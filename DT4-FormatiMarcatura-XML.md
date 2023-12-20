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

![SLIDE 12](img/LT4-FormatiMarcatura-XML/)

Con XML semplici file di testo possono essere usati per condividere dati o per configurare applicazioni (leggibilità per macchina e utente): RSS, Calendar, Apache

**TEI (Text Encoding Initiative)**, per codifica di testi letterari .

## Multicanale
![SLIDE 13](img/LT4-FormatiMarcatura-XML/)

### Web 2.0
![SLIDE 14](img/LT4-FormatiMarcatura-XML/)
Ora sostituito da JSON

## Inforset XML
XML Infoset è un modello astratto dei dati XML
- descrive le relazioni valide tra gli elementi di un XML
- è un modo alternativo di definire la sintassi che risulta più adeguato all’uso di applicazioni come parser, strumenti di query, API di vari linguaggi

![Infoset XML](img/LT4-FormatiMarcatura-XML/Infoset_XML.png)

Source: https://www.ukoln.ac.uk/metadata/dcmi/dc-elem-prop/

## Sintassi
Sintassi semplice ma rigida:
- dichiarazione XML
- la dichiarazione di schema è opzionale
- è richesto un nodo radice
- chiusura degli elementi
- corretto annidamento (albero)
- rispettare il vincolo di “case sensitive”
- elemento - attributo - valore
- il ritorno a capo è sempre memorizzato con un LF
- caratteri riservati < > ‘ “ &
- commenti e CDATA


```xml
<?xml version-"1.0" encoding-"UTF-8"?»
<poem type="elegy">
 <author>Rupert Brooke</author>
 <date>1912</date>
 <!-- The title is not original but imposed to the scope of this collection-->
 <title>Song</title>
 <stanza>
  <line> And suddenly the wind comes soft, </line>
  <line> And Spring is here again; </line>
  <line> And the hawthorn quickens with buds of green </line>
  <line> And my heart with buds of pain. </line>
 </stanza>
 <stanza>
  <line> My heart all Winter lay son numb, </line>
  <line> The earth so dead and frore, </line>
  <line> That I never thought the Spring would come again </line>
  <line> Or my heart wake any more. </line>
 </stanza>
 <stanza>
  <line> But Winter`s broken and earth has woken, </line>
  <line> And the small birds cry again; </line>
  <line> And the hawthorn hedge puts forth its buds, </line>
  <line> And my heart puts forth its pain. </line>
 </stanza>
 <source>
  <![CDATA[ http://www.example.org/docbook/xml/4.1.2/repository.xml&poem ]]>
 </source>
</poem>
```

### Documenti ben formati
Se la sintassi è rispettata il documento **è ben formato**
- Un programma che definisce se un documento è ben formato è detto parser
- Seguendo le regole sintattiche il **parser** analizza il documento seguendo la sua struttura ad albero se non riesce a costruire l’albero il documento non è valido
- Alcuni parser costruiscono una rappresentazione in memoria del documento, da sfruttare ai fini di interrogazione

### Documenti validi
**È valido** un documento conforme a uno schema DTD o XML Schema (xsd)
- Lo schema descrive la struttura di un documento XML e alcuni vincoli di integrità sui dati
- La struttura (albero XML) è conforme allo schema ovvero è un’istanza dello schema

### Dichiarazione
Parte dello standard XML 1.0
Nodo DOCTYPE
- riporta il riferimento all’URI del DTD <br/>
 es:  
``` <!DOCTYPE archivioDomande SYSTEM "pdd_0_2.dtd"> ```
- SYSTEM indica uno schema locale. Alcuni DTD molto utilizzati hanno un “nome” pubblico (PUBLIC); come il DTD di XHTML, <br/>
   es:  ``` <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN“ "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> ```

### Nodi di un DTD
- Nodi ordinari: documento ed elementi
- Nodi per attributi: vincoli sugli attributi (nome e tipo)
- Nodi per i valori (#PCDATA)
- Nodi speciali
 - nodi che descrivono l’ordine degli elementi sequenza o alternativa
 - indicatori di cardinalità

#### Elementi
**Dichiarazioni di elementi**
Ogni dichiarazione di elemento contiene il nome dell’elemento e il tipo di dati definito da uno tra i seguenti quattro tipi:
- Altri elementi
- Contenuto di testo PCDATA
- Qualunque altro elemento (parola chiave ANY)
- Elemento vuoto (parola chiave EMPTY)

```<!ELEMENT EMAIL (TO, FROM, CC, SUBJECT, BODY)>```

Le specifiche di contenuto possono essere costituite da un insieme di alternative separate da pipe (|):
```<!ELEMENT EXAMPLE (#PCDATA|x|y|z)*>```
Indicatori di cardinalità:
- una o più occorrenze – 1..* oppure +
- zero o una occorrenza – 0..1 oppure ?
- zero o più occorrenze – 0..* oppure *

Se una dichiarazione di elemento utilizza la parola chiave ANY, l’elemento potrà avere qualsiasi tipo di contenuto disposto in un qualsiasi ordine :
``` <!ELEMENT TEST ANY>```

Per dichiarare che un elemento non può avere alcun contenuto, si utilizza la parola chiave EMPTY
```<!ELEMENT soluzione EMPTY>```
Un elemento dichiarato come elemento vuoto può avere attributi:
```<soluzione lettera="b" />```

#### Attributi
In un DTD, gli attributi vengono dichiarati utilizzando:

```<!ATTLIST ElementName AttributeName Type Default>```
- _ElementName_ rappresenta il nome dell’elemento a cui vengono associati gli attributi
- _AttributeName_ rappresenta il nome dell’attributo
- _Type_ identifica il tipo di attributo dichiarato
- _Default_ specifica le impostazioni predefinite relative all’attributo

##### Tipi di attributo
- **CDDATA** : Un attributo di tipo CDATA utilizza dati generici in formato carattere.
- **ENTITY** : Il valore dell'attributo fa riferimento a un'entità dichiarata nel DTD (argomento spiegato successivamente).
- **ENTITIES** : è equivalente all'attributo ENTITY, ma consente l'utilizzo di valori separati da spazi.
- **ID** : Il valore dell’attributo deve essere un **identificatore univoco**. In un documento XML, un solo attributo di tipo ID puo’ essere definito. Viceversa, il parser produce un errore.
- **IDREF** : Il valore deve essere un riferimento a un ID associato ad un altro elemento del documento XML. Se l’attributo non corrisponde ad valore esistente, il parser produrrà un errore.
- **IDREFS** : È equivalente all’attributo IDREF, ma consente l’utilizzo di più valori separati da spazi.
- **NMTOKEN** : Il valore dell’attributo puo’ contenere caratteri alfanumerici (numeri e lettere) e i caratteri "." (punto), "-" (trattino), "_" (underscore), ":" (due punti). Permette un controllo più fine su ciò che verrà specificato come valore dell'attributo. 
- **NMTOKENS** : È equivalente all’attributo NMTOKEN, ma consente l’utilizzo di più valori separati da spazi. 
- **Enumerated** : Il valore dell’attributo deve corrispondere a uno dei valori inclusi. Ad esempio: ```<!ATTLIST MyAttribute (valore1 | valore2)>```.  

#### Entità
Un'entità è un modo per definire singoli blocchi di informazioni.
Faccio riferimento ad entità esterne o interne per includerle in documenti. Possono essere file diversi o risorse accessibili via URL

XML usa un meccanismo di riferimenti per includere un’entità in un’altra (ad esempio includere una parte di codice XML contenuto in un certo file, all’interno di un documento XML)

***Esempio di entità***
Dichiarazione di entità generale interna (in DTD)
```xml
 <!ENTITY digits “0123456789”>
```
``` xml
 <!ENTITY LR1 "light requirement: mostly shade“>
```

Uso di entità generale interna (in documento XML)
```xml 
 <numeri>&digits;</numeri>
```
```xml 
 <dicitura>&LR1;</dicitura>
```

***Esempio DTD***
```xml
<?xml version="1.0" encoding="UTF-8"?>

<!ELEMENT poem (author+, date, title, stanza+, source?)>

<!ATTLIST poem type (elegy|ballad|song) #IMPLIED>

<!ELEMENT author (#PCDATA)>
<!ELEMENT date (#PCDATA)>
<!ELEMENT title (#PCDATA)>
<!ELEMENT stanza (line+)>
<!ELEMENT source (#PCDATA)>
<!ELEMENT line (#PCDATA)>
```

# XML schema
## Cos'è uno schema XML
Gli Schemi XML sono un miglioramento dei DTD.

Sono documenti XML e descrivono la struttura di un documento XML
- Definisce gli elementi che possono apparire in un documento
- Definisce le relazioni tra elementi (padre-figlio)
- Definisce l’ordine degli elementi
- Definisce il numero degli elementi
- Definisce quando un elemento può contenere testo o essere vuoto
- Definisce il tipo di elementi ed attributi
- Definisce valori fissi o di default per elementi ed attributi

## XML schema vs DTD
I DTD sono ancora molto diffusi, ma vengono via via sostituiti
dagli Schemi XML.

XML Schema ha dei vantaggi rispetto DTD:
- Sono adatti per futuri ampliamenti
- Sono più completi ed dettagliati dei DTD
- Sono documenti XML
- Supportano i tipi di dati (datatypes)
- Supportano i namespace

Gli schemi XML sono stati proposti da Microsoft. Sono diventati una raccomandazione del W3C nel Maggio 2001.

## Supporto dei tipi di dati
Uno dei maggiori punti di forza di XML Schema è quello di
supportare i tipi di dati (datatypes)

Grazie a questo supporto
- È più facile descrivere la struttura di un documento
- È più facile controllare la correttezza dei dati
- È più facile lavorare con dati provenienti da database
- È più facile definire restrizioni sui dati
- È più facile definire il formato dei dati
- È più facile convertire dati da un tipo all’altro

## Estendibilità
Come XML anche gli schemi sono estendibili.

Con uno schema è possibile:
- Riusare uno schema all’interno di altri
- Creare dei propri tipi di dati derivandoli da quelli standard
- Fare riferimento a più schemi dallo stesso documento

***Esempio: documento XML***
```xml
<EMAIL>
 <TO>mrossi@rossi.it</TO>
 <FROM>pbianchi@bianchi.it</FROM>
 <CC>gverdi@verdi.it</CC>
 <SUBJECT>Primo DTD</SUBJECT>
 <BODY>Doc XML con un DTD</BODY>
</EMAIL> 
```
***Esempio: DTD***
Quello che segue è il DTD corrispondente
```xml
<!ELEMENT EMAIL (TO, FROM, CC, SUBJECT, BODY)>
 <!ELEMENT TO (#PCDATA)>
 <!ELEMENT FROM (#PCDATA)>
 <!ELEMENT CC (#PCDATA)>
 <!ELEMENT SUBJECT (#PCDATA)>
 <!ELEMENT BODY (#PCDATA)>
```
***Esempio: XSD***
```xml
<?xml version=“1.0” encoding=“ISO-8859-1”?>
<xs:schema xmlns:xs=“http://www.w3c.org/2001/XMLSchema”
 targetNamespace=“http://www.mioindirizzo.org”
  elementFormDefault=“qualified”>
 <xs:element name=“EMAIL”>
  <xs:complexType>
   <xs:sequence>
    <xs:element name=“TO” type=“xs:string”/>
    <xs:element name=“FROM” type=“xs:string”/>
    <xs:element name=“CC” type=“xs:string”/>
     <xs:element name=“SUBJECT” type=“xs:string”/>
    <xs:element name=“BODY” type=“xs:string”/>
   </xs:sequence>
  </xs:complexType>
 </xs:element>
</xs:schema>
```

## L'elemento schema
È l’elemento radice di ogni XML schema.

Può contenere alcuni attributi. _Esempio_:
```
 <xs:schema xmlns:xs=“http://www.w3c.org/2001/XMLSchema”
  targetNamespace=“http://www.mioindirizzo.org”
  elementFormDefault=“qualified”>
```
Il seguente frammento indica che gli elementi e i datatype usati nello schema (schema, element, complexType, sequence) appartengono al namespace ```http://www.w3c.org/2001/XMLSchema```

```xmlns:xs=“http://www.w3c.org/2001/XMLSchema”```

Indica inoltre che gli elementi appartenenti a questo namespace devono essere preceduti da xs:
- Il frammento ```targetNamespace=“http://miapagina.org”``` indica che gli elementi definiti dallo schema ```(EMAIL, TO, FROM, CC, SUBJECT e BODY)``` appartengono al namespace ```“http://miapagina.org”```
- Il frammento ```elementFormDefault=“qualified”``` indica che gli elementi usati nei documenti XML conformi a questo schema, hanno nomi qualificati

### Spazio dei nomi
Il prefisso del spazio dei nomi, a meno che si tratti di xml o di **xmlns**, DEVE essere dichiarato:
- In un attributo di dichiarazione del spazio dei nomi
```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/css" href="/stylesheets/rss.css"?>
<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/"
 xmlns:trackback="http://madskills.com/public/xml/rss/module/
 trackback/">
```

- Nel tag iniziale dell’elemento in cui il prefisso è usato o in un elemento antenato
 ```xml
<!-- il spazio dei nomi dell’elemento 'price' è http://ecommerce.example.org/schema -->
<edi:price xmlns:edi='http://ecommerce.example.org/schema'
 units='Euro'>32.18</edi:price>
```

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


