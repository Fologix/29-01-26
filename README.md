# TimeTravel Agency — Webapp Interactive

Webapp fictive pour une agence de voyage temporel de luxe, présentant 3 destinations (Paris 1889, Crétacé -65M, Florence 1504) avec fonctionnalités IA (chatbot + recommandation).

## Membres du groupe
- VERRIEZ Yassine
- VIANEZ Titouan
- GOTTI Florent
- MACIPE Pablo
- CHAPOTON André

## Stack technique
- Frontend: React (ou Next.js) + Tailwind CSS
- Animations: Framer Motion (ou animations Tailwind)
- IA: Chatbot via (API LLM OU widget no-code)
- Déploiement: Vercel (ou Netlify)

## Features implémentées
- Landing page (hero + CTA) + navigation par ancres
- Galerie “Destinations” (3 cards interactives + détails)
- Intégration des assets du projet Session 1 (visuels destinations)
- Chatbot IA (assistant “Chronos”) : infos, prix, conseils, FAQ
- Quiz de personnalisation (recommandation de destination)
- FAQ (accordion)
- Animations UI/UX subtiles (hover, fade-in)

## IA & transparence (outils utilisés)
- Génération/itérations code: (Bolt.new / v0.dev / Cursor / autre)
- Prompts (résumé):
  - Prompt structure UI + sections
  - Prompt animations subtiles
  - System prompt chatbot “Chronos” (voir ci-dessous)
- Modèle/solution chatbot:
  - (ex: API LLM via serveur) OU (widget no-code)

## Prompts (extraits)
### UI
“Landing page for luxury time travel agency… hero… 3 destination cards… chatbot widget… dark mode… premium feel…”
### Chatbot (system prompt)
Chronos = concierge luxe, connaît uniquement Paris 1889 / Crétacé -65M / Florence 1504, propose prix cohérents, conseils pratiques.

## Installation (si applicable)
```bash
npm install
npm run dev
