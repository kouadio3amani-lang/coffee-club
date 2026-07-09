# 🐇 Rabbit Market

<div align="center">

![Rabbit Market Logo](assets/icone.png)

**La première marketplace cunicole de Côte d'Ivoire**

*Achetez et vendez des lapins, aliments, équipements et produits agricoles*

[![Status](https://img.shields.io/badge/Status-En%20développement-orange?style=for-the-badge)]()
[![Platform](https://img.shields.io/badge/Platform-iOS%20%7C%20Android-blue?style=for-the-badge)]()
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)]()
[![PRs Welcome](https://img.shields.io/badge/PRs-Bienvenues-brightgreen?style=for-the-badge)]()

[🚀 Demo](#demo) · [📱 Fonctionnalités](#fonctionnalités) · [🛠️ Installation](#installation) · [🤝 Contribuer](#contribuer) · [📬 Contact](#contact)

</div>

---

## 🌍 À propos du projet

**Rabbit Market** est une marketplace mobile dédiée à l'élevage cunicole en Côte d'Ivoire. Elle connecte les éleveurs de lapins avec les acheteurs, et propose une expérience d'achat de niveau **Jumia** adaptée au marché local ivoirien.

### 🎯 Problème résolu
- Les éleveurs de lapins en CI n'ont pas de plateforme dédiée pour vendre leurs produits
- Les acheteurs peinent à trouver des lapins de qualité, aliments et équipements fiables
- Aucune solution locale ne supporte les paiements mobile money (Wave, MTN MoMo, Orange Money)

### 💡 Notre solution
Une app mobile complète avec :
- Catalogue de lapins vivants + vente en poids carcasse 🥩
- Paiement via **Wave**, **MTN MoMo** et **Orange Money**
- Livraison avec choix du livreur partenaire (**Yango**, **Glovo**, **Koli Express**...)
- Espace vendeur pour gérer sa boutique en ligne
- Espace admin pour modérer la plateforme

---

## 📱 Fonctionnalités

### 🛍️ Espace Acheteur
- Parcourir le catalogue (lapins, aliments, soins, équipements, fourrages)
- Recherche en temps réel avec filtres par catégorie
- Fiche produit détaillée avec variantes et avis
- Vente au kg carcasse avec sélecteur de poids
- Panier multi-vendeurs avec code promo
- Choix du livreur partenaire avec tarifs en temps réel
- Suivi de commande en temps réel
- Système de favoris
- Avis et notes des vendeurs

### 🏪 Espace Vendeur
- Dashboard avec statistiques de ventes
- Gestion des produits (ajouter, modifier, supprimer)
- Gestion des commandes reçues
- Répondre aux avis clients
- Profil public de la ferme
- Graphique des revenus

### ⚙️ Espace Administrateur
- KPIs globaux de la plateforme
- Validation des vendeurs
- Modération des produits
- Gestion des utilisateurs
- Codes promo
- Revenus et statistiques

### 🚚 Livraison Intelligente
- Calcul dynamique selon le poids et la ville
- Choix entre plusieurs livreurs partenaires :
  - 🟡 **Yango Delivery** — 30-60 min (Abidjan)
  - 🟡 **Glovo** — 45-90 min (Abidjan)
  - 🔵 **Koli Express** — 1-3 jours (national)
  - 🟢 **NSIA Transport** — Spécial animaux vivants
  - 🏪 **Retrait vendeur** — Gratuit

---

## 🏗️ Architecture technique

```
Rabbit Market
├── 📱 Frontend      React Native + Expo
├── 🗄️ Backend       Node.js + Express
├── 🐘 Base données  PostgreSQL + Prisma ORM
├── 🔐 Auth          JWT (Access + Refresh Token)
└── 💳 Paiement      Wave · MTN MoMo · Orange Money
```

### Stack complète

| Couche | Technologie |
|--------|------------|
| Mobile | React Native + Expo SDK |
| Navigation | React Navigation v6 |
| Backend | Node.js + Express.js |
| Base de données | PostgreSQL + Prisma ORM |
| Authentification | JWT + bcrypt |
| State management | React Context API |
| Storage local | AsyncStorage |
| HTTP Client | Axios |
| Icons | Expo Vector Icons |

---

## 📁 Structure du projet

```
RabbitMarket/
│
├── 📱 Frontend (Expo)
│   ├── app/
│   │   ├── (tabs)/              # Navigation acheteur
│   │   ├── (seller-tabs)/       # Navigation vendeur
│   │   └── auth/                # Écrans authentification
│   ├── src/
│   │   ├── components/ui/       # Composants réutilisables
│   │   ├── context/             # AuthContext, CartContext, FavoritesContext
│   │   ├── screens/             # Tous les écrans
│   │   ├── theme/               # Couleurs, typographie, spacing
│   │   └── utils/               # Helpers, formatPrice, api.js
│   └── assets/                  # Logo, images
│
└── 🗄️ Backend (Node.js)
    ├── prisma/
    │   └── schema.prisma        # Modèles PostgreSQL
    ├── src/
    │   ├── controllers/         # Logique métier
    │   ├── routes/              # Endpoints API
    │   ├── middleware/          # Auth, rôles, validation
    │   ├── utils/               # JWT, deliveryCalculator, deliveryPartners
    │   └── seed/                # Données de départ
    └── server.js
```

---

## 🎨 Design System

| Élément | Valeur |
|---------|--------|
| Couleur principale | `#F97316` Orange |
| Couleur secondaire | `#7C3AED` Violet |
| Couleur accent | `#EC4899` Rose |
| Fond sombre | `#1E1B4B` Navy |
| Monnaie | FCFA |
| Langue | Français |

---

## 🚀 Installation

### Prérequis

- Node.js v18+ 
- npm ou yarn
- PostgreSQL 14+
- Expo Go (sur votre téléphone Android/iOS)
- Git

### 1. Cloner le projet

```bash
git clone https://github.com/[VOTRE_USERNAME]/rabbit-market.git
cd rabbit-market
```

### 2. Installer PostgreSQL (Linux/Ubuntu)

```bash
sudo apt install postgresql postgresql-contrib -y
sudo systemctl start postgresql
sudo systemctl enable postgresql

# Créer la base de données
sudo -u postgres psql -c "CREATE DATABASE rabbitmarket;"
sudo -u postgres psql -c "CREATE USER rabbituser WITH PASSWORD 'rabbit2024';"
sudo -u postgres psql -c "GRANT ALL PRIVILEGES ON DATABASE rabbitmarket TO rabbituser;"
```

### 3. Configurer le Backend

```bash
cd RabbitMarket-Backend
npm install

# Copier le fichier d'environnement
cp .env.example .env
```

Modifier `.env` :
```env
DATABASE_URL="postgresql://rabbituser:rabbit2024@localhost:5432/rabbitmarket"
JWT_SECRET=rabbit_market_secret_key_2024_ci
JWT_REFRESH_SECRET=rabbit_market_refresh_secret_2024
PORT=5000
```

```bash
# Créer les tables
npx prisma migrate dev --name init

# Peupler la base avec les données de départ
npm run seed

# Démarrer le serveur
npm run dev
```

✅ Le serveur tourne sur `http://localhost:5000`

### 4. Configurer le Frontend

```bash
cd ../RabbitMarket-Frontend
npm install

# Trouver votre IP locale
hostname -I
# Ex: 192.168.1.45
```

Modifier `src/utils/api.js` :
```javascript
const API_URL = 'http://192.168.1.45:5000/api'; // Votre IP ici
```

```bash
# Démarrer Expo
npx expo start
```

Scannez le QR code avec **Expo Go** sur votre téléphone 📱

### 5. Comptes de test

| Rôle | Email | Mot de passe |
|------|-------|-------------|
| 👤 Acheteur | acheteur@test.ci | 123456 |
| 🏪 Vendeur | vendeur@test.ci | 123456 |
| ⚙️ Admin | admin@rabbitmarket.ci | 123456 |

---

## 🧪 Tester l'API

```bash
# Santé du serveur
curl http://localhost:5000/api/health

# Liste des produits
curl http://localhost:5000/api/products

# Connexion
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"acheteur@test.ci","password":"123456"}'

# Valider un code promo
curl -X POST http://localhost:5000/api/promo/validate \
  -H "Content-Type: application/json" \
  -d '{"code":"RABBIT10","orderTotal":15000}'

# Calculer la livraison
curl -X POST http://localhost:5000/api/delivery/partners \
  -H "Content-Type: application/json" \
  -d '{"city":"Abidjan","items":[{"productId":"xxx","qty":2}]}'
```

---

## 🤝 Contribuer

Rabbit Market est un projet **open source** et nous cherchons activement des collaborateurs motivés ! 🙌

### 👥 Profils recherchés

| Profil | Missions |
|--------|----------|
| 📱 **Dev React Native** | Améliorer les écrans, ajouter des fonctionnalités |
| 🔧 **Dev Backend Node.js** | Optimiser les APIs, intégrations paiement |
| 🐘 **Dev PostgreSQL/Prisma** | Optimisation des requêtes, migrations |
| 🎨 **UI/UX Designer** | Améliorer l'expérience utilisateur |
| 🧪 **QA Tester** | Tests sur Android/iOS, rapports de bugs |
| 📊 **Data / Analytics** | Dashboard admin, statistiques vendeurs |
| 🔌 **Intégration API** | Yango, Glovo, Wave, MTN MoMo, Orange Money |
| 📝 **Technical Writer** | Documentation, guides d'utilisation |

### 🛠️ Comment contribuer

1. **Fork** le projet
```bash
git fork https://github.com/[USERNAME]/rabbit-market
```

2. **Crée une branche** pour ta fonctionnalité
```bash
git checkout -b feature/nom-de-ta-feature
```

3. **Développe** ta fonctionnalité

4. **Commit** tes changements
```bash
git commit -m "feat: description de ta fonctionnalité"
```

5. **Push** sur ta branche
```bash
git push origin feature/nom-de-ta-feature
```

6. **Ouvre une Pull Request** en décrivant tes changements

### 📋 Convention de commits

```
feat:     Nouvelle fonctionnalité
fix:      Correction de bug
style:    Changement de style/design
refactor: Refactoring du code
docs:     Documentation
test:     Tests
chore:    Maintenance
```

### 🐛 Signaler un bug

Ouvre une **Issue** sur GitHub avec :
- Description claire du bug
- Étapes pour reproduire
- Comportement attendu vs observé
- Captures d'écran si possible
- Appareil et version OS

---

## 🗺️ Roadmap

### ✅ Version 1.0 (En cours)
- [x] Design system & navigation
- [x] Authentification complète (OTP, JWT)
- [x] Catalogue produits
- [x] Panier & commandes
- [x] Espace vendeur
- [x] Espace admin
- [x] Backend PostgreSQL + Prisma
- [x] Livraison avec choix du livreur

### 🔄 Version 1.1 (Prochainement)
- [ ] Intégration Wave API réelle
- [ ] Intégration MTN MoMo API réelle
- [ ] Intégration Orange Money API réelle
- [ ] Intégration Yango Delivery API
- [ ] Notifications push (Expo Notifications)
- [ ] Chat acheteur ↔ vendeur
- [ ] Système de parrainage

### 🔮 Version 2.0 (Futur)
- [ ] Version web (React)
- [ ] Application vendeur dédiée
- [ ] Expansion en Afrique de l'Ouest
- [ ] IA pour recommandations produits
- [ ] Système de enchères pour animaux rares
- [ ] Vétérinaire en ligne (téléconsultation)

---

## 📊 État du projet

| Module | Statut |
|--------|--------|
| Design System | ✅ Terminé |
| Authentification | ✅ Terminé |
| Catalogue Acheteur | ✅ Terminé |
| Panier & Commandes | ✅ Terminé |
| Espace Vendeur | ✅ Terminé |
| Espace Admin | ✅ Terminé |
| Backend API | ✅ Terminé |
| PostgreSQL/Prisma | ✅ Terminé |
| Livraison dynamique | ✅ Terminé |
| Vente carcasse | ✅ Terminé |
| Paiement Wave | 🔄 Mock — intégration réelle à venir |
| Paiement MTN MoMo | 🔄 Mock — intégration réelle à venir |
| Paiement Orange Money | 🔄 Mock — intégration réelle à venir |
| Notifications push | ⏳ Planifié v1.1 |
| Chat | ⏳ Planifié v1.1 |

---

## 📬 Contact & Communauté

Tu veux rejoindre l'équipe ou tu as des questions ?

- 📧 **Email :** rabbitmarket.ci@gmail.com
- 💬 **WhatsApp :** +225 XX XX XX XX XX
- 🐙 **GitHub :** [github.com/rabbit-market-ci](https://github.com)
- 📸 **Instagram :** [@rabbitmarket.ci](https://instagram.com)

---

## 📄 Licence

Ce projet est sous licence **MIT** — libre d'utilisation, modification et distribution.

---

<div align="center">

**Fait avec ❤️ en Côte d'Ivoire 🇨🇮**

*Rabbit Market — Élevage & Marketplace*

⭐ **Si ce projet vous plaît, laissez une étoile sur GitHub !** ⭐

</div>
