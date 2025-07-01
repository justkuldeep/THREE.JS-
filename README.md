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
    <canvas class="wbgl"></canvas>

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

const target = document.querySelector(".wbgl");
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

**Scene 🏞️** : 
The 3D space or virtual world where everything exists.

> Think of it as an empty stage waiting to be filled.

**Objects 📦** : 
The physical or visual elements inside the scene — like cubes, models, lights, etc.

> These are the “actors” of your 3D movie.

**Camera 🎥** : 
Represents the viewer’s perspective. It decides what part of the scene the audience sees and from what angle.

>It's like the eye of the viewer or the lens of the camera.

**Renderer (or Director) 🎬** : 
The engine that renders the final output by converting the scene and camera view into pixels on your screen.

> It's the “director” that brings everything together and shows it to the audience.


