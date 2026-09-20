# 🔧 Tuto Firebase — Activer le Multiplayer

Suis ce guide pour transformer l'arcade en vrai jeu multiplayer en ligne avec synchronisation en temps réel ! ⚡

## Étape 1️⃣ : Créer un projet Firebase

### Sur https://console.firebase.google.com

1. **Clique sur "Ajouter un projet"** (ou "Create a project")
2. Entre un nom : `arcade-des-potes`
3. Coche "✓ I accept the controller-controller data processing terms"
4. **Clique "Créer le projet"**
5. Attends 30 sec... puis clique **"Continuer"**

![Step 1](https://i.imgur.com/placeholder1.png)

---

## Étape 2️⃣ : Ajouter une Realtime Database

Dans la barre latérale gauche :

1. Va à **Build** → **Realtime Database**
2. Clique **"Créer une base de données"**
3. Choisis la région la plus proche (ex: `europe-west1` pour la France)
4. **Mode de sécurité : `Test mode`** (on peut changer après)
   ```
   ✓ Test mode
   Accessible en lecture/écriture par tous
   (Parfait pour dev)
   ```
5. Clique **"Activer"**

💾 **Tu vas voir une URL comme :** `https://arcade-des-potes.firebaseio.com`
*(note-la, tu en auras besoin)*

![Step 2](https://i.imgur.com/placeholder2.png)

---

## Étape 3️⃣ : Récupérer tes credentials Firebase

Dans la barre latérale : **Project Settings** (⚙️ en bas à gauche)

### Onglet "General"

1. Scroll vers le bas jusqu'à **"Vos applications"**
2. Clique sur **"</>"** (Web)
3. Donne un nom : `arcade-web`
4. Clique **"Enregistrer l'application"**

### La page affichera ton code :

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyD1234567890...",
  authDomain: "arcade-des-potes.firebaseapp.com",
  projectId: "arcade-des-potes",
  storageBucket: "arcade-des-potes.appspot.com",
  messagingSenderId: "1234567890",
  appId: "1:1234567890:web:abcd1234efgh5678"
};
```

**📋 Copie TOUT ce code.**

![Step 3](https://i.imgur.com/placeholder3.png)

---

## Étape 4️⃣ : Ajouter le fichier `firebase-config.js`

Va sur ton repo GitHub : **https://github.com/XyoTToyX/arcade-des-potes**

### Crée un nouveau fichier :

1. Clique **"Add file"** → **"Create new file"**
2. Nom du fichier : **`firebase-config.js`**
3. Colle ce code (remplace par tes vraies credentials) :

```javascript
// firebase-config.js
// ⚠️ NE partage PAS ce fichier publiquement (il est dans .gitignore)

export const firebaseConfig = {
  apiKey: "AIzaSyD1234567890...",
  authDomain: "arcade-des-potes.firebaseapp.com",
  projectId: "arcade-des-potes",
  storageBucket: "arcade-des-potes.appspot.com",
  messagingSenderId: "1234567890",
  appId: "1:1234567890:web:abcd1234efgh5678"
};
```

4. **Commit** avec le message : `Configure Firebase credentials`

✅ **Le fichier est en `.gitignore` donc tes secrets sont sûrs !**

![Step 4](https://i.imgur.com/placeholder4.png)

---

## Étape 5️⃣ : Tester le Multiplayer 🎮

### Ouvre 2 onglets du lien public :

```
https://xyottoyx.github.io/arcade-des-potes
```

**Onglet 1 :**
- Pseudo : "Alice"
- Crée une salle : `Eddy Boum`
- Note le **code de salle** (ex: `AB12CD`)

**Onglet 2 :**
- Pseudo : "Bob"  
- Rejoins : colle le code `AB12CD`
- Clique **"Rejoindre"**

✨ **C'est fait !** Vous êtes dans la même salle, synchronisé en temps réel !

---

## Sécurité : Mettre à jour les règles Firebase

Quand tu es prêt pour la **vraie vie** (pas juste test) :

### Dans Firebase Console

1. Va à **Realtime Database** → **Règles**
2. Remplace par :

```json
{
  "rules": {
    "lobbies": {
      ".read": true,
      ".write": true,
      "$roomId": {
        ".validate": "newData.hasChildren(['code', 'players', 'game'])"
      }
    },
    "games": {
      ".read": true,
      ".write": true,
      "$gameId": {
        ".validate": "newData.hasChildren(['state', 'players'])"
      }
    }
  }
}
```

3. **Publie** les règles

---

## 🆘 Troubleshooting

### "Impossible de se connecter"
- Vérifie que `firebase-config.js` est à la racine du repo
- Redéploie GitHub Pages (attend 1-2 min)
- Vérifie que **Realtime Database** est activée

### "Pas de synchronisation entre joueurs"
- Ouvre la **console** (F12 → Console)
- Cherche une erreur Firebase
- Vérifie les **règles de Firebase** (Realtime Database → Règles)

### "Les données ne persistent pas"
- C'est normal pour le mode test
- Change le **règles Firebase** (voir ci-dessus)

---

## 📊 Bonus : Voir tes données en direct

Dans **Firebase Console** → **Realtime Database** → **Data** :

Tu verras en temps réel :
- Qui joue
- Quelles salles existent
- L'état de chaque partie

C'est magique pour déboguer ! ✨

---

## 🚀 T'es prêt !

Voilà, t'as un **vrai jeu multiplayer en ligne** 100% gratuit, auto-hébergé sur GitHub Pages + Firebase !

**Next steps optionnels :**
- Ajouter une base de données pour tracker les scores
- Ajouter des achievements 🏆
- Faire un leaderboard 📊

Des questions ? Relis l'étape où tu as bloqué ou demande ! 💬
