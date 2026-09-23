# 📘 GUIDE COMPLET : Git, GitHub et Jira

# 📗 الدليل الكامل : Git و GitHub و Jira

> Guide bilingue Français / العربية — دليل ثنائي اللغة

---

# PARTIE 1 : GIT — جيت

## 1.1 Définition / التعريف

### 🇫🇷 Français

**Git** est un **système de gestion de versions (VCS)** créé par Linus Torvalds en 2005.
C'est un outil qui enregistre l'historique de toutes les modifications de vos fichiers (code source), ce qui permet de :

- Revenir à n'importe quelle version antérieure du projet.
- Travailler à plusieurs sans écraser le travail des autres.
- Travailler hors ligne (Git est local, installé sur votre machine).

### 🇸🇦 العربية

**Git** هو **نظام لإدارة النسخ والإصدارات (VCS)** أنشأه لينوس تورفالدس سنة 2005.
هو أداة تسجّل تاريخ جميع التعديلات على ملفاتك (الشيفرة المصدرية)، مما يتيح لك:

- العودة إلى أي نسخة سابقة من المشروع.
- العمل جماعياً دون أن تمسح عمل الآخرين.
- العمل دون اتصال بالأنترنت (Git محلي، مثبّت على جهازك).

### 🎯 Rôle de Git / دور Git

| FR                                             | AR                         |
| ---------------------------------------------- | -------------------------- |
| Suivre l'historique des fichiers               | تتبّع تاريخ الملفات        |
| Gérer les branches (versions parallèles)       | إدارة الفروع (نسخ متوازية) |
| Fusionner le travail de plusieurs développeurs | دمج عمل عدة مطوّرين        |
| Annuler les erreurs                            | التراجع عن الأخطاء         |

---

## 1.2 Installation de Git / تثبيت Git

### 🪟 Windows

1. Télécharger depuis : https://git-scm.com/download/win
2. Lancer `Git-xxx.exe`.
3. Cliquer **Next** à chaque étape (options par défaut recommandées pour un débutant).
4. À l'étape "Choosing the default editor", choisir **Visual Studio Code** si vous l'avez.
5. Terminer, puis vérifier l'installation.

### 🐧 Linux (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install git -y
```

### 🍎 macOS

```bash
brew install git
```

### ✅ Vérification / التحقق

```bash
git --version
# Exemple de résultat : git version 2.45.0
```

### ⚙️ Configuration initiale (obligatoire la 1ère fois) / الإعداد الأولي (إلزامي في المرة الأولى)

```bash
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@example.com"
git config --global core.editor "code --wait"   # éditeur VS Code
git config --list                                # voir toute la config / رؤية كل الإعدادات
```

---

## 1.3 Toutes les commandes Git avec leur rôle / كل أوامر Git مع دورها

### A) Configuration / الإعدادات

| Commande                                | Rôle (FR)                  | الدور (AR)             |
| --------------------------------------- | -------------------------- | ---------------------- |
| `git config --global user.name "Nom"`   | Définir votre nom          | تحديد اسمك             |
| `git config --global user.email "mail"` | Définir votre email        | تحديد بريدك الإلكتروني |
| `git config --list`                     | Afficher la configuration  | عرض الإعدادات          |
| `git config --global alias.st status`   | Créer un alias (raccourci) | إنشاء اختصار لأمر      |

### B) Création de dépôt / إنشاء المستودع

| Commande                     | Rôle (FR)                             | الدور (AR)                |
| ---------------------------- | ------------------------------------- | ------------------------- |
| `git init`                   | Transformer un dossier en dépôt Git   | تحويل مجلد إلى مستودع Git |
| `git clone <URL>`            | Copier un dépôt distant vers votre PC | نسخ مستودع بعيد إلى جهازك |
| `git clone -b branche <URL>` | Cloner une branche spécifique         | استنساخ فرع معيّن         |

### C) Suivi des fichiers / تتبّع الملفات

| Commande                | Rôle (FR)                                     | الدور (AR)             |
| ----------------------- | --------------------------------------------- | ---------------------- |
| `git status`            | Voir l'état des fichiers (modifiés, ajoutés…) | رؤية حالة الملفات      |
| `git add fichier.txt`   | Préparer UN fichier (zone de staging)         | تحضير ملف واحد         |
| `git add .`             | Préparer TOUS les fichiers                    | تحضير كل الملفات       |
| `git rm fichier.txt`    | Supprimer un fichier du dépôt                 | حذف ملف من المستودع    |
| `git mv ancien nouveau` | Renommer/déplacer un fichier                  | إعادة تسمية أو نقل ملف |

### D) Commits / الحفظ (كومِت)

| Commande                    | Rôle (FR)                                   | الدور (AR)                        |
| --------------------------- | ------------------------------------------- | --------------------------------- |
| `git commit -m "message"`   | Enregistrer un point de sauvegarde          | حفظ نقطة في التاريخ               |
| `git commit -am "message"`  | Ajouter + commiter les fichiers déjà suivis | إضافة وحفظ الملفات المتتبّعة معاً |
| `git commit --amend`        | Modifier le DERNIER commit                  | تعديل آخر كومِت                   |
| `git log`                   | Voir l'historique complet                   | عرض التاريخ الكامل                |
| `git log --oneline --graph` | Historique court et graphique               | تاريخ مختصر ورسومي                |
| `git show <id>`             | Détails d'un commit                         | تفاصيل كومِت معيّن                |
| `git diff`                  | Modifications non préparées                 | التعديلات غير المحضّرة            |
| `git diff --staged`         | Modifications préparées                     | التعديلات المحضّرة                |

### E) Branches / الفروع

| Commande                      | Rôle (FR)                             | الدور (AR)                     |
| ----------------------------- | ------------------------------------- | ------------------------------ |
| `git branch`                  | Lister les branches                   | عرض الفروع                     |
| `git branch nom-branche`      | Créer une branche                     | إنشاء فرع                      |
| `git checkout nom-branche`    | Changer de branche                    | الانتقال إلى فرع               |
| `git checkout -b nom-branche` | Créer + changer de branche            | إنشاء فرع والانتقال إليه       |
| `git switch nom-branche`      | (nouveau) changer de branche          | (أمر حديث) الانتقال إلى فرع    |
| `git switch -c nom-branche`   | (nouveau) créer + changer             | (أمر حديث) إنشاء فرع والانتقال |
| `git branch -d nom-branche`   | Supprimer une branche                 | حذف فرع                        |
| `git merge nom-branche`       | Fusionner une branche dans l'actuelle | دمج فرع في الفرع الحالي        |
| `git merge --abort`           | Annuler une fusion en conflit         | إلغاء دمج فيه تعارض            |

### F) Dépôt distant (GitHub…) / المستودع البعيد

| Commande                      | Rôle (FR)                             | الدور (AR)                   |
| ----------------------------- | ------------------------------------- | ---------------------------- |
| `git remote add origin <URL>` | Relier le projet local à GitHub       | ربط المشروع المحلي بـ GitHub |
| `git remote -v`               | Voir les dépôts distants              | عرض المستودعات البعيدة       |
| `git push -u origin main`     | Envoyer la 1ère fois (lien établi)    | الإرسال للمرة الأولى         |
| `git push`                    | Envoyer les commits                   | إرسال الكومِتات              |
| `git push origin branche`     | Envoyer une branche                   | إرسال فرع                    |
| `git pull`                    | Récupérer + fusionner les changements | جلب التغييرات ودمجها         |
| `git fetch`                   | Récupérer SANS fusionner              | جلب التغييرات دون دمج        |

### G) Annulation / التراجع (⚠️ à utiliser avec prudence)

| Commande                       | Rôle (FR)                                             | الدور (AR)                       |
| ------------------------------ | ----------------------------------------------------- | -------------------------------- |
| `git restore fichier`          | Annuler les modifications d'un fichier (avant commit) | إلغاء تعديلات ملف قبل الكومِت    |
| `git restore --staged fichier` | Retirer un fichier du staging                         | إخراج ملف من منطقة التحضير       |
| `git reset HEAD~1`             | Annuler le dernier commit (garde les fichiers)        | إلغاء آخر كومِت مع إبقاء الملفات |
| `git reset --hard <id>`        | Revenir à un commit et EFFACER tout après ⚠️          | العودة لكومِت ومسح ما بعده ⚠️    |
| `git revert <id>`              | Créer un commit qui annule un autre (sûr)             | إنشاء كومِت يلغي كومِت آخر (آمن) |
| `git stash`                    | Mettre les modifications "de côté"                    | تخزين التعديلات مؤقتاً           |
| `git stash pop`                | Récupérer ce qui est "de côté"                        | استرجاع التعديلات المخزّنة       |
| `git reflog`                   | Journal de tous les déplacements (sauvetage)          | سجل كل الحركات (للإنقاذ)         |

### H) Tags / الوسوم

| Commande               | Rôle (FR)              | الدور (AR)       |
| ---------------------- | ---------------------- | ---------------- |
| `git tag v1.0`         | Créer un tag (version) | إنشاء وسم (نسخة) |
| `git tag`              | Lister les tags        | عرض الوسوم       |
| `git push origin v1.0` | Envoyer un tag         | إرسال وسم        |

---

## 1.4 Workflow complet Git (pas à pas) / سير العمل الكامل خطوة بخطوة

### Exemple pratique / مثال عملي

```bash
# 1) Créer un dossier / إنشاء مجلد
mkdir mon-projet
cd mon-projet

# 2) Initialiser Git / تهيئة Git
git init

# 3) Créer un fichier / إنشاء ملف
echo "Bonjour" > index.html

# 4) Vérifier l'état / التحقق من الحالة
git status                     # fichier en rouge = non suivi

# 5) Préparer / التحضير
git add .

# 6) Commiter / الحفظ
git commit -m "Premier commit: ajout index.html"

# 7) Créer une branche / إنشاء فرع
git switch -c feature/login

# 8) Travailler, puis / العمل ثم
git add . && git commit -m "Ajout page login"

# 9) Revenir sur main et fusionner / العودة إلى main والدمج
git switch main
git merge feature/login

# 10) Envoyer vers GitHub / الإرسال إلى GitHub
git push origin main
```

### 🔙 Comment revenir en arrière / كيفية الرجوع للخلف

| Situation                                  | Commande                                                            | الحالة                    |
| ------------------------------------------ | ------------------------------------------------------------------- | ------------------------- |
| J'ai modifié un fichier et je veux annuler | `git restore fichier`                                               | عدّلت ملفاً وأريد الإلغاء |
| J'ai fait `git add` par erreur             | `git restore --staged fichier`                                      | أضفت الملف بالخطأ         |
| Je veux annuler le dernier commit          | `git reset HEAD~1`                                                  | أريد إلغاء آخر كومِت      |
| Je veux revenir à un commit précis         | `git checkout <id>` (visite) ou `git reset --hard <id>` (définitif) | العودة لكومِت محدّد       |
| Je dois annuler un commit déjà poussé      | `git revert <id>`                                                   | إلغاء كومِت مُرسَل        |
| Je suis perdu(e)                           | `git reflog` puis `git reset --hard HEAD@{n}`                       | إذا ضعت، استعمل reflog    |

---

# PARTIE 2 : GITHUB — غيت هاب

## 2.1 Définition / التعريف

### 🇫🇷 Français

**GitHub** est une **plateforme web** (site internet, propriété de Microsoft) qui héberge vos dépôts Git **dans le cloud**. Git = l'outil local, GitHub = l'hébergement en ligne + collaboration.

### 🇸🇦 العربية

**GitHub** هو **منصة على الأنترنت** (مملوكة لشركة Microsoft) تستضيف مستودعات Git **في السحابة**. Git = أداة محلية، GitHub = استضافة سحابية + تعاون.

### 🎯 Rôle de GitHub / دور GitHub

- Héberger le code en ligne / استضافة الشيفرة أونلاين
- Partager et collaborer en équipe / المشاركة والعمل الجماعي
- Revue de code (Pull Requests) / مراجعة الشيفرة
- Documentation (README, Wiki) / التوثيق
- Héberger des sites gratuits (GitHub Pages) / استضافة مواقع مجانية
- Automatisation (GitHub Actions) / الأتمتة

## 2.2 Installation / Installation / ما نثبّته

- **Rien à installer obligatoirement** : GitHub fonctionne dans le navigateur (https://github.com).
- Recommandé / موصى به :
  - Un compte GitHub (gratuit) / حساب مجاني
  - **Git** installé localement (voir Partie 1)
  - **GitHub Desktop** (interface graphique, pour débutants) : https://desktop.github.com
  - **GitHub CLI** (optionnel) : `winget install GitHub.cli` — commande `gh`

## 2.3 Créer un compte et un dépôt / إنشاء حساب ومستودع

1. Aller sur https://github.com → **Sign up** (إنشاء حساب)
2. Vérifier l'email / تأكيد البريد الإلكتروني
3. Cliquer sur **+** (en haut à droite) → **New repository**
4. Remplir :
   - **Repository name** : `mon-projet` / اسم المستودع
   - **Description** (optionnelle)
   - **Public / Private** : public = visible par tous, privé = seulement vous / عام أم خاص
   - ✅ Cocher **Add a README file** (recommandé)
5. Cliquer **Create repository** / إنشاء المستودع

## 2.4 Connecter le projet local à GitHub / ربط المشروع المحلي بـ GitHub

```bash
cd mon-projet
git remote add origin https://github.com/VOTRE-NOM/mon-projet.git
git branch -M main
git push -u origin main
```

> 🔐 GitHub demande un **Personal Access Token (PAT)** à la place du mot de passe :
> Settings → Developer settings → Personal access tokens → Generate new token (classic) → cocher `repo` → copier le token et l'utiliser comme mot de passe.
> 🔐 يطلب GitHub **رمز وصول شخصي** بدل كلمة المرور.

## 2.5 Commandes GitHub CLI (gh) / أوامر GitHub CLI

| Commande                             | Rôle (FR)                          | الدور (AR)              |
| ------------------------------------ | ---------------------------------- | ----------------------- |
| `gh auth login`                      | Se connecter à GitHub              | تسجيل الدخول            |
| `gh repo create mon-projet --public` | Créer un dépôt depuis le terminal  | إنشاء مستودع من الطرفية |
| `gh repo clone nom/projet`           | Cloner                             | استنساخ                 |
| `gh pr create`                       | Créer une Pull Request             | إنشاء طلب دمج           |
| `gh pr list` / `gh pr checkout 5`    | Lister / tester une PR             | عرض / تجربة طلب دمج     |
| `gh issue create -t "Titre"`         | Créer une issue                    | إنشاء مشكلة (issue)     |
| `gh repo view --web`                 | Ouvrir le dépôt dans le navigateur | فتح المستودع في المتصفح |

## 2.6 Ce qu'on peut créer sur GitHub / ما يمكن إنشاؤه على GitHub

- 📦 **Dépôts (Repositories)** / مستودعات
- 🌿 **Branches** / فروع
- 🔀 **Pull Requests** (proposer une fusion) / طلبات دمج
- 🐞 **Issues** (signaler un bug, une idée) / مشاكل وأفكار
- 👥 **Organisations et équipes** / منظمات وفرق
- 🌐 **GitHub Pages** (site web gratuit) / موقع مجاني
- ⚙️ **GitHub Actions** (CI/CD, automatisation) / أتمتة
- 📋 **Wiki et README** / توثيق
- 🎣 **Webhooks** / خطافات ويب
- ⭐ Forks (copie du projet d'un autre) / نسخة من مشروع غيرك

## 2.7 Workflow GitHub classique (Pull Request) / سير العمل الكلاسيكي

```bash
# 1) Cloner / استنساخ
git clone https://github.com/equipe/projet.git
cd projet

# 2) Créer une branche pour la tâche / إنشاء فرع للمهمة
git switch -c feature/paiement

# 3) Travailler + commits / العمل والحفظ
git add . && git commit -m "Ajout module paiement"

# 4) Pousser la branche / إرسال الفرع
git push origin feature/paiement

# 5) Sur GitHub : bouton "Compare & pull request" → décrire → "Create pull request"
# في الموقع: اضغط على زر طلب الدمج

# 6) Revue de code par l'équipe, puis bouton vert "Merge pull request"
# مراجعة الفريق ثم الضغط على زر الدمج الأخضر

# 7) Mettre à jour votre copie locale / تحديث نسختك المحلية
git switch main && git pull
```

## 2.8 Erreurs courantes et solutions / أخطاء شائعة وحلولها

| Erreur                                  | Solution                                    | الحل                 |
| --------------------------------------- | ------------------------------------------- | -------------------- |
| `push rejected (non-fast-forward)`      | `git pull --rebase` puis `git push`         | سحب ثم إرسال         |
| `remote origin already exists`          | `git remote set-url origin <URL>`           | تغيير الرابط         |
| J'ai poussé vers la mauvaise branche    | `git push origin --delete mauvaise-branche` | حذف الفرع البعيد     |
| Mot de passe refusé                     | Utiliser un **PAT** (token)                 | استعمال الرمز الشخصي |
| Supprimer un dossier commité par erreur | `git rm -r --cached dossier/` puis commit   | إزالة مجلد من التتبع |

---

# PARTIE 3 : JIRA — جيرا

## 3.1 Définition / التعريف

### 🇫🇷 Français

**Jira** est un **outil de gestion de projets et de suivi du travail** édité par Atlassian. Très utilisé dans la méthode **Agile (Scrum/Kanban)** pour organiser les tâches, suivre les bugs et planifier les versions.

### 🇸🇦 العربية

**Jira** هو **أداة لإدارة المشاريع وتتبّع العمل** من شركة Atlassian. تُستعمل كثيراً في المنهجية **الأجايل (Scrum/Kanban)** لتنظيم المهام، تتبّع الأخطاء، والتخطيط للإصدارات.

### 🎯 Rôle de Jira / دور Jira

- Créer et assigner des tâches (tickets) / إنشاء المهام وتعيينها
- Tableau Kanban et Sprints Scrum / لوحة كانبان وسبرنتات
- Suivi des bugs / تتبّع الأخطاء
- Backlog (liste des besoins) / قائمة الاحتياجات
- Rapports et graphiques (burndown…) / تقارير ورسوم بيانية
- Lien avec Git/GitHub (brancher les commits aux tickets) / الربط مع Git وGitHub

## 3.2 Installation / ما نثبّته

- **Rien à installer** : Jira est un service web → https://www.atlassian.com/software/jira
- Créer un compte gratuit → **Get Jira Free**
- Optionnel : l'application mobile Jira.
- Pour les entreprises : **Jira Data Center** (installation sur serveur, payant) — non nécessaire pour débuter.

## 3.3 Créer un projet Jira / إنشاء مشروع

1. Se connecter → **Create project** (إنشاء مشروع)
2. Choisir un modèle : **Scrum** (sprints) ou **Kanban** (flux continu) / اختر النموذج
3. Nom : `Mon Projet` ; Clé : `MP` (les tickets s'appelleront MP-1, MP-2…) / الاسم والمفتاح
4. Créer → vous arrivez sur le **Backlog** ou le **Board**.

## 3.4 Types d'éléments qu'on peut créer / ما يمكن إنشاؤه في Jira

| Type                   | Description (FR)                               | (AR)                       |
| ---------------------- | ---------------------------------------------- | -------------------------- |
| **Epic**               | Grande fonctionnalité qui se divise en stories | قصة كبيرة تُقسّم إلى قصص   |
| **Story (User Story)** | Besoin exprimé du point de vue utilisateur     | حاجة من منظور المستخدم     |
| **Task**               | Tâche technique (sans utilisateur)             | مهمة تقنية                 |
| **Bug**                | Défaut à corriger                              | خطأ يجب إصلاحه             |
| **Sub-task**           | Sous-tâche d'un ticket                         | مهمة فرعية                 |
| **Sprint**             | Itération de 1 à 4 semaines                    | دورة عمل من 1 إلى 4 أسابيع |
| **Release / Version**  | Version livrée du logiciel                     | إصدار من البرنامج          |
| **Component**          | Composant du projet                            | مكوّن من المشروع           |

## 3.5 Rôles Scrum dans Jira / الأدوار في سكرم

| Rôle                                     | Rôle (FR)                                                                          | الدور (AR)                                           |
| ---------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **Product Owner (PO)**                   | Définit QUOI faire, écrit les User Stories, priorise le backlog, valide le travail | يحدّد ماذا يُعمل، يكتب قصص المستخدم، يرتّب الأولويات |
| **Scrum Master**                         | Veille au bon processus, lève les obstacles, anime les cérémonies                  | يضبط العملية ويزيل العوائق                           |
| **Équipe de développement (Developers)** | Font le travail, estiment les stories                                              | ينفّذون العمل ويقدّرون الجهد                         |

### 👤 Le Product Owner en détail / مالك المنتج بالتفصيل

- Il est **la voix du client** / هو صوت العميل
- Il crée et priorise le **Product Backlog** / ينشئ ويرتّب قائمة الاحتياجات
- Il écrit les **User Stories** avec le format ci-dessous / يكتب قصص المستخدم
- Il accepte ou refuse le travail fini (Definition of Done) / يقبل أو يرفض العمل المنجز

## 3.6 Créer une User Story (pas à pas) / إنشاء قصة مستخدم خطوة بخطوة

### Format d'une User Story / صيغة قصة المستخدم

> **En tant que** [rôle] , **je veux** [action] , **afin de** [bénéfice]
> **بصفتي** [دور] ، **أريد** [وظيفة] ، **حتى** [فائدة]

### Exemple / مثال

> **En tant que** client, **je veux** réinitialiser mon mot de passe, **afin de** retrouver l'accès à mon compte.
> **بصفتي** زبوناً ، **أريد** إعادة تعيين كلمة المرور ، **حتى** أستعيد الدخول إلى حسابي.

### Étapes dans Jira / الخطوات في Jira

1. Ouvrir le projet → onglet **Backlog** / افتح المشروع ثم قائمة الاحتياجات
2. Cliquer **+ Create** (ou bouton **+** en haut) / اضغط زر الإنشاء
3. Choisir **Issue Type = Story** / اختر النوع: قصة
4. **Summary** : titre court ("Réinitialisation du mot de passe") / عنوان مختصر
5. **Description** : la User Story au format ci-dessus + **critères d'acceptation** / الوصف + معايير القبول
6. Remplir : **Assignee** (responsable), **Story Points** (estimation), **Epic Link** (lien vers l'Epic), **Priority**, **Sprint** / املأ: المسؤول، النقاط، القصة الأم، الأولوية، السبرنت
7. **Create** → la story apparaît dans le Backlog / إنشاء
8. **Prioriser** : glisser-déposer les stories (en haut = prioritaire) / رتّب بالسحب
9. Glisser la story dans un **Sprint** puis **Start sprint** / اسحبها إلى سبرنت وابدأه

### ⭐ DÉTAIL COMPLET : Créer un projet Jira, étape par étape / شرح كامل: إنشاء مشروع جيرا خطوة بخطوة
#### 🟦 ÉTAPE 0 — Créer un compte Jira / الخطوة 0 — إنشاء حساب
1. Ouvrir le navigateur → aller sur **https://www.atlassian.com/software/jira** / افتح المتصفح واذهب إلى الموقع
2. Cliquer sur le bouton bleu **« Get it free »** (obtenir gratuitement) / اضغط على الزر الأزرق « Get it free »
3. Choisir **« Continue with Google »** (le plus rapide si vous avez un Gmail) **ou** saisir votre email → **Sign up** / اختر الدخول عبر Google أو أدخل بريدك
4. Vérifier votre boîte mail → cliquer sur le lien de confirmation reçu / افتح بريدك واضغط على رابط التأكيد
5. Choisir un **nom de site** : ce sera votre URL personnelle, ex : `mon-equipe.atlassian.net` / اختر اسم الموقع، سيكون رابطك الشخصي
6. Question « Tell us about your team » : répondre librement (ex : 2-10 personnes) puis **Skip / Continue** — ce n'est pas bloquant / أجب عن أسئلة التقديم أو اضغط تخطٍ

✅ Résultat : vous êtes sur la **page d'accueil Jira**. À gauche : `Your work`, `Projects`, `Filters`, `Dashboards`… / النتيجة: أنت في الصفحة الرئيسية
#### 🟦 ÉTAPE 1 — Lancer la création du projet / الخطوة 1 — بدء إنشاء المشروع
1. Dans le **menu latéral gauche**, cliquer sur **`Projects`** → **`Create project`** (ou depuis l'accueil, bouton **`+ Create project`**) / في القائمة الجانبية اليسرى اضغط Projects ثم Create project
2. Une page **« Create project »** s'ouvre avec des **modèles** (templates) groupés en 2 catégories :
   - **Team-managed** (l'équipe gère tout elle-même — 👉 **choisissez ça pour apprendre**, c'est le plus simple) / إدارة من الفريق (الأفضل للمبتدئين)
   - **Company-managed** (géré par les administrateurs de l'entreprise, plus verrouillé) / إدارة من الشركة (للمؤسسات)

#### 🟦 ÉTAPE 2 — Choisir le modèle / الخطوة 2 — اختيار النموذج
Trois choix principaux s'affichent / تظهر ثلاثة اختيارات:
| Modèle | Quand l'utiliser (FR) | متى تستعمله (AR) |
|---|---|---|
| **Scrum** ✅ | Vous travaillez par **Sprints** (itérations de 2 semaines) avec un Backlog | تعمل بـ **السبرنتات** مع قائمة احتياجات |
| **Kanban** | Flux **continu** de tâches, pas de sprints, colonnes To Do → Done | تدفق **مستمر** بدون سبرنتات |
| **Bug tracking** | Suivi uniquement des bugs / incidents | تتبّع الأخطاء فقط |
3. Cliquer sur la carte **`Scrum`** → bouton **`Use template`** / اضغط على بطاقة Scrum ثم Use template
#### 🟦 ÉTAPE 3 — Nom, clé et type / الخطوة 3 — الاسم والمفتاح والنوع
Un formulaire apparaît / يظهر استمارة:
| Champ | Quoi mettre (FR) | ماذا تضع (AR) | Exemple |
|---|---|---|---|
| **Name** | Le nom du projet | اسم المشروع | `Mon Projet` |
| **Key** | 2-3 lettres en MAJUSCULES, identifiant chaque ticket — **elle est proposée automatiquement mais modifiable** | حرفان أو ثلاثة بالأحجام الكبيرة، مفتاح كل تذكرة | `MP` |
| **Type** | Team-managed (recommandé) | إدارة من الفريق (موصى به) | Team-managed |
> 💡 Avec la clé `MP`, les tickets s'appelleront automatiquement **MP-1, MP-2, MP-3…** / مع المفتاح MP ستُسمّى التذاكر تلقائياً MP-1، MP-2…

#### 🟦 ÉTAPE 4 — Créer / الخطوة 4 — الإنشاء
1. Cliquer sur le bouton bleu **`Create`** / اضغط الزر الأزرق Create
2. Jira ouvre automatiquement votre projet sur l'onglet **`Board`** (ou `Backlog` si Scrum) / يفتح جيرا المشروع على اللوحة أو قائمة الاحتياجات
3. Découverte des onglets (en haut) / استكشاف التبويبات:
   - **Board** : le tableau Kanban (colonnes TO DO / IN PROGRESS / DONE) — on y déplace les cartes / اللوحة: تنقل فيها البطاقات
   - **Backlog** : liste de TOUTES les stories non planifiées + les sprints / قائمة الاحتياجات وكل القص والسبرنتات
   - **Timeline** : vue calendrier (Gantt) / عرض زمني
   - **Reports** : graphiques (burndown, vélocité…) / التقارير والرسوم
   - **Issues** : toutes les tâches filtrables / كل التذاكر
   - **Project settings** : colonnes du board, types d'issues, permissions… / إعدادات المشروع
4. Inviter l'équipe : **Project settings → People → Add people** (email des collègues) / لدعوة الفريق من الإعدادات
✅ Le projet est prêt ! Maintenant on va y créer des User Stories.
✅ المشروع جاهز! الآن سننشئ قص المستخدم.

### 📝 DÉTAIL COMPLET : Créer une User Story dans Jira (avec chaque champ expliqué) / شرح كامل: إنشاء قصة مستخدم في جيرا مع شرح كل حقل
#### 🟩 ÉTAPE 1 — Ouvrir le Backlog / افتح قائمة الاحتياجات
1. Ouvrir le projet (menu gauche `Projects` → votre projet) / افتح مشروعك
2. Cliquer sur l'onglet **`Backlog`** (en haut, sous le titre du projet) / اضغط على تبويب Backlog
> 💡 Astuce rapide : le bouton **`+ Create`** en haut de l'écran marche depuis N'IMPORTE QUELLE page / الزر Create يعمل من أي صفحة
#### 🟩 ÉTAPE 2 — Cliquer sur Create / اضغط Create
- Dans le Backlog : cliquer **`+ Create`** en haut à droite (ou raccourci clavier **`c`**) / في القائمة اضغط Create أو الحرف c من لوحة المفاتيح
- Un formulaire latéral **« Create issue »** s'ouvre à droite / تفتح استمارة على اليمين
#### 🟩 ÉTAPE 3 — Remplir chaque champ / املأ كل حقل (شرح كل حقل)
| Champ (Ordre) | Explication (FR) | الشرح (AR) | Valeur d'exemple |
|---|---|---|---|
| **1. Issue type** ⚠️ le plus important | Le TYPE de ticket : `Story` pour une fonctionnalité utilisateur, `Bug`, `Task`, `Epic` | نوع التذكرة: Story لميزة المستخدم | `Story` |
| **2. Summary** | Le TITRE, court et clair (une seule phrase) | العنوان: قصير وواضح | `Réinitialisation du mot de passe` |
| **3. Description** | La User Story complète + les critères d'acceptation (voir format ⬇️) | الوصف الكامل + معايير القبول | voir format ci-dessous |
| **4. Assignee** | QUI va travailler dessus (vous pouvez laisser « Unassigned » pour l'instant) | من سيعمل عليها (يمكن تركها فارغة) | `Achraf` |
| **5. Priority** | Importance : Highest / High / Medium / Low / Lowest | الأولوية | `High` |
| **6. Story Points** ⭐ champ Scrum | L'effort estimé (1, 2, 3, 5, 8, 13) — permet de mesurer la vitesse de l'équipe | التقدير بالجهد (نقاط) | `3` |
| **7. Epic Link** | La grande fonctionnalité parente à laquelle la story est rattachée | القصة الكبيرة الأم | `EPIC-1 Comptes utilisateurs` |
| **8. Labels** | Des étiquettes libres pour filtrer (ex : `securite`, `frontend`) | وسوم للتصفية | `securite` |
| **9. Due date** | Date limite (optionnelle) | تاريخ الاستحقاق (اختياري) | `2025-01-30` |

#### 🟩 ÉTAPE 4 — Écrire la User Story dans Description / اكتب قصة المستخدم في الوصف
Copier ce modèle dans le champ **Description** / انسخ هذا القالب في حقل الوصف:
```markdown
h2. User Story
*En tant que* client,
*je veux* réinitialiser mon mot de passe,
*afin de* retrouver l'accès à mon compte.

h2. Critères d'acceptation
* L'utilisateur reçoit un email avec un lien de réinitialisation
* Le lien expire après 24 heures
* Message d'erreur clair si l'email est inconnu
* Le nouveau mot de passe doit contenir 8 caractères minimum
h2. Notes techniques
- Utiliser le service d'emails SendGrid
- Page : /reset-password
```
> 💡 `h2.` crée un titre dans Jira, `*mot*` = gras, `-` = liste à puces.
> 💡 العناوين والتنسيقات داخل جيرا كما هو موضح أعلاه.

#### 🟩 ÉTAPE 5 — Créer / إنشاء
- Cliquer sur le bouton bleu **`Create`** en bas du formulaire / اضغط الزر الأزرق Create
- La story apparaît maintenant dans le **Backlog** avec son numéro : `MP-1`, `MP-2`… / تظهر القصة في القائمة برقمها
- 🔄 Pour en créer d'autres : cocher **« Create another »** avant de valider / لتكرار الإنشاء فعّل خيار Create another
#### 🟩 ÉTAPE 6 — Prioriser le Backlog / ترتيب الأولويات
1. Dans le Backlog, **glisser-déposer** les stories : **en haut = le plus prioritaire** / اسحب القص: الأعلى = الأولوية الأكبر
2. L'ordre du Backlog = l'ordre dans lequel l'équipe travaillera / ترتيب القائمة = ترتيب العمل
#### 🟩 ÉTAPE 7 — Créer et démarrer un Sprint / إنشاء سبرنت وبدؤه
1. Dans le Backlog, cliquer sur **`Create sprint`** (en haut, sous le titre Backlog) / اضغط Create sprint
2. **Glisser-déposer** les stories priorisées DANS le sprint (entre les lignes grises « Sprint 1 ») / اسحب القص داخل السبرنت
3. Cliquer sur **`Start sprint`** → choisir **Duration** (ex : 2 weeks) + **Start date** / اضغط Start sprint واختر المدة والتاريخ
4. Le sprint apparaît avec une date de fin, et les stories passent sur le **Board** / يظهر السبرنت بتاريخ نهاية وتنتقل القص إلى اللوحة
5. Pendant le sprint : les devs **déplacent** chaque story de `TO DO` → `IN PROGRESS` → `DONE` / أثناء السبرنت تُنقل البطاقات بين الأعمدة
6. À la fin : **`Complete sprint`** — les stories non finies retournent au Backlog / في النهاية أنهِ السبرنت، وما لم يُنجز يعود للقائمة
#### 🟩 ÉTAPE 8 — Lier la story à Git/GitHub / اربط القصة بـ Git و GitHub
1. Ouvrir la story → menu **`⋯` (trois points) → Link** ou copier son ID (`MP-1`) / افتح القصة وانسخ رقمها
2. Nommer votre branche et vos commits avec ce numéro / سمِّ الفرع والكومِتات بهذا الرقم:
```bash
git switch -c MP-1-reset-password
git commit -m "MP-1: formulaire de réinitialisation fonctionne"
```
3. Jira affiche automatiquement dans la story les branches/PR/commits liés (si l'intégration GitHub est connectée : **Apps → Explore more apps → GitHub for Jira**) / يعرض جيرا تلقائياً الفروع المرتبطة
#### 🟩 RÉSUMÉ VISUEL / ملخص بصري
```
Créer compte Jira → Create project → Scrum → Nom + Clé (MP) → Create
   → Backlog → + Create → Type: Story → Summary + Description (User Story)
   → Story Points + Assignee → Create → Glisser dans Sprint 1 → Start sprint
   → Board (déplacer les cartes) → Complete sprint
إنشاء الحساب → إنشاء المشروع → سكرم → الاسم والمفتاح → الإنشاء
   → قائمة الاحتياجات → إنشاء قصة → تعبئة الحقول → السحب للسبرنت → البدء
```

### Critères d'acceptation (exemple) / معايير القبول (مثال)

- ✅ L'utilisateur reçoit un email de réinitialisation / يتلقى المستخدم بريد إعادة التعيين
- ✅ Le lien expire après 24h / تنتهي صلاحية الرابط بعد 24 ساعة
- ✅ Un message d'erreur s'affiche si l'email est inconnu / تظهر رسالة خطأ

## 3.7 Cycle de vie d'un ticket / دورة حياة التذكرة

```
TO DO (à faire) → IN PROGRESS (en cours) → IN REVIEW (en revue)
→ TESTING (test) → DONE (terminé)
قائمة الانتظار → قيد التنفيذ → قيد المراجعة → الاختبار → منجز
```

Sur le **Board**, on déplace les cartes d'une colonne à l'autre. / على اللوحة ننقل البطاقات بين الأعمدة.

## 3.8 Workflow Scrum complet dans Jira / سير عمل سكرم الكامل

1. Le **PO** écrit les User Stories dans le Backlog / مالك المنتج يكتب القصص
2. **Sprint Planning** : l'équipe choisit les stories + estimation en points / تخطيط السبرنت والتقدير
3. **Démarrer le Sprint** (1-4 semaines) / بدء السبرنت
4. Chaque jour : **Daily Stand-up** (15 min) / اجتماع يومي قصير
5. Les devs déplacent les cartes : To Do → In Progress → Done / تحريك البطاقات
6. Lier chaque commit/branche à la story (clé MP-12 dans le message de commit) / ربط الكومِت بالقصة
   ```bash
   git switch -c MP-12-reset-password
   git commit -m "MP-12: ajout réinitialisation mot de passe"
   ```
7. **Sprint Review** (démo) + **Rétrospective** / مراجعة واستعراض السبرنت
8. Fin de sprint → nouveau sprint / نهاية السبرنت وبدء آخر

---

# PARTIE 4 : PROJET COMPLET — END-TO-END / مشروع كامل من البداية للنهاية

## 🇫🇷 Scénario : vous devez développer un site de tâches (To-Do).

## 🇸🇦 السيناريو : عليك تطوير موقع للمهام اليومية.

1. **Jira** : créer le projet `TODO` (modèle Scrum) / أنشئ المشروع في Jira
2. **Epic** : `TODO-1 Gestion des tâches` / أنشئ قصة كبيرة
3. **User Story** (par le Product Owner) :
   > En tant qu'utilisateur, je veux ajouter une tâche, afin de ne rien oublier.
   > بصفتي مستخدماً، أريد إضافة مهمة، حتى لا أنسى شيئاً.
4. **Estimer** la story (story points) + la mettre dans **Sprint 1** / قدّرها وضعها في السبرنت
5. **Start sprint** / ابدأ السبرنت
6. **GitHub** : créer le dépôt `todo-app` / أنشئ المستودع على GitHub
7. **Localement** / على جهازك :
   ```bash
   git clone https://github.com/vous/todo-app.git
   cd todo-app
   git switch -c TODO-3-ajouter-tache      # branche nommée d'après la story Jira
   # ... coder la fonctionnalité ...
   git add .
   git commit -m "TODO-3: ajout de tâches fonctionne"
   git push origin TODO-3-ajouter-tache
   ```
8. **Pull Request** sur GitHub → revue → **Merge** / طلب دمج ومراجعة
9. **Jira** : déplacer la story vers **DONE** / انقل القصة إلى منجز
10. Fin du sprint → review → sprint suivant / نهاية السبرنت ثم دورة جديدة

---

# PARTIE 5 : RÉSUMÉ DES INSTALLATIONS / ملخص ما يجب تثبيته

| Outil              | Qu'installer ?                                                  | ماذا نثبّت؟                    |
| ------------------ | --------------------------------------------------------------- | ------------------------------ |
| **Git**            | Git for Windows (git-scm.com)                                   | برنامج Git على الجهاز          |
| **GitHub**         | Rien (navigateur) + Git + optionnel GitHub Desktop / GitHub CLI | لا شيء إلزامياً — المتصفح يكفي |
| **Jira**           | Rien (navigateur : atlassian.com)                               | لا شيء — يعمل من المتصفح       |
| Éditeur recommandé | Visual Studio Code (code.visualstudio.com)                      | محرر الأكواد                   |

---

# PARTIE 6 : BONNES PRATIQUES / نصائح مهمة

### 🇫🇷

- Committer **souvent** avec des messages clairs (`feat:`, `fix:`, `MP-12:`…).
- Une **branche par fonctionnalité**, jamais travailler directement sur `main`.
- Toujours `git pull` **avant** de commencer à travailler.
- Ne jamais commiter les mots de passe → fichier `.gitignore` (node_modules/, .env…).
- Dans Jira : toujours mettre à jour le statut de la story pendant le travail.

### 🇸🇦

- احفظ (commit) **بشكل متكرر** برسائل واضحة.
- **فرع لكل ميزة**، ولا تعمل مباشرة على `main`.
- اجعل `git pull` **قبل** بدء العمل دائماً.
- لا تحفظ كلمات المرور → استعمل ملف `.gitignore`.
- في Jira: حدّث حالة القصة باستمرار أثناء العمل.

---

# PARTIE 7 : ANNEXE — Annexes utiles / ملحق مفيد

### `.gitignore` exemple / مثال

```gitignore
node_modules/
.env
*.log
dist/
```

### Ressources / مصادر

- Git : https://git-scm.com/doc
- GitHub Docs : https://docs.github.com
- Jira Guide : https://www.atlassian.com/agile

---

✅ **Fin du guide — نهاية الدليل**
