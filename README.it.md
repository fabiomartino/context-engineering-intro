# Template di Ingegneria del Contesto

Un template completo per iniziare con l’Ingegneria del Contesto – la disciplina che progetta il contesto per gli assistenti di codifica basati su IA, affinché abbiano tutte le informazioni necessarie per completare i compiti dall'inizio alla fine.

> **L’ingegneria del contesto supera la prompt engineering di un ordine di grandezza – e offre molta più struttura e affidabilità rispetto alla codifica "a sensazione". Questo template è ottimizzato per l’uso con Gemini CLI.**

## 🚀 Avvio Rapido

```bash
# 1. Clona questo template
git clone https://github.com/coleam00/Context-Engineering-Intro.git
cd Context-Engineering-Intro

# 2. Installa e autentica Gemini CLI
npm install -g @google/gemini-cli
gemini auth

# 3. Configura le regole del tuo progetto (opzionale – è fornito un template)
# Modifica GEMINI.md per aggiungere le linee guida specifiche del tuo progetto

# 4. Aggiungi esempi (altamente consigliato)
# Inserisci esempi di codice pertinenti nella cartella `examples/`

# 5. Crea la tua prima richiesta di funzionalità
# Modifica INITIAL.md con i requisiti della funzionalità

# 6. Genera un PRP (Prompt di Requisiti di Prodotto) completo
gemini -p "@./.gemini/commands/generate-prp.md" "INITIAL.md"

# 7. Esegui il PRP per implementare la funzionalità
gemini -p "@./.gemini/commands/execute-prp.md" "PRPs/your-feature-name.md"
````

## 📚 Indice

* [Cos'è l’Ingegneria del Contesto](#cosè-lingegneria-del-contesto)
* [Struttura del Template](#struttura-del-template)
* [Guida Passo-Passo](#guida-passo-passo)
* [Come Scrivere File INITIAL.md Efficaci](#come-scrivere-file-initialmd-efficaci)
* [Flusso di Lavoro PRP](#flusso-di-lavoro-prp)
* [Uso Efficace degli Esempi](#uso-efficace-degli-esempi)
* [Migliori Pratiche](#migliori-pratiche)
* [Errori Comuni](#errori-comuni)
* [Risorse](#risorse)

## Cos'è l’Ingegneria del Contesto?

L’ingegneria del contesto rappresenta un cambio di paradigma rispetto alla classica prompt engineering:

### Prompt Engineering vs. Ingegneria del Contesto

**Prompt Engineering:**

* Si concentra sulla formulazione creativa delle richieste
* Limitata al modo in cui viene espressa la domanda
* Come lasciare un post-it

**Ingegneria del Contesto:**

* Sistema completo che fornisce contesto esaustivo
* Include documentazione, esempi, regole, pattern e validazioni
* Come scrivere una sceneggiatura dettagliata

### Perché è Importante

1. **Riduce gli errori dell’IA**: La maggior parte dei fallimenti non dipendono dal modello, ma dalla mancanza di contesto
2. **Garantisce coerenza**: L'IA segue i tuoi pattern e convenzioni
3. **Abilita funzionalità complesse**: L'IA può gestire implementazioni a più fasi se il contesto è adeguato
4. **È auto-correttiva**: I loop di validazione permettono all’IA di correggere i propri errori

## Struttura del Template

```text
context-engineering-intro/
├── .gemini/
│   ├── commands/
│   │   ├── generate-prp.md         # Genera PRP completi
│   │   └── execute-prp.md          # Esegue PRP per implementare funzionalità
│   └── settings.local.json         # Permessi per Gemini CLI
├── PRPs/
│   ├── templates/
│   │   └── prp_base.md             # Template base per PRP
│   └── EXAMPLE_multi_agent_prp.md  # Esempio completo di PRP
├── examples/                       # Esempi di codice (essenziali!)
├── GEMINI.md                       # Regole globali per l’assistente IA
├── INITIAL.md                      # Template per richieste funzionalità
├── INITIAL_EXAMPLE.md              # Esempio di richiesta
└── README.md                       # Questo file
```

Altri template e supporto per architetture basate su RAG saranno aggiunti in futuro.

## Guida Passo-Passo

### 1. Definisci le Regole Globali (GEMINI.md)

Il file `GEMINI.md` contiene le regole del progetto che l’assistente IA seguirà in ogni conversazione:

* **Consapevolezza del progetto**
* **Struttura del codice**
* **Requisiti di testing**
* **Stile e formattazione**
* **Documentazione e commenti**

Usa il template fornito o personalizzalo per il tuo progetto.

### 2. Crea la Richiesta Iniziale

Modifica `INITIAL.md` come segue:

```markdown
## FUNZIONALITÀ:
[Descrivi in dettaglio cosa vuoi costruire]

## ESEMPI:
[Elenca file nella cartella `examples/` e spiega come devono essere utilizzati]

## DOCUMENTAZIONE:
[Includi link a documenti, API, o risorse MCP]

## ALTRE CONSIDERAZIONI:
[Dettagli importanti da non trascurare]
```

Consulta `INITIAL_EXAMPLE.md` per un esempio.

### 3. Genera il PRP

I PRP sono piani completi per l’assistente IA. Includono:

* Contesto dettagliato
* Istruzioni passo-passo
* Validazioni e test
* Gestione degli errori

Tabella comparativa:

| PRD (Requisiti Prodotto)       | PRP (Prompt Requisiti Prodotto)        |
| ------------------------------ | -------------------------------------- |
| Scritto per sviluppatori umani | Ottimizzato per assistenti IA          |
| Può essere ambiguo             | Richiede precisione e validazione      |
| Alto livello descrittivo       | Orientato all’implementazione concreta |

Comando:

```bash
gemini -p "@./.gemini/commands/generate-prp.md" "INITIAL.md"
```

### 4. Esegui il PRP

```bash
gemini -p "@./.gemini/commands/execute-prp.md" "PRPs/your-feature-name.md"
```

L’assistente IA:

1. Legge il contesto
2. Pianifica i task
3. Implementa passo-passo
4. Esegue test
5. Corregge problemi
6. Verifica che tutto sia conforme

## Come Scrivere File INITIAL.md Efficaci

Consulta la [tabella PRD vs PRP](#3-genera-il-prp) per comprendere le differenze.

### Sezioni Chiave

**FUNZIONALITÀ**

* ❌ "Crea uno scraper"
* ✅ "Crea uno scraper asincrono con BeautifulSoup, gestione rate limiting, e salvataggio in PostgreSQL"

**ESEMPI**

* Inserisci pattern in `examples/`
* Spiega cosa deve essere imitato

**DOCUMENTAZIONE**

* API, guide librerie, schemi DB, documenti MCP

**ALTRE CONSIDERAZIONI**

* Autenticazione, limiti di utilizzo, errori frequenti, performance

## Flusso di Lavoro PRP

### Come funziona `/generate-prp`

1. Analizza il codice
2. Raccoglie documentazione
3. Genera piano operativo
4. Controlla qualità e fiducia

### Come funziona `/execute-prp`

1. Carica contesto
2. Pianifica
3. Implementa
4. Valida con test
5. Itera se necessario
6. Completa

Vedi `EXAMPLE_multi_agent_prp.md` per un esempio.

## Uso Efficace degli Esempi

La cartella `examples/` è cruciale.

### Cosa Includere

1. **Struttura del codice**
2. **Test e mocking**
3. **Integrazioni (API, DB, auth)**
4. **CLI (argomenti, output, errori)**

```text
examples/
├── README.md
├── cli.py
├── agent/
│   ├── agent.py
│   ├── tools.py
│   └── providers.py
└── tests/
    ├── test_agent.py
    └── conftest.py
```

## Migliori Pratiche

1. Sii specifico in `INITIAL.md`
2. Fornisci molti esempi
3. Usa validazioni
4. Collega documentazione ufficiale
5. Personalizza `GEMINI.md` con le tue regole

## Errori Comuni

Evita questi errori frequenti:

* **Senza esempi**: L’IA genera codice generico
* **Descrizioni vaghe**: Essere specifici migliora i risultati
* **Ignorare GEMINI.md**: Comportamento incoerente
* **Niente test o linting**: PRP incompleto o fallace

## Risorse

* [Documentazione Gemini CLI](https://github.com/google/gemini-cli)
* [Best practice di Context Engineering](https://www.philschmid.de/context-engineering)

---

**Inizia a progettare il tuo contesto oggi stesso – e libera tutto il potenziale dello sviluppo assistito da IA.**
