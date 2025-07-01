<h1 align="center"> Learning Three JS</h1>
Learning THREE.JS and documenting whatever I learned.

---

What is THREE.JS and what it is used for ?

Three.js is a JavaScript **library** that simplifies the creation of **3D graphics** within web browsers using **WebGL**. It allows developers to build and display interactive 3D scenes, animations, and games without needing to write extensive **low-level WebGL code**. Essentially, Three.js acts as a **bridge** between JavaScript and WebGL, making 3D graphics on the web more accessible and easier to manage. 

--- 

What is WebGL?

WebGL (Web Graphics Library) is a **JavaScript API** that allows web browsers to render 2D and 3D graphics without the need for **browser plugins**. It leverages the **computer's graphics processing unit (GPU)** to accelerate the rendering of complex visuals, enabling high-performance interactive graphics on the web. 

---

~Let's get start with THREE.JS

Step-1 : Create a folder, and within the folder Create two files `index.html` and `index.js`.
Step-2 : Paste the code below, don't worry I will explain everything to you, just copy-paste for now.

> **Copy and paste this code into your HTML file**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3D-Square</title>
</head>
<body>
    <canvas id="wbgl"></canvas>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.js"></script>
    <script src="./index.js"></script>
</body>
</html>
```

>> **Copy and paste this code into your Javascript file**

```javascript
const scene = new THREE.Scene();

const geometry = new THREE.BoxGeometry(2,2,2);
const material = new THREE.MeshBasicMaterial({color : "red"});

const box = new THREE.Mesh(geometry,material);
scene.add(box);


const size = {
    width : 1580,
    height : 710
}
const camera = new THREE.PerspectiveCamera(75,size.width/size.height);
camera.position.z = 4;
scene.add(camera);

const target = document.querySelector("#wbgl");
const renderer = new THREE.WebGLRenderer({canvas : target});
renderer.setSize(size.width,size.height);
renderer.render(scene,camera);
```
> Now **Run** the `index.html` file, you can see the folloing image as output :

![Screenshot 2025-07-01 112845](https://github.com/user-attachments/assets/91d7a16c-0269-44ab-bb1c-9f3890722ccd)

---


Let's Understand, How it works ?

Firstly, In **three.js**, we are making a 3D-movie.

🎬 Key Components to Create Any 3D Movie (Using Three.js or Any 3D Engine)
To build any 3D experience, you need **4** essential components:

`Scene 🏞️` : 
The 3D space or virtual world where everything exists.

> Think of it as an empty stage waiting to be filled.

`Objects 📦` : 
The physical or visual elements inside the scene — like cubes, models, lights, etc.

> These are the “actors” of your 3D movie.

`Camera 🎥` : 
Represents the viewer’s perspective. It decides what part of the scene the audience sees and from what angle.

>It's like the eye of the viewer or the lens of the camera.

`Renderer (or Director) 🎬` : 
The engine that renders the final output by converting the scene and camera view into pixels on your screen.

> It's the “director” that brings everything together and shows it to the audience.

## You can take Notes from here : 

![Screenshot 2025-07-01 115404](https://github.com/user-attachments/assets/f087a11b-111f-412a-8318-fa4ac1dd0ae6)


Understanding `HTML` - code file. 
It's just a HTML boilerplate code having a **canvas** with **id="wbgl"**, to let the user view some part of our 3D movie through camera.

---


# Scene vs Canvas
Scene - The 3D space of our website.

Canvas - The part of 3D space (or Scene), viewed by the camera.

---


Understanding `JavaScript` - code file.

To make any 3D movie (code Implementation mindset) : Follow the steps below :

1. Create the **Scene** :
```javascript
const scene = new THREE.Scene(); // Created a 3D Space.
```
2. Create the **Object** :
```javascript
const geometry = new THREE.BoxGeometry(2,2,2);
//BoxGeometry is a prebuilt method in three.js and is used to create a 3D rectangular box (or cuboid) with specified dimensions (width, height, and depth).
const material = new THREE.BasicMeshMaterial({ color : "red"});
// MeshBasicMaterial another pre-built method is used to create simple, flat-shaded objects that are not affected by lighting or shading.

const box = new THREE.Mesh(geometry,material);
// Joining the geometry and material and create the object
scene.add(box);
// Adding our object to the scene.
```   

Objects in three-js are made through the combination of two components - `Geometry` and `Material`. 

3. **Define and palce the camera** :

```javascript
// Defining the size of the camera-view like how much area can be viewed of the 3D space.
const size = {
    width : 1580,
    height : 710
}
const camera = new THREE.PerspectiveCamera(85,size.width/size.height);
// PerspectiveCamera another pre-built method which is used to mimic how the human eye sees the world, creating a sense of depth and perspective in 3D scenes
camera.position.z = 4;
scene.add(camera); // Adding camera to the Scene.
```

4. **Define the Rederer** :
```javascript
// Firstly, Understand this - We need a canvas to view some part of our 3D space, so we have selected the cnavas.
const target = document.querySelector(".wbgl");

const renderer = new THREE.WebGLRenderer({canvas : target});
// WebGLRenderer another pre-built method is used to render 3D scenes onto a webpage using the WebGL API. It acts as the bridge between the Three.js scene graph and the browser's ability to display graphics using the GPU.

renderer.setSize(size.width,size.height); // Setting up the size

renderer.render(scene,camera);
// render is used to draw the 3D scene onto the canvas, displaying it on the screen. It takes the scene and a camera as input and outputs the visual result to the canvas element

```



