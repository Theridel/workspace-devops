# 🧱 Roadmap del Workspace DevSecOps

## ⏳ STEP 0 — Inizializzazione Repository Centrale

**Obiettivo:**
Inizializzare il repository remoto della piattaforma con i file di configurazione globali e agnostici.

### 📋 Checklist Operativa
- [x] Creazione del repository centrale su GitHub (es. `workspace-devops`).
- [x] Creazione del file `README.md` aggiornato con la visione globale (Monorepo).
- [x] Creazione del file `roadmap.md` (questo documento).
- [x] Inserimento della `LICENSE` (MIT) per la futura condivisione pubblica.
- [ ] Configurazione di un `.gitignore` globale (esclusione cache, log, `node_modules` locali di test).

**Perché (Shift Left & Everything as Code):**
Garantisce che la radice del progetto sia pulita, tracciata e pronta a ospitare i tre macro-moduli senza ereditare configurazioni specifiche di un singolo applicativo.

---

## ⏳ STEP 1 — Architettura delle Cartelle (I Moduli)

**Obiettivo:**
Definire l'alberatura strutturale del monorepo per ospitare i tre pilastri definiti nel documento "Repository workspace", usando file segnaposto per forzare il tracciamento di Git.

├── .github/
│   └── dependabot.yml
├── workflow/
│   └── todo.md          <-- Pipeline CI/CD riutilizzabili via link
├── modules/
│   ├── linux/
│   │   └── todo.md      <-- Script Bash e LISP
│   └── docker/
│       └── todo.md      <-- Dockerfile e utility containerizzate
└── docs/
└── archive/         <-- Memoria storica del progetto

### 📋 Checklist Operativa
- [ ] Creare la cartella `workflow/` con un file `todo.md`.
- [ ] Creare la sottocartella `modules/linux/` con un file `todo.md`.
- [ ] Creare la sottocartella `modules/docker/` con un file `todo.md`.
- [ ] Creare la cartella d'archivio `docs/archive/`.

**Perché:**
Git non traccia le cartelle vuote. Questa struttura definisce i confini dei tuoi moduli logici prima di iniziare a scrivere il codice effettivo.

---

## ⏳ STEP 2 — Automazione delle Dipendenze (Dependabot)

**Obiettivo:**
Configurare il guardiano automatico della catena di fornitura (Supply Chain Security) per mantenere aggiornati i moduli di base.

### 📋 Checklist Operativa
- [ ] Creare il file `.github/dependabot.yml`.
- [ ] Configurare l'ecosistema `github-actions` per aggiornare i componenti delle pipeline in `/workflow`.
- [ ] Configurare l'ecosistema `docker` puntando alla cartella `modules/docker` per monitorare le immagini base.

**Perché (Automazione):**
I tuoi moduli verranno usati da altri progetti. Se una GitHub Action o un'immagine Docker di base diventa obsoleta o vulnerabile, Dependabot crea una Pull Request automatica nel repository centrale, proteggendo a cascata tutti i progetti figli.

---

## ⏳ STEP 3 — Qualità del Codice Multilinguaggio (Linting)

**Obiettivo:**
Introdurre i controlli statici specifici per i linguaggi usati nella piattaforma (YAML per le Actions, Bash per Linux, Dockerfile per i container).

### 📋 Checklist Operativa
- [ ] Configurare un sistema di verifica per i workflow (es. `actionlint`).
- [ ] Configurare un linter per gli script Bash in `modules/linux` (es. `shellcheck`).
- [ ] Configurare un linter per i file Docker in `modules/docker` (es. `hadolint`).

**Perché (Shift Left & Fail Fast):**
Prima ancora di eseguire uno script Linux o buildare un container, il linter analizza la sintassi per intercettare errori di sicurezza elementari o cattive pratiche direttamente nel repository centrale.

---

## ⏳ STEP 4 — Sicurezza Automatizzata (SAST & Vulnerability Scanning)

**Obiettivo:**
Integrare strumenti di scansione statica della sicurezza (SAST) dedicati all'infrastruttura e alle configurazioni (IaC).

### 📋 Checklist Operativa
- [ ] Configurare uno scanner di sicurezza (es. `Trivy` o `Semgrep`) focalizzato sull'analisi dei Dockerfile e delle configurazioni.
- [ ] Definire le regole di blocco (es. la pipeline fallisce se viene rilevata una vulnerabilità di livello *High* o *Critical* nelle immagini o negli script).

**Perché (Fail Fast):**
Evita che un container non sicuro o uno script con falle di sicurezza strutturali possa essere distribuito ed eseguito altrove.

---

## ⏳ STEP 5 — Sviluppo del Primo Modulo CI/CD Riutilizzabile

**Obiettivo:**
Scrivere la prima pipeline globale riutilizzabile che i tuoi progetti esterni (come il Timer) potranno incorporare tramite link.

### 📋 Checklist Operativa
- [ ] Creare il file del workflow riutilizzabile nella cartella `workflow/` (es. `workflow/ci-web-template.yml`).
- [ ] Configurare il trigger nativo `on: workflow_call` accettando parametri flessibili in input (es. versione di Node, flag per abilitare/disabilitare i test).
- [ ] Scrivere i job standard di validazione (Checkout, Lint, Audit, Test).

**Perché (Everything as Code):**
Questo file diventa il "prodotto" che il tuo repository offre. I progetti esterni non configureranno più la CI localmente, ma la importeranno tramite URL/link puntando a questo modulo.

---

## ⏳ STEP 6 — Sviluppo dei Moduli Linux e Docker Base

**Obiettivo:**
Scrivere i primi script di automazione OS e i Dockerfile ottimizzati secondo i criteri senior (immagini multi-stage, utenti non-root).

### 📋 Checklist Operativa
- [ ] Implementare i primi script Bash/LISP stabili in `modules/linux/`.
- [ ] Scrivere i primi Dockerfile sicuri in `modules/docker/`.

**Perché:**
Popola le sezioni operative del workspace trasformando i concetti teorici in utility di sistema reali e pronte all'uso.

---

## ⏳ STEP 7 — CI Interna del Monorepo

**Obiettivo:**
Creare la pipeline di automazione interna che testa il monorepo stesso ad ogni commit.

### 📋 Checklist Operativa
- [ ] Creare il file `.github/workflows/main-ci.yml`.
- [ ] Configurare l'esecuzione automatica di tutti i linter e scanner impostati negli Step 3 e 4.
- [ ] Abilitare il Path Filtering per fare in modo che modifiche alla documentazione non sovraccarichino inutilmente i runner di GitHub.

**Perché (Fail Fast):**
Se modifichi uno script Linux o un workflow riutilizzabile e commetti un errore, la pipeline interna del monorepo fallisce immediatamente, impedendo la corruzione dei moduli distribuiti.

---

## ⏳ STEP 8 — Strategia di Rilascio e Distribuzione

**Obiettivo:**
Gestire il ciclo di via e il versionamento dei moduli per evitare che aggiornamenti distruttivi rompano i progetti esterni che li usano.

### 📋 Checklist Operativa
- [ ] Definire la strategia di versionamento tramite Git Tags (es. `@v1`, `@v1.1.0`).
- [ ] Configurare la pubblicazione automatica dei container sul GitHub Container Registry (GHCR) se necessario.

**Perché:**
Permette a progetti esterni di agganciarsi a una versione stabile (es. `@v1`), lasciandoti libero di fare esperimenti sul ramo `main` senza interrompere la produzione altrui.

---

## ⏳ STEP 9 — Proof of Concept (PoC) di Collegamento Esterno

**Obiettivo:**
Verificare sul campo il funzionamento dell'architettura richiamando i moduli dal repository separato del Timer.

### 📋 Checklist Operativa
- [ ] Andare nel repository separato del Timer.
- [ ] Creare una pipeline locale minima che contiene esclusivamente il link (`uses: tuo-utente/tuo-repo/workflow/ci-web-template.yml@v1`).
- [ ] Verificare che GitHub Actions scarichi correttamente il modulo centrale ed esegua i controlli sul codice del Timer.

**Perché:**
È la validazione finale del progetto: dimostra che il monorepo funziona correttamente come fornitore centralizzato di servizi CI/CD.

---

## ⏳ STEP 10 — Iterazione e Manutenzione

**Obiettivo:**
Eseguire il refactoring continuo, spostare i file `todo.md` nell'archivio e raccogliere i feedback di utilizzo.
