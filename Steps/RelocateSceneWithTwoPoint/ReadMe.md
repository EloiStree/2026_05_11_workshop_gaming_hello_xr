
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




# Step by step

To Do
