# 🎮 Arcade des Potes

Salle de jeux arcade en ligne — **Eddy Boum**, Morpion, Puissance 4, Air hockey, Uno, Yams, Qui est-ce ?, Bataille navale, Poker.

**Lien public** : https://xyottoyx.github.io/arcade-des-potes

## Jouer

1. Ouvre le lien ci-dessus
2. Entre ton pseudo
3. Crée une salle ou rejoins-en une
4. Partage le code de salle avec tes potes 🎉

## Jeux disponibles

| Jeu | Joueurs | Type |
|-----|---------|------|
| **Eddy Boum** 💣 | 2-5 | Cartes explosives |
| **Morpion** ⭕ | 2 | Trois de suite |
| **Puissance 4** 🔴 | 2 | Aligne 4 jetons |
| **Air Hockey** 🏒 | 2 | Premier à 7 buts |
| **Uno** 🎴 | 2-6 | Pose tes cartes |
| **Yams** 🎲 | 1-4 | 5 dés, 13 figures |
| **Qui est-ce ?** 🕵️ | 2 | Devine le visage |
| **Bataille navale** 🚢 | 2 | Coule la flotte |
| **Poker** 🃏 | 2-6 | Texas Hold'em |

## Configuration

### Multiplayer (Firebase)

L'app est prête pour **Firebase Realtime Database**. Pour activer le multiplayer en ligne :

1. Crée un projet Firebase (gratuit) : https://console.firebase.google.com
2. Ajoute une Realtime Database (mode `test` pour dev)
3. Crée un fichier `firebase-config.js` à la racine :

```javascript
// firebase-config.js
export const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

4. L'app charge automatiquement cette config

Sinon, les jeux fonctionnent en **mode local** (chacun sur sa machine).

## Développement

```bash
# Cloner
git clone https://github.com/XyoTToyX/arcade-des-potes
cd arcade-des-potes

# Servir localement
python3 -m http.server 8000
# Puis va sur http://localhost:8000
```

## Deploy

Le repo utilise **GitHub Pages** automatiquement :
- Branche `main` → publiée sur `https://xyottoyx.github.io/arcade-des-potes`
- C'est gratuit et en direct ✨

## Partager le lien

Copie simplement : **https://xyottoyx.github.io/arcade-des-potes**

N'importe qui peut y jouer, c'est public et sans inscription.

---

Made with ❤️ & JavaScript vanilla
