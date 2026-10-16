# Taikeron Map Chooser — Releases publiques

Dépôt **public de distribution** de Taikeron Map Chooser (TMC), consommé par **Taikeron Launcher**.

- **Code source privé :** `servicesathe-eng/Taikeron-TMC`
- **Exécutables officiels :** [Releases](https://github.com/servicesathe-eng/Taikeron-TMC-Releases/releases)
- **Canal WMS :** publication directe du dépôt TMC vers ce dépôt public, **sans DEV**
- **Manifest stable attendu :** `releases/tmc/stable.json`
- **Runtime Windows :** exécutable portable `Taikeron_Map_Chooser_<version>_Portable.exe`
- **Installation du Launcher :** `AppsRoot/MapChooser/Taikeron Map Chooser.exe`
- **Cartes :** accès à `TAIKERON_MAPS_ROOT` partagé entre TL/TMB/TMC

## État initial

Ce dépôt est initialisé mais **aucune release TMC n'est encore publiée**. Il serait incorrect de créer dès maintenant un `stable.json` disponible sans binaire réel : le Launcher exige une URL officielle, une taille et un SHA-256 vérifiables.

La première exécution réussie de **WMS TMC direct public** génère la release GitHub et met à jour `releases/tmc/stable.json` avec `product: "TMC"`, `channel: "stable"`, `available: true`, les coordonnées du Portable Windows, sa taille et son SHA-256.

## Autorisation nécessaire pour le premier WMS

Le workflow est dans le dépôt source privé : `Taikeron-TMC/.github/workflows/wms.yml`.

Créer un **fine-grained personal access token** limité au dépôt **Taikeron-TMC-Releases**, avec **Contents: Read and write**, puis enregistrer ce token comme secret GitHub Actions du dépôt privé source :

`Taikeron-TMC → Settings → Secrets and variables → Actions → New repository secret → TMC_PUBLIC_RELEASE_TOKEN`

Ne jamais placer le token dans le code, dans ce dépôt public, ni dans une discussion. Le `GITHUB_TOKEN` du dépôt source est limité à celui-ci et ne peut pas publier dans un autre dépôt.

Lancer ensuite le workflow **WMS TMC direct public** via **Actions → Run workflow** sur `Taikeron-TMC`. WMS compile et valide les sources en privé et ne publie ici que le Portable Windows et son manifeste stable.

**Attention :** le prototype TMC 0.1.0 embarque une grille TGG *DRAFT*. Sa distribution en tant qu'application n'implique pas la certification des identifiants TGG ni la disponibilité de TaikerMap de production.
