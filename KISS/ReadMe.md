
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












--------------
# Version Godot

Faire suivre le bas de la manette par le curseur de placement.
```gdscript
class_name SELoadFollowNode3D
extends Node3D

@export var what_to_follow:Node3D
@export var what_to_move:Node3D

func _process(delta: float) -> void:
	if what_to_follow and what_to_move:
		what_to_move.global_position = what_to_follow.global_position
		what_to_move.global_rotation = what_to_follow.global_rotation
```

Écoutons les entrées de la manette.
```gdscript
class_name SELoadXrButtonInputChanged
extends Node

signal on_button_state_changed(is_on:bool)
signal on_button_down()
signal on_button_up()

@export var controller_to_observe: XRController3D
@export var button_name_press_release:String = "primary_click"

@export var button_state:bool = 0

func _ready() -> void:
	if controller_to_observe:
		controller_to_observe.button_pressed.connect(_pressed)
		controller_to_observe.button_released.connect(_released)

func _pressed(name:String):
	#print("Pressed XR:", name)
	if button_name_press_release == name:
		#print("Pressed XR FOUND:", name)
		on_button_down.emit()
		if not button_state:
			on_button_state_changed.emit(true)

func _released(name:String):
	#print("Released XR:", name)
	if button_name_press_release == name:
		#print("Released XR FOUND:", name)
		on_button_up.emit()
		if button_state:
			on_button_state_changed.emit(false)
```

On replace les points de départ (*start*) et d'arrivée (*end*) à partir du curseur.
```gdscript
class_name SELoadSetAndEmitStartEndPoints
extends Node3D

signal on_start_end_points_emitted(start_point:Vector3,end_point:Vector3)

@export var start_anchor:Node3D
@export var end_anchor:Node3D
@export var cursor_anchor:Node3D

func emit_current_points_in_signal():
	var start := start_anchor.global_position
	var end := end_anchor.global_position
	on_start_end_points_emitted.emit(start,end)

func emit_zero_origine_points_in_signal():
	var start := Vector3.ZERO
	var end := Vector3.RIGHT * 0.21
	on_start_end_points_emitted.emit(start,end)

func set_start_anchor_with_cursor():
	start_anchor.position = cursor_anchor.position

func set_end_anchor_with_cursor():
	end_anchor.position = cursor_anchor.position

func set_cursor_global_position(global_position:Vector3):
	cursor_anchor.position = global_position

func set_random_positions_around_1_meter():
	start_anchor.global_position = Vector3(randf(),randf(),randf())
	end_anchor.global_position = Vector3(randf(),randf(),randf())
	cursor_anchor.global_position = (end_anchor.position - start_anchor.position) / 2.0
```

Rappelons que le projet utilise OpenXR.
```gdscript
class_name SELoadSetupXR
extends Node

var xr_interface: XRInterface

func _ready():
	xr_interface = XRServer.find_interface("OpenXR")
	if xr_interface and xr_interface.is_initialized():
		print("OpenXR initialized successfully")

		# Turn off v-sync!
		DisplayServer.window_set_vsync_mode(DisplayServer.VSYNC_DISABLED)

		# Change our main viewport to output to the HMD
		get_viewport().use_xr = true
	else:
		print("OpenXR not initialized, please check if your headset is connected")
```

On utilise les deux vecteurs 3D générés par les scripts précédents.
```gdscript
class_name SELoadRelocateNodeToStartEnd
extends Node3D

@export var what_to_relocate:Node3D

func relocate_node_from_start_end_points(start:Vector3,end:Vector3):
	if what_to_relocate == null:
		return

	what_to_relocate.global_position = Vector3.ZERO
	what_to_relocate.global_rotation = Vector3.ZERO

	start.z *= -1.0
	end.z *= -1.0

	var direction :Vector3 = end - start
	var direction_flat:Vector3 = Vector3(direction.x, 0, direction.z)
	var angle :float = Vector3(1,0,0).signed_angle_to(direction_flat, Vector3.UP)

	what_to_relocate.rotate_y(-angle)

	start.z *= -1
	what_to_relocate.global_position = start
```

Et voilà, nous avons un outil permettant de repositionner un niveau avec Godot.   
Le code Godot est fonctionnel.    
Il reste à configurer le projet, mais l'idée est là.   
   

  
