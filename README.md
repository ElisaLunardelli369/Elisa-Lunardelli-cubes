
If you wanna run this project you need a local server 

# Paesaggio marino

![paesaggio marino3](https://user-images.githubusercontent.com/79991821/149623708-25f0a9d7-80c8-43e7-8523-4a9609e5636e.JPG)

## Overview del progetto

La scena rappresenta un piccolo arcipelago con un faro e barca che attraversa il mare. Tutto è realizzato utilizzando cubi a cui vengono applicate trasformazioni. 

## Elementi del progetto

- TERRENO: è formato da una griglia 40x40 di altezza 3 sul piano più basso ricavata sfruttando una height map. Ogni elemento della griglia è influenzato dalla heightmap sotto due aspetti. Il primo è l'altezza e il secondo è il tipo di materiale. 
I valori contenuti nella heightmap non determinano direttamente l'altezza del cubo, ma servono per discriminare i diversi livelli o zone della mappa. Ogni livello di altitudine è un materiale diverso ed ha una altezza prestabilita. Questo approccio è possibile inquanto la scena che si va a creare è molto semplice, ma in uno scenario più complesso occorrerebbe fare delle considerazioni aggiuntive: la prima è che conviene ricavare l'altezza finale, che verrà applicata al cubo, direttamente in fase di estrapolazione dei valori di grigio (nel caso di questo progetto nella funzione getHeightData) in modo da evitare un controllo o confronto aggiuntivo per ogni elemento. La seconda considerazione è che il codice diventa molto legato ad una specifica heightmap e che quindi una volta scelta non si può cambiare facilmente in fase di creazione. Tuttavia questo approccio ha il vantaggio di rendere molto facile l'assegnazione dei materiali specie se si volesse rendere il terreno interagibile. 
Nel caso di questo progetto la discriminazione tra le varie altitudini avviene sfruttando un costrutto switch: non viene utilizzato un più comune if() per rendere il codice un po' più efficiente in quanto, con switch, non si fa il controllo su tutte le condizioni prestabilite fino a raggiungere il caso di verità, ma si salta direttamente ad eseguire il blocco di codice interessato. 

- OGGETTI DELLA SCENA:

![faro](https://user-images.githubusercontent.com/79991821/149623871-43f1fb78-2127-450f-a53f-fcddb6cdefd9.JPG)

![barca](https://user-images.githubusercontent.com/79991821/149623891-d6b8e373-e86e-47fe-b25f-5fe91f1c91af.JPG)

Gli oggetti della scena sono costruiti in modo molto semplice unendo primitive manipolate con trasformazioni. L'aspetto importante è che sono stati creati per essere il più comodi possibili da manipolare: ogni oggetto è rappresentato da un gruppo che contiene tutti i suoi elementi singoli. Questi vengono creati nell'origine con una grandezza arbitraria (maggiore di quella vista a schermo) e poi manipolati per costruire la forma finale rimanendo in quel punto. Una volta costruito l'oggetto è possibile scegliere la sua dimensione passando un valore di scala all'esecuzione della sua funzione di creazione. Questo permette di scegliere con facilità il valore di input guardando direttamente il risultato finale. Nel caso del faro è possibile scegliere anche la sua posizione allo stesso modo. Questo è stato possibile perchè gli elementi sono organizzati in gerarchia utilizzando una struttura a gruppo. Intervenendo sul gruppo si manipolano facilmente tutti gli elementi che contiene.

- ANIMAZIONE:L'animazione consiste nel far attraversare la zona di mare alla barca. La barca percorre una circonferenza appoggiata sul piano che coinvolge l'asse x e l'asse z quindi si è intervenuto su queste coordinate per l'animazione. Sfruttando la trigonometria sono state calcolate le coordinate di un punto (che rappresenta la posizione della barca) ad un determinato angolo. Variando questo angolo è possibile ottenere le coordinate di tutti i punti che disegnano la circonferenza. Inoltre è stata applicata una rotazione aggiuntiva alla barca in modo che la punta rimanga sempre orientata nel verso di navigazione. Il primo problema che si affronta in questa animazione è il fatto che utilizzando questa formula trigonometrica otteniamo valori compresi tra -1 e 1 e il risultato che otteniamo è quello di avere la barca che ruota attorno all'origine. La prima cosa da fare è moltiplicare il risultato per un valore scalare in modo che si allarghi il raggio della circonferenza che percorre la barca. Per poter posizionare la barca nel punto che più ci piace dobbiamo struttare di nuovo le gerarchie: è stato creato un gruppo con funzione di pivot. Al suo interno è presente la barca che ruota attorno alla circonferenza e su se stessa. Spostando il pivot si sposta anche il centro di questa circonferenza e quindi della animazione. Infine, per evitare che la barca navigasse al di fuori del terreno è stata introdotta una condizione in modo che la barca restasse sempre nella zona di circonferenza più o meno compresa tra 180° e 270°.
Per dare l'impressione che la barca sia immersa nell'acqua è stata fatta sprofondare un po' al di sotto della geometria del mare. Questo è avvenuto in fase di creazione della mesh della barca e non coinvolge l'animazione.

- LUCI E MATERIALI:
Le luci e i materiali sono stati scelti prendendo ad esempio il codice del file StartingCode-withLights inquanto permettevano di ottenere un effetto estetico molto gradevole. Inizialmente è stata applicata una sola luce ambientale, ma non si è dimostrata sufficiente. La presenza della directional light, delle ombre e del materiale di tipo phong ha donato alla scena un gradevole effetto pastello molto luminoso perfettamente in linea con il paesaggio marino.

- BACKGROUND: 
Ho impostato il colore di sfondo della pagina uguale a quello presente nel canvas, in modo che all'avvio del progetto, in caso ci metta un attimo a caricare gli elementi, non si veda uno stacco, ma che risulti un semplice pop-up della scena dando un effetto più gradevole.

## Credits

La heightMap terrain.png è stata realizzata utilizzando [Piskel](https://www.piskelapp.com/)

Per la scelta dei colori mi sono appoggiata a [Coolors](https://coolors.co/).

