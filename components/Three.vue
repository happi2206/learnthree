<template>
  <div></div>
</template>
<script>
import * as THREE from "three";
export default {
  data() {
    return {};
  },
  components: {},

  mounted() {
    const scene = new THREE.Scene();

    // the camera with three attributes
    // first attribute (75) is the field of view.
    // second one is the aspect ratio
    //  third (0.1) is the near clipping pane and fourth is the far clipping pane
    const camera = new THREE.PerspectiveCamera(
      75,
      window.innerWidth / window.innerHeight,
      0.1,
      1000
    );

    // the renderer.

    const renderer = new THREE.WebGLRenderer();

    renderer.setSize(window.innerWidth, window.innerHeight);
    document.body.appendChild(renderer.domElement);

    const geometry = new THREE.BoxGeometry(1, 1, 1);

    const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 });

    const cube = new THREE.Mesh(geometry, material);

    scene.add(cube);

    camera.position.z = 5;

    const animate = () => {
      requestAnimationFrame(animate);

      cube.rotation.x += 0.01;
      cube.rotation.y += 0.01;

      renderer.render(scene, camera);
    };

    animate();
  },

  methods: {},
};
</script>