[AP_v3_README.md](https://github.com/user-attachments/files/27324158/AP_v3_README.md)
# 📦 AlternancePilot v3 — Dossier complet

Bienvenue ! Ce dossier contient tout ce qu'il vous faut pour mettre en place une **base de test multi-utilisateurs** d'AlternancePilot, connectée à un Google Sheet partagé.

---

## 📁 Contenu du dossier

| Fichier | À quoi ça sert | Quand l'utiliser |
|---|---|---|
| **GUIDE_INSTALLATION.md** | Guide pas-à-pas en 4 étapes | **Commencez par celui-ci** |
| **script_google_apps.gs** | Code à coller dans Google Sheets | Étape 2 du guide |
| **AlternancePilot_v3.html** | L'application elle-même | Étape 4 du guide |
| **comptes_initiaux.md** | Vos 10 identifiants pré-créés | Pour distribuer les accès |
| **README.md** | Ce fichier | Vue d'ensemble |

---

## 🎯 Ce que ça apporte par rapport à la v2

| Fonctionnalité | v2 (HTML local) | v3 (Sheet partagé) |
|---|---|---|
| Stockage des suivis | Navigateur local | Google Sheet partagé |
| Multi-utilisateurs | ❌ Chacun ses données | ✅ Tout le monde voit la même chose |
| Identification | ❌ Anonyme | ✅ Login + mot de passe |
| Audit (qui fait quoi) | ❌ Rien | ✅ Journal complet |
| Sauvegarde | Manuelle (export JSON) | Automatique (Google) |
| Accès depuis plusieurs PC | ❌ | ✅ |
| Coût | Gratuit | Gratuit |
| Temps d'installation | 0 min | 15-20 min |

---

## ⚙️ Démarrage rapide

**Si vous voulez juste tester :**
1. Ouvrez `GUIDE_INSTALLATION.md`
2. Suivez les 4 étapes (15-20 minutes)
3. Connectez-vous avec `admin` / `Test2026!`

**Si vous voulez d'abord visualiser :**
- Ouvrez la v2 (`AlternancePilot_v2.html`) dans votre navigateur — l'interface est identique à 95%, seul change l'écran de connexion en plus.

---

## 🆘 Besoin d'aide ?

Toutes les sections de dépannage sont dans `GUIDE_INSTALLATION.md`.

Pour les questions techniques : revenez vers moi avec l'erreur exacte que vous voyez à l'écran.

---

## 🚀 Prochaines évolutions possibles (V4)

Quand cette base test aura fait ses preuves auprès de votre équipe, voici ce qu'on pourra ajouter :

- **Synchronisation temps réel** : voir les modifications des collègues sans recharger la page
- **Notifications** : alerte email quand une offre devient urgente
- **Module candidats** : matching automatique candidats ↔ offres
- **Import drag-and-drop** d'un nouveau fichier Hub3e (pour rafraîchir les 471 offres)
- **Export Excel** par campus / gestionnaire / période
- **Migration vers Kreativmedia** quand le besoin sera validé

---

## 📊 Limites de cette version test

- **20 000 appels API/jour** (limite Google Apps Script — large pour 10 utilisateurs)
- **Pas de synchronisation push** — chaque utilisateur voit l'état au moment de son chargement, il faut recharger pour voir les modifs des autres
- **Pas de récupération de mot de passe** par utilisateur — l'admin doit le réinitialiser
- **Sécurité raisonnable** mais pas niveau bancaire — adapté à un usage interne

Pour une version pro, prévoir le déploiement Kreativmedia avec PHP + MySQL.

---

*Bon lancement avec votre équipe ! N'hésitez pas à me faire un retour après quelques jours d'utilisation pour ajuster.*
