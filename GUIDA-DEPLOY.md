# Guida al deploy online — Reality Hacking

Questa cartella (`Deploy-Online/`) contiene **tutto** ciò che serve per pubblicare il sito.

## Contenuto della cartella
- `index.html` — il sito (rebrand "Reality Hacking", autocontenuto, ~340 KB)
- `.nojekyll` — file vuoto che dice a GitHub Pages di non processare i nomi dei file

**Nota importante**: rispetto a una versione precedente, in questa cartella **non ci sono più i PDF dei libri**. La sezione Biblioteca è stata rimossa dal sito per motivi di copyright, e i materiali originali di Zeland non vengono più pubblicati online. Tutto il sapere dei libri è ora **incorporato nel chatbot** del sito (sezione "Chat & Domande"), che è stato alimentato con concetti, tecniche, linea storica ed esempi pratici. Chi visita il sito può fare domande e ricevere risposte approfondite sul Reality Transurfing di Vadim Zeland senza che nessun PDF protetto sia mai servito dal dominio.

## Posizionamento del sito (importante per copyright)

Il sito si chiama **Reality Hacking** — è una community indipendente di studio. Non si appropria del marchio "Reality Transurfing" di Zeland. Riferisce l'autore e le sue opere con rispetto, ma la forma è quella di un **luogo di discussione e pratica**, non di un archivio di contenuti protetti. Questa scelta ti mette in una posizione legalmente molto più difendibile.

Nel footer del sito è presente la dicitura: *"Community indipendente di studio del Reality Transurfing di V. Zeland · non ufficiale, non affiliata · uso educativo"*.

## Opzione scelta: GitHub Pages + dominio personalizzato

### Passo 1 — Crea l'account GitHub (se non ce l'hai)

Vai su https://github.com e crea un account gratuito.

### Passo 2 — Crea un nuovo repository

1. In alto a destra, clicca **+ → New repository**.
2. Nome: qualcosa come `reality-hacking` o `reality-hacking-community`.
3. Puoi tenerlo **Public** senza problemi: ora la cartella contiene solo l'HTML, niente PDF protetti.
4. Non aggiungere README, .gitignore o license.
5. Clicca **Create repository**.

### Passo 3 — Carica i file

**Via web (più semplice):**
1. Nella pagina del repo vuoto, clicca **uploading an existing file**.
2. Trascina il contenuto della cartella `Deploy-Online/` (`index.html`, `.nojekyll`, e questa guida). Su Windows/Mac, per vedere `.nojekyll` nel Finder/Esplora risorse abilita la visualizzazione dei file nascosti.
3. Clicca **Commit changes**.

**Via terminale (se preferisci):**
```bash
cd percorso/a/Deploy-Online
git init
git add -A
git commit -m "Primo deploy Reality Hacking"
git branch -M main
git remote add origin https://github.com/TUO-USERNAME/reality-hacking.git
git push -u origin main
```

### Passo 4 — Attiva GitHub Pages

1. Vai su **Settings → Pages** del repo.
2. Sotto *Source*: seleziona **Deploy from a branch**, ramo **main**, cartella **/ (root)**.
3. Clicca **Save**. Dopo 1-2 minuti, in cima alla pagina apparirà l'URL tipo:
   `https://TUO-USERNAME.github.io/reality-hacking/`
4. Aprilo: dovrebbe chiederti la password.

**Password del sito:** `117933`.

### Passo 5 — Registrare un dominio economico

Consigliati, in ordine di convenienza:

| Registrar | Prezzo .com/anno | Note |
|---|---|---|
| **Cloudflare Registrar** | ~8 € | Prezzo di costo, nessun markup. Serve account Cloudflare (gratuito). **Consigliato.** |
| **Porkbun** | ~9 € primo anno | Buoni prezzi anche su rinnovi, interfaccia chiara. |
| **Namecheap** | ~10-12 € | Popolare, WHOIS privacy inclusa. |

**Estensioni alternative più economiche:**
- `.xyz` — ~2-3 €/anno
- `.online` — ~3-5 €/anno
- `.space` — ~2-5 €/anno
- `.it` — ~8-12 €/anno (dominio italiano)

**Nomi coerenti con il rebrand** (verifica disponibilità):
- `realityhacking.it` / `realityhacking.online`
- `reality-hacking.community`
- `realityhacking.space`
- `rhacking.xyz`

**Attenzione**: evita domini con "Reality Transurfing" o "Transurfing" dentro — è verosimilmente marchio registrato da Zeland. Un dominio come `realitytransurfing.com` ti esporrebbe a rivendicazioni marchio.

### Passo 6 — Collegare il dominio a GitHub Pages

Una volta comprato il dominio:

1. Nel registrar, vai alla gestione DNS del dominio.
2. Aggiungi questi record:

**Record A** (per il dominio principale):
```
@   A   185.199.108.153
@   A   185.199.109.153
@   A   185.199.110.153
@   A   185.199.111.153
```

**Record CNAME** (per www):
```
www   CNAME   TUO-USERNAME.github.io
```

3. Torna su GitHub → **Settings → Pages** del repo.
4. Sotto *Custom domain* scrivi il tuo dominio (es. `realityhacking.it`) e clicca Save.
5. Dopo qualche minuto/ora (propagazione DNS), spunta **Enforce HTTPS**.

Fatto. Il sito è online sul tuo dominio con lucchetto HTTPS.

---

## Come funziona adesso la chat (senza PDF online)

Il chatbot del sito è stato alimentato con un sistema di conoscenza che copre:

- La linea storica completa dei libri di Zeland dal 2004 al 2025.
- Tutti i concetti del glossario zelandiano (42 termini tecnici).
- 15 tecniche pratiche con istruzioni operative ("come si fa").
- Una decina di FAQ di riferimento con citazione delle fonti.
- Note specifiche sui libri meno tradotti (Il Proiettore, Tafti 2, Trasferirsi) basate sui compendi della community.

Quando un utente fa una domanda sul Reality Transurfing, il chatbot risponde in modo concreto, cita il libro/era di riferimento, e invita a leggere gli originali di Zeland per la forma completa del pensiero. Non sostituisce i libri — li accompagna.

L'utente deve fornire una propria API key (Anthropic, OpenAI o OpenRouter) per usare la chat. Il costo è a suo carico, pochi centesimi per domanda.

---

## Alternativa rapida: Netlify Drop (1 minuto, senza account)

Se vuoi testare subito:
1. Vai su https://app.netlify.com/drop
2. Trascina l'intera cartella `Deploy-Online/` nella finestra
3. Ti dà subito un URL tipo `eloquent-lamport-abc123.netlify.app`
4. Il sito è online, password funzionante, zero setup.

Poi se vuoi aggiungere un dominio personalizzato, in Netlify **Domain settings → Add custom domain**.

---

## Aggiornamenti futuri

Quando modifichi il sito:

**Via web**: vai nel repo, carica il nuovo `index.html` sostituendo quello vecchio → commit. GitHub Pages si aggiorna in 1-2 minuti.

**Via terminale:**
```bash
cd percorso/a/Deploy-Online
# copia qui il nuovo index.html
git add index.html
git commit -m "Aggiornamento"
git push
```

---

## Disclaimer legale da tenere visibile

Il sito già include nel footer un disclaimer. Se vuoi rafforzarlo ulteriormente, puoi aggiungere una pagina o una nota in home tipo:

> *Reality Hacking è una community indipendente di studio e pratica ispirata al pensiero di Vadim Zeland (Reality Transurfing). Non è affiliata con l'autore, con i suoi editori o con rappresentanti ufficiali. Tutti i marchi registrati appartengono ai rispettivi proprietari. I contenuti di questo sito sono sintesi originali, commenti, discussioni e strumenti didattici prodotti dalla community per scopi educativi e non commerciali. Per il pensiero completo di Zeland, consigliamo l'acquisto dei libri originali presso i rivenditori ufficiali.*

Ultima revisione: aprile 2026.
