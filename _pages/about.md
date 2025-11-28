---
permalink: /
title: "About"
excerpt: ""
author_profile: false
redirect_from: 
  - /about/
  - /about.html
---

{% include base_path %}

<div style="float:left">Our goal is to build the <i>smart and connected</i> water systems of the future ... <div id="cursor"></div></div>

<div id="webgl"></div>
<script src="../lib/three.min.js"></script>
<script src="../lib/TerrainLoader.js"></script>
<script>

 "use strict";

 var scene = new THREE.Scene();
 scene.background = new THREE.Color( 0x1a202c );

 var axes = new THREE.AxesHelper(0);
 scene.add(axes);

 const ambientLight = new THREE.AmbientLight(0xffffff, 0.9);

 scene.add(ambientLight);

 var renderer = new THREE.WebGLRenderer();
 document.body.appendChild(renderer.domElement);

 var camera = new THREE.PerspectiveCamera(45, 1, 0.1, 1000);
 camera.position.set(0, -50, 50);
 camera.rotation.set(3.14 / 4, 0, 0);

 function resizeCanvasToDisplaySize() {
    const canvas = renderer.domElement;
    const width = canvas.clientWidth;
    const height = canvas.clientHeight;
    if (canvas.width !== width ||canvas.height !== height) {
        renderer.setSize(width, height, false);
        camera.aspect = width / height;
        camera.updateProjectionMatrix();
    }
 }

 var terrainLoader_0 = new THREE.TerrainLoader();
 var terrainLoader_1 = new THREE.TerrainLoader();
 terrainLoader_0.load('../files/jotunheimen_flood.bin', function(data) {

     terrainLoader_1.load('../files/jotunheimen.bin', function(data) {
         const width = 200;
         const height = 200;
         const size = width * height;
         var geometry = new THREE.PlaneGeometry(45, 45, width - 1, height - 1);
         var texture_data = new Uint8ClampedArray(size);

         for (var i = 0, l = geometry.attributes.position.count; i < l; i++) {
             geometry.attributes.position.setZ(i, data[i] / 65535 * 10);
         }

         for (var i = 0, l = size; i < l; i++) {
             texture_data[i] = (data[i] / 65535 * 255);
         }

         const texture = new THREE.DataTexture(texture_data, width, height,
                                               THREE.LuminanceFormat, THREE.UnsignedByteType,
                                               THREE.UVMapping,
                                               THREE.ClampToEdgeMapping, THREE.ClampToEdgeMapping);
         texture.flipY = true;

         var material = new THREE.MeshBasicMaterial({
             map: texture,
             wireframe: false
         });

         var plane = new THREE.Mesh(geometry, material);
         scene.add(plane);
     });

     const width = 200;
     const height = 200;
     const size = width * height;
     var geometry = new THREE.PlaneGeometry(45, 45, width - 1, height - 1);
     var texture_data = new Uint8ClampedArray(size);

     for (var i = 0, l = geometry.attributes.position.count; i < l; i++) {
         geometry.attributes.position.setZ(i, (data[i] - 200) / 65535 * 10);
     }

     var material = new THREE.MeshBasicMaterial({
         color: 0x00ffff,
         opacity: 0.4,
         transparent: true,
         wireframe: false
     });

     var plane = new THREE.Mesh(geometry, material);
     scene.add(plane);

 });

 document.getElementById('webgl').appendChild(renderer.domElement);

 function animate() {

     resizeCanvasToDisplaySize();

     if (scene.children.length > 3) {
         scene.children[2].rotation.z += 0.005;
         scene.children[3].rotation.z += 0.005;
     }
     requestAnimationFrame(animate);
     renderer.render(scene, camera);
 }

 animate();

</script>

<!-- <div class="page__col-wrap"></div> -->

<h1>News</h1>

<details open>
    <summary><u>Recent</u></summary>
     <ul>
         <li>[2025-11-17] :: Min-Gyu successfully defends his dissertation! &nbsp; 🎉 🎊 🥂</li>
         <li>[2025-10-30] :: Matt presents at the National Academies of Engineering on <a href="https://www.youtube.com/watch?v=Em5VB2Jmmuo">AI in water resources</a> &nbsp;✨💧</li>
         <li>[2025-10-30] :: Min-Gyu's <a href="https://www.youtube.com/watch?v=Em5VB2Jmmuo">「EufoRiA」</a> algal blooms model paper published &nbsp; 🦠 📔</li>
         <li>[2025-10-07] :: Jeil's sensor placement paper published in <a href="https://www.nature.com/articles/s44221-025-00496-7">Nature Water</a> &nbsp;📡📔</li>
         <li>[2025-09-15] :: Matt runs JCUD RTC workshop at <a href="https://www.uibk.ac.at/en/congress/udm2025/">UDM 2025</a> &nbsp;🕹️🇦🇹</li>
         <li>[2025-07-17] :: Jeil's flood forecasting paper published in <a href="https://www.nature.com/articles/s44304-025-00116-0">npj Natural Hazards</a> &nbsp;🌊📔</li>
         <li>[2025-05-21] :: Matt serves as instructor at the <a href="https://www.cuahsi.org/summer-institute">2025 CUAHSI Summer Institute</a> urban flooding theme &nbsp;🏫👨‍🏫 </li>
         <li>[2025-05-21] :: Yeji presents at <a href="https://www.ewricongress.org/">EWRI 2025</a> &nbsp;🚰📔</li>
         <li>[2025-05-21] :: Yeji's stormwater digital twin paper published in <a href="https://www.sciencedirect.com/science/article/abs/pii/S2210670724008060">Sustainable Cities and Society</a> &nbsp;🤖📔</li>
         <li>[2024-12-13] :: Jeil presents at <a href="https://www.agu.org/annual-meeting-2024">AGU 2024</a> &nbsp;🎤🌎</li>
     </ul>
</details>

<details>
    <summary><u>Older</u></summary>
     <ul>
         <li>[2024-07-31] :: <a href="https://doi.org/10.1016/j.watres.2024.122201">「Online state estimation in WDSs」</a> published in Water Research &nbsp;🚰📔</li>
         <li>[2024-06-24] :: Yeji and Min-Gyu present at <a href="https://conference.iemss.org/">iEMS 2024</a> &nbsp;💻🎤</li>
         <li>[2024-06-10] :: Aditi's paper published in <a href="https://www.tandfonline.com/doi/full/10.1080/23744731.2024.2351309">STBE</a> &nbsp;🛁📔</li>
         <li>[2024-06-09] :: Matt, Jimmy, and Jeil present at <a href="https://icud2024.org/">ICUD 2024</a> &nbsp;🧇🇳🇱</li>
         <li>[2024-01-04] :: Matt wins the <a href="https://www.nsf.gov/awardsearch/showAward?AWD_ID=2340176&HistoricalAwards=false">NSF CAREER Award</a> &nbsp;🏅👨‍🏫</li>
         <li>[2023-11-03] :: Min-Gyu's <a href="https://doi.org/10.1016/j.envsoft.2023.105868">「PipeDream-WQ」</a> paper accepted at EMS &nbsp;🦠 📔</li>
         <li>[2023-09-27] :: <a href="https://future-water.github.io/publication/2023-09-24-state">Best poster</a> at Watermatex 2023 🥇 🪧</li>
         <li>[2023-09-07] :: <a href="https://future-water.github.io/publication/2023-09-04-state">Best paper presentation</a> at CCWI 2023 🏆 📜</li>
         <li>[2023-07-03] :: Matt, Yeji, and Min-Gyu present at <a href="https://www.novatech2023.org/en">Novatech 2023</a> &nbsp;🇫🇷 🥐</li>
         <li>[2023-06-14] :: Matt attends <a href="https://www.linkedin.com/posts/venkatesh-merwade-255633b9_the-cybertraining-workshop-led-by-venkatesh-activity-7075566765581205504-ycIa">NSF Cybertraining Workshop</a> &nbsp;🧑‍💻 🦾</li>
         <li>[2023-06-11] :: Jeil attends <a href="https://www.cuahsi.org/summer-institute">CUASHI Summer Institute</a> &nbsp;🏫 🎓</li>
         <li>[2023-05-16] :: Yeji, Jeil, and Min-Gyu pass their qualifying exams! &nbsp;🎉 🎊 🥂</li>
         <li>[2023-03-27] :: Matt interviewed in <a href="https://thedailytexan.com/2023/03/27/ut-researchers-develop-smart-stormwater-basin-to-prevent-flooding-protect-water-quality/">The Daily Texan</a> &nbsp;🤠 📰</li>
         <li>[2023-03-08] :: Jeil's <a href="https://doi.org/10.1016/j.watres.2023.119825">MPC paper</a> accepted at Water Research &nbsp;📈 📔</li>
         <li>[2023-03-05] :: Jimmy presents at <a href="https://liberalarts.utexas.edu/events/planet-texas-2050-symposium-resilience-research-in-action-3">PT2050 research symposium</a> &nbsp;🎤 🤠</li>
         <li>[2022-12-12] :: Yeji presents at <a href="https://agu2022fallmeeting-agu.ipostersessions.com/default.aspx?s=EE-07-F8-EC-79-06-9C-43-B1-81-C4-E7-B2-3B-50-DB">AGU</a> &nbsp;🎤 🌎</li>
         <li>[2022-08-26] :: Matt presents at <a href="https://www.tfma.org/mpage/2022-summit">TFMA</a> &nbsp;🌊</li>
         <li>[2022-06-08] :: Matt and Jeil present at <a href="https://www.ewricongress.org/">EWRI</a> &nbsp;🚰</li>
         <li>[2022-05-09] :: Matt and Jeil present at <a href="https://www.awra.org/AWRA/Members/Events_and_Education/Events/2022_GIS_Conference/2022_GIS_Conference.aspx">AWRA</a> &nbsp;🗺️</li>
         <li>[2022-04-13] :: Yeji presents at <a href="https://bridgingbarriers.utexas.edu/events/planet-texas-2050-research-symposium-week-resilience-action">PT2050 research symposium</a> 🎤</li>
         <li>[2022-02-11] :: Matt interviewed in <a href="https://www.estormwater.com/software/software-modeling/article/10983678/new-real-time-digital-twin-can-forecast-storm-water-overflows">Stormwater Solutions</a> 🌧️</li>
        <li>[2022-01-10] :: Matt and Jeil present at <a href="https://udm2022.org/">UDM</a> 🚰</li>
        <li>[2021-12-14] :: Matt presents at <a href="https://agu2021fallmeeting-agu.ipostersessions.com/default.aspx?s=F1-C8-0B-47-ED-CA-AA-4A-E8-4E-61-8B-E6-19-33-99">AGU</a> 🌎</li>
        <li>[2021-10-22] :: Matt presents at the <a href="https://www.jsg.utexas.edu/dgs/events/wce-seminar">WCE Seminar Series</a> &nbsp;🎤</li>
        <li>[2021-10-01] :: <a href="https://www.sciencedirect.com/science/article/pii/S1364815221001638">「PipeDream」</a> published in EMS &nbsp;📔</li>
        <li>[2021-07-21] :: Matt interviewed in <a href="https://elpasomatters.org/2021/07/21/stagnant-floodwaters-pose-public-health-problem/">El Paso Matters</a> &nbsp;🤠</li>
        <li>[2021-06-26] :: <a href="https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2020WR029551">「Observability-based sensor placement」</a> published in WRR &nbsp;📔</li>
        <li>[2021-05-13] :: Matt presents at <a href="https://www.incose.org/">INCOSE</a> &nbsp;🚰</li>
        <li>[2021-02-09] :: <a href="https://amt.copernicus.org/articles/14/995/2021/">「Multipollutant monitors」</a> published in AMT &nbsp;📔</li>
        <li>[2021-01-21] :: Matt presents at <a href="https://cwe.engr.utexas.edu/resources/ewre-seminar/">EWRE Seminar Series</a> &nbsp;🚰</li>
    </ul>
</details>

<br>

<h1>Links</h1>

<ul style="list-style-type:none;">
<li><i class="fas fa-graduation-cap" aria-hidden="true"></i> &nbsp; <a href="https://scholar.google.com/citations?user=RmuqfEAAAAAJ&hl=en">Google Scholar</a></li>
<li><i class="fab fa-github" aria-hidden="true"></i> &nbsp; <a href="https://github.com/future-water">Github</a></li>
<li><i class="fab fa-youtube" aria-hidden="true"></i> &nbsp; <a href="https://www.youtube.com/playlist?list=PLHovUGJUgy1DvJoaJuBWdF_maE1-YzOfm">Recordings for CE 397: Control Theory</a></li>
<li><i class="fab fa-youtube" aria-hidden="true"></i> &nbsp; <a href="https://www.youtube.com/playlist?list=PLHovUGJUgy1CGUAPj9UwRGqs83jyNZ73l">Recordings for CE 374U: Urban Stormwater</a> </li>
<li><i class="fab fa-youtube" aria-hidden="true"></i> &nbsp; <a href="https://www.youtube.com/playlist?list=PLHovUGJUgy1Dtpt8QBt1sxK_SAPasG3g2">Recordings for CE 356: Elements of Hydraulic Engineering</a> </li>
</ul>

