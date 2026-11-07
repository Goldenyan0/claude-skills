# claude-skills

Skills pour [Claude Code](https://claude.com/claude-code).

| Skill | À quoi il sert |
|---|---|
| `blender-game-artist` | Artiste 3D Blender pour jeux Roblox : recherche de références réelles avant de modéliser, textures PBR, bake, UV, export vers Roblox (SurfaceAppearance, limites des MeshPart). Inclut 2 scripts Blender (`midpoly.py`, `bake_unique.py`). |
| `publier-video` | Publier ou programmer une vidéo sur TikTok et Instagram en pilotant Chrome (extension Claude in Chrome) : bon profil, légende vérifiée, label IA, programmation, couverture, journal. |

## Installation

1. Téléchargez le dépôt (**Code > Download ZIP**, ou `git clone`).
2. Copiez le dossier du skill voulu dans :
   - Windows : `%USERPROFILE%\.claude\skills\`
   - macOS / Linux : `~/.claude/skills/`
3. Pour `publier-video` : remplissez `config.md` avec vos comptes et vos profils Chrome. Ce skill a besoin de l'extension **Claude in Chrome**, et vous devez déjà être connecté à vos comptes : il ne saisit jamais de mot de passe.
4. Redémarrez Claude Code.

## Licence

MIT
