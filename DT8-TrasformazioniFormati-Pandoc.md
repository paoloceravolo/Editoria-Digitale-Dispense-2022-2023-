# Trasformazioni di formato

La gestione di un workflow implica la gestione di passaggi di trasformazione da un formato a un altro.

Idealmente si parte da formati semplici e portabili per poter ottenere molteplici formati di destinazione.

Insieme al contenuto testuale è necessario gestire file multimediali e riferimenti ad altri documenti (include, citazioni, link).

Le trasformazioni avvengono attraverso la rappresentazione di un formato in un modello intermedio (spesso resta solo nella memoria del programma di trasformazione) che poi può essere trasformato in un formato di destinazione.
- Diventa quindi essenziale conoscere la struttura e l’espressività del modello intermedio di riferimento
- Tipicamente i formati usati per i sorgenti dei contenuti sono meno espressivi o al più espressivi come il formato intermedio
- I formati di destinazione potranno essere più espressivi del formato intermedio e potranno essere quindi necessari degli interventi manuali (_Esempio:_ formattazione tabelle) 

# Pandoc
[Pandoc](https://pandoc.org/MANUAL.html) è una libreria scritta in Haskell per la conversione di documenti da un formato di origine a formato di destinazione.

Pandoc è in grado di convertire numerosi formati di markup e di elaborazione testi, tra cui vari tipi di Markdown, HTML, LaTeX, ePub e Word docx.

La versione estesa di Markdown usata da Pandoc include una sintassi per le tabelle, elenchi di definizioni, blocchi di metadati, note a piè di pagina, citazioni, formule matematiche e altro.

## Organizzazione
Pandoc ha un design modulare
- un insieme di reader, che analizzano un dato formato e producono una rappresentazione astratta del documento (un albero sintattico astratto o AST)
- un insieme di writer, che convertono questa rappresentazione astratta in un formato di destinazione

AST è meno espressivo di molti formati di marcatura, questo implica che le trasformazioni conserveranno la struttura dei documenti ma non certi dettagli di formattazione come i margini.

Gli utenti possono anche comporre degli script detti [pandoc filters](https://pandoc.org/filters.html) per modificare l'AST intermedio di un processo di trasformazione

## Come usarlo
Pandoc può essere stato in diversi modi:
- Da linea di comando
```
pandoc -o output.html input.txt
pandoc -s -o output.html input.txt
pandoc -f markdown -t latex hello.txt
```
- Attraverso interfaccia online https://pandoc.org/try/
- Attraverso Python https://pypi.org/project/pandoc/
- Interfacciandosi attraverso la sua API https://hackage.haskell.org/package/pandoc

### Installazione
Per installare Pandoc è possibile usare diversi strumenti https://pandoc.org/installing.html
- Installer forniti dalla distribuzione
- Attraverso diversi sitemi software management come Chocolatey, Brew, Crew, …
- Attraverso Docker

Per un funzionamento completo, oltre alla libreria è necessario installare
- [Python](https://www.python.org/) per l’esecuzione dei Pandoc filter
- un motore LaTex (
 [MiKTeX](https://miktex.org/)
 [BasicTeX](https://www.tug.org/mactex/morepackages.html)
 [MacTeX](https://tug.org/mactex/)
 [TeX Live](https://www.tug.org/texlive/)
 ) per la compilazione di file LaTex

Può essere necessario installare ulteriori estensioni per la gestione di particolari formati multimediali

### *Esempi* come usarlo
_Esempio 1_: Conversione di base

Pandoc consente di convertire documenti da un formato all'altro

```pandoc input.md -o output.pdf```


_Esempio 2_: Intestazione del documento

Puoi personalizzare il layout, ad esempio, con intestazioni e piè di pagina

```pandoc input.md -H header.tex -o output.pdf```


_Esempio 3_: Applicare un foglio di stile

È possibile migliorare l'aspetto dei documenti generati da Pandoc applicando un foglio di stile CSS. È necessario usare l’opzione -s per forzare la generazione del head

```pandoc -s input.md -o output.html --css stile.css```


_Esempio 4_: Unire documenti

Pandoc può unire più documenti in uno

```pandoc doc1.md doc2.md -o unione.pdf```


_Esempio 5_: Associazione di Metadati

È possibile utilizzare un file YAML esterno per specificare metadati da associare al documento

```
pandoc input.md -o output.pdf --metadata-file metadati.yaml
---
title: "Il mio documento"
author:
 - Nome Autore
 - Autore Aggiuntivo
date: 2023-11-02
keywords:
 - Pandoc
 - Metadati
 - YAML
abstract: "Questo è un esempio di documento Markdown con metadati in formato YAML."
---
```
## AST
L’Abstract Syntax Tree di Pandoc modella ogni documento come un albero di elementi
- Ogni documento appartiene a un tipo, il meta-modello del documento, che definisce come si strutturano gli elementi all’interno del documento
- Ogni elemento ha un tipo definito, ad esempio _paragrafo_, _immagine_, _nota_, _link_, ecc.

Se si desidera analizzare, creare o trasformare documenti, è necessaria una certa conoscenza del meta-modello

https://hackage.haskell.org/package/pandoc-types-1.22.2.1/docs/Text-Pandoc-Definition.html

## Filtri
Un filtro è un programma che modifica lo AST tra un reader e un writer
```
INPUT --reader--> AST --filter--> AST --writer-->
OUTPUT
```
È possibile scrivere questi programmi utilizzando LUA oppure JSON
```
INPUT --reader--> JSON-formatted AST --filter-->
JSON-formatted AST --writer--> OUTPUT
```
Ad esempio in Haskell è possibile
```
#!/usr/bin/env runhaskell
-- behead.hs
import Text.Pandoc.JSON

main :: IO ()
main = toJSONFilter behead

behead :: Block -> Block
behead (Header n _ xs) | n >= 2 = Para [Emph xs]
behead x = x
```

### Esempio
Uso di filtri personalizzati
I filtri personalizzati consentono di applicare trasformazioni speciali.
```
pandoc input.md --filter filtro.py -o
output.pdfpandoc input.md -o output.pdf
```
