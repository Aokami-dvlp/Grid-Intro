# GRID

I grid sono un prezioso supporto nella creazione di layout responsive per i nostri lavori.

La struttura di base è molto semplice e consiste in 5 righe di codice:

Innanzitutto, come per i flexbox definiamo un container:
```
.container {}
```
Definiamo che questo container dovrà contenere un grid:
```
 .container {
     display: grid;
 }
```
Successivamente andiamo a definire righe e colonne della nostra griglia:
```
 .container {
     display: grid;
     grid-template-row: 100px auto 100px;
     grid-template-column: 20% 80%;
 }
```
In questo modo abbiamo definito una griglia con 3 righe, la prima e l'ultima di height 100px che andranno a costituire header e footer per il nostro layout, mentre quella centrale di height auto andrà ad adattare le sue dimensioni a quelle del suo contenuto.
Per quanto riguarda le colonne abbiamo stabilito 2 colonne (che si svilupperanno da sinistra a destra seguendo il naturale flow della pagina), la prima occuperà il 20% della larghezza della pagina (andando a costituire una sidebar) mentre l'altra occuperà il restante 80% e sarà l'area dei nostri contenuti.

Con queste istruzioni il browser è già in grado di renderizzare la nostra griglia, non gli sarà però chiaro come posizionare gli elementi al suo interno.

A questo proposito ci viene in soccorso l'istruzione grid-template-areas la quale ci permette di definire quali celle della nostra griglia utilizzare per sistemare i nostri contenuti, esponendoli semplicemente riga per riga:
```
 .container {
     display: grid;
     grid-template-row: 100px auto 100px;
     grid-template-column: 20% 80%;
     grid-template-area: 
     "header header"
     "sidebar content"
     "footer footer";
 }
```
In questo modo abbiamo assegnato un ruolo a tutte le celle che vanno a formare la nostra grid di 3 righe e 2 colonne.
ora non ci resta che andare a comunicare ai nostri elementi a quale area devono fare riferimento:
```
 .container {
     display: grid;
     grid-template-row: 100px auto 100px;
     grid-template-column: 20% 80%;
     grid-template-area: 
     "header header"
     "sidebar content"
     "footer footer";
 }

 .header {
     grid-area:header;
 }
 
 aside {
     grid-area:sidebar;
 }

 .articles {
     grid-area:content;
 }

 footer {
     grid-area:footer;
 }
 ```

Nella definizione delle dimensioni di righe e colonne, una unità di misura che può essere molto utile è **fr** la quale ci divide la pagina in frazioni in base alle quantità indicate. Ad esempio:
```
grid-template-row: 1fr 2fr 1fr 1fr; /*Crea 4 righe con dimensione 20% 40% 20% 20%*/ 
grid-template-column: repeat(3, 1fr); /*Crea 3 colonne con dimensione 33% 33% 33%*/
```
Per quanto riguarda il posizionamento degli elementi invece, possiamo, alternativamente alla combinazione **grid-template-area** e **grid-area** effettuare un posizionamento preciso sfruttando le linee della griglia (**attenzione, il riferimento sono le linee che dividono le celle non le righe della griglia**). Ad esempio:
```
grid-column: 4/5; /* l'elemento si estende dalla linea verticale 4 alla linea verticale 5 della griglia*/
grid-row: 2/6; /*l'elemento si estende dalla linea orizzontale 2 alla linea orizzontale 6 della griglia*/
```

Il codice all'interno della repo può essere utilizzato per esercitarsi e vederne il comportamento.