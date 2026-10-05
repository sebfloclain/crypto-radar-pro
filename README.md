# Crypto Radar PRO

Application web progressive (PWA) d'analyse technique multi-timeframe pour **Bitcoin (BTC/USDT)** et **Solana (SOL/USDT)**.

## Fonctionnalités

- Analyse multi-timeframe : 15m, 1h, 4h, 1j
- Indicateurs : SMA 20/50/200, EMA 20/50, RSI 14, MACD, ATR, Bollinger, volume, structure
- Score global 0-100 avec composantes transparentes
- Confiance basée sur l'alignement des timeframes + confirmations croisées
- Détection de faux signaux (filtres RSI vs SMA200 / MACD)
- Signaux : 🔵 ACHAT / ⚪ ATTENDRE / 🔴 VENTE
- Horizons : Court terme / Swing / Tendance
- Niveau de risque (Faible / Modéré / Élevé)
- Graphiques interactifs (bougies + EMA20 / EMA50 / SMA200)
- Zones techniques indicatives (entrée, support, résistance, stop, objectifs)
- Alertes basées sur de vrais changements
- Explications en français (« Pourquoi ? »)
- Mode hors-ligne de l'interface (PWA)
- Données 100 % réelles via API publique Binance

## Arborescence

```
crypto-radar-pro/
├── index.html          # Application complète (HTML + CSS + JS)
├── manifest.json       # Manifeste PWA
├── sw.js               # Service Worker
├── icons/
│   ├── icon-192.png
│   └── icon-512.png
└── README.md
```

## Source de données

- **API** : `https://data-api.binance.vision/api/v3` (miroir public Binance, aucune clé API)
- Endpoints utilisés :
  - `/ticker/24hr` (prix + variation 24h)
  - `/klines` (bougies OHLCV)
- CORS activé (`Access-Control-Allow-Origin: *`)
- Limites : weight system Binance (~1200/min/IP). L'app fait ~10 requêtes toutes les 45 s → largement sous les limites.

Aucune donnée simulée. En cas d'échec réseau → message « Données indisponibles ».

## Installation & Hébergement (recommandé)

Une page ouverte en `file://` ne permet **pas** une vraie installation PWA sur Android.

### Option la plus simple : GitHub Pages (gratuit)

1. Créez un compte GitHub (si besoin).
2. Créez un nouveau dépôt public, ex. `crypto-radar-pro`.
3. Uploadez **tous** les fichiers du dossier (index.html, manifest.json, sw.js, dossier icons/).
4. Allez dans **Settings → Pages**.
5. Source : branch `main` (ou `master`), dossier `/ (root)`.
6. Attendez 1-2 minutes. L'URL sera :
   `https://VOTRE_USERNAME.github.io/crypto-radar-pro/`

### Alternatives gratuites

- **Netlify** : drag & drop du dossier sur netlify.com → URL instantanée.
- **Cloudflare Pages** : connectez le repo GitHub.
- **Vercel** : idem.

## Ajouter à l'écran d'accueil (Samsung / Android Chrome)

1. Ouvrez l'URL de l'application dans **Chrome** (pas Samsung Internet de préférence pour le meilleur support PWA).
2. Appuyez sur le menu ⋮ (trois points).
3. Choisissez **« Installer l'application »** ou **« Ajouter à l'écran d'accueil »**.
4. Confirmez. L'icône « Crypto Radar PRO » apparaît sur l'écran d'accueil.
5. Elle s'ouvre en mode standalone (sans barre d'adresse).

## Utilisation locale (développement)

```bash
# Depuis le dossier du projet
npx serve .
# ou
python3 -m http.server 8080
```

Puis ouvrez `http://localhost:8080` dans le navigateur.

## Avertissement

Crypto Radar PRO est un **outil d'analyse algorithmique expérimental**.  
Les marchés crypto sont extrêmement volatils. Aucun signal ne garantit une hausse ou une baisse.  
Ceci **ne constitue pas un conseil financier**.

## Licence

Code fourni à des fins éducatives et personnelles. Utilisez à vos propres risques.
