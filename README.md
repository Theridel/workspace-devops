# 🛠 Workspace DevSecOps: Piattaforma Unificata & Learning Path

## 🎯 Obiettivo del Repository

Questo repository è un **monorepo** (un unico contenitore centralizzato) che unifica i miei workflow, le utility di sistema e gli ambienti containerizzati. 

Più che una semplice raccolta di codice, questo spazio funge da **palestra e Proof of Concept (PoC)** per progettare e implementare un ciclo di vita del software sicuro, standardizzato e automatizzato. L'obiettivo principale è la **formazione continua** e l'acquisizione pratica di competenze architetturali e metodologiche.

### Cosa imparerai e troverai qui:
- Mentalità DevOps applicata a scenari eterogenei (Web, OS, Container)
- Integrazione della sicurezza in ogni fase (DevSecOps)
- Automazione spinta tramite pipeline CI/CD (GitHub Actions)
- Qualità del codice, testing e standardizzazione

---

## 📂 Struttura del Progetto (Moduli)

Il repository è diviso in moduli logici indipendenti, ma governati dalle stesse regole di sicurezza e automazione:

- 🌐 **`/workflow`**: GitHub Actions permette di creare pipeline che possono essere richiamate da altri repository semplicemente usando un link per testare il deploy, le pipeline CI/CD e il testing automatizzato.
- 🐧 **`/modules/linux`**: Script di automazione e utility di sistema (Bash e LISP) per gestire e configurare comodamente ambienti Linux.
- 🐳 **`/modules/docker`**: Risultati formativi, Dockerfile ottimizzati e configurazioni per generare e testare container in modo sicuro.

---

## 🧠 Principi Guida Universali

Le seguenti regole si applicano a **tutto** il codice presente in questo repository, che sia un un workflow o uno script di sistema:

### 1. Shift Left
La qualità e la sicurezza vengono introdotte **prima**, non alla fine. (es. scansioneremo i Dockerfile per le vulnerabilità prima ancora di creare le immagini).

### 2. Automazione
Tutto ciò che può essere automatizzato **deve essere automatizzato**. Se un'operazione richiede più di due passaggi manuali, merita uno script o un workflow.

### 3. Fail Fast
Gli errori devono emergere subito (build fallita > bug in produzione). Testeremo il codice a ogni singolo *commit*.

### 4. Everything as Code
Configurazioni, pipeline e regole vivono in questo repository e sono tracciate tramite Git.

---

# 🚀 Metodo di Lavoro

Per garantire la massima comprensione, lo sviluppo in questo repository segue un processo rigoroso:

1. **Analisi dello step**: Capire il *perché* prima del *come*.
2. **Implementazione guidata**: Scrittura del codice un modulo alla volta.
3. **Feedback e dubbi**: Revisione di quanto fatto e validazione.
4. **Iterazione**: Miglioramento continuo tramite refactoring.

👉 **Regola d'oro:** Ogni step, script o configurazione di pipeline deve essere **compreso a fondo**, non solo eseguito o copiato.

---

# 📊 Obiettivo Finale

Alla fine del percorso, questo workspace disporrà di:

✅ Pipeline CI/CD globali e modulari (GitHub Actions)
✅ Testing e linting automatizzato per JS, Bash e Docker
✅ Sicurezza integrata (scansione dipendenze, SAST, secret detection)
✅ Architettura pulita e priva di vendor lock-in
