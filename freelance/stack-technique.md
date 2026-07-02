# Stack technique — Bureau (Axel)
# Principe : outils qui font 90%, toi tu fais 10%
# Dernière mise à jour : juin 2026 (audit effectué)

---

## Règle d'or
Si PocketBase peut le faire → PocketBase.
Si shadcn-svelte a le composant → shadcn-svelte.
Tu codes uniquement ce qui n'existe pas encore.

---

## Le socle (sur chaque projet)

| Rôle | Outil | Ce qu'il fait sans toi |
|---|---|---|
| Backend + Auth + DB + Admin | PocketBase | API REST, auth, dashboard admin, fichiers, realtime |
| CMS client non-tech | Payload CMS | Admin UI accessible, permissions granulaires, TypeScript |
| UI Components | shadcn-svelte | Boutons, formulaires, tableaux, modals — déjà beaux |
| Frontend / Full-stack | SvelteKit | Routing, SSR, SEO, API routes, moins de CVEs |
| Paiement | Stripe | Checkout, factures, abonnements, webhooks |
| Email | Resend | Emails transactionnels en 5 lignes |
| Hébergement | VPS OVH + Dokploy | Déploiement Git, SSL auto, logs |

Toi tu ajoutes : logique métier spécifique, intégrations manquantes, automatisations custom en Golang.

---

## Arbre de décision

```
Nouveau projet client
│
├── Site vitrine / portfolio
│   └── Astro + CSS vanilla → déployé en 1 jour
│
├── Site avec contenu géré par le client
│   └── Payload CMS + SvelteKit → 2-4 jours
│
├── App avec utilisateurs + données
│   └── PocketBase + SvelteKit + shadcn-svelte → 3-5 jours
│
├── Logique métier complexe
│   └── Golang + PocketBase + SvelteKit → 1-3 semaines
│
├── E-commerce standard
│   └── WooCommerce + Stripe → 2-3 jours, zéro code
│
└── E-commerce sur mesure
    └── Medusa.js + Stripe + Golang → 3-6 semaines
```

---

## Ce que tu n'installes JAMAIS from scratch

| Besoin | Tu prends | Tu n'inventes pas |
|---|---|---|
| Auth (login, JWT, OAuth) | PocketBase auth | Système auth maison |
| UI | shadcn-svelte | Tes propres composants CSS |
| Paiement | Stripe | Intégration bancaire custom |
| Email | Resend | Serveur SMTP |
| Upload fichiers | PocketBase storage | S3 custom |
| Admin panel (devs) | PocketBase dashboard | Dashboard from scratch |
| Admin panel (non-tech) | Payload CMS | Interface admin custom |
| E-commerce standard | WooCommerce | Shop from scratch |

---

## Temps de livraison réaliste

| Projet | Stack | Délai |
|---|---|---|
| Site vitrine | Astro | 1 jour |
| Landing page + formulaire | Astro + Resend | 1 jour |
| Site avec blog / contenu | Payload CMS + SvelteKit | 2-4 jours |
| App gestion simple | PocketBase + SvelteKit + shadcn-svelte | 3-5 jours |
| App métier sur mesure | Golang + PocketBase + SvelteKit | 2-4 semaines |
| Boutique standard | WooCommerce + Stripe | 2-3 jours |
| Boutique sur mesure | Medusa.js + Stripe + Golang | 3-6 semaines |

---

## Stack par techno — détail

### Backend
- **Golang** — logique métier custom, APIs complexes, performance
- **PocketBase** — BaaS 1 binaire : auth + DB SQLite + API + admin + storage
- **PostgreSQL** — si plusieurs services partagent la DB ou rapports complexes
  - Lib Go : `pgx`
  - Routing Go : `chi` ou `gin`

### CMS
- **Payload CMS** — remplace Strapi. TypeScript natif, permissions gratuites, admin UI non-tech, schéma en code versionné dans Git
  - Doc : payloadcms.com/docs
  - Quand l'utiliser : client doit gérer du contenu (blog, catalogue, actualités)
  - Avantage vs Strapi : permissions avancées gratuites, TypeScript first

### Frontend
- **SvelteKit** — SSR, routing, API routes, SEO natif, moins de CVEs que Next.js
  - Utilisé en prod par NYT, Apple, Spotify
- **shadcn-svelte** — composants UI prêts, accessibles, copiés-collés
  - shadcn-svelte.com — migration Svelte 5 complète
- **HTMX** — si tu restes 100% Golang sans framework JS
- **Turbo + Stimulus (Hotwire)** — alternative HTMX, même philosophie
- **Astro** — sites statiques, portfolios, vitrines

### E-commerce
- **WooCommerce** — boutique standard PME, zéro code, 2-3 jours
- **Medusa.js** — e-commerce sur mesure, API-first, connecte à Golang
- **Stripe** — paiement sur tous les projets

### IA (déjà utilisé)
- **Gemini API** — génération texte + images (ai.google.dev/gemini-api/docs)
- **DeepSeek** — génération texte, compatible API OpenAI
- **Tavily** — recherche web pour l'IA (docs.tavily.com)

### Infra
- **VPS OVH VPS-2** — 4 vCores, 8 Go RAM, 75 Go SSD, déjà en place
- **Dokploy** — déploiement Git, SSL auto, reverse proxy Traefik
- **Docker** — 1 container par projet, docker-compose
- **Resend** — emails transac (port 25 bloqué sur OVH)

---

## Tes projets perso — stack de référence

### roadmaps.cc
Plateforme d'apprentissage IA — parcours personnalisés, quiz, flashcards
- Golang · SQLite · HTMX · DeepSeek · Tavily · Gemini API · Google OAuth · Dokploy

### howifeel.today
Journal émotionnel Year in Pixels
- Golang · SQLite · Turbo (Hotwire) · Stimulus · Dokploy

---

## Documentation à lire — par priorité

### Priorité 1 (débloque 80% des projets)
- PocketBase : pocketbase.io/docs
- SvelteKit : kit.svelte.dev/docs
- shadcn-svelte : shadcn-svelte.com
- Stripe : stripe.com/docs → Payments, Webhooks, Checkout

### Priorité 2 (projets contenu + e-commerce)
- Payload CMS : payloadcms.com/docs
- WooCommerce : developer.woocommerce.com
- Medusa.js : docs.medusajs.com

### Priorité 3 (projets IA)
- Gemini API : ai.google.dev/gemini-api/docs
- DeepSeek : platform.deepseek.com/api-docs
- Tavily : docs.tavily.com

### Référence permanente
- Golang : go.dev/doc
- Astro : docs.astro.build
- Dokploy : dokploy.com/docs
- Docker : docs.docker.com
