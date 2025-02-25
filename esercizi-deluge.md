# esercizi-deluge

Creare in questa repository su github, un branch con nome "esercizio X deluge", X sta per il numero dell'esercizio, e per ogni branch (esercizio) creare un file con estensione '*.dg'. Scrivere la funzione su ambiente zoho crm e una volta testata la funzione copiarla nel file con estensione dg su github eseguendo un commit e push da riga di comando/app desktop.

## ES 1

Realizzare un'automazione con funzione associata per:

- recuperi due numeri A e B, da due campi di un modulo;
- calcoli il resto della divisione A/B;
- il risultato campo "Risultato" deve salvare il messaggio testuale: "Il resto della divisione A/B è: C".

## ES 2

Dichiarare una lista di 10 numeri. Per ogni elemento della lista verificare che:

- L'elemento sia un numero compreso tra 0 e 50:
  - Se no, stampare messaggio di errore;

- L'elemento sia un numero pari:
  - Se no, stampare messaggio "numero X dispari"
  - Altrimenti, stampare messaggio "numero X pari"

## ES 3

- Creare un campo "status" all'interno del modulo Azienda e Contatti. Quando in azienda il campo status viene aggiornato in "sospeso" aggiornare il campo omonimo di tutti I contatti associati a quella azienda con il medesimo valore. Il campo "status" è una picklist ['sospeso', 'avviato', 'concluso'] e il valore inserito nei contatti (sospeso) se non è presente sui valori della picklist, cosa succede?
- Creare un modulo "Richieste_Trattative" con un campo valuta "valore" e un lookup collegato alle trattative (modulo Affari). Quando la fase di una trattativa passa a "chiusa vinta" creare un record omonimo all'interno del modulo Progetti e, nella stessa chiamata, popolare il campo "valore" con lo stesso valore della trattativa e collegare la trattativa al record creato.

## ES 4

- Creare dei prodotti tramite una invokeUrl dal sito [fakestoreapi](https://fakestoreapi.com/), utilizza una creazione massiva.
- Nel modulo prodotti con almeno 300 records, recuperare una lista ordinata per data modifica dei record dal numero 201 al 250 (search o query COQL).

## ES 5

- Creare una funzione associata a un bottone (all'interno di un record di visualizzazione) nel modulo Contatti, al click la funzione deve recuperare il nome dell'azienda collegata (se presente) e sul servizio di Zoho chiamato "Project", all'interno del progetto chiamato "prova", creare un task con lo stesso nome dell'azienda, status "Attivo" e scadenza tra una settimana dalla creazione del task.

Aiuto: utilizzare le integration task di [zoho project](https://www.zoho.com/deluge/help/projects/create.html) per creare un task su project.

Aiuto 2: per creare una funzione su un bottone, andare su configurazione -> cerca la voce "collegamenti e pulsanti" e cliccare su nuovo pulsante

## ES 6

- Creare una funzione che si triggera alla modifica di un qualsiasi campo di un record del modulo affari e salvi tutti i campi in formato json in un file sul servizio di Zoho "Workdrive" e carichi una copia di esso nella Related list "allegati" dello stesso record.

Aiuto: utilizzare le integration task di [zoho workdrive](https://www.zoho.com/deluge/help/workdrive/upload-file.html) per creare un file su workdrive.

Aiuto 2: utilizzare le integration task di [zoho crm](https://www.zoho.com/deluge/help/crm/attach-file.html) per allegare un file nella related list "Allegati" di un record.

## ES 7

- Creare una funzione da pulsante, nel modulo lead, legge tutti i record (posizionarlo nella vista di tutti i record) e convertire in Contatto il Lead se:
  - "Stato Lead" e' impostato su "Contacted";
  - "Origine Lead" e' impostato a "Employee Referral";
- Crea a piacere massivamente almeno 100 lead con "Stato Lead" random tra quelli proposti e aggiungere ad alcuni di essi dei prodotti;
- Nella conversione il nuovo contatto dovra' avere tutte le informazioni precedenti del lead (nome, via, cellullare, email, ecc...) e lo "status" in "attivo";
- Assicurarsi che i prodotti collegati vadano collegati correttamente al nuovo contatto;
- Eventuali Lead che non soddisfano i requisiti di conversione, dovranno essere cancellati definitivamente dal CRM.

## ES 8

- Creare una funzione, con trigger: qualsiasi modifica sui Contatti;
  - la funzione deve eseguirsi se il contatto ha collegato almeno un prodotto;
  - se contiene almeno un prodotto "ATTIVO" recuperare il prodotto e creare un record nel modulo Affari con:
    - nome del prodotto con l'aggiunta della stringa "-new-prodotto-[count]" (count inserito se i prodotti sono piu' di uno);
    - contatto collegato;
    - azienda collegata (se presente);
    - data di chiusura a tre giorni dalla data di creazione;
    - calcolare l' "Importo Richiesto" tramite questo calcolo dal prodotto: ("Prezzo Unitario" * "Quantita' ordinata") + ("imposta" calcolata da percentuale, se il campo "Tassabile" e' selezionato);

N.B.: creare i prodotti, i contatti, e aziende a piacere; Inserire i dati di calcolo dell'importo a tutti i prodotti creati. Nessun prodotto deve essere sprovvisto di almeno: Prezzo Unitario e Quantita' ordinata, e almeno 2 prodotti devono essere tassabili sull'iva 22%.
  
## ES 9

- Creare un [modello template](https://help.zoho.com/portal/en/kb/writer/user-guide/creating-managing/working-with-templates/articles/working-with-templates-writer#Using_public_templates) su Zoho Writer con alcuni campi unione ([placeholder](https://help.zoho.com/portal/en/kb/writer/user-guide/editing-formatting/working-with-fields/articles/working-with-fields#Autofields)) del modulo affari, modello a piacere.
- Creare un pulsante associanta a una funzione che se cliccato su singolo record del modulo Affari dovra':
  - fare il [merge document API di zoho writer](https://www.zoho.com/writer/help/api/v1/merge-document.html) per la creazione di un pdf;
  - allegare il file pdf al record selezionato da pulsante nella related list "Allegati".
