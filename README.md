# TimeLock - Server Access Control

**TimeLock** est un mod Minecraft conçu avec MCreator pour réguler l'accès à un serveur en fonction de l'horloge réelle. Il permet de synchroniser la progression de la communauté en instaurant un couvre-feu obligatoire.

## 🚀 Fonctionnalités
- **Plage horaire stricte** : Le serveur accepte les connexions uniquement de **12h00 à 02h00 du matin** (heure du serveur).
- **Refus de connexion automatique** : Tout joueur tentant de se connecter en dehors des heures d'ouverture est automatiquement éjecté (kick) avec un message d'explication.
- **Préservation de la communauté** : Idéal pour éviter le *hardcore farming* nocturne et maintenir un esprit de compétition sain et équitable.

## 🛠️ Logique de la Procédure MCreator

Le mod s'appuie sur le déclencheur global `Player logs in` (Le joueur se connecte). La vérification de l'heure est gérée directement en Java pour éviter les failles :

```java
int hour = java.time.LocalTime.now().getHour();

// Le serveur est FERMÉ si l'heure est entre 2h du matin (inclus) et midi (exclu)
if (hour >= 2 && hour < 12) {
    // Code pour kick le joueur avec le message de fermeture
}
