# 3D Model using Mapbox

[Mapbox](https://docs.mapbox.com/mapbox-gl-js/api/) together with [Threejs](https://threejs.org/) are used together to visualize custom 3D models from a variety of
3D file formats such as [GLTF](https://en.wikipedia.org/wiki/GlTF).

## 3D Lighting

Lighting the 3d model relies on [threejs lighting](https://threejsfundamentals.org/threejs/lessons/threejs-lights.html) such as:
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
### Changing the position of Light source
Using [SunCalc](https://github.com/mourner/suncalc) to calculate the azimuth and elevation angle of the 
Sun at any location on Earth Surface.

The SunCalc API takes in a date, latitude and longitude of an area and return a object with a number of details about the Sun's position however we are interested in the elevation and the altitude.

```javascript
    var date = new Date();
    var lat = -0.12;
    var lng = 37.987

    var sunPosition = SunCalc(date, lat, lng);
```

#### Changing the position of DirectionalLight
Directional Light position is defined in 3d vector (x,y,z)
```
    directionalLight.position.set(
        Math.sin(sunPosition.azimuth),
        Math.cos(sun.azimuth)
        Math.sin(sin.elevation)
    )
```
