# <div align="center">

# 🇮🇹 OpenSign-IT
### Ecosistema Aperto di Intelligenza Artificiale per la Lingua dei Segni Italiana (LIS)
**Traduzione Bidirezionale in Tempo Reale • Generazione Avatar 3D • Dataset Pose-Native Espandibile**

[![Organization: OpenSign-IT](https://img.shields.io/badge/GitHub-OpenSign--IT-181717?style=for-the-badge&logo=github)](https://github.com/OpenSign-IT)
[![Python: 3.10+](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![PyTorch: 2.x](https://img.shields.io/badge/PyTorch-2.x-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://pytorch.org/)
[![Pose Standard: 128 Punti](https://img.shields.io/badge/Standard-DWPose_128--pt-00b894?style=for-the-badge&logo=ai)](https://github.com/OpenSign-IT/opensign-lis-dataset)
[![3D Engine: SMPL--X & Three.js](https://img.shields.io/badge/3D_Avatars-SMPL--X_%2B_Three.js-005CED?style=for-the-badge&logo=threedotjs&logoColor=white)](https://threejs.org/)
[![Code License: Apache 2.0](https://img.shields.io/badge/Code_License-Apache_2.0-0984e3?style=for-the-badge)](https://opensource.org/licenses/Apache-2.0)
[![Data License: CC BY 4.0](https://img.shields.io/badge/Dataset_License-CC_BY_4.0-6c5ce7?style=for-the-badge)](https://creativecommons.org/licenses/by/4.0/)

<br/>

*Un'iniziativa aperta e non profit guidata dal principio «Nothing About Us Without Us», per abbattere le barriere comunicative e fare della Lingua dei Segni Italiana (LIS) un punto di riferimento nell'accessibilità digitale globale.*

</div>

---

## 🎯 Visione & Mission

Nel panorama scientifico dell'Intelligenza Artificiale e del Natural Language Processing, la **Lingua dei Segni Italiana (LIS - ISO 639-3: `ise`)** è storicamente considerata una lingua a basse risorse (*low-resource language*). La scarsità di dataset annotati e di modelli computazionali dedicati limita fortemente l'accessibilità digitale per le persone sorde.

**OpenSign-IT** nasce per colmare questo divario attraverso un **ecosistema tecnologico simmetrico e open-source**. La vera inclusione non può essere a senso unico: la nostra missione è sviluppare strumenti per la **comunicazione bidirezionale in tempo reale**, unendo la comprensione visiva del segnato umano alla generazione espressiva di avatar 3D parlanti e segnanti.

---

### 🔄 Il Ciclo di Comunicazione Bidirezionale

L'ecosistema è progettato per garantire una comunicazione simmetrica e senza attriti:

#### 🟢 Canale 1: Dall'Udente al Sordo (`Text-to-Sign / 3D Avatar`)
> **1. Input Utente**: 🗣️ **Persona Udente** parla al microfono (Voice-to-Text) o digita un messaggio.  
> **2. Analisi Linguistica**: 🧠 **NLP & Morfosintassi LIS** traduce la grammatica italiana in struttura a Gloss LIS.  
> **3. Sintesi Cinematica**: 🤖 **Modello Generativo Pose 3D** sintetizza le traiettorie scheletriche a 128 punti.  
> **4. Raffinamento**: ⚡ **Filtro 1-Euro** rimuove il micro-jitter da falangi, labbra e capo senza ritardi.  
> **5. Rendering Espressivo**: 🧍 **Avatar 3D SMPL-X / Three.js** anima il segnato con labio-lettura ed espressioni.  
> **6. Ricezione**: 🤟 **Persona Sorda** visualizza e comprende il segnato in modo chiaro e naturale.

#### 🔵 Canale 2: Dal Sordo all'Udente (`Sign-to-Text / CSLR`)
> **1. Input Segnato**: 🤟 **Persona Sorda** segna liberamente davanti alla webcam del dispositivo.  
> **2. Vision Tracking**: 👁️ **DWPose Wholebody** rileva in tempo reale 128 punti anatomici (corpo, mani e viso) @ 24 FPS.  
> **3. Riconoscimento Spazio-Temporale**: 🧠 **Reti GCN & Transformers** decodificano configurazione, movimento e labiale.  
> **4. Traduzione Linguistica**: 📝 **Sign Language Translation (SLT)** genera la frase corrispondente in italiano.  
> **5. Ricezione**: 👂 **Persona Udente** legge i sottotitoli a video o ascolta la voce sintetizzata.

---

### 📊 Matrice di Funzionamento dei Due Canali

| Fase del Flusso | 🟢 Canale 1: Text-to-Sign (Per la Persona Sorda) | 🔵 Canale 2: Sign-to-Text (Per la Persona Udente) |
| :--- | :--- | :--- |
| **Soggetto Emittente** | 🗣️ Persona Udente | 🤟 Persona Sorda |
| **Modalità di Input** | Voce al microfono o testo digitato | Segnato naturale ripreso da Webcam |
| **Tecnologia di Input** | Trascrizione vocale (STT) / Parsing testuale | **DWPose Wholebody**: 128 keypoints @ 24 FPS |
| **Motore di Elaborazione AI** | **Modello Generativo Text-to-Pose**: Glossing + Diffusione traiettorie 3D | **Modello CSLR / SLT**: Reti neurali spazio-temporali (GCN + Transformers) |
| **Controllo Qualità Cinetico** | **1-Euro Filter**: azzeramento tremolio su dita e labbra | Tracciamento robusto a occlusioni e incroci rapidi |
| **Output Finale Ricevuto** | 🧍 **Avatar 3D (Three.js / SMPL-X)** con articolazione completa e labiale | 👂 **Testo a schermo** o **Sintesi vocale (TTS)** in tempo reale |


---

## 🔬 I Moduli Chiave dell'Ecosistema

### 1. 🧍 Text-to-Avatar 3D: Generazione di Segnato Iper-Realistico
La Lingua dei Segni non è una semplice sequenza di gesti isolati, ma una lingua visuo-spaziale ricca di sfumature:
* **Articolazione Fine delle Mani (42 keypoints)**: Modella i movimenti di tutte le 5 dita (falangi prossimali, intermedie e distali) con gestione precisa delle auto-occlusioni.
* **Labio-Lettura ed Espressioni Facciali (68 keypoints)**: La componente non-manuale (labializzazione, movimenti di sopracciglia e postura del capo) veicola informazioni morfo-sintattiche essenziali (interrogative, negazioni, qualificatori).
* **Filtro Cinetico Adattivo (1-Euro Filter)**: Azzeramento del jitter e del tremolio nei fermo-posta, preservando la massima reattività durante gli scatti veloci delle mani.
* **Mesh Parametriche SMPL-X**: Generazione di corpi 3D anatomicamente coerenti, pronti per essere renderizzati in real-time su WebGL (Three.js) o esportati verso Unreal Engine e Unity.

### 2. 👁️ Vision-to-Text: Continuous Sign Language Recognition (CSLR)
* **Pipeline Pose-Native DWPose**: Due stadi (YOLOX + RTMPose Wholebody) per estrarre 128 punti anatomici normalizzati a 24 FPS.
* **Architettura Spazio-Temporale**: Reti Graph Convolutional (GCN) e Transformers per interpretare le relazioni tra giunzioni corporee nel tempo.
* **Privacy-by-Design a Norma GDPR**: L'estrazione converte i pixel in matrici numeriche anonime (`poses.npz`). Nessuna immagine o dato biometrico identificativo viene archiviato o distribuito.

### 3. 🌐 Web App di Traduzione Bidirezionale in Tempo Reale
* **Accessibile Ovunque**: Applicazione Web progressiva (PWA) fruibile da browser desktop e smartphone senza installare software proprietario.
* **Interfaccia Split-Screen Interattiva**: Un riquadro per la webcam che traduce il segnante LIS in testo/audio, e un riquadro con l'avatar 3D che traduce le risposte dell'interlocutore in LIS.
* **Inferenza Edge / Client-Side**: Esecuzione dei modelli nel browser (WebAssembly, WebGPU, Three.js) per garantire zero latenza e massima riservatezza dei dati.

### 4. 🚀 Dataset Vivo ed Espandibile via Crowdsourcing
Il dataset non è una collezione chiusa, ma una piattaforma collaborativa in continua crescita:
* **Punto di Partenza**: 929 video in LIS selezionati dal corpus *YouTube-SL-25* di Google Research (ICLR 2025).
* **Espansione Aperta alla Comunità**: Interpreti LIS, università, associazioni di persone sorde e volontari possono contribuire caricando nuovi video e allineando sottotitoli tramite strumenti guidati.
* **Mappatura delle Varianti Regionali**: La LIS è ricca di variazioni lessicali sul territorio italiano; il nostro benchmark punta a preservare e rappresentare questa diversità socio-linguistica.
* **Quality Assurance con la Comunità Sorda**: Verifica umana dei segmenti temporali e delle traduzioni per garantire un'accuratezza linguistica reale.

---

## 🗺️ Mappa dei Repository dell'Organizzazione

| Repository | Stato | Descrizione | Stack Principale |
| :--- | :---: | :--- | :--- |
| [**`opensign-lis-dataset`**](https://github.com/OpenSign-IT/opensign-lis-dataset) | ![Attivo](https://img.shields.io/badge/Stato-Attivo_Benchmark-success?style=flat-square) | **Benchmark & Pipeline Ingestion**: Estrazione 128 keypoints @ 24 FPS per 929 video LIS, allineamento VTT e checkpointing. | Python, DWPose, ONNX, yt-dlp |
| [**`opensign-text-to-avatar`**](https://github.com/OpenSign-IT) | ![In Sviluppo](https://img.shields.io/badge/Stato-In_Sviluppo-orange?style=flat-square) | **Motore Generativo Text-to-Sign**: Da testo/voce a traiettorie articolari 3D e animazione di mesh parametriche SMPL-X. | PyTorch, SMPL-X, Diffusion, SciPy |
| [**`opensign-vision-translator`**](https://github.com/OpenSign-IT) | ![In Sviluppo](https://img.shields.io/badge/Stato-In_Sviluppo-orange?style=flat-square) | **Riconoscimento & Traduzione LIS $\rightarrow$ Testo**: Reti neurali spazio-temporali per CSLR e Sign Language Translation. | PyTorch, Spatio-Temporal GCN, Transformers |
| [**`opensign-web-app`**](https://github.com/OpenSign-IT) | ![In Arrivo](https://img.shields.io/badge/Stato-In_Arrivo-blue?style=flat-square) | **Web App Hub Bidirezionale**: Applicazione web per comunicare in tempo reale via webcam e avatar 3D. | Three.js, WebGL, WebRTC, Vanilla JS |
| [**`opensign-preview-tools`**](https://github.com/OpenSign-IT) | ![Attivo](https://img.shields.io/badge/Stato-Attivo_Tool-success?style=flat-square) | **Viewer & Kinematic Studio**: Studio di confronto side-by-side (video reale vs manichino 3D) con parser client-side `.npz`. | Three.js, JSZip, PBR Shaders, HTML5 |

---

## 🛠️ Stack Tecnologico

| Ambito | Tecnologie Adottate | Dettagli di Utilizzo |
| :--- | :--- | :--- |
| **Computer Vision** | `DWPose Wholebody`, `YOLOX`, `RTMPose` | Rilevamento simultaneo di corpo (18 pt), mani (42 pt) e viso (68 pt). |
| **Smoothing Cinetico** | `1-Euro Filter`, `Savitzky-Golay` | Filtri adattivi a bassa latenza implementati in Python e JavaScript. |
| **AI Generativa & NLP** | `PyTorch 2.x`, `Hugging Face`, `Transformers` | Modelli sequenza-a-sequenza per traduzione, allineamento gloss e diffusion. |
| **Grafica 3D & Avatar** | `SMPL-X`, `Trimesh`, `PyRender`, `Three.js` | Rigging scheletrico, cinematica diretta/inversa e rendering PBR WebGL. |
| **Accelerazione Hardware** | `ONNX Runtime`, `CUDA`, `Apple CoreML` | Inferenza ad alte prestazioni su server, Apple Silicon e notebook GPU. |
| **Web & Comunicazione** | `HTML5`, `CSS3 Modern Glassmorphism`, `WebRTC` | Interfaccia utente ultra-reattiva, accessibile e conforme agli standard W3C. |

---

## ⚖️ Etica, Privacy e Diritto alla Ricerca

* **Privacy-Preserving by Design**: Non distribuiamo video grezzi o dati biometrici identificativi. I file del dataset contengono solo coordinate numeriche normalizzate (`poses.npz`) e segmenti testuali (`caption.json`).
* **Eccezione TDM (Direttiva UE 2019/790)**: L'estrazione delle feature matematiche per scopi scientifici è protetta dall'**Articolo 3** della direttiva europea sul diritto d'autore per il Text and Data Mining.
* **Centralità della Comunità Sorda**: Crediamo che l'Intelligenza Artificiale debba nascere con e per la comunità sorda, valorizzando gli interpreti professionisti e gli standard linguistici ufficiali.

---

## 🤝 Collaborazioni, Ricerca e Accesso ai Dati

Accogliamo contributi da ricercatori, sviluppatori, associazioni e cittadini:
* **Ricerca Accademica**: Sperimentazione su modelli CSLR, Text-to-Pose e architetture spazio-temporali.
* **Donazione di Dati & Revisione Linguistica**: Ampliamento del corpus con nuovi segni, conversazioni e varianti regionali.
* **Integrazioni Software**: Dataloaders per Hugging Face, PyTorch Dataset, Unity o WebDataset.

> [!NOTE]
> **Licenze e Contatti**:
> Il codice sorgente è rilasciato sotto licenza **Apache 2.0**, mentre le annotazioni del dataset sono distribuite con licenza **Creative Commons Attribution 4.0 International (CC BY 4.0)**.
> Per richieste scientifiche, collaborazioni o accesso ai tensori pre-estratti: **opensign.dataset@gmail.com** o apri una discussione su [GitHub Discussions](https://github.com/OpenSign-IT).

---

### Citazione Scientifica (BibTeX)

```bibtex
@misc{opensign_it_2026,
  author    = {OpenSign-IT Contributors},
  title     = {OpenSign-IT: An Open-Source AI Ecosystem for Bidirectional Italian Sign Language Processing and 3D Avatar Generation},
  year      = {2026},
  publisher = {GitHub},
  url       = {https://github.com/OpenSign-IT}
}

@inproceedings{tanzer2025youtubesl25,
  title     = {YouTube-SL-25: A Large Multilingual Corpus for Sign Language Translation},
  author    = {Tanzer, Garrett and Zhang, Biao},
  booktitle = {International Conference on Learning Representations (ICLR)},
  year      = {2025}
}

@article{signverse2024,
  title     = {SignVerse-2M: A Large-Scale Whole-Body Sign Language Dataset},
  author    = {SignVerse Contributors},
  journal   = {arXiv preprint arXiv:2408.00000},
  year      = {2024}
}
```

---

<div align="center">

Costruito con cura dalla comunità **OpenSign-IT** — *Tecnologia aperta al servizio dell'inclusione.*

[![Segui su GitHub](https://img.shields.io/github/followers/OpenSign-IT?label=Segui%20%40OpenSign-IT&style=social)](https://github.com/OpenSign-IT)

</div>
