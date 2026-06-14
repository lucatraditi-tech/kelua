# KELŪA — Sezione "Pratiche"
## Istruzioni per Claude Code

Leggi prima `CLAUDE.md` per il design system, la palette, i font e il tono del sito.
Questo file aggiunge una nuova sezione — non modifica niente di esistente.

---

## Obiettivo

Creare la sezione `/pratiche` del sito KELŪA.
È una sezione editoriale con articoli di approfondimento su temi wellness.
Deve integrarsi perfettamente con il sito esistente — stesso stile, stessi font, stesse variabili CSS.

---

## Struttura da creare

```
pratiche/
├── index.html          ← Hub con carosello delle 5 pratiche
├── breathwork.html
├── sound-healing.html
├── movimento-consapevole.html
├── slow-morning.html
└── mente-corpo.html
```

Aggiungi "Pratiche" come voce di navigazione in tutte le pagine del sito esistenti.

---

## Pagina hub — `/pratiche/index.html`

### Layout dall'alto verso il basso

**Hero:**
Titolo: "Pratiche"
Sottotitolo: "Strumenti concreti per chi vuole vivere con più presenza"
Corpo (centrato, max-width 640px, serif):
> "Ci sono argomenti che sembrano profondi finché restano nelle parole. Queste pagine esistono per il momento dopo — quando hai capito abbastanza e vuoi fare qualcosa con quello che hai capito."

**Carosello 5 card** — scroll orizzontale, CSS scroll snap nativo, drag-to-scroll JS vanilla.

**CTA newsletter** — riusa il componente già esistente nel sito.

### Le 5 card del carosello

Ogni card ha:
- Numero decorativo (01–05), font serif, colore `--muted`, corpo grande
- Titolo pratica, font serif
- Tagline in italic
- Lista di 3-4 tag tematici come pill piccoli
- Link "Leggi →" colore `--cta`
- Hover: `translateY(-4px)`, border `--cta`, transizione 0.3s

**Card 01 — Breathwork**
Tagline: *Il respiro è il telecomando del tuo sistema nervoso*
Tag: sistema nervoso · stress · quotidiano
Hook preview: "Il respiro è l'unica funzione involontaria del corpo che puoi controllare. Questo lo rende un ponte diretto verso il tuo sistema nervoso autonomo."

**Card 02 — Sound Healing**
Tagline: *Il suono entra nel corpo prima che la mente lo elabori*
Tag: vibrazione · nervo vago · campane tibetane
Hook preview: "Certe frequenze non si ascoltano soltanto. Si percepiscono — nella pelle, nelle ossa, nello stomaco. E il sistema nervoso risponde, che tu lo voglia o no."

**Card 03 — Movimento Consapevole**
Tagline: *C'è una differenza enorme tra fare yoga e sentire il corpo*
Tag: corpo · interocezione · pratica somatica
Hook preview: "Puoi fare yoga per anni e restare completamente disconnesso. Il movimento consapevole sposta l'attenzione dall'esteriore all'interiore — e cambia il rapporto con il tuo corpo in modo permanente."

**Card 04 — Slow Morning**
Tagline: *I primi 30 minuti della giornata decidono tutto il resto*
Tag: rituale · cortisolo · intenzione
Hook preview: "Non è una lista di cose da fare prima delle sette. È un approccio deliberato al risveglio — basato su neurobiologia reale e su un principio semplice: scegliere come vuoi entrare nella tua giornata."

**Card 05 — Connessione Mente-Corpo**
Tagline: *Il corpo decide prima. La mente interpreta dopo.*
Tag: neuroscienze · trauma · polyvagal
Hook preview: "Il corpo elabora quantità enormi di informazioni al di sotto della soglia della coscienza. Imparare ad ascoltarlo non è un esercizio spirituale. È una competenza neurologica."

### CSS carosello (scroll snap nativo)

```css
.pratiche-carousel {
  display: flex;
  gap: 1.5rem;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  scrollbar-width: none;
  padding: 2rem 2.5rem;
  cursor: grab;
}
.pratiche-carousel::-webkit-scrollbar { display: none; }
.pratica-card {
  scroll-snap-align: start;
  flex: 0 0 300px;
  background: var(--bg);
  border: 1px solid rgba(127,138,117,0.2);
  border-radius: 3px;
  padding: 2rem 1.75rem;
  transition: transform 0.3s, border-color 0.3s;
}
.pratica-card:hover {
  transform: translateY(-4px);
  border-color: var(--cta);
}
@media (max-width: 768px) {
  .pratica-card { flex: 0 0 85vw; }
}
```

### JS drag-to-scroll (vanilla, nessuna libreria)

```javascript
const carousel = document.querySelector('.pratiche-carousel');
let isDown = false, startX, scrollLeft;
carousel.addEventListener('mousedown', e => {
  isDown = true;
  startX = e.pageX - carousel.offsetLeft;
  scrollLeft = carousel.scrollLeft;
  carousel.style.cursor = 'grabbing';
});
['mouseleave','mouseup'].forEach(ev =>
  carousel.addEventListener(ev, () => {
    isDown = false;
    carousel.style.cursor = 'grab';
  })
);
carousel.addEventListener('mousemove', e => {
  if (!isDown) return;
  e.preventDefault();
  carousel.scrollLeft = scrollLeft - (e.pageX - carousel.offsetLeft - startX) * 1.5;
});
```

---

## Template pagina articolo

Ogni articolo ha la stessa struttura. Il contenuto cambia, il layout no.

### Layout

```
[Nav — identica al sito]

[Article hero — background --bg]
  Breadcrumb: Pratiche → [Titolo articolo]   (sans, --muted, 0.7rem)
  Numero decorativo: "01"  (serif, 5rem, colore #EDE8E0)
  H1: titolo  (serif, clamp 2rem–3.2rem)
  Sottotitolo  (serif italic, --accent)
  Tag pill  (stile label già usato nel sito)

[Article body — max-width 720px, centrato]
  H2: serif, --text, spacing generoso
  H3: sans bold, --accent
  Paragrafi: sans, line-height 1.85, --text

[Stub "prossimamente"]
  Vedi stile sotto

[CTA KELŪA — sfondo --dark]
  Testo breve, bottone --cta

[Navigazione articoli]
  ← Precedente  |  Successivo →   (sans, --muted, hover --text)

[Footer — identico al sito]
```

### Stile stub "prossimamente"

```css
.stub-card {
  background: var(--bg-alt);
  border-left: 2px solid var(--cta);
  border-radius: 0 2px 2px 0;
  padding: 0.9rem 1.4rem;
  margin: 1.25rem 0;
}
.stub-label {
  font-size: 0.58rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--cta);
  display: block;
  margin-bottom: 0.3rem;
}
.stub-text {
  font-size: 0.82rem;
  color: var(--muted);
  font-style: italic;
}
```

Non sono link cliccabili — sono placeholder visivi per futuri approfondimenti.

---

## Contenuto dei 5 articoli

---

### ARTICOLO 01 — Breathwork
**Slug:** `/pratiche/breathwork`
**H1:** Breathwork
**Sottotitolo:** *Il respiro è il telecomando del tuo sistema nervoso*
**Tag:** sistema nervoso · stress · quotidiano

**[SEZIONE — hook]**
Hai mai notato come il respiro cambia quando hai paura? O come un respiro profondo ti calma prima ancora che tu abbia capito perché?

Non è un caso. È biologia.

Il respiro è l'unica funzione involontaria del corpo che puoi controllare consapevolmente. Questo lo rende qualcosa di straordinario: un ponte diretto tra la tua mente e il sistema nervoso autonomo — il sistema che decide se sei in modalità stress o in modalità riposo.

Usarlo bene cambia come ti senti in 60 secondi. Usarlo con costanza cambia come funzioni nel tempo.

---

**[SEZIONE H2 — Cosa succede nel corpo]**
Quando rallenti il respiro, attivi il nervo vago — il nervo più lungo del corpo, che connette il cervello agli organi interni. Il risultato è immediato: il cuore rallenta, la pressione scende, i muscoli si allentano, il cortisolo comincia a diminuire.

La ricerca lo conferma: una revisione di 58 studi clinici ha dimostrato che tecniche di respirazione regolata riducono stress, ansia e depressione in modo misurabile. Non è meditazione esoterica — è fisiologia.

Tra i benefici documentati: riduzione della tensione muscolare in 2-3 minuti, pressione sanguigna più bassa con 10 minuti al giorno, sonno più profondo, mente più chiara, reattività emotiva ridotta.

---

**[SEZIONE H2 — Le 5 tecniche]**

**[H3 — Respirazione diaframmatica]**
La base di tutto. Inspira dal naso espandendo la pancia — non il petto. Espira lentamente dalla bocca. Cinque minuti al mattino cambiano la qualità dell'intera giornata.

**[STUB]** → *Guida completa alla respirazione diaframmatica*

**[H3 — Box Breathing]**
Inspira 4 secondi. Trattieni 4. Espira 4. Trattieni 4. Usata da operatori militari e atleti d'élite per gestire lo stress acuto. Funziona in qualsiasi momento — prima di una riunione difficile, nel mezzo di una discussione.

**[STUB]** → *Box Breathing: guida pratica passo per passo*

**[H3 — Respirazione 4-7-8]**
Inspira 4 secondi. Trattieni 7. Espira 8. Il respiro lungo verso l'esterno attiva profondamente il parasimpatico. Ideale prima di dormire o nei momenti di ansia acuta.

**[STUB]** → *4-7-8: il respiro che ti addormenta in minuti*

**[H3 — Respirazione Coerente]**
Sei respiri al minuto — 5 secondi inspiro, 5 espiro. Questa frequenza massimizza la variabilità della frequenza cardiaca (HRV), indicatore di resilienza allo stress tra i più affidabili che esistano.

**[STUB]** → *HRV e respirazione coerente: cosa misura davvero*

**[H3 — Nadi Shodhana]**
Dalla tradizione yogica. Si alternano inspirazione ed espirazione da una narice alla volta. Bilancia i due emisferi cerebrali e crea uno stato di calma vigile difficile da raggiungere con altre tecniche.

**[STUB]** → *Pranayama: le origini della respirazione consapevole*

---

**[SEZIONE H2 — Come iniziare oggi]**
Non serve un'app. Non serve un corso. Non serve molto tempo.

Inizia con cinque minuti al mattino, prima di guardare il telefono. Sdraiato o seduto, respira lentamente espandendo la pancia. Inspira 4 secondi, espira 6. Ripeti.

Fallo per sette giorni. La coerenza vale più della tecnica perfetta.

---

**[SEZIONE H2 — Il punto profondo]**
Il breathwork non è una tecnica di rilassamento. È un atto di riappropriazione.

In un mondo che ti chiede di essere sempre reattivo, sempre disponibile, sempre performativo — fermarsi a respirare consapevolmente è un gesto radicale. Stai dicendo al tuo sistema nervoso: sono al sicuro. Posso rallentare. Sono qui.

Il corpo risponde ogni volta. Senza eccezioni.

---

**[CTA — sfondo dark]**
Se vuoi esplorare il breathwork in un contesto guidato — con altri che stanno cercando le stesse cose — la nostra community è il posto giusto.
Bottone: "Entra nella community" → link WhatsApp

---

### ARTICOLO 02 — Sound Healing
**Slug:** `/pratiche/sound-healing`
**H1:** Sound Healing
**Sottotitolo:** *Il suono entra nel corpo prima ancora che la mente lo elabori*
**Tag:** vibrazione · nervo vago · campane tibetane

**[SEZIONE — hook]**
Hai mai sentito una musica che ti ha fatto venire i brividi? O un suono che ti ha fermato — dentro — prima ancora di capire perché?

Quello non è romanticismo. È neuroscienza.

Il suono non viene solo ascoltato. Viene percepito dall'intero corpo — attraverso la pelle, le ossa, gli organi interni. Certi suoni, a certe frequenze, parlano direttamente al sistema nervoso autonomo. E il sistema nervoso risponde, che tu lo voglia o no.

Il Sound Healing usa questo principio in modo intenzionale.

---

**[SEZIONE H2 — Cosa sono le campane tibetane]**
Le campane tibetane himalayane sono strumenti forgiati a mano — tradizionalmente in Nepal e Tibet — in leghe metalliche che producono suoni ricchi di armonici. Non una frequenza semplice: una nuvola complessa di suoni sovrapposti che il corpo elabora a livelli diversi simultaneamente.

Vengono usate da secoli nelle tradizioni buddhiste per la meditazione e la guarigione. Oggi la ricerca scientifica sta capendo perché funzionano.

---

**[SEZIONE H2 — La scienza]**
Una revisione sistematica del 2025 pubblicata su Integrative Medicine Research — 14 studi analizzati nell'arco di 16 anni — ha documentato che l'esposizione alle campane tibetane produce riduzione misurabile di stress e ansia, aumento della variabilità della frequenza cardiaca, attivazione del sistema nervoso parasimpatico più pronunciata rispetto al semplice riposo in silenzio.

La chiave è il nervo vago — il nervo più lungo del corpo, responsabile del 75% del sistema nervoso parasimpatico. Le vibrazioni delle campane lo stimolano direttamente. Quando si attiva, il corpo passa da "allerta" a "riposo e guarigione".

---

**[SEZIONE H2 — Cosa succede durante una sessione]**
Ci si distende. Pienamente vestiti, coperti se si vuole. Non c'è niente da fare, niente da capire, niente da raggiungere.

Le campane vengono suonate intorno al corpo — a volte posate direttamente su di esso per amplificare la conduzione vibrazionale. Il suono non è solo nell'aria: lo senti nelle ossa, nello stomaco, nel petto.

La maggior parte delle persone entra in uno stato di rilassamento profondo nei primi 10-15 minuti — comparabile alla meditazione avanzata, anche senza aver mai meditato in vita loro.

---

**[SEZIONE H2 — Le forme del Sound Healing]**

**[H3 — Campane tibetane himalayane]**
Lo strumento principe. Ogni campana ha una frequenza fondamentale e una serie di armonici unici. Le sessioni possono essere individuali o collettive.

**[STUB]** → *Come scegliere una campana tibetana — guida pratica*

**[H3 — Gong bath]**
Strumento di dimensioni maggiori, produce onde sonore che investono l'intero corpo. Usato spesso nelle sessioni collettive per momenti di rilascio profondo.

**[STUB]** → *Gong bath: cosa aspettarsi dalla prima volta*

**[H3 — Voce e vocal toning]**
La tua voce è uno strumento di Sound Healing. Cantare, canticchiare, o fare "mmm" a labbra chiuse stimola il nervo vago dall'interno. Gratuito, disponibile sempre, efficace.

**[STUB]** → *Vocal toning: usare la voce per regolare il sistema nervoso*

---

**[SEZIONE H2 — Il punto profondo]**
Viviamo in un'epoca di rumore costante. Il sistema nervoso è bombardato in un modo che nessuna generazione prima di noi ha mai vissuto.

Il Sound Healing non è una via di fuga dal rumore. È un modo di usare il suono con intenzione — di tornare a una qualità di ascolto che il corpo conosce ma che abbiamo quasi dimenticato.

Quando sei nel mezzo di una sessione e il suono della campana riempie lo spazio, non stai ascoltando qualcosa di esterno. Stai ascoltando il tuo corpo che risponde.

---

**[CTA — sfondo dark]**
I nostri facilitatori conducono sessioni di Sound Healing regolari — in presenza e nella community. Se non hai mai vissuto una sessione con le campane tibetane, è un'esperienza che difficilmente si dimentica.
Bottone: "Guarda i prossimi eventi" → link pagina eventi

---

### ARTICOLO 03 — Movimento Consapevole
**Slug:** `/pratiche/movimento-consapevole`
**H1:** Movimento Consapevole
**Sottotitolo:** *C'è una differenza enorme tra fare yoga e sentire il proprio corpo*
**Tag:** corpo · interocezione · pratica somatica

**[SEZIONE — hook]**
Puoi fare yoga per anni e restare completamente disconnesso dal tuo corpo.
Puoi anche stare fermi per cinque minuti e imparare più di quanto avresti mai immaginato.

La differenza non è nella tecnica. È nell'attenzione.

Il movimento consapevole sposta il focus dall'esteriore all'interiore. Non quanto sei flessibile, ma cosa senti mentre ti muovi. Non la posizione perfetta, ma questa posizione, in questo corpo, oggi.

Sembra una sfumatura. Cambia tutto.

---

**[SEZIONE H2 — Il corpo ha una memoria che la mente non conosce]**
Il corpo accumula tutto ciò che viviamo — stress, tensioni, emozioni non elaborate, risposte di allerta ripetute nel tempo. Non come ricordi cognitivi: come pattern fisici. Tensioni croniche, zone del corpo che non riesci a sentire, movimenti che eviti inconsciamente.

I ricercatori lo chiamano memoria somatica. Il sistema nervoso ricorda cose che la mente ha già dimenticato.

Il movimento consapevole crea uno spazio per ascoltare questa memoria — non per riparare qualcosa, ma per entrarci in dialogo.

---

**[SEZIONE H2 — La scienza dell'interocezione]**
Il nome tecnico di questa capacità è interocezione — la percezione degli stati interni del corpo: battito cardiaco, tensione muscolare, temperatura, sensazioni viscerali. Quello che Stephen Porges chiama il sesto senso.

Una ricerca su Frontiers in Psychology (2024) dimostra che allenare l'interocezione attraverso il movimento somatico migliora la regolazione emotiva, riduce lo stress cronico e aumenta la capacità di prendere decisioni allineate con i propri bisogni reali.

---

**[SEZIONE H2 — Fare vs. sentire: la differenza concreta]**
Fare yoga: segui le istruzioni, cerchi la posizione giusta, misuri dalla flessibilità raggiunta. L'attenzione è fuori.

Sentire il corpo in movimento: esplori come si sente questa posizione per te oggi. L'attenzione è dentro — cosa noto, dove c'è tensione, dove c'è spazio.

Nessuno dei due è sbagliato. Ma se il tuo obiettivo è tornare in contatto con te stesso, uno funziona molto più dell'altro.

---

**[SEZIONE H2 — Le tradizioni del movimento somatico]**

**[H3 — Yoga somatico]**
Posture yogiche esplorate per come si sentono dall'interno piuttosto che per come appaiono dall'esterno. Rallentato, con enfasi sull'ascolto.

**[STUB]** → *Yoga somatico: come cambia la pratica quando smetti di guardarti da fuori*

**[H3 — Metodo Feldenkrais]**
Piccoli movimenti gentili per migliorare la comunicazione tra cervello e muscoli. Spesso le sequenze sembrano quasi impercettibili — eppure producono cambiamenti profondi.

**[STUB]** → *Feldenkrais: muoversi meno per sentire di più*

**[H3 — Pilates consapevole]**
Il Pilates tradizionale lavora su forza e allineamento. Il Pilates consapevole aggiunge la dimensione dell'ascolto: ogni esercizio diventa anche un'opportunità di riconoscere pattern abituali.

**[STUB]** → *Pilates e sistema nervoso: oltre la forma fisica*

---

**[SEZIONE H2 — Il punto profondo]**
Viviamo prevalentemente nella testa. Il corpo lo portiamo dietro come un carrello — lo sistemiamo quando fa male, lo ignoriamo nel mezzo.

Il movimento consapevole non è un modo per avere un corpo migliore. È un modo per abitare il corpo che hai. Per tornare a casa in un posto che è sempre stato tuo.

E quando riesci a sentirti nel corpo — davvero — il rumore nella testa si abbassa da solo.

---

**[CTA — sfondo dark]**
Le nostre sessioni integrano principi somatici: la sensazione prima della forma, il respiro come guida del movimento, la pratica come ascolto piuttosto che come performance. Non importa il tuo livello. Importa la tua curiosità.
Bottone: "Guarda i prossimi eventi" → link pagina eventi

---

### ARTICOLO 04 — Slow Morning
**Slug:** `/pratiche/slow-morning`
**H1:** Slow Morning
**Sottotitolo:** *I primi 30 minuti della giornata decidono tutto il resto*
**Tag:** rituale · cortisolo · intenzione mattutina

**[SEZIONE — hook]**
Non è una questione di produttività.
Non è una lista di cose da fare prima delle sette.

È qualcosa di più semplice e più radicale: scegliere come vuoi entrare nella tua giornata.

La maggior parte delle persone non sceglie. Si sveglia e viene immediatamente catturata — dal telefono, dalle notifiche, dai pensieri che già rincorrono la giornata. Il sistema nervoso passa da zero a cento prima ancora di aver bevuto un bicchiere d'acqua.

La Slow Morning è il contrario di questo.

---

**[SEZIONE H2 — La biologia del risveglio]**
Nei primi 30-45 minuti dopo il risveglio, il corpo produce un picco naturale di cortisolo chiamato Cortisol Awakening Response. Non è cortisolo da stress — è cortisolo funzionale, che prepara il cervello e il corpo per la giornata. Il picco è tra il 38% e il 75% sopra i livelli basali.

Quello che fai in questi minuti influenza il tono emotivo dell'intera giornata, la qualità dell'attenzione, la reattività allo stress nelle ore successive e — paradossalmente — la qualità del sonno della notte successiva.

---

**[SEZIONE H2 — Il problema con il telefono al mattino]**
Guardare il telefono entro i primi minuti dal risveglio non è solo una cattiva abitudine. È un interrupt neurologico.

L'amigdala — il centro di allerta del cervello — si attiva immediatamente. Questo porta il sistema nervoso in modalità reattiva prima che la corteccia prefrontale sia pienamente online. Stai reagendo prima di aver scelto come rispondere. E quella modalità tende a durare per ore.

---

**[SEZIONE H2 — I cinque elementi]**

**[H3 — Luce naturale]**
Esponi gli occhi alla luce naturale entro i primi 10-15 minuti dal risveglio. Segnala all'orologio circadiano che il giorno è iniziato. Regola il cortisolo, la serotonina e — paradossalmente — la qualità della melatonina serale.

**[STUB]** → *Luce mattutina e ritmo circadiano: la guida completa*

**[H3 — Idratazione consapevole]**
Il corpo si sveglia disidratato. Un grande bicchiere d'acqua, bevuto lentamente e con presenza, prima del caffè. Non è una regola salutista — è fisiologia di base.

**[STUB]** → *Idratazione al mattino: perché conta più di quanto pensi*

**[H3 — Respiro o movimento]**
Cinque minuti di respirazione consapevole o di movimento lento prima che il giorno inizi. Crea un buffer fisiologico tra il sonno e le richieste esterne. Non devi meditare un'ora.

**[STUB]** → *Vai all'approfondimento: Breathwork*

**[H3 — Silenzio o intenzione]**
Prima di consumare contenuti, produci un pensiero. Tre cose per cui sei grato. Un'intenzione per la giornata — non un obiettivo, una qualità con cui vuoi muoverti. Qualche minuto di silenzio vero.

**[STUB]** → *Morning pages e journaling: scrivere per pensare*

**[H3 — Il caffè come rituale]**
Preparalo lentamente. Sentine l'aroma prima di berlo. Siediti. Non fare altro mentre lo bevi. Cinque minuti di presenza assoluta trasformano un gesto abitudinario in una pratica.

**[STUB]** → *Il rituale della tazza: mindfulness quotidiana senza cercarla*

---

**[SEZIONE H2 — Come costruire la tua Slow Morning]**
La Slow Morning peggiore è quella che diventa un'altra cosa da fare bene. Un'altra performance.

Inizia con un solo elemento. Non dieci. Uno. Fallo per due settimane. Poi, se vuoi, aggiungi qualcosa.

La domanda guida non è "cosa dovrei fare di mattina?" — è "come voglio svegliarmi nel mio corpo e nella mia testa prima che la giornata inizi?"

---

**[SEZIONE H2 — Il punto profondo]**
Ogni mattina hai la possibilità di scegliere il punto da cui parti.

Non è una metafora motivazionale. È una realtà neurobiologica: il tuo sistema nervoso è più ricettivo in quei primi minuti. Quello che semini lì — intenzionalmente o per inerzia — cresce durante il giorno.

La Slow Morning non è una routine del benessere. È un atto di rispetto verso te stesso.

---

**[CTA — sfondo dark]**
Ogni settimana proponiamo appuntamenti mattutini — pratiche di respiro, movimento gentile e silenzio condiviso. Certe mattine è più facile rallentare quando non sei solo.
Bottone: "Guarda i prossimi eventi" → link pagina eventi

---

### ARTICOLO 05 — Connessione Mente-Corpo
**Slug:** `/pratiche/mente-corpo`
**H1:** Connessione Mente-Corpo
**Sottotitolo:** *Il corpo decide prima. La mente interpreta dopo.*
**Tag:** neuroscienze · sistema nervoso · polyvagal

**[SEZIONE — hook]**
Hai mai preso una decisione "di pancia" che si è rivelata giusta, anche se non riuscivi a spiegarla razionalmente? O sentito qualcosa stringersi nello stomaco prima ancora di capire cosa stava succedendo?

Non era istinto vago. Era intelligenza somatica.

Il corpo elabora enormi quantità di informazioni al di sotto della soglia della coscienza. Imparare ad ascoltarlo non è un esercizio spirituale. È una competenza neurologica.

---

**[SEZIONE H2 — Il corpo parla al cervello più di quanto il cervello parli al corpo]**
C'è un dato che molte persone trovano sorprendente: le fibre nervose che vanno dal corpo al cervello superano numericamente quelle che vanno dal cervello al corpo.

Il flusso di informazioni è prevalentemente ascendente. Quello che senti nel corpo in questo momento sta attivamente influenzando i tuoi pensieri e le tue emozioni. Non solo il contrario.

Mente e corpo non sono in una relazione di comando e obbedienza. Sono in conversazione costante. E spesso è il corpo a fare la prima mossa.

---

**[SEZIONE H2 — La Polyvagal Theory]**
Nel 1994 il neuroscienziato Stephen Porges ha ridisegnato la mappa del sistema nervoso autonomo con la Polyvagal Theory — oggi tra le teorie più influenti in neuroscienze e psicologia clinica.

Non due stati (stress / riposo) — ma tre:

Stato ventrale vagale: sicurezza, connessione, calma vigile. Sei pienamente presente e puoi pensare con chiarezza.

Stato simpatico: il sistema rileva una minaccia e ti prepara a combattere o fuggire. Utile in situazioni di pericolo reale. Logorante se cronico.

Stato dorsale vagale: quando la minaccia sembra insormontabile, il sistema si spegne. Dissociazione, intorpidimento. Una risposta di sopravvivenza — non una scelta.

Il passaggio tra questi stati avviene automaticamente, al di sotto della coscienza. Il corpo decide. La mente trova la spiegazione dopo.

---

**[SEZIONE H2 — Il corpo ricorda quello che la mente ha dimenticato]**
Esperienze di stress intenso o trauma non completamente elaborato lasciano tracce nel sistema nervoso — non solo come ricordi, ma come pattern fisici.

Tensione cronica nelle spalle. Difficoltà a respirare profondamente. Reattività sproporzionata in certe situazioni. Sensazione di non riuscire mai a rilassarsi davvero.

Non sono segnali di debolezza. Sono il corpo che cerca di proteggerti — usando strategie imparate in momenti difficili che magari non esistono più.

---

**[SEZIONE H2 — Come ascoltare l'intelligenza somatica]**
L'interocezione si allena come un muscolo.

Un esercizio semplice: tre volte al giorno, fermati trenta secondi. Chiudi gli occhi. Fatti una domanda: cosa sento nel corpo adesso? Non interpretare. Non giudicare. Solo osserva.

Con il tempo, il segnale diventa più chiaro.

---

**[SEZIONE H2 — Pratiche che lavorano sulla connessione]**

**[H3 — Grounding]**
Tecniche per portare l'attenzione al presente attraverso sensazioni fisiche — i piedi sul pavimento, le mani che tengono qualcosa. Attivano il sistema nervoso ventrale e interrompono la spirale della ruminazione.

**[STUB]** → *Tecniche di grounding: come tornare nel corpo in 60 secondi*

**[H3 — Body Scan]**
Una meditazione che porta l'attenzione sistematicamente attraverso ogni parte del corpo. Non per cambiare quello che c'è — per ascoltarlo.

**[STUB]** → *Body scan guidato: istruzioni per principianti*

**[H3 — Somatic Experiencing]**
Approccio terapeutico per lavorare con il trauma attraverso la consapevolezza corporea. Insegna al sistema nervoso a completare i cicli di risposta allo stress rimasti incompleti.

**[STUB]** → *Somatic Experiencing: quando il corpo ha bisogno di un professionista*

---

**[SEZIONE H2 — Il punto profondo]**
Ci hanno insegnato a fidarci della mente. A ragionare, analizzare, trovare la risposta giusta.

Nessuno ci ha insegnato a fidarci del corpo. A sentire prima di pensare. A stare nella sensazione senza doverla immediatamente trasformare in parole.

Eppure il corpo è rimasto lì, tutto il tempo, a fare il suo lavoro. A proteggerti. A segnalarti. A sapere cose.

La connessione mente-corpo non si costruisce. Si recupera.

---

**[CTA — sfondo dark]**
Tutte le pratiche che proponiamo — breathwork, sound healing, movimento, meditazione — hanno un punto in comune: lavorano sul sistema nervoso attraverso il corpo. Non per migliorare la performance. Per creare spazio.
Bottone: "Entra nella community" → link WhatsApp

---

## Note tecniche finali

**Animazioni:** riusa esattamente l'IntersectionObserver già presente nel sito. Aggiungi `.reveal` alle card del carosello (stagger 100ms) e alle sezioni H2 degli articoli.

**SEO:** ogni pagina articolo deve avere `<title>[Titolo] — KELŪA Pratiche</title>` e `<meta name="description">` con il testo dell'hook, troncato a 155 caratteri.

**Link interni:** gli stub non sono cliccabili. I link tra articoli (precedente/successivo) sì.

**Mobile first:** il carosello deve funzionare perfettamente su touch. Testa su iPhone prima di desktop.

**Non reimportare i font:** sono già caricati nelle pagine esistenti del sito. Usa solo le variabili CSS già definite.

**Nomi propri:** nessun nome di persona negli articoli. Usa "i nostri facilitatori", "chi guida le sessioni", "i nostri esperti della pratica".
