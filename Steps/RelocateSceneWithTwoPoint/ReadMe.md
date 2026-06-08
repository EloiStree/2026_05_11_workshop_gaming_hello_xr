
# Exercice en vidéo

Voir l'énoncé vidéo ici :
[![alt text](image-7.png)](https://youtu.be/JzbzqD78Xyg?t=249)

* Savoir charger un objet 3D sur une feuille A4.
* Savoir charger un objet 3D autour de votre écran à partir de la table.
* Savoir charger un niveau à partir de deux points éloignés sur le sol de la pièce.

---

Créons un projet de quarantaine.

Un projet non XR, non Git.

**Q_HelloUnityA4**

![alt text](image.png)

---

La version précédente, simplifiée pour les étudiants de Charleroi 2025 :

[![alt text](image-1.png)](https://github.com/EloiStree/2025_06_05_upm_two_points_quad_loader)

[https://github.com/EloiStree/2025_06_05_upm_two_points_quad_loader](https://github.com/EloiStree/2025_06_05_upm_two_points_quad_loader)


Mon futur code Godot sur le sujet :  
[https://github.com/EloiStree/2025_06_05_gdp_two_points_quad_loader](https://github.com/EloiStree/2025_06_05_gdp_two_points_quad_loader)  
(Car je vais devoir le recoder en Godot par la suite.)   

Même concept, mais avec davantage de rotations et des triangles :
[![Triangle](image-4.png)](https://youtu.be/0k1kqoNi4UM?t=36)    
[![Triangle](image-5.png)](https://youtu.be/0k1kqoNi4UM?t=36)     
[https://youtu.be/0k1kqoNi4UM?t=36](https://youtu.be/0k1kqoNi4UM?t=36)  

---

# Repartons de zéro

Vous pourriez avoir besoin de ceci :   
[Download: Gizmo.obj](direction_gizmo.obj)   

Considérons notre feuille avec un coin en bas à gauche.   
![alt text](image-3.png)
  
Une feuille A4 mesure **210 × 297 mm**.   
Si l'on place les deux points aux extrémités, cela donne :     
**0.3637444**   
(*h = sqrt(210 × 210 + 297 × 297)*)  

---

# Direction

**Exercice :**
[![alt text](image-8.png)](https://youtu.be/JzbzqD78Xyg?t=236)    
[![alt text](image-9.png)](https://youtu.be/JzbzqD78Xyg?t=236)   
[https://www.youtube.com/watch?v=JzbzqD78Xyg&t=18s](https://www.youtube.com/watch?v=JzbzqD78Xyg&t=18s)   
  
**Solution :**
[![alt text](image-10.png)](https://youtu.be/5VOHJKlRwCE?t=28)    
[![alt text](image-11.png)](https://youtu.be/5VOHJKlRwCE?t=140)   
[https://youtu.be/5VOHJKlRwCE?t=28](https://youtu.be/5VOHJKlRwCE?t=28)   

**Code Git :**
[https://github.com/EloiStree/2026_06_07_upm_load_prefab_from_two_points](https://github.com/EloiStree/2026_06_07_upm_load_prefab_from_two_points)

```json
"be.elab.twopointsloader": "https://github.com/EloiStree/2026_06_07_upm_load_prefab_from_two_points.git"
```

------------




# Load from prefab from two points in Unity

> Tool to load scene or prefab from two points from start to end.


Add to `manifest.json` in `Packages`:
```
    "be.elab.twopointsloader": "https://github.com/EloiStree/2026_06_07_upm_load_prefab_from_two_points.git",
```

**Add to an not git project**
```
git clone https://github.com/EloiStree/2026_06_07_upm_load_prefab_from_two_points.git Packages/2026_06_07_upm_load_prefab_from_two_points
```

**Add in a existing git project**
```
git submodule add https://github.com/EloiStree/2026_06_07_upm_load_prefab_from_two_points.git Packages/2026_06_07_upm_load_prefab_from_two_points
```
<img width="1024"  alt="image" src="https://github.com/user-attachments/assets/09ff182e-8343-47e2-9faa-c758b8965468" />


<img width="1024" alt="image" src="https://github.com/user-attachments/assets/0893d855-c10e-4b28-82a3-a8fbbd94832d" />




**Exercice:**   
https://www.youtube.com/watch?v=JzbzqD78Xyg&t=18s     


**Step By step:**   
https://github.com/EloiStree/2026_06_07_upm_load_prefab_from_two_points  


**Solution:**   
https://youtu.be/5VOHJKlRwCE?t=28   

---------------

# Video 

## Step by step

- [ ] Énoncé https://youtu.be/ZpomlkT-XaQ?t=1
- [ ] Solution https://youtu.be/ZpomlkT-XaQ?t=83
- [ ] Créer un projet de quarantaine https://youtu.be/ZpomlkT-XaQ?t=114
- [ ] Créer le package Git https://youtu.be/ZpomlkT-XaQ?t=232
- [ ] Créer un package.json https://youtu.be/ZpomlkT-XaQ?t=273
- [ ] Git clone et submodules https://youtu.be/ZpomlkT-XaQ?t=399
- [ ] Ajoutons-le dans le projet de quarantaine https://youtu.be/ZpomlkT-XaQ?t=473
- [ ] Nettoyons le package.json https://youtu.be/ZpomlkT-XaQ?t=534
- [ ] Créons l'assembly https://youtu.be/ZpomlkT-XaQ?t=575
- [ ] Créons une scène de test https://youtu.be/ZpomlkT-XaQ?t=744
- [ ] Ajoutons un gizmo https://youtu.be/ZpomlkT-XaQ?t=847
- [ ] Créons un prefab A4 pour notre objet https://youtu.be/ZpomlkT-XaQ?t=936
- [ ] Ajoutons deux points de charge pour les tests https://youtu.be/ZpomlkT-XaQ?t=1097
- [ ] Git pull et push https://youtu.be/ZpomlkT-XaQ?t=1159
- [ ] Aller dans le projet Git XR https://youtu.be/ZpomlkT-XaQ?t=1223
- [ ] Ajouter le package dans le Package Manager https://youtu.be/ZpomlkT-XaQ?t=1252
- [ ] Importer la démo https://youtu.be/ZpomlkT-XaQ?t=1291
- [ ] Allons voir le manifest https://youtu.be/ZpomlkT-XaQ?t=1329
- [ ] PackageCache https://youtu.be/ZpomlkT-XaQ?t=1405
- [ ] Créons notre script d'input https://youtu.be/ZpomlkT-XaQ?t=1473
- [ ] performed CallbackContext https://youtu.be/ZpomlkT-XaQ?t=1533
- [ ] InputActionReference https://youtu.be/ZpomlkT-XaQ?t=1614
- [ ] UnityEvent https://youtu.be/ZpomlkT-XaQ?t=1689
- [ ] OnChange https://youtu.be/ZpomlkT-XaQ?t=1720
- [ ] Créer l'InputAction https://youtu.be/ZpomlkT-XaQ?t=1806
- [ ] Configurer les inputs Start et Stop Point https://youtu.be/ZpomlkT-XaQ?t=1842
- [ ] Créons le script CreatePrefab https://youtu.be/ZpomlkT-XaQ?t=1953
- [ ] Un prefab et une méthode d'entrée https://youtu.be/ZpomlkT-XaQ?t=2041
- [ ] GameObject.Instantiate https://youtu.be/ZpomlkT-XaQ?t=2071
- [ ] Quaternion.identity https://youtu.be/ZpomlkT-XaQ?t=2111
- [ ] Rotation sur l'axe Y https://youtu.be/ZpomlkT-XaQ?t=2136
- [ ] UnityEvent<V3,V3> https://youtu.be/ZpomlkT-XaQ?t=2241
- [ ] Start, End et Cursor https://youtu.be/ZpomlkT-XaQ?t=2460
- [ ] [ContextMenu] https://youtu.be/ZpomlkT-XaQ?t=2499
- [ ] Couleur rouge Unlit https://youtu.be/ZpomlkT-XaQ?t=2564
- [ ] Translate https://youtu.be/ZpomlkT-XaQ?t=2627
- [ ] Aplatir l'axe Y https://youtu.be/ZpomlkT-XaQ?t=2739
- [ ] Magnitude https://youtu.be/ZpomlkT-XaQ?t=2760
- [ ] Rappel de l'exercice https://youtu.be/ZpomlkT-XaQ?t=2825
- [ ] Distance requise et seuil (threshold) https://youtu.be/ZpomlkT-XaQ?t=2883
- [ ] Delta et Abs https://youtu.be/ZpomlkT-XaQ?t=2940
- [ ] Threshold https://youtu.be/ZpomlkT-XaQ?t=2976
- [ ] Testons notre code avec deux points https://youtu.be/ZpomlkT-XaQ?t=3031
- [ ] Vector3.forward https://youtu.be/ZpomlkT-XaQ?t=3156
- [ ] Vector3.SignedAngle() https://youtu.be/ZpomlkT-XaQ?t=3230
- [ ] Ça fonctionne ;) https://youtu.be/ZpomlkT-XaQ?t=3347
- [ ] Ajouter l'input à notre code https://youtu.be/ZpomlkT-XaQ?t=3397
- [ ] Ajoutons un Set Point en deux étapes https://youtu.be/ZpomlkT-XaQ?t=3500
- [ ] Faire suivre le curseur à la main droite https://youtu.be/ZpomlkT-XaQ?t=3721
- [ ] Git add, pull, push et passage en XR https://youtu.be/ZpomlkT-XaQ?t=3855
- [ ] Mise à jour depuis le Package Manager https://youtu.be/ZpomlkT-XaQ?t=3914
- [ ] Reconstruisons la scène https://youtu.be/ZpomlkT-XaQ?t=3978
- [ ] Ajoutons la caméra, le passthrough et les contrôleurs https://youtu.be/ZpomlkT-XaQ?t=4011
- [ ] Ajoutons le curseur à la manette https://youtu.be/ZpomlkT-XaQ?t=4055
- [ ] Écoutons les inputs du Quest pour les actions https://youtu.be/ZpomlkT-XaQ?t=4112
- [ ] Vérifions que les inputs fonctionnent pour les points https://youtu.be/ZpomlkT-XaQ?t=4295
- [ ] Copions les inputs dans la boîte à outils https://youtu.be/ZpomlkT-XaQ?t=4337
- [ ] Un petit safeguard https://youtu.be/ZpomlkT-XaQ?t=4534
- [ ] La version corrigée fonctionne-t-elle ? https://youtu.be/ZpomlkT-XaQ?t=4648
- [ ] `[System.Serializable]` https://youtu.be/ZpomlkT-XaQ?t=4684
- [ ] ScriptableObject https://youtu.be/ZpomlkT-XaQ?t=4802
- [ ] Inspector vs ScriptableObject https://youtu.be/ZpomlkT-XaQ?t=4906
- [ ] Déplacer un fichier https://youtu.be/ZpomlkT-XaQ?t=4913
- [ ] Refactorisation du code https://youtu.be/ZpomlkT-XaQ?t=4957
- [ ] Préparer les méthodes pour les variables privées https://youtu.be/ZpomlkT-XaQ?t=5020
- [ ] foreach sur les prefabs https://youtu.be/ZpomlkT-XaQ?t=5077
- [ ] internal vs public https://youtu.be/ZpomlkT-XaQ?t=5204
- [ ] Créer un fichier ScriptableObject https://youtu.be/ZpomlkT-XaQ?t=5246
- [ ] Ajoutons notre premier élément https://youtu.be/ZpomlkT-XaQ?t=5272
- [ ] Ajoutons un objet pour les 297 mm de la feuille https://youtu.be/ZpomlkT-XaQ?t=5322
- [ ] N'oubliez pas de donner votre ScriptableObject au script dans l'inspecteur https://youtu.be/ZpomlkT-XaQ?t=5388
- [ ] Créons un prefab en drag-and-drop https://youtu.be/ZpomlkT-XaQ?t=5436
- [ ] Add, commit, pull, push et test https://youtu.be/ZpomlkT-XaQ?t=5487
- [ ] Ajoutons une table IKEA de 55 cm https://youtu.be/ZpomlkT-XaQ?t=5610
- [ ] Allons chercher le GLB d'Open Brush https://youtu.be/ZpomlkT-XaQ?t=5683
- [ ] Dessinez les mesures https://youtu.be/ZpomlkT-XaQ?t=5704
- [ ] Export Open Brush https://youtu.be/ZpomlkT-XaQ?t=5761
- [ ] GLB vers OBJ https://youtu.be/ZpomlkT-XaQ?t=5792
- [ ] Vérification dans Blender https://youtu.be/ZpomlkT-XaQ?t=5820
- [ ] Mettre le mesh de la pièce dans la scène https://youtu.be/ZpomlkT-XaQ?t=5891
- [ ] Un matériau Unlit rouge et un prefab https://youtu.be/ZpomlkT-XaQ?t=5919
- [ ] Configuration de la room pour la table 120x80 https://youtu.be/ZpomlkT-XaQ?t=6006
- [ ] Essayons d'ajouter le tracé de la room https://youtu.be/ZpomlkT-XaQ?t=6146
- [ ] Fossify https://youtu.be/ZpomlkT-XaQ?t=6224
- [ ] Vérification https://youtu.be/ZpomlkT-XaQ?t=6409
- [ ] Démo finale https://youtu.be/ZpomlkT-XaQ?t=6519

