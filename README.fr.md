# Minuteur de présentation

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [हिन्दी](README.hi.md) | [Español](README.es.md) | [Français](README.fr.md) | [العربية](README.ar.md) | [বাংলা](README.bn.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Bahasa Indonesia](README.id.md) | [Deutsch](README.de.md) | [한국어](README.ko.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

Un minuteur d’une seule page pour que chacun se présente à tour de rôle lors de retrouvailles ou d’événements similaires. Il suffit d’ouvrir `index.html` dans un navigateur : ni installation, ni serveur, ni connexion internet.

## Utilisation

1. Ouvrez `index.html` dans un navigateur (Safari / Chrome).
2. Sur l’écran de réglages : chargez un CSV (voir `sample/participants.csv` ou « Charger un exemple »), indiquez la présence de chacun, triez selon n’importe quel champ, réglez le titre / la durée par personne / la civilité / la langue, et testez les sons.
3. Cliquez sur « Aller au minuteur » (cela active aussi le son).
4. Lancez le minuteur :

| Action | Effet |
|---|---|
| `Espace` / bouton Démarrer | Lance la personne suivante (avec applaudissements) |
| Clic sur un nom de la liste de droite | Lance cette personne ; ceux qui précédaient passent dans « Sautés » |
| Clic sur un nom de « Sautés » | Lance cette personne |
| Décocher « Présent » dans « Sautés » | Après confirmation, la personne est marquée absente et retirée (le minuteur continue) |

À 10 s de la fin : un tic par seconde · à 3 s : bips rapides · à 0 s : explosion et étiquette « Temps écoulé ! ». En haut à droite : temps total écoulé ; colonne de droite : les 10 prochaines personnes.

## Format CSV

La première ligne est l’en-tête. UTF-8 et Shift_JIS sont détectés automatiquement. Les colonnes du nom et de la civilité sont choisies d’après l’en-tête (p. ex. `nom`, `civilité`) et modifiables dans les réglages. Si la cellule de civilité est vide, la civilité par défaut est utilisée.

```csv
name,honorific,group,year
Alex Morgan,,A,2001
Sam Rivera,Dr.,B,2001
```

## Langues

16 langues : changez avec « Langue » sur l’écran de réglages (la langue du navigateur est utilisée au départ, votre choix est mémorisé). Les textes, le titre et la civilité par défaut, les données d’exemple et la position de la civilité (avant/après le nom) suivent la langue ; l’arabe utilise une mise en page de droite à gauche. Les traductions n’ont pas été relues par des locuteurs natifs : modifiez `I18N` dans `index.html` pour les corriger. Pour ajouter une langue, ajoutez des entrées dans `LANGS`, `I18N` et `SAMPLE_NAMES`.

## Mobile

Mises en page pour téléphone en portrait et en paysage. Sur iPhone, le commutateur de sourdine coupe le son. Ouvrir le fichier via l’app Fichiers est le plus fiable ; avec GitHub Pages, il suffit d’ouvrir une URL.

## Structure

```
.
├── index.html            # app (HTML / CSS / JavaScript in one file)
├── sample/
│   └── participants.csv  # sample list
├── README.md             # + README.<lang>.md (16 languages)
└── LICENSE               # MIT
```

`index.html` contient tout : le dictionnaire des langues, un analyseur CSV, l’écran de réglages, la synthèse sonore Web Audio (aucun fichier audio), la logique du minuteur (basée sur l’horodatage, sans dérive) et l’écran de passage. Les réglages et la progression sont enregistrés automatiquement dans `localStorage`.

Licence : [MIT](LICENSE)
