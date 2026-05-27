# 📋 ROADMAP IMANPARIS — v1.1.0
> Retours utilisateur compilés — session du 27/05/2026

---

## 🏷️ SECTION MARQUE

### 🔴 Bug — Scraping d'offres incorrect
- **Problème** : L'agent scrape des offres et génère des prix fictifs même quand la page source n'en contient pas.
- **Correction** : Avant de créer une offre, vérifier qu'un **prix est bien présent** dans la page scrapée. Si aucun prix détecté → ne pas créer d'offre, ou créer une entrée vide avec un avertissement "Prix non détecté".

---

### 🟡 Amélioration — Upload de plusieurs logos
- **Problème** : Actuellement, un seul logo peut être uploadé.
- **Correction** : Permettre l'upload de **plusieurs déclinaisons de logo** (ex: logo couleur, logo blanc, logo carré, logo horizontal…).
- Chaque logo doit pouvoir être nommé/labellisé.

---

### 🟡 Amélioration — Upload d'assets graphiques supplémentaires
- **Problème** : La charte graphique peut contenir d'autres éléments (icônes, motifs, illustrations, typographies…).
- **Correction** : Ajouter une section **"Assets graphiques"** dans la marque pour uploader librement d'autres éléments de la charte.
- L'IA doit pouvoir utiliser ces assets comme références lors de la génération.

---

### 🟡 Amélioration — Renommer "Code de voix"
- **Problème** : Le terme "Code de voix" n'est pas compris / pas en français courant.
- **Correction** : Renommer en **"Ton & style de communication"** ou **"Identité éditoriale"**.
- Sous-titré : *"Décrivez le ton, les valeurs et la vision de votre marque."*

---

## 📣 SECTION CAMPAGNE

### 🔴 Refonte des statuts

Voici le **nouveau ordre et comportement** des statuts :

| Ordre | Ancien nom | Nouveau nom | Comportement |
|-------|-----------|-------------|-------------|
| 1 | À évaluer | **À évaluer** ✅ | Statut par défaut à la création — inchangé, mettre EN PREMIER |
| 2 | À retoucher | **À retoucher** 🖊️ | ⚠️ NOUVEAU COMPORTEMENT (voir ci-dessous) |
| 3 | _(nouveau)_ | **À refaire** 🔄 | ⚠️ NOUVEAU STATUT (voir ci-dessous) |
| 4 | Validé | **Recréer dans un autre format** 📐 | ⚠️ NOUVEAU COMPORTEMENT (voir ci-dessous) |
| 5 | Prête à poster | **Prête à poster** ✅ | Inchangé — déclenche ajout auto au planning |
| 6 | Corbeille | **Corbeille** 🗑️ | Inchangé |
| — | Brouillon | ~~Brouillon~~ | ❌ À supprimer |

---

#### Statut "À retoucher" — Nouveau comportement
- **Objectif** : Retoucher une image déjà générée (pas en recréer une nouvelle de zéro).
- **Comportement attendu** :
  1. L'image existante est passée en **image de référence (img2img / image ref)**.
  2. L'utilisateur précise les **éléments à modifier** (couleur, texte, composition…).
  3. L'IA génère **5 nouvelles variantes** basées sur cette image ref + les retours.
- ❌ Ne PAS reprendre uniquement le prompt texte et régénérer une image from scratch.

---

#### Statut "À refaire" — Nouveau statut
- **Objectif** : Recréer une image en repartant du prompt d'origine (sans utiliser l'image précédente comme référence).
- **Comportement attendu** :
  1. L'IA reprend le **prompt texte original**.
  2. Option : l'utilisateur peut ajouter une **légère modification au prompt**.
  3. L'IA génère une **nouvelle image** (batch de 5 comme d'habitude).
- ℹ️ Subtilité vs "À retoucher" : ici on repart du texte, pas de l'image.

---

#### Statut "Recréer dans un autre format" (ex-Validé)
- **Objectif** : Adapter l'image validée à un autre format/réseau.
- **Comportement attendu** :
  1. Afficher un **sélecteur de format** (ex: Story 9:16, Post carré 1:1, Bannière 16:9, LinkedIn…).
  2. L'IA recrée l'image dans le nouveau format choisi.
- ❌ Supprimer l'ancien statut "Validé" tel quel.

---

### 🟡 Amélioration — Icône de téléchargement sur les images
- Ajouter une **petite icône de téléchargement** en haut à droite de chaque image générée.
- Au clic → téléchargement direct de l'image (format original).

---

### 🟡 Amélioration — Passage auto au planning
- Quand une image passe en statut **"Prête à poster"** ET que l'utilisateur envoie ses retours à l'IA → l'IA **place automatiquement les images "Prêtes à poster" dans le planning**.
- Les posts Facebook et Instagram d'une même image doivent être programmés aux **mêmes horaires**.

---

## 📅 SECTION PLANNING

### 🟡 Amélioration — Vue Semaine (en plus de Mois)
- La vue Mois existe déjà ✅ — la garder.
- Ajouter une **vue Semaine** (style Google Calendar) : tableau 7 colonnes × heures de la journée.
- La vue Liste existante → la garder également.

### 🟡 Amélioration — Posts déplaçables dans le calendrier
- Les posts dans le calendrier doivent pouvoir être **glissés-déposés** (drag & drop) pour changer leur horaire/jour.

### 🟡 Amélioration — Même horaire Facebook + Instagram
- Une image programmée doit apparaître **simultanément** sur les slots Facebook ET Instagram au même créneau horaire.

### 🟡 Amélioration — Alimentation automatique du calendrier
- Quand l'IA traite les retours et que des images sont en "Prêtes à poster" → les placer **automatiquement dans le calendrier** sans action manuelle supplémentaire.

---

## ✅ RÉSUMÉ DES PRIORITÉS

| Priorité | Tâche |
|----------|-------|
| 🔴 P0 | Fix scraping offres/prix fantômes |
| 🔴 P0 | Refonte statuts campagne + comportements IA |
| 🟡 P1 | Upload multi-logos + assets graphiques |
| 🟡 P1 | Renommer "Code de voix" |
| 🟡 P1 | Icône téléchargement sur images |
| 🟡 P1 | Vue Semaine dans le planning |
| 🟡 P2 | Drag & drop dans le calendrier |
| 🟡 P2 | Alimentation auto calendrier via IA |
| 🟡 P2 | Synchro horaires FB + Insta |
