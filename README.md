# TimeTravel Agency — Webapp Interactive

Webapp **one-page** (statique) pour une agence fictive de voyage temporel premium, avec **3 destinations** et un **agent conversationnel** intégré.

## Membres du groupe
- VERRIEZ Yassine
- VIANEZ Titouan
- GOTTI Florent
- MACIPE Pablo
- CHAPOTON André

## Liens (à compléter)
- Démo en ligne : http://digiticar.fr/
- Repo : https://github.com/Fologix/29-01-26

---

## Stack technique
- **HTML5 / CSS3 / JavaScript (vanilla)**
- Aucune dépendance, aucun build : le projet tourne en **site statique**

---

## Features
- **Landing / Hero** avec fond animé (canvas “starfield”) + CTA
- **Navigation** par ancres (Agence / Destinations / Réservation)
- **3 destinations** : Paris 1889, Crétacé (-65M), Florence 1504
  - Cards interactives (hover)
  - **Modal** de détails (infos, CTA réservation, CTA chat)
- **Réservation (simulation)**
  - Sélection destination + dates + préférence
  - Validation front + message de confirmation (toast)
- **Agent conversationnel (widget)**
  - Bouton flottant + fenêtre de chat
  - Réponses contextualisées selon la destination sélectionnée
  - Intents gérés : prix/budget, durée, sécurité, culture, aventure, art, réservation
- **Animations UX**
  - Apparition des sections au scroll (IntersectionObserver)
  - Micro-interactions (boutons, cards, modal)

---

## Structure du projet
├── index.html # Structure de la page (sections, modal, chat, toast)
├── style.css # Thème dark premium + gold, layout, components (cards/modal/chat)
└── app.js # Logique : starfield, reveal, modal, booking, chatbot

---

## Lancer en local
### Option 1 — Double-clic
Ouvrir `index.html` dans un navigateur.

### Option 2 — Serveur local (recommandé)
```bash
# Python
python -m http.server 5173
# puis ouvrir http://localhost:5173

##Déploiement (statique)
Vercel

Importer le repo GitHub

Framework preset : “Other”

Build command : (vide)

Output : (racine)

## Deploy

Netlify

Drag & drop du dossier du projet

Vérifier la page en mobile + desktop

GitHub Pages

Push sur GitHub

Settings → Pages → Deploy from branch → / (root)

Personnalisation rapide
Remplacer les visuels des destinations

Dans index.html, chaque card contient une div.thumb avec un background-image.
Remplacez la partie url(...) par l’URL de vos images (Session 1), ou modifiez la card pour afficher un <img>.

Modifier les contenus / prix / règles

Dans app.js, modifiez l’objet DESTS :

name, short, vibe

priceBase (base de calcul)

duration, safety, tips, opener

IA / Agent conversationnel (implémentation)

Le chatbot est un agent conversationnel côté front :

détection d’intent par mots-clés (prix, sécurité, etc.)

génération de réponse contextuelle selon la destination sélectionnée

estimation de prix en fonction des dates (heuristique simple)

Extension possible : brancher un vrai LLM via une fonction serverless (/api/chat) et remplacer la fonction de réponse locale par un appel API.

Méthode de réalisation (Vibe Coding) + Prompts utilisés
1) Génération de la base UI (structure + style)

Prompt

Crée une webapp one-page “TimeTravel Agency” (luxe, dark mode, accents dorés).
Sections : Header (ancres), Hero premium avec fond animé, About, Destinations (3 cards),
Modal de détails, Réservation (formulaire), Widget chatbot en bas à droite, Footer.
Responsive mobile-first, micro-interactions, animations subtiles.
Aucune dépendance : HTML/CSS/JS.

2) Itération design premium (CSS)

Prompt

Améliore le design : thème dark premium + gold, glassmorphism, ombres douces.
Ajoute : hover effects cards, boutons premium, modal élégant, chat widget cohérent.
Priorité : lisibilité, responsive, performance.

3) Ajout des animations et interactions (JS)

Prompt

Ajoute les fonctionnalités JS suivantes :
- Fond animé canvas (starfield) dans le hero
- Apparition des sections au scroll (IntersectionObserver)
- Cards destinations -> ouverture modal + remplissage dynamique
- CTA modal : pré-remplir réservation + ouvrir chat
- Formulaire : validation dates + toast de confirmation
- Navigation ancres en smooth scroll

4) Conception de l’agent conversationnel

Prompt (spécification)

Implémente un chatbot UI (bulle flottante) avec :
- ouverture/fermeture, historique messages, envoi sur Enter, ESC pour fermer
- réponses selon destination sélectionnée (Paris 1889 / Crétacé / Florence 1504)
- intents : prix, durée, sécurité, culture, aventure, art, réservation
- réponses courtes, cohérentes, ton “concierge historique premium”


Prompt (si branchement LLM — optionnel)

System prompt :
Tu es “Chronos”, concierge premium de TimeTravel Agency.
Tu ne connais que : Paris 1889, Crétacé -65M, Florence 1504.
Réponds de façon concise, crédible, propose des prix cohérents, conseils pratiques.
Pose au plus une question si nécessaire pour recommander.

5) QA / corrections

Prompt

Relis le projet : accessibilité (aria), responsive, performance.
Corrige : éléments cliquables, focus, gestion ESC, cohérence des textes,
erreurs JS éventuelles, et vérifie que tout fonctionne sans dépendances.

Crédits & transparence

Projet pédagogique (M1/M2).

Code + copywriting réalisés avec itérations “vibe coding” + prompts (section ci-dessus).

Les visuels des destinations peuvent provenir du projet Session 1 (à intégrer/remplacer).

Licence

Usage pédagogique uniquement.


Sources projet (structure / features décrites) : :contentReference[oaicite:0]{index=0} :contentReference[oaicite:1]{index=1} :contentReference[oaicite:2]{index=2} :contentReference[oaicite:3]{index=3}  
Critères + exigences de documentation (README + prompts) : :contentReference[oaicite:4]{index=4}  
Conseils méthodo (MVP / versioning prompts / déploiement) : :contentReference[oaicite:5]{index=5}
::contentReference[oaicite:6]{index=6}