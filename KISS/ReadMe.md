
# KISS

En espérant que cette version de l'exercice soit plus réalisable en une matinée.

**Solution :**   
[https://github.com/EloiStree/2026_06_07_upm_load_prefab_from_two_points/tree/main/Runtime](https://github.com/EloiStree/2026_06_07_upm_load_prefab_from_two_points/tree/main/Runtime)

Il nous faut deux points (verts) que l'on déplace à l'aide d'un curseur (rouge) :

![alt text](image.png)

Le point rouge, lui, suivra l'arrière de la manette.

[![alt text](image-1.png)](https://youtu.be/ZpomlkT-XaQ?t=4068)
[![alt text](image-2.png)](https://youtu.be/ZpomlkT-XaQ?t=4068)

Comme notre outil ne connaît pas encore le point à suivre, qui sera placé par le designer sur la manette du jeu, nous pouvons créer un script pour suivre ce futur point.

```csharp
public class TwoPointsLoad_FollowTarget : MonoBehaviour
{
    public Transform whatToFollow;
    public Transform whatToMove;

    private void Update()
    {
        if (whatToFollow != null && whatToMove != null)
        {
            whatToMove.position = whatToFollow.position;
            whatToMove.rotation = whatToFollow.rotation;
        }
    }
}
```

Créons un script pour écouter un bouton choisi par le designer avec l'Input System de Unity.

Cela nous servira à placer les points.

```csharp
public class TwoPointsLoad_InputButton : MonoBehaviour
{

    public InputActionReference m_inputAction;
    public UnityEvent<bool> m_onChanged;
    public UnityEvent m_onDown;
    public UnityEvent m_onUp;

    // Pour le débogage
    public bool m_isPressed;

    void OnEnable()
    {
        m_inputAction.action.Enable();
        m_inputAction.action.performed += ctx => Context(ctx);
        m_inputAction.action.started += ctx => Context(ctx);
        m_inputAction.action.canceled += ctx => Context(ctx);
    }

    private void OnDisable()
    {
        m_inputAction.action.Disable();
        m_inputAction.action.performed -= ctx => Context(ctx);
        m_inputAction.action.started -= ctx => Context(ctx);
        m_inputAction.action.canceled -= ctx => Context(ctx);
    }

    void Context(InputAction.CallbackContext ctx)
    {
        bool isPressed = ctx.ReadValue<float>() > 0.5f;

        // L'état du bouton a-t-il changé ?
        if (isPressed != m_isPressed)
        {
            m_isPressed = isPressed;
            m_onChanged.Invoke(isPressed);

            if (m_isPressed)
            {
                m_onDown.Invoke();
            }
            else
            {
                m_onUp.Invoke();
            }
        }
    }
}
```

Il nous faut maintenant un script qui permette de placer les deux points là où l'utilisateur le demande, grâce à un curseur qui sert d'abstraction de position.

```csharp
using UnityEngine;
using UnityEngine.Events;

public class TwoPointsLoad_EmitStartEndPoints : MonoBehaviour
{
    [SerializeField] private UnityEvent<Vector3, Vector3> m_onStartEndPointEmitted;

    [SerializeField] private Transform m_startPoint;
    [SerializeField] private Transform m_endPoint;
    [SerializeField] private Transform m_cursorToSetPoints;

    [ContextMenu("Emit Current Points")]
    public void EmitCurrentPoint()
    {
        m_onStartEndPointEmitted?.Invoke(m_startPoint.position, m_endPoint.position);
    }

    public void SetStartPointToCursor()
    {
        m_startPoint.transform.position = m_cursorToSetPoints.position;
    }

    public void SetEndPointToCursor()
    {
        m_endPoint.transform.position = m_cursorToSetPoints.position;
    }
}
```

Nous pouvons maintenant écouter les entrées de la manette ainsi que la position de son curseur.

Avec le script précédent, nous pouvons émettre deux `Vector3` comme requête de chargement.

Dans la vidéo, je crée un prefab en fonction de la distance et je le place.

Mais nous n'avons qu'une demi-journée.

Je vous propose donc de simplement déplacer une scène préconstruite.

```csharp
using UnityEngine;
using UnityEngine.Events;

namespace Eloi.TwoPointsLoader
{
    public class TwoPointsLoad_MoveAtStartEndPoint : MonoBehaviour
    {
        [SerializeField] private Transform m_whatToMove;

        public void MoveTheSceneFrom(Vector3 worldPointStart, Vector3 worldPointEnd)
        {
            Vector3 start = worldPointStart;
            Vector3 end = worldPointEnd;

            Vector3 endFlat = end;
            endFlat.y = start.y;

            m_whatToMove.transform.position = Vector3.zero;
            m_whatToMove.transform.rotation = Quaternion.identity;

            Vector3 unityForward = Vector3.forward;
            Vector3 startEndDirection = endFlat - start;

            float rotationToApply =
                Vector3.SignedAngle(unityForward, startEndDirection, Vector3.up) - 90f;

            m_whatToMove.transform.Rotate(Vector3.up, rotationToApply);

            Vector3 directionStart = worldPointStart;
            m_whatToMove.transform.position = directionStart;
        }
    }
}
```

Pour comprendre ce que j'ai fait ici, regardons cet exemple :

[https://youtu.be/JzbzqD78Xyg?t=490](https://youtu.be/JzbzqD78Xyg?t=490)

On a une ligne :

![alt text](image-3.png)

On écrase le Y de la destination :

![alt text](image-4.png)

Cela nous donne un vecteur plat sur le plan XZ, plus facile à mesurer :

![alt text](image-5.png)

Cela nous donne un axe Y au point de départ :

![alt text](image-6.png)

Et un axe Z (forward) au point de départ :

![alt text](image-7.png)

Si on compare cette direction avec le forward de Unity, cela nous donne un angle signé.

Notre but est donc de déplacer notre prefab :

* vers le point de départ ;
* dans la direction du forward.

Pour que cela soit possible, il faut également construire correctement notre prefab.

[https://youtu.be/ZpomlkT-XaQ?t=6164](https://youtu.be/ZpomlkT-XaQ?t=6164)

[https://youtu.be/ZpomlkT-XaQ?t=6204](https://youtu.be/ZpomlkT-XaQ?t=6204)

Dans le cas de ma pièce, par exemple, le forward est ici :

![alt text](image-8.png)

Du coup, nous pouvons placer notre pivot :

[![alt text](image-9.png)](https://youtu.be/ZpomlkT-XaQ?t=6269)

[https://youtu.be/ZpomlkT-XaQ?t=6269](https://youtu.be/ZpomlkT-XaQ?t=6269)

Et nous plaçons ensuite le mesh de la pièce dans le point d'ancrage que nous venons de créer :

![alt text](image-10.png)

[https://youtu.be/ZpomlkT-XaQ?t=6282](https://youtu.be/ZpomlkT-XaQ?t=6282)

---

# Récapitulons

Le point sur la manette bouge avec la manette et notre curseur le suit.

Le designer demande d'ajouter le point de départ.

Puis il demande d'ajouter le point de fin.

Une fois le point de fin défini, le designer émet les deux points pour demander un repositionnement.

```csharp
// Le designer fournit le niveau à repositionner.
[SerializeField] private Transform m_whatToMove;

// Appelé lorsque le designer fournit les deux points.
public void MoveTheSceneFrom(
    Vector3 worldPointStart,
    Vector3 worldPointEnd)
{
    Vector3 start = worldPointStart;
    Vector3 end = worldPointEnd;

    // On stocke le point de fin de la ligne.
    Vector3 endFlat = end;

    // On l'aplatit à la hauteur du point de départ.
    endFlat.y = start.y;

    // On prépare le niveau en le remettant à l'origine.
    m_whatToMove.transform.position = Vector3.zero;
    m_whatToMove.transform.rotation = Quaternion.identity;

    // Nous devons calculer l'angle de rotation.
    Vector3 unityForward = Vector3.forward;

    // Destination moins origine nous donne une direction.
    Vector3 startEndDirection = endFlat - start;

    // On calcule l'angle entre le forward de Unity (Z)
    // et la direction calculée.
    float rotationToApply =
        Vector3.SignedAngle(unityForward, startEndDirection, Vector3.up) - 90f;

    // Comme nous utilisons mentalement l'axe X comme référence
    // lors de la construction du prefab, nous devons compenser
    // avec un décalage de 90 degrés.
    m_whatToMove.transform.Rotate(Vector3.up, rotationToApply);

    // Une fois orienté correctement,
    // nous déplaçons le niveau au point de départ.
    m_whatToMove.transform.position = worldPointStart;

    // Le niveau est maintenant placé au bon endroit.
}
```


-----------------------------



# Open Brush

* Ouvrir Open Brush.
* Utiliser l’option **ligne droite**.

  * Dessiner des triangles sur le sol et les murs.
  * Dessiner des angles dans les coins de la pièce.
  * Trouver deux points qui ne changeront pas, les plus éloignés possible dans la pièce.

    * Y dessiner une ligne.
  * Exporter le modèle 3D avec Open Brush.
  * Récupérer le modèle 3D sur votre ordinateur.
  * L’ajouter au projet.
  * Le placer dans une ancre et en faire un prefab.
  * Ajouter un matériau **Unlit Double-Sided** pour bien le voir.

    * Ajouter du décor et des colliders invisibles.
* Essayer de le charger sans la VR.
* Essayer de l’ajouter au projet et de le charger en VR.

# Inputs du Quest

Choisissez votre bonheur ici
et ajoutez-le à la scène :

[2026_04_02_unity_input_and_toys](https://github.com/EloiStree/2026_04_02_unity_input_and_toys?utm_source=chatgpt.com)

Puis pratiquez les entrées suivantes :

* Boutons (*Buttons*)
* Axes (*Axis*)
* Joystick

Si vous êtes masochiste :

[2025_02_18_upm_outer_wilds_ship](https://github.com/EloiStree/2025_02_18_upm_outer_wilds_ship?utm_source=chatgpt.com)

# Room Mesh

On peut ajouter à votre scène VR le maillage (*mesh*) scanné par l’utilisateur à l’aide du bloc Meta.
[<img width="541" height="353" alt="image" src="https://github.com/user-attachments/assets/5b5fa780-6279-4cf1-ae75-24d534680837" />](https://github.com/EloiStree/2026_05_11_workshop_gaming_hello_xr/blob/main/3D/DevRoom.obj)  
[Download 3D](https://github.com/EloiStree/2026_05_11_workshop_gaming_hello_xr/blob/main/3D/DevRoom.obj)  
  
