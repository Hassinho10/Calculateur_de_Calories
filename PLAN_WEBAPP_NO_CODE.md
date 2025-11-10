# Plan de réalisation de l'application web no-code de coaching créatif

## Objectif général
Créer une application web no-code qui combine :

1. Un quiz de profil créatif pour segmenter les utilisateurs.
2. Un coach IA alimenté par un modèle personnel (GPT-5 ou équivalent) et éventuellement Blackbox AI pour le co-pilotage créatif.
3. Des sessions de flow créatif avec timer, mini-défis et suivi des progrès.

L'application doit rester dans une enveloppe budgétaire nulle ou quasi-nulle en s'appuyant sur des outils gratuits.

---

## Stack technique recommandée

| Fonction | Outil | Coût | Notes |
|----------|-------|------|-------|
| Interface utilisateur | Lovable (prioritaire) ou Bubble | 0 € | Lovable offre une mise en page simple. Bubble apporte plus de logique si nécessaire. |
| Base de données | Google Sheets (prioritaire) ou Airtable Free | 0 € | Stockage des profils, résultats de quiz, historiques de sessions et feedbacks. |
| IA intégrée | Compte personnel GPT-5 via API, Webhooks Lovable/Bubble | Inclus | Utiliser une clé API personnelle pour éviter les coûts. |
| IA additionnelle | Blackbox AI (optionnel) | 0 € | Pour assistance à la génération d'idées ou de code. |
| Automatisations | Make (ex-Integromat) | 0 € (jusqu'à 1 000 ops/mois) | Rappels, résumés hebdomadaires, synchronisation de données. |
| Design | Figma ou Canva | 0 € | Conception de la charte visuelle et des maquettes UI. |
| Audio d'ambiance | Playlists Spotify publiques | 0 € | Pour les sessions de flow. |

---

## Répartition des rôles et responsabilités

### Rôle 1 — UX/UI & Expérience utilisateur
- **Responsable** : Personne 1.
- **Missions** :
  - Cartographier le parcours utilisateur (onboarding → quiz → coach → flow → suivi → récapitulatif).
  - Concevoir la charte visuelle (palette, typographies, iconographie, ton de voix) dans Figma.
  - Prototyper les écrans clés dans Figma puis répliquer la structure dans Lovable/Bubble.
  - Assembler un prototype cliquable avec navigation cohérente et flux de données fictifs.
- **Livrable Semaine 1** : Prototype Lovable/Bubble fonctionnel aligné sur les maquettes Figma.

### Rôle 2 — IA & Logique conversationnelle
- **Responsable** : Personne 2.
- **Missions** :
  - Définir les profils-types (ex. Rêveur, Perfectionniste, Explorateur, Producteur) et les attributs associés (ton, besoins, blocages fréquents, tactiques de motivation).
  - Rédiger les prompts systèmes et contextuels pour chaque profil afin d'adapter la voix du coach IA.
  - Construire un mini "prompt engine" (Google Sheets ou table JSON) listant les réponses types, suggestions de défis et scripts de relance par profil et par étape du parcours.
  - Intégrer le modèle GPT-5 via API/Webhook (Lovable ou Bubble) en configurant :
    - Les appels API sécurisés avec la clé personnelle.
    - Le routage conditionnel selon le profil renvoyé par le quiz.
    - Les messages d'état (chargement, erreurs) et la modération de contenu.
  - En option : brancher Blackbox AI pour offrir des inspirations supplémentaires (ex. idées de projets). 
- **Livrable Semaine 1-2** : Chat IA opérationnel qui adapte ses réponses au profil et au contexte de session.

### Rôle 3 — Automatisation & Data
- **Responsable** : Personne 3.
- **Missions** :
  - Structurer la base Google Sheets/Airtable avec des tables pour : utilisateurs, résultats du quiz, sessions de flow, feedbacks, notifications.
  - Créer des scénarios Make :
    - Sauvegarde automatique des interactions et sessions.
    - Rappels avant les sessions planifiées et résumés hebdomadaires (générés via GPT-5).
    - Synchronisation des scores du quiz et du statut des défis dans la base.
  - Construire un mini-dashboard admin (Lovable/Bubble ou Google Data Studio) pour suivre l'engagement et les retours utilisateurs.
- **Livrable Semaine 2-3** : Infrastructure de données fiable avec automatisations et reporting minimal.

---

## Parcours utilisateur MVP
1. **Page d'accueil**
   - Accroche "Découvre ton profil créatif".
   - CTA vers le quiz.
2. **Quiz (5 questions)**
   - Questions multiples sur motivation, obstacles, rythme de travail.
   - Résultat immédiat avec description du profil.
3. **Espace coach IA**
   - Message de bienvenue personnalisé (nom + profil).
   - Chat continu pour fixer un objectif, proposer un défi ou débloquer un blocage.
4. **Session de flow créatif**
   - Timer (25, 45 ou 60 min), mini-défis, playlist Spotify intégrée.
   - Visualisation du progrès (barre ou cercle).
5. **Clôture de session**
   - Formulaire rapide de feedback (humeur, accomplissements, difficultés).
   - Résumé envoyé par email ou notification + plan d'action suivant.

---

## Feuille de route sur 3 semaines

### Semaine 1 — Design & Structure
- Finaliser la charte graphique et les composants UI dans Figma.
- Configurer les pages principales dans Lovable/Bubble avec données fictives.
- Définir les profils-types et la structure du prompt engine.

### Semaine 2 — IA & Base de données
- Brancher le quiz aux profils et stocker les résultats dans Google Sheets/Airtable.
- Implémenter le chat IA connecté au modèle GPT-5 personnel.
- Ajouter un mode "idées rapides" via Blackbox AI (optionnel).

### Semaine 3 — Automatisation & Tests
- Mettre en place les scénarios Make : rappels, sauvegardes, résumés hebdomadaires.
- Construire le dashboard de suivi.
- Organiser un test utilisateur (3-5 personnes) et intégrer les retours critiques.

---

## Contrôle des coûts
- Utiliser l'API personnelle GPT-5 uniquement via des appels rationnels (limiter tokens, logs).
- Limiter les opérations Make en regroupant les actions (batch hebdomadaires).
- Conserver les données légères dans Google Sheets pour rester sur le plan gratuit.
- Utiliser des ressources audio libres/Spotify public pour l'ambiance.

---

## Prochaines étapes immédiates
1. Personne 1 : lancer la maquette Figma et structurer le projet Lovable.
2. Personne 2 : rédiger les prompts par profil et préparer les scripts d'appel GPT-5.
3. Personne 3 : créer la structure Google Sheets et esquisser les scénarios Make.

Une réunion de synchronisation en fin de semaine 1 validera l'alignement design/logique/data avant l'intégration finale.
