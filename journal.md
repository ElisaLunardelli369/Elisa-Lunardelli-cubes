# journal

## Scelte di design

La prima scelta per l' ambientazione a cui ho pensato è stata quella di un paesaggio di montagna, perchè si presta bene per applicazioni in stile Minecraft. Da qui la scelta di sfruttare una height map è stata naturale, perchè consente in modo pratico di generare un terreno. Ho pensato a creare personalmente la height map per avere più controllo sul effetto finale. Dovendo inserire anche un'animazione mi sono però scontrata con le problematiche che un ambiente così può comportare:
- quali elementi animati sono coerenti con questa ambientazione? (un animale, un mezzo di trasporto, la luce del sole ecc....)
- quanto sono complicati da realizzare questi elementi? (quali sono le parti mobili, come approssimare con dei cubi le forme ecc...)
- come posiziono sulla superficie questi elementi?

U'altra problematica di origine più estetica è quella dei colori. Molti livelli richiedono colorazioni diverse per metterli in risaldo e utilizzare moltissimo verde (e le sue sfumature) rischiava di sembrare monotono. Sarebbe stato necessario inserire molti elementi aggiuntivi a scopo decorativo.

Per tutti questi motivi ho deciso di realizzare un ambiente marino dove è presente una grande quantità di superficie regolare continua e permette di utilizzare diversi colori (blu, giallo e verde).

Una volta scelta l'ambientazione e realizzata la height map la scelta degli elementi da aggiungere è stata semplice. Una barca è un oggetto perfetto da animare con poche semplici trasformazioni come richiesto dalla consegna. Il faro ha dato un tocco di colore restando molto coerente con il tema della scena.

Ho scelto di realizzare l'animazione in modo che andasse a riempire uno spazio vuoto: dal lato destro della scena sono presenti molte isole e il faro, quindi l'imbarcazione è stata messa nella meta sinistra per controbilanciare. Avrei potuto realizzare una traiettoria dritta per l'imbarcazione, ma questa non si adattava bene alla scena. Ho pensato che fosse molto più interessante e naturale che la barca passasse disegnando un arco. 

I colori pastello garantiscono un effetto gradevole e leggero. Utilizzando un tipo di materiale non fotorealistico ho preferito abbracciare completamente uno stile che non fosse tale e questi colori tenui si adattano perfettamente allo scopo.

Come ultimo tocco ho applicato un colore di sfondo che ricordasse il cielo.

## Problematiche di realizzazione

- Al momento di creare il terreno ho subito realizzato che avrei dovuto utilizzare una heigt map dalle dimensioni ridotte per evitare di generare troppe mesh. Con una heigt map troppo grande la scena risultava molto pesante. 

- Durante la creazione della height map ho evitato di utilizzare il nero assoluto (0,0,0) perchè avrebbe generato un valore di altezza molto basso. Per evitare di andare poi a correggere questa cosa con il codice ho preferito direttamente usare una scala di grigi che non avesse questi valori così estremi.
Questo problema è comunque stato risolto poi dall'utilizzo dei valori di altezza come discriminante e non più come valore effettivo per la creazione della geometria. 

- capire come gestire l'animazione: avendo in mente che la parte di codice per l'animazione va inserita all'interno della funzione qui denominata Update() che si occupa del loop di rendering e che per individuare i punti di una circonferenza occorre usare la trigonometria sono stati necessari diversi tentativi per raggiungere il risultato finale. I punti fondamentali per gestire l'animazione sono stati: la creazione di un gruppo pivot per gestire la gerarchia delle trasformazioni e l'aver messo al di fuori della funzione Update() la variabile che contiene il grado dell'angolo in modo che si potesse incrementare alla fine di ogni ciclo di rendering.



