---
name: publier-video
description: "Publier ou programmer une vidéo sur TikTok et Instagram via le navigateur Chrome (Claude in Chrome) : bon profil Chrome, légende, label IA, programmation, vérifications et journal. À utiliser quand l'utilisateur dit « poste », « programme », « publie » ou « mets en ligne » une vidéo."
---

# Publier une vidéo (TikTok + Instagram)

Ce skill est **modulable** : tous les réglages (comptes, horaires, règles de légende, label IA, vérifications) sont dans `config.md`, à côté de ce fichier. **Lis toujours `config.md` en premier** : pour changer une règle, on modifie `config.md`, pas ce fichier.

## Étapes

1. **Préparer**
   - Lire `config.md`.
   - Identifier l'univers de la vidéo et donc les comptes cibles (TikTok + Insta du même univers).
   - Vérifier le fichier : il existe, respecte la taille maximale de `config.md`, est en 1080x1920 et les zones sûres ont été contrôlées.
2. **Choisir le bon navigateur**
   - `list_connected_browsers` puis `select_browser` pour le profil Chrome qui contient le compte (table dans `config.md`).
   - Contrôler le compte connecté : nom affiché sur tiktok.com/profile ou dans la barre Instagram.
   - Si le compte n'est pas celui attendu : STOP, le signaler. Ne jamais saisir de mot de passe.
3. **Légende**
   - Construire la légende selon les règles de `config.md` : accroche, question ou appel à identifier, hashtags, crédits obligatoires des ressources utilisées.
   - La garder identique sur TikTok et Insta.
4. **TikTok** (tiktokstudio/upload)
   - `find` l'input file, puis `file_upload`.
   - Fermer les popups : vérification automatique selon `config.md`, et « J'ai compris ».
   - Description : clic, ctrl+a, Delete, saisie, Échap. Vérifier par JS que `[contenteditable=true]` contient la légende exacte.
   - Ouvrir « Afficher plus », activer « Contenu généré par IA » si `config.md` le demande (popup « Activer » s'il apparaît). Vérifier que le texte « Le créateur a indiqué » est présent.
   - Selon le mode :
     - « Maintenant » : bouton Publier, puis « Publier maintenant » si demandé.
     - « Programmer » : radio Programmer, « Autoriser », date, heure (molette des heures et des minutes, puis vérification par zoom), puis bouton Programmer.
     - En mode Programmer, couper la vérification de contenu si elle bloque : sinon le seul bouton proposé est « Publier maintenant ».
   - Contrôle final : sur tiktokstudio/content, la légende et la date apparaissent (pas « Aucune description »).
5. **Instagram**
   - Créer, puis Publication, puis `find` l'input file dans le dialogue, puis `file_upload`.
   - « Sélectionner un format », puis « Original », puis Suivant.
   - Vérifier que le son est activé : la checkbox doit être à true.
   - Suivant, puis légende (même texte), puis « Ajouter une mention IA » si demandé. Vérifier par JS que la checkbox est à true : le 1er clic peut seulement retirer le focus de la légende, recliquer si besoin.
   - Partager, puis attendre « a été partagé ».
   - Le web ne permet pas de programmer : publier à l'heure prévue, en local (session ouverte).
6. **Journal**
   - Mettre à jour le fichier de suivi indiqué dans `config.md` (statut, heure, comptes).
7. **Rapport** en 3 lignes maximum : quoi, où, quand. Signaler tout écart avec `config.md`.

## Pièges connus
- Saisie au clavier qui perd une lettre : toujours relire le texte par JS. Pour un champ long, utiliser le setter natif ou `execCommand('insertText')`.
- Légende TikTok : ne jamais utiliser `execCommand` (hashtags doublés puis éditeur planté) ; taper au clavier et relire par JS.
- Heure TikTok : la molette fait seulement défiler la liste ; cliquer ensuite sur l'heure puis la minute, et zoomer pour vérifier.
- Comparaison JS de la légende : normaliser les espaces insécables autour de « » et €.
- Onglet bloqué (« Cannot access a chrome-extension:// URL ») : ouvrir un nouvel onglet, sans insister.
- Une publication programmée sur TikTok ne se modifie pas. Pour la changer, il faut la supprimer puis la refaire, avec l'accord explicite de l'utilisateur.
- Ne jamais supprimer une publication sans accord explicite.

## Couvertures
- Chaque vidéo a une couverture `<nom>_couv.jpg` (1080x1920) livrée à côté du mp4. Titre court et lisible en vignette, image forte.
- TikTok : appliquer la couverture À L'IMPORT (Modifier la couverture > onglet d'import d'image s'il existe, sinon choisir l'image clé + Texte). Après publication, TikTok web ne permet plus d'importer une image.
- Instagram : à l'étape « Modifier », « Photo de couverture » > importer `_couv.jpg`. Impossible de la changer après coup sur le web.
- YouTube Shorts : pas de miniature personnalisée sur le web ; mettre la couverture comme 1re image de la vidéo si besoin.
