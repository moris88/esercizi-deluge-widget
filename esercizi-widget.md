# esercizi-widget

Creare in questa repository su github, un branch con nome "esercizio X widget", X sta per il numero dell'esercizio, e per ogni branch (esercizio) creare un progetto react. Scrivere il codice su ambiente VSCODE e una volta testata il codice eseguire un commit e push da riga di comando/app desktop.

### REQUISITI

- Linguaggio di programmazione: Javascript;
- Basi di React;
- HTML e CSS.

## ES 1

Prima di proseguire rivedere le [Promise](https://github.com/moris88/Promise).

Realizzare una interfaccia web (HTML & Javascript) che restituisca a video:

- 2 post, solo i primi due;
- 5 todo, non adiacenti (es: 1,3,8,10,14);
- 5 user, solo con id dispari.

da un servizio server gratuito chiamato [JsonPlaceholder](https://jsonplaceholder.typicode.com/).

Output che deve restituire:

```html
<div>
    <div>
        <p>POST:</p>
        <ul id='posts'>
            <li> post 1</li>
            <li> post 2</li>
            <li> ...</li>
            <li> post n</li>
        </ul>
    </div>
    <div>
        <p>TODO:</p>
        <ul id='todos'>
            <li> todo 1</li>
            <li> todo 2</li>
            <li> ...</li>
            <li> todo n</li>
        </ul>
    </div>
    <div>
        <p>UTENTI:</p>
        <ul id='users'>
            <li> user 1</li>
            <li> user 2</li>
            <li> ...</li>
            <li> user n</li>
        </ul>
    </div>
</div>
```

Consiglio:

- usare le chiamate http native di javascript [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API), senza uso di librerie esterne.

Esempio di request http:

```javascript
fetch('https://jsonplaceholder.typicode.com/comments/1')
    .then(response => response.json())
    .then(json => console.log(json))
```

N.B.: utilizza React, bonus con Typescript, style dell'app irrilevante.

## ES 2

Prima di proseguire rivedere la documentazione Zoho [SDK.js](https://help.zwidgets.com/help/v1.2/index.html) o [SDK.ts](https://github.com/crmpartners/crmpartnerslib/blob/main/use.md) e la [cli](https://github.com/crmpartners/crmpartnerscli).

Realizzare un widget-demo utilizzando il template-widget-zoho della cli aziendale, per realizzare un widget (installarlo su un modulo tra Lead, Contatti, Affari o Aziende, in una related list) che faccia:

- stampi in un riquadro modulo e id del record in cui il widget si avvia;
- abbia 5 pulsanti (getRecord, updateRecord, deleteRecord, createRecord e reloadRecord) che cliccando facciano:
  - 1: getRecord - stampi in un riquadro sotto, il record in cui il widget si avvia, ma solo i campi: nome, cognome, email;
  - 2: updateRecord - far comparire un form per aggiornare due campi a piacere del record, stampando un alert di successo o errore;
  - 3: deleteRecord - far comparire un alert di conferma, e se si clicca ok, cancellare il record, altrimenti no;
  - 4: createRecord - indirizzare l'utente alla pagina di creazione di un nuovo record;
  - 5: reloadRecord - ricaricare il record in cui il widget si avvia.

## ES 3

Realizzare un widget-demo utilizzando il template-widget-zoho della cli aziendale, per realizzare un widget (installarlo su un modulo tra Lead o Contatti, nella pagina della lista record al click di un pulsante) che faccia:

- lista tabellare dei record del modulo (solo tre campi: nome, cognome, email);
- cliccando su un record dalla tabella far comparire un modale con dettagli del record selezionato (almeno 8 campi a piacere);

## ES 4

Realizzare un widget-demo utilizzando il template-widget-zoho della cli aziendale, per realizzare un widget (installarlo sul modulo affari, in una related list), che faccia:

- aggiungere una lista in formato tabellare dinamica, aggiungendo righe (prodotti) dall'apposito pulsante;
- poter modificare i campi (prodotto, descrizione, quantita', prezzo, sconto, tassa) dinamicamente, e calcolare l'importo (quantita' *prezzo + (tassa = quantita'* prezzo *tassa / 100) - (sconto = quantita'* prezzo * sconto / 100);
- poter eliminare la riga creata dal pulsante;
- nel footer della tabella applicare la somma degli importi;
- aggiungere sotto la tabella il pulsante "salva" che salva le informazioni della tabella, in un campo (JSON) del modulo "affari", questo perche' all'avvio del widget se sono presenti dati deve recuperarli e visualizzarli nella tabella.

```JSON
fattura: [
    {
        descrizione: "",
        prodotto: {
            id: "73248174687124",
            name: "Samsung S20",
        },
        quantita': 2,
        prezzo: 300,00,
        sconto: 5%,
        tassa: 22% IVA
        importo: 580,00,
    },
    ...
]
```

Lista operazioni widget:

1. getRecord() -> campo JSON;
2. if (JSON popolato?) sei si le info vanno nella tabella altrimenti tabella vuota;
3. recupero tutti i prodotti getRecords();
4. pulsante "aggiungi" -> aggiungere una riga alla tabella -> seleziona un prodotto i campi quantita', prezzo, sconto e tassa devono essere inizializzati dai dati del prodotto;
5. click sul pulsante "salva" -> updateRecord() -> campo JSON (con le info della tabella modificata dall'utente).

Screen esempio widget:

![image](https://github.com/crmpartners/esercizi-formazione/assets/37340833/5986d81c-ad4e-453e-aea8-cd27fee1b99d)

## ES 5

Realizzare un widget-demo utilizzando il template-widget-zoho della cli aziendale, per realizzare un widget (installarlo sul modulo contatti, in un pulsante), che faccia:

- visualizzi tutti i contatti su una tabella (nome, cognome, email, eta, data di nascita, azienda);
- aggiungere i seguenti filtri:
  - nome (nell'input, aggiungere il componente Autocomplete);
  - email (nell'input, aggiungere una espressione regolare);
  - data di nascita (nell'input, aggiungere un componente DataPicker);
  - azienda (nell'input, aggiungere il componente Autocomplete);
  - eta (nell'input, aggiungere un componente Numerico);
- aggiungere un pulsante "filtra" che applica i filtri, sopra citati, alla tabella;
- aggiungere un pulsante "aggiunti a Cliente" (deve comparire quando selezioni almeno un contatto) che ti apre un modale, far selezionare il cliente attraverso un autocomplete (o select), successivamente al click "ok" aggiungere tutti i contatti selezionati, sotto forma di JSON, aggiornando il campo nel modulo "clienti" nel campo "JSON";

Realizzare un secondo widget (nel modulo clienti, come related list) utilizzando la libreria "react-router" con un secondo path, che faccia:

- visualizzi i contatti selezionati all'interno del campo "JSON" del modulo "clienti", sotto forma di tabella;

![image](https://github.com/crmpartners/esercizi-formazione/assets/37340833/13f76592-b0ab-4150-b196-6f4b46d2ba65)

N.B.: utilizza tailwind css.

## ES 6

Esercizio: Sviluppo di un Widget per Zoho CRM con Generazione PDF

Obiettivo:

Sviluppare un widget personalizzato per Zoho CRM che:

1. Recuperi una un record di Zoho CRM (es. Leads o Opportunità).
2. Formatti i dati in un documento utilizzando le API di Zoho Writer.
3. Generi un PDF e lo renda disponibile per il download all’interno del widget.

Requisiti Tecnici:

- Stack Tecnologico: React, Typescript, Zoho CRM SDK, Zoho Writer API

Chiamate API:

- Zoho CRM coql per ottenere i dati del record
- Zoho Writer API per creare e convertire il documento in PDF (merge document)

Passaggi da Sviluppare:

1. Creare il widget all’interno di Zoho CRM usando il proprio ambiente di sviluppo.
2. Ottenere il record dal modulo CRM scelto (ad esempio Leads).
3. Strutturare i dati per la generazione del documento (visualizzare il dettaglio).
4. Utilizzare Zoho Writer API per creare un documento con i dati del record.
5. Convertire il documento in PDF e fornire un link di download.

Extra (Opzionale ma graditi):

- Aggiungere filtri per scegliere solo alcuni dati.
- Salvare il PDF come allegato nel CRM.
