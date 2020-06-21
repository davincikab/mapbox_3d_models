# 3D Model using Mapbox

Mapbox together with threejs are used together to visualize custom 3D models from a variety of
3D file formats such as GLTF.

## 3D Lighting

Lighting the 3d model relies on threejs lighting such as:
    - AmbientLight
    - HemisphereLight
    - PointLight
    - DirectionalLight

Models rendered in Mapbox are mainly geographical hence DirectionalLight is mainly used to simulate the sun.

### Using Directional Light with Custom Models
Create a light, add the color and the intensity

```javascript
    var directionalLight = new THREE.DirectionalLight(0xfffff, 1)
```
Specify the light position, the target position and add the light the scene

```javascript
    directionalLight.position.set(10,2,8).normalize();
    directionLight.target.position.set(0,0,0).normalize();
    scene.add(directionalLight);
```