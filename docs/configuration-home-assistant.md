# Configurer WallDock Echo depuis Home Assistant

Cette première méthode utilise **les tableaux de bord natifs Home Assistant**. Les lumières, volets, caméras et thermostats se configurent dans l'éditeur visuel Home Assistant. Aucun jeton d'accès n'est stocké dans GitHub Pages.

## 1. Vérifier l'accès depuis Silk

Ouvrir directement `http://ADRESSE-IP-HA:8123` dans Silk, sur le même réseau que Home Assistant. Vérifier l'adresse IP dans Home Assistant > Paramètres > Système > Réseau. Si la page ne charge pas, vérifier Wi-Fi, VLAN/réseau invité, isolation des appareils, pare-feu et IP réelle. L'URL locale ne fonctionne pas forcément depuis un autre réseau.

## 2. Créer un tableau de bord Echo

Dans Home Assistant : Paramètres > Tableaux de bord > Ajouter un tableau de bord. Nom : **WallDock Echo**. Choisir un chemin d'URL stable, par exemple `wall-dock-echo` si l'interface le permet. Créer des vues : Maison, Lumières, Volets, Caméras, Alarme, Climatisation et Calendrier. Les chemins réels dépendent du nom du tableau de bord et des chemins de chaque vue.

Utiliser l'éditeur de chaque vue pour ajouter les cartes natives Home Assistant. Par exemple :
- Lumières : cartes Tuile avec des entités `light` ou `switch` choisies dans l'éditeur.
- Volets : cartes Tuile pour les entités `cover`.
- Caméras : cartes Caméra ou Image selon les capacités des caméras et du navigateur.
- Climatisation : carte Thermostat pour une entité `climate`.
- Alarme : carte Alarme, avec les protections et codes Home Assistant appropriés.

Les entités sont choisies dans Home Assistant, **jamais codées en dur dans WallDock Echo**. Éviter de donner au compte utilisé sur l'Echo des droits d'administration si ce n'est pas nécessaire.

## 3. Configurer WallDock Echo

Ouvrir WallDock Echo > ⚙️ Réglages. Entrer l'adresse de Home Assistant, par exemple `http://192.168.1.10:8123` (remplacer par l'adresse réelle). Pour chaque rubrique, entrer le chemin exact de sa vue, par exemple `/wall-dock-echo/lumieres`. Laisser « Afficher les vues dans WallDock (expérimental) » **désactivé**. Enregistrer.

Les boutons ouvrent alors les vues configurées dans Silk. L'authentification est gérée par Home Assistant. Le bouton Retour de Silk permet de revenir à WallDock. Si une page est inaccessible, vérifier d'abord que l'adresse racine de Home Assistant fonctionne directement dans Silk.

## Limites actuelles

- Ce mode est une **configuration centralisée dans Home Assistant**, pas encore une intégration native WallDock Echo détectée comme appareil Home Assistant.
- Home Assistant ne peut pas encore envoyer des commandes de changement de page, notifications ou réveil de l'écran à WallDock Echo.
- L'affichage intégré via iframe peut être bloqué par la politique de sécurité de Home Assistant ou Silk.
- Les caméras peuvent nécessiter des formats de flux compatibles Silk.
- Une intégration bidirectionnelle sécurisée nécessitera un composant dédié et des tests sur l'appareil.
