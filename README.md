# OligoPlus — Préconisation Foliaire (template dynamique)

Template HTML autonome qui affiche la préconisation foliaire d'un lead Odoo
en lisant les paramètres depuis l'URL. Servi en GitHub Pages.

## URL de production

https://oligoplus.github.io/oligoplus-preco-foliaire/

## Paramètres URL attendus

| Param | Description | Exemple |
|---|---|---|
| `lead` | ID du lead Odoo | `49077` |
| `so` | ID du bon de commande | `4726` |
| `partner` | Nom du client | `Didier Sire` |
| `surface` | Surface totale en ha | `85` |
| `dept` | Département | `45` |
| `vendeur` | Nom du vendeur | `Nicolas Rathier` |
| `vendeur_tel` | Téléphone vendeur (optionnel) | `+33 6 XX XX XX XX` |
| `comment` | Commentaire optionnel | `Priorité colza` |
| `data` | JSON préco encodé en base64 | `eyJjcm9wcyI6...` |

## Flow

1. Vendeur remplit le form Foliaire dans Odoo
2. Make poll `crm.lead` toutes les 5 min, détecte les nouveaux leads Foliaire
3. Make construit l'URL dynamique avec les data du lead
4. Make écrit l'URL dans le champ `x_studio_url_preco_foliaire` sur Odoo
5. Sales ouvre la fiche Odoo → clique URL → voit la préco rendue
6. Sales fait Cmd+P si besoin d'archiver le PDF

## Édition du template

Fichier `index.html` autonome. Toute modif se fait directement dessus :
commit + push → GitHub Pages redéploie en ~1 min.

## Mapping produits / cultures / stades

Les dictionnaires sont dans le `<script>` du `index.html`. Pour ajouter un
produit ou un stade, éditer les constantes `PRODUCT_DICT`, `CROP_DICT`, 
`STAGE_PICTO` en haut du script.
