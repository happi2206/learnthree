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

  computed: {
    aspectRatio() {
      return window.innerWidth / window.innerHeight;
    },
  },

  mounted() {
    const renderer = new THREE.WebGLRenderer();
    renderer.setSize(window.innerWidth, window.innerHeight / 2);
    document.body.appendChild(renderer.domElement);

    // camera

    const camera = new THREE.PerspectiveCamera(45, this.aspectRatio, 1, 500);
    camera.position.set(0, 0, 100);
    camera.lookAt(0, 0, 0);

    const scene = new THREE.Scene();

    const material = new THREE.LineBasicMaterial({ color: 0x0cc3b });

    const points = [];

    points.push(new THREE.Vector3(10, 0, 0));
    points.push(new THREE.Vector3(0, 10, 10));
    points.push(new THREE.Vector3(10, 0, 0));

    const geometry = new THREE.BufferGeometry().setFromPoints(points);

    const line = new THREE.Line(geometry, material);

    scene.add(line);
    renderer.render(scene, camera);

    const animate = () => {
      requestAnimationFrame(animate);

      line.rotation.x += 0.001;
      line.rotation.y += 0.01;

      renderer.render(scene, camera);
    };

    animate();
  },

  methods: {},
};
</script>