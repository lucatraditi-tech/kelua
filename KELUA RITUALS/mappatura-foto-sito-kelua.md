# Inserimento foto sito Kelua — mappatura da Google Drive

Istruzioni per Claude Code: prendere le foto elencate sotto dalla cartella **"Fotos editatas"** su Google Drive (hai già accesso) e inserirle nelle posizioni indicate del sito, mantenendo il design/layout attuale.

Ogni riga = 1 foto da cercare per nome file (colonna B) e posizionare nel punto indicato (colonna A).

---

## Sezione principale (hero/cover)

| Posizione sul sito | Nome file da cercare su Drive |
|---|---|
| Immagine — Rituals (cover/hero) | `0T6A7423` |
| Immagine — Flow (cover/hero) | `0T6A6829` |
| Immagine — Essence (cover/hero) | `0T6A6596` |

## Sezione Rituals

| Posizione sul sito | Nome file da cercare su Drive |
|---|---|
| Rituals — immagine sezione | `0T6A7423` |
| Rituals — Breathwork | `0T6A6781` |
| Rituals — Sound Healing | `0T6A7405` |
| Rituals — Movimento Consapevole | `0T6A6248` |
| Rituals — Slow Morning | `Marocco_verticale` |
| Rituals — Mente-Corpo | `Marocco_orizzontale` |

## Sezione Momenti

| Posizione sul sito | Nome file da cercare su Drive |
|---|---|
| Momento 1 | `0T6A6845` |
| Momento 2 | `0T6A6803` |
| Momento 3 | `0T6A6787` |
| Momento 4 | `_AU_6435` |

---

## ⚠️ Foto Team — attenzione, gestione speciale

**File:** `0T6A7362`

**Non è un inserimento standard**, richiede queste modifiche specifiche:

1. **Posizione**: va messa nella **parte finale della sezione Essence**, al posto delle **3 iconcine "chi siamo"** attualmente presenti lì (quelle vanno rimosse)
2. **Testo**: nella stessa area, ripristinare il **testo che era presente in "FILOSOFIA KELUA"** nelle versioni precedenti del sito, che è stato rimosso in un passaggio successivo insieme a un vecchio elemento vicino alla foto del team (recuperalo dalla cronologia/versioni precedenti del repo, es. `git log` sui file della sezione Essence, o dai commit precedenti a quando è stato tolto)
3. **Layout**: la foto è **verticale** (non orizzontale come le altre), quindi il layout della sezione va adattato di conseguenza — valuta tu (Claude Code) la disposizione migliore vista l'orientazione, mantenendo coerenza con lo stile del resto del sito

---

## Note generali

- **Coerenza card ↔ pagina di dettaglio**: per ogni elemento che ha sia una card/anteprima sia una pagina di dettaglio che si apre al click (es. Breathwork, Sound Healing, Movimento Consapevole, Slow Morning, Mente-Corpo, e qualsiasi altro elemento cliccabile che apre un documento/pagina dedicata), la **stessa foto** usata nella card va usata anche come immagine principale nella pagina di dettaglio che si apre. Non usare foto diverse tra anteprima e dettaglio per lo stesso elemento.
- Se un nome file su Drive ha estensione diversa da quella attesa o multiple varianti (es. `_v2`, `_final`), usa la versione più recente/definitiva
- Se un file non viene trovato con il nome esatto, cerca corrispondenze parziali prima di segnalare l'assenza
- Ottimizza le immagini per il web (compressione ragionevole) durante l'inserimento, mantenendo qualità visiva alta vista la natura fotografica del brand
