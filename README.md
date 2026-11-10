# Compagnies Aériennes — squelette SwiftUI natif

App iOS 17+ (SwiftUI, MapKit, Swift Charts), bilingue FR/EN, 100 % hors-ligne.

## Contenu

```
CompagniesAeriennes/
├── App/CompagniesAeriennesApp.swift   point d'entrée + TabView (4 onglets)
├── Models/Models.swift                Airline, Airport, Alliance, Continent, helper L.t(fr, en)
├── Models/AirlineStore.swift          chargement des JSON (@Observable)
├── Views/GlobeView.swift              globe satellite 3D, hubs colorés par alliance, routes géodésiques
├── Views/AirlineListView.swift        liste + recherche + filtres alliance/continent + drapeau FR/EN
├── Views/AirlineDetailView.swift      fiche : carte des routes, chiffres clés, hubs, distances
├── Views/CompareView.swift            comparateur de 2 compagnies (Swift Charts)
├── Views/QuizView.swift               quiz de 10 questions (hub, pays, alliance, année), record sauvegardé
└── Resources/airlines.json            58 compagnies (19 Star, 15 SkyTeam, 15 oneworld, 9 indépendantes)
    Resources/airports.json            93 aéroports (code IATA, ville, coordonnées)
```

## Mise en place dans Xcode

1. Fichier › Nouveau › Projet › iOS › App. Nom : **Compagnies Aériennes**, interface SwiftUI, cible iOS 17.
   Bundle ID suggéré : `com.michel.garlandat.compagniesaeriennes`.
2. Supprimer le `ContentView.swift` et le fichier `…App.swift` générés par Xcode.
3. Glisser les dossiers `App`, `Models`, `Views` et `Resources` dans le projet
   (cocher « Copy items if needed » et la cible de l'app).
4. Vérifier que `airlines.json` et `airports.json` figurent dans *Build Phases › Copy Bundle Resources*.
5. Lancer sur simulateur ou iPhone.

Aucune clé d'API, aucun réseau, aucune permission requise (App Privacy : Data Not Collected).

## Points d'attention

- **Logos** : l'app n'affiche aucun logo déposé, seulement un monogramme (code IATA) généré
  par l'app, pour éviter un refus 5.2.1. Les couleurs d'alliance sont aussi propres à l'app.
- **Données à relire avant publication** : les tailles de flotte sont des ordres de grandeur
  (≈ 2025-2026) et les « routes emblématiques » sont une sélection, pas un réseau exhaustif.
  Alliances vérifiées au 05/11/2026 : ITA Airways membre de Star Alliance depuis le 1er avril 2026,
  Air Europa toujours chez SkyTeam (malgré l'entrée de Turkish Airlines à son capital),
  SAS chez SkyTeam depuis 2024, Oman Air chez oneworld depuis 2025.
- **Régénérer les données** : les JSON viennent d'un petit script Python ; on peut aussi les
  éditer à la main (même structure).

## Pistes pour la V2 (et pour s'éloigner encore du 4.3)

- Widget « compagnie du jour » (WidgetKit).
- Favoris et historique de quiz avec SwiftData.
- Vue « réseau des alliances » (toutes les routes d'une alliance d'un coup sur le globe).
- Liens croisés vers Avions de Légende et Aéroports Mythiques.
