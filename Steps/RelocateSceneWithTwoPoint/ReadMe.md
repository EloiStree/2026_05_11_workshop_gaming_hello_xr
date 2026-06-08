
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
- [00:00:01](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1s) Énoncé
- [00:01:23](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=83s) Solution
- [00:01:54](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=114s) Créer un projet de quarantaine
- [00:03:52](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=232s) Créer le package Git
- [00:04:33](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=273s) Créer un package.json
- [00:06:39](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=399s) Git clone et submodules
- [00:07:53](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=473s) Ajoutons-le dans le projet de quarantaine
- [00:08:54](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=534s) Nettoyons le package.json
- [00:09:35](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=575s) Créons l'assembly
- [00:12:24](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=744s) Créons une scène de test
- [00:14:07](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=847s) Ajoutons un gizmo
- [00:15:36](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=936s) Créons un prefab A4 pour notre objet
- [00:18:17](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1097s) Ajoutons deux points de charge pour les tests
- [00:19:19](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1159s) Git pull et push
- [00:20:23](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1223s) Aller dans le projet Git XR
- [00:20:52](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1252s) Ajouter le package dans le Package Manager
- [00:21:31](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1291s) Importer la démo
- [00:22:09](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1329s) Allons voir le manifest
- [00:23:25](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1405s) PackageCache
- [00:24:33](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1473s) Créons notre script d'input
- [00:25:33](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1533s) performed CallbackContext
- [00:26:54](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1614s) InputActionReference
- [00:28:09](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1689s) UnityEvent
- [00:28:40](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1720s) OnChange
- [00:30:06](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1806s) Créer l'InputAction
- [00:30:42](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1842s) Configurer les inputs Start et Stop Point
- [00:32:33](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=1953s) Créons le script CreatePrefab
- [00:34:01](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2041s) Un prefab et une méthode d'entrée
- [00:34:31](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2071s) GameObject.Instantiate
- [00:35:11](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2111s) Quaternion.identity
- [00:35:36](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2136s) Rotation sur l'axe Y
- [00:37:21](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2241s) UnityEvent V3,V3
- [00:41:00](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2460s) Start, End et Cursor
- [00:41:39](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2499s) ContextMenu
- [00:42:44](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2564s) Couleur rouge Unlit
- [00:43:47](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2627s) Translate
- [00:45:39](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2739s) Aplatir l'axe Y
- [00:46:00](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2760s) Magnitude
- [00:47:05](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2825s) Rappel de l'exercice
- [00:48:03](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2883s) Distance requise et seuil (threshold)
- [00:49:00](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2940s) Delta et Abs
- [00:49:36](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=2976s) Threshold
- [00:50:31](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=3031s) Testons notre code avec deux points
- [00:52:36](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=3156s) Vector3.forward
- [00:53:50](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=3230s) Vector3.SignedAngle()
- [00:55:47](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=3347s) Ça fonctionne ;)
- [00:56:37](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=3397s) Ajouter l'input à notre code
- [00:58:20](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=3500s) Ajoutons un Set Point en deux étapes
- [01:02:01](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=3721s) Faire suivre le curseur à la main droite
- [01:04:15](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=3855s) Git add, pull, push et passage en XR
- [01:05:14](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=3914s) Mise à jour depuis le Package Manager
- [01:06:18](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=3978s) Reconstruisons la scène
- [01:06:51](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=4011s) Ajoutons la caméra, le passthrough et les contrôleurs
- [01:07:35](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=4055s) Ajoutons le curseur à la manette
- [01:08:32](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=4112s) Écoutons les inputs du Quest pour les actions
- [01:11:35](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=4295s) Vérifions que les inputs fonctionnent pour les points
- [01:12:17](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=4337s) Copions les inputs dans la boîte à outils
- [01:15:34](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=4534s) Un petit safeguard
- [01:17:28](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=4648s) La version corrigée fonctionne-t-elle ?
- [01:18:04](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=4684s) System.Serializable
- [01:20:02](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=4802s) ScriptableObject
- [01:21:46](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=4906s) Inspector vs ScriptableObject
- [01:21:53](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=4913s) Déplacer un fichier
- [01:22:37](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=4957s) Refactorisation du code
- [01:23:40](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5020s) Préparer les méthodes pour les variables privées
- [01:24:37](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5077s) foreach sur les prefabs
- [01:26:44](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5204s) internal vs public
- [01:27:26](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5246s) Créer un fichier ScriptableObject
- [01:27:52](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5272s) Ajoutons notre premier élément
- [01:28:42](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5322s) Ajoutons un objet pour les 297 mm de la feuille
- [01:29:48](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5388s) N'oubliez pas de donner votre ScriptableObject au script dans l'inspecteur
- [01:30:36](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5436s) Créons un prefab en drag-and-drop
- [01:31:27](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5487s) Add, commit, pull, push et test
- [01:33:30](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5610s) Ajoutons une table IKEA de 55 cm
- [01:34:43](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5683s) Allons chercher le GLB d'Open Brush
- [01:35:04](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5704s) Dessinez les mesures
- [01:36:01](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5761s) Export Open Brush
- [01:36:32](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5792s) GLB vers OBJ
- [01:37:00](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5820s) Vérification dans Blender
- [01:38:11](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5891s) Mettre le mesh de la pièce dans la scène
- [01:38:39](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=5919s) Un matériau Unlit rouge et un prefab
- [01:40:06](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=6006s) Configuration de la room pour la table 120x80
- [01:42:26](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=6146s) Essayons d'ajouter le tracé de la room
- [01:43:44](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=6224s) Fossify
- [01:46:49](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=6409s) Vérification
- [01:48:39](https://www.youtube.com/watch?v=ZpomlkT-XaQ&t=6519s) Démo finale
