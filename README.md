# oc-projet4

OpenClassrooms - dév JS react - projet 4 - gameon

## Version en ligne
Branche `Master` publiée sur [GitHub Pages](https://sedomu.github.io/GameOn-website-FR/)

## Projet GameOn
1. Forkez ce repo ;
2. Il est conseillé d'utiliser VisualStudio Code et vous pouvez utiliser Docker, mais ce n'est pas obligatoire ;
3. Il n'y a aucune dépendance ;
4. Vous ne devez utiliser que du CSS personnalisé et du JavaScript pur, sans jQuery, Bootstrap ou autre librairie.

## issues
- [X] TODO : fermer la modale
- [X] Implémenter entrées du formulaire
- [X] Ajouter validation ou messages d'erreur
- [X] Ajouter confirmation quand envoi réussi
- [X] Tests manuels
- [ ] +1: voir conclusions protocole de test

## protocole de test
tests manuels pour valider la vérification des données

| Description | Champ | Valeur | Résultat attendu | Résultat obtenu | Conclusion |
| ----------- | ----- | ------ | ---------------- | --------------- | ---------- |
| Remplissage correct du formulaire | Tous | Correctes | Accès page validation | Accès page validation | ✅ |
| validation de champ | Prénom | Cedric | ✅ | ✅ | ✅ |
| validation de champ | Prénom | Cédric | ✅ | ✅ | ✅ |
| validation de champ | Prénom | Marie-Alice | ✅ | ✅ | ✅ |
| validation de champ | Prénom | Marie Alice | ✅ | ✅ | ✅ |
| validation de champ | Prénom | C3dric | ❌ | ❌ | ✅ |
| validation de champ | Prénom | C | ❌ | ❌ | ✅ |
| validation de champ | Nom | Cedric | ✅ | ✅ | ✅ |
| validation de champ | Nom | Cédric | ✅ | ✅ | ✅ |
| validation de champ | Nom | Marie-Alice | ✅ | ✅ | ✅ |
| validation de champ | Nom | Marie Alice | ✅ | ✅ | ✅ |
| validation de champ | Nom | C3dric | ❌ | ❌ | ✅ |
| validation de champ | Nom | C | ❌ | ❌ | ✅ |
| validation de champ | Email | marie-alice@cedric.com | ✅ | ✅ | ✅ |
| validation de champ | Email | marie-alice@cédric.com | ❌ | ✅ | ❌ |
| validation de champ | Email | marie-alice@cedric.c | ❌ | ❌ | ✅ |
| validation de champ | Email | marie.alice@cedric.com | ✅ | ✅ | ✅ |
| validation de champ | Email | marie_alice@cedric.com | ✅ | ✅ | ✅ |
| validation de champ | Email | marie-alice75@cedric.com | ✅ | ✅ | ✅ |
| validation de champ | Email | marie@alice75@cedric.com | ❌ | ❌ | ✅ |
| validation de champ | Email | marie-alice@cedric | ❌ | ❌ | ✅ |
| validation de champ | Email | marie-alice@cedric. | ❌ | ❌ | ✅ |
| validation de champ | Email | marie!alice@cedric.com | ❌ | ❌ | ✅ |
| validation de champ | Date de naissance | 01/01/2000 | ✅ | ✅ | ✅ |
| validation de champ | Date de naissance | cedric | ❌ | ❌ | ✅ |
| validation de champ | Date de naissance | 25 | ❌ | ❌ | ✅ |
| validation de champ | Date de naissance | 28/02/2025 | ✅ | ✅ | ✅ |
| validation de champ | Date de naissance | 31/02/2025 | ❌ | ❌ | ✅ |
| validation de champ | Date de naissance | 29/02/2025 | ❌ | ❌ | ✅ |
| validation de champ | Date de naissance | 29/02/2024 | ✅ | ✅ | ✅ |
| validation de champ | Nombre de tournois | 0 | ✅ | ✅ | ✅ |
| validation de champ | Nombre de tournois | 1 | ✅ | ✅ | ✅ |
| validation de champ | Nombre de tournois | 01 | ✅ | ✅ | ✅ |
| validation de champ | Nombre de tournois | 99 | ✅ | ✅ | ✅ |
| validation de champ | Nombre de tournois | 100 | ❌ | ❌ | ✅ |
| validation de champ | Nombre de tournois | 099 | ❌ | ❌ | ✅ |
| validation de champ | Nombre de tournois | -1 | ❌ | ❌ | ✅ |
| validation de champ | Nombre de tournois | e | ❌ | ❌ | ✅ |
| validation de champ | Boutons radio | 1 coché | ✅ | ✅ | ✅ |
| validation de champ | Boutons radio | aucun coché | ❌ | ❌ | ✅ |
| validation de champ | Checkbox CGU | cochée | ✅ | ✅ | ✅ |
| validation de champ | Checkbox CGU | décochée | ❌ | ❌ | ✅ |
| validation de champ | Checkbox Newsletter | cochée | ✅ | ✅ | ✅ |
| validation de champ | Checkbox Newsletter | décochée | ✅ | ✅ | ✅ |
| injection: clic sur `submit`avec 1 erreur sur le formulaire (`submitBtn.disabled = false;` via la console) | Submit | N/A | ❌ | ❌ | ✅ |

Conclusion des tests: tous ok sauf 1. Les accents ne devraient pas être acceptés dans une adresse e-mail.
Tentative de correction en (double)-échappant le caractère `.`.
La solution qui est correcte sur Regex101 (``^[a-z0-9-_\\.]+@[a-z0-9-_\\.]+\\.[a-z]{2,}$``), laisse l'utilisateur mettre une lettre accentuée dans le domaine du mail (``RegExp("^[a-z0-9-_\\.]+@[a-z0-9-_\\.]+\\.[a-z]{2,}$")``).

> Issue: les accents ne passent pas dans la validation d'une adresse e-mail, sauf au niveau du domaine.
> Testé sur mon mobile (iPhone/Firefox): tous les accents sont bien rejetés.
> Retour sur MacOS: ce mauvais comportement ne concerne que les navigateurs sous Chromium (Arc, Chrome, Opera). Ok avec Gecko et WebKit.