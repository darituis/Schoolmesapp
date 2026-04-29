# 📱 Schoolmes — Projet App Mobile (Capacitor)

App Android & iOS générée avec **Capacitor 6**.

---

## 📁 Structure du projet

```
schoolmes-app/
├── www/                  ← Ton app web (index.html + assets)
├── capacitor.config.json ← Config Capacitor
├── package.json          ← Dépendances npm
├── android/              ← Projet Android (Android Studio)
│   ├── app/
│   │   ├── src/main/
│   │   │   ├── AndroidManifest.xml
│   │   │   ├── java/com/schoolmes/app/MainActivity.java
│   │   │   └── res/  ← Icônes, styles, couleurs
│   └── build.gradle
└── ios/
    └── App/
        ├── App/          ← Code Swift + assets
        ├── Podfile       ← Dépendances CocoaPods
        └── App.xcodeproj/
```

---

## 🚀 Installation rapide

### 1. Prérequis

| Outil | Version |
|-------|---------|
| Node.js | 18+ |
| npm | 9+ |
| Android Studio | Hedgehog+ |
| Xcode | 15+ (Mac seulement) |
| CocoaPods | 1.13+ (Mac seulement) |
| JDK | 17+ |

### 2. Installer les dépendances

```bash
cd schoolmes-app
npm install
```

---

## 🤖 Android

### Builder l'APK

```bash
# 1. Synchroniser les fichiers web → Android
npx cap sync android

# 2. Ouvrir dans Android Studio
npx cap open android
```

Dans Android Studio :
- **Build → Generate Signed Bundle/APK**
- Choisis **APK** (ou AAB pour le Play Store)
- Crée une keystore si tu n'en as pas
- `Build → Build APK(s)` pour un APK de test

### APK de debug rapide (sans signing)

```bash
cd android
./gradlew assembleDebug
# APK généré : android/app/build/outputs/apk/debug/app-debug.apk
```

---

## 🍎 iOS (Mac uniquement)

### Builder l'IPA

```bash
# 1. Installer les pods
cd ios/App && pod install && cd ../..

# 2. Synchroniser les fichiers web → iOS
npx cap sync ios

# 3. Ouvrir dans Xcode
npx cap open ios
```

Dans Xcode :
- Sélectionne ton équipe de développement (Apple Developer Account)
- **Product → Archive**
- **Distribute App → App Store Connect** ou **Ad Hoc**

---

## ⚙️ Configuration

### Changer l'ID de l'app

Dans `capacitor.config.json` :
```json
{
  "appId": "com.TONNOM.schoolmes",
  "appName": "Schoolmes"
}
```

Puis dans `android/app/build.gradle` :
```
applicationId "com.TONNOM.schoolmes"
```

Et dans `ios/App/App.xcodeproj` → Target → Bundle Identifier.

### Mettre à jour le contenu web

Modifie les fichiers dans `www/` puis relance :
```bash
npx cap sync
```

---

## 🔥 Firebase

Firebase est configuré directement dans `www/index.html`.  
Aucune modification nécessaire pour les builds Android/iOS — Firebase web SDK fonctionne dans la WebView.

---

## 📦 Publier sur les stores

### Google Play Store
- Génère un AAB signé (`Build → Generate Signed Bundle`)
- Crée une app sur [play.google.com/console](https://play.google.com/console)

### Apple App Store
- Archive depuis Xcode → Distribute → App Store Connect
- Crée une app sur [appstoreconnect.apple.com](https://appstoreconnect.apple.com)

---

## 🛠️ Commandes utiles

```bash
npm run sync:android   # Sync web → Android
npm run sync:ios       # Sync web → iOS
npm run open:android   # Ouvrir Android Studio
npm run open:ios       # Ouvrir Xcode
npm run run:android    # Lancer sur device/emulateur Android
npm run run:ios        # Lancer sur simulateur iOS
```

---

*Généré automatiquement — Schoolmes v1.0.0*
