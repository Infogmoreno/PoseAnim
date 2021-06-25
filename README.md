# Pose Animator

Pose Animator takes a 2D vector illustration and animates its containing curves in real-time based on the recognition result from PoseNet and FaceMesh. It borrows the idea of skeleton-based animation from computer graphics and applies it to vector characters.

This is running in the browser in realtime using [TensorFlow.js](https://www.tensorflow.org/js). Check out more cool TF.js demos [here](https://www.tensorflow.org/js/demos).

*This is not an officially supported Google product.*

<img src="/resources/gifs/avatar-new-1.gif?raw=true" alt="cameraDemo" style="width: 250px;"/>

<img src="/resources/gifs/avatar-new-full-body.gif?raw=true" alt="cameraDemo" style="width: 250px;"/>

In skeletal animation a character is represented in two parts:
1. a surface used to draw the character, and 
1. a hierarchical set of interconnected bones used to animate the surface. 

In Pose Animator, the surface is defined by the 2D vector paths in the input SVG files. For the bone structure, Pose Animator provides a predefined rig (bone hierarchy) representation, designed based on the keypoints from PoseNet and FaceMesh. This bone structure’s initial pose is specified in the input SVG file, along with the character illustration, while the real time bone positions are updated by the recognition result from ML models.

<img src="https://firebasestorage.googleapis.com/v0/b/pose-animator-demo.appspot.com/o/ml-keypoints.png?alt=media" style="width:250px;"/>

<img src="/resources/gifs/avatar-new-bezier-1.gif?raw=true" alt="cameraDemo" style="width: 250px;"/>

// TODO: Add blog post link.
For more details on its technical design please check out this blog post.

### Demo 1: [Camera feed](https://pose-animator-demo.firebaseapp.com/camera.html)

The camera demo animates a 2D avatar in real-time from a webcam video stream.


### Demo 2: [Static image](https://pose-animator-demo.firebaseapp.com/static_image.html)

The static image demo shows the avatar positioned from a single image.

## Build And Run

Install dependencies and prepare the build directory:

```sh
yarn
```

To watch files for changes, and launch a dev server:

```sh
yarn watch
```

## Platform support

Demos are supported on Desktop Chrome and iOS Safari.

It should also run on Chrome on Android and potentially more Android mobile browsers though support has not been tested yet.

# Animate your own design

1. Download the [sample skeleton SVG here](/resources/samples/skeleton.svg).
1. Create a new file in your vector graphics editor of choice. Copy the group named ‘skeleton’ from the above file into your working file. Note: 
	* Do not add, remove or rename the joints (circles) in this group. Pose Animator relies on these named paths to read the skeleton’s initial position. Missing joints will cause errors.
	* However you can move the joints around to embed them into your illustration. See step 4.
1. Create a new group and name it ‘illustration’, next to the ‘skeleton’ group. This is the group where you can put all the paths for your illustration.
    * Flatten all subgroups so that ‘illustration’ only contains path elements.
    * Composite paths are not supported at the moment.
    * The working file structure should look like this:
	```
        [Layer 1]
        |---- skeleton
        |---- illustration
              |---- path 1
              |---- path 2
              |---- path 3
	```
1. Embed the sample skeleton in ‘skeleton’ group into your illustration by moving the joints around.
1. Export the file as an SVG file.
1. Open [Pose Animator camera demo](https://pose-animator-demo.firebaseapp.com/camera.html). Once everything loads, drop your SVG file into the browser tab. You should be able to see it come to life :D


Traducción_ instrucciones:
Anima tu propio diseño
Descargue el esqueleto SVG de muestra.
Cree un nuevo archivo en el editor de gráficos vectoriales de su elección. Copie el grupo llamado ‘esqueleto’ del archivo anterior en su archivo de trabajo. Nota:

No agregue, elimine ni cambie el nombre de las uniones (círculos) en este grupo. Pose Animator se basa en estos caminos nombrados para leer la posición inicial del esqueleto. La falta de articulaciones provocará errores.
Sin embargo, puede mover las articulaciones para incrustarlas en su ilustración. Ver paso 4.
Cree un nuevo grupo y asígnele el nombre ‘ilustración’, junto al grupo ‘esqueleto’. Este es el grupo donde puede poner todos los caminos para su ilustración.
Acoplar todos los subgrupos para que ‘ilustración’ solo contenga elementos de ruta.
Las rutas compuestas no son compatibles en este momento.
La estructura del archivo de trabajo debería verse así:

[Layer 1]
|---- skeleton
|---- illustration
|---- path 1
|---- path 2
|---- path 3

Incruste el esqueleto de muestra en el grupo ‘esqueleto’ en su ilustración moviendo las articulaciones.

Exporte el archivo como un archivo SVG.

Abra la demo de la cámara Pose Animator. Una vez que todo se carga, suelte su archivo SVG en la pestaña del navegador. Deberías poder verlo cobrar vida: D
