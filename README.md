# FacturoAfrik - SaaS de Facturation, Devis & Relances pour Freelances & PME

> **SaaS de création automatique de devis, factures, reçus et bons de commande avec gestion des clients, relances impayées sur WhatsApp et encaissement Mobile Money & Cartes bancaires.**

---

## 🚀 Fonctionnalités Clés

1. **Génération Instantanée de Documents Commerciaux**
   - **Factures** : Calcul automatique des totaux HT/TTC, remises, acomptes et arrêté du montant en toutes lettres en français selon les normes OHADA.
   - **Devis** : Proposition commerciale chiffrée avec durée de validité et conversion en facture en 1 clic.
   - **Reçus de paiement** : Quittance libératoire générée automatiquement dès qu'un paiement est enregistré.
   - **Bons de commande** : Validation formelle d'ordre de commande avec date de livraison.
   - **Export & Impression PDF A4** : Rendu vectoriel propre, haute définition, sans éléments d'interface parasites.

2. **Écosystème Financier & Fiscal Africain**
   - **Multi-Devises** : Franc CFA (XOF, XAF), Franc Guinéen (GNF), Franc Congolais (CDF), Dirham Marocain (MAD), Naira (NGN), Cedi (GHS), Shilling (KES), Euro (€), Dollar ($).
   - **Mobile Money & Banque** : Coordonnées Wave, Orange Money, MTN MoMo, Moov Money, Airtel Money et RIB/IBAN bancaires intégrés aux documents.
   - **Identifiants Fiscaux** : Prise en charge des NINEA (Sénégal), RCCM (Côte d'Ivoire/UEMOA), IFU (Bénin), NIU (Cameroun), ICE (Maroc), SIRET, etc.
   - **Cachet d'entreprise officiel** : Sceau d'entreprise avec date et mention légale.

3. **Module de Relances Automatiques pour Impayés**
   - Détection des retards de paiement en temps réel.
   - 4 niveaux d'alerte (Courtois, Jour J, Ferme, Mise en demeure légale OHADA).
   - Envoi instantané en 1 clic sur **WhatsApp** et par **Email**.

4. **Tableau de Bord & Graphique Recharts**
   - Chiffre d'affaires encaissé, factures en attente, montant impayé.
   - Graphique interactif de l'évolution mensuelle sur 6 mois (encaissé vs facturé) avec bascule Courbe / Colonnes.

5. **Modèle Économique & Monétisation SaaS**
   - **Starter Gratuit** : 0 FCFA/mois (3 factures, 5 clients).
   - **Pro Indépendant** : 4 900 FCFA/mois ou 49 000 FCFA/an (Illimité, relances WhatsApp, logo & cachet).
   - **Business PME** : 14 900 FCFA/mois ou 149 000 FCFA/an (Multi-utilisateurs, export OHADA).
   - Page vitrine commerciale intégrée (Landing Page).
   - Passerelles d'encaissement SaaS configurables (Paystack, Wave Business, CinetPay, Stripe).

---

## 🛠️ Installation & Démarrage Local

### Prérequis
- [Node.js](https://nodejs.org/) version 18 ou supérieure.
- Gestionnaire de paquets `npm` ou `pnpm` ou `yarn`.

### Étapes d'installation
```bash
# 1. Installer les dépendances
npm install

# 2. Lancer le serveur de développement en local
npm run dev
```

L'application s'ouvrira sur `http://localhost:3000` (ou le port indiqué par Vite).

---

## 📦 Déploiement en Production

### Option 1 : Déploiement Statique (Vercel, Netlify, Render, Cloudflare Pages)
```bash
npm run build
```
Le dossier `dist/` généré contient l'application prête pour la production. Déployez simplement ce dossier sur Vercel ou Netlify.

### Option 2 : Déploiement Docker ou VPS (Cloud Run, Railway, DigitalOcean)
Créez un simple `Dockerfile` ou servez le dossier `dist` avec Nginx.

---

## 📂 Structure du Code Source

```text
facturoafrik/
├── index.html                  # Point d'entrée HTML avec polices & métadonnées
├── package.json                # Dépendances (React 19, Vite, Recharts, Lucide, Tailwind 4, JSZip)
├── tsconfig.json               # Configuration TypeScript
├── vite.config.ts              # Configuration Vite & Tailwind
├── src/
│   ├── main.tsx                # Montage de l'application React
│   ├── App.tsx                 # Composant racine, routage et gestion des états globaux
│   ├── index.css               # Styles globaux Tailwind 4 et règles d'impression PDF A4
│   ├── types/
│   │   ├── index.ts            # Modèles de données (Document, Client, CompanyProfile, Items)
│   │   └── pricing.ts          # Forfaits SaaS, abonnements et passerelles de paiement
│   ├── utils/
│   │   ├── currencies.ts       # Devises africaines, formats monétaires et suggestions
│   │   ├── numberToWordsFrench.ts # Algorithme d'arrêté de sommes en toutes lettres OHADA
│   │   ├── sampleData.ts       # Données de démonstration réalistes (6 mois d'historique)
│   │   ├── storage.ts          # Persistance locale localStorage et calculs de totaux
│   │   └── zipGenerator.ts     # Générateur dynamique de téléchargement du code source ZIP
│   ├── components/
│   │   ├── Header.tsx          # Barre de navigation avec badge d'abonnement et actions
│   │   ├── Dashboard.tsx       # Tableau de bord financier, métriques et actions rapides
│   │   ├── RevenueChart.tsx    # Graphique Recharts d'évolution mensuelle du CA sur 6 mois
│   │   ├── DocumentList.tsx    # Liste, filtres avancés, recherche et conversion en 1 clic
│   │   ├── DocumentEditor.tsx  # Création & modification de Factures, Devis, Reçus et BC
│   │   ├── DocumentViewer.tsx  # Fiche A4 imprimable, export PDF et partage WhatsApp
│   │   ├── RemindersManager.tsx# Gestionnaire interactif des relances impayées WhatsApp/Email
│   │   ├── ClientsManager.tsx  # CRM clients avec historique des documents et soldes
│   │   ├── PaymentModal.tsx    # Enregistrement de règlements et génération automatique de reçu
│   │   ├── SubscriptionModal.tsx # Checkout d'abonnements Wave, Orange Money, MoMo et Cartes
│   │   ├── SettingsModal.tsx   # Paramètres d'activité et configuration des passerelles SaaS
│   │   └── LandingPage.tsx     # Page vitrine publique pour acquérir des clients
│   └── assets/                 # Images et avatars professionnels
└── public/
    └── facturoafrik-saas.zip   # Fichier d'archive ZIP complet téléchargeable
```

---

## 🔒 Confidentialité & Sécurité
- Aucune donnée client ou financière n'est transmise à des tiers sans votre consentement.
- Les données sont stockées en local et peuvent être sauvegardées/restaurées à tout moment via des fichiers JSON ou exportées en code source complet.

---

© 2026 FacturoAfrik. Conçu pour booster l'entrepreneuriat africain.
