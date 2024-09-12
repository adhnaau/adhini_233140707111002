<template>
  <div id="app">
    <div class="container">
      <!-- Click Counter -->
      <div class="section counter">
        <h2>Click Counter</h2>
        <button @click="incrementCounter">Click Me!</button>
        <p>Count: {{ count }}</p>
      </div>

      <!-- Box Color Changer -->
      <div class="section color-changer">
        <h2>Box Color Changer</h2>
        <button @click="changeColor">Change Color</button>
        <div :style="{ backgroundColor: boxColor, width: '100px', height: '100px', marginTop: '10px' }"></div>
      </div>

      <!-- Image Carousel -->
      <div class="section carousel">
        <h2>Image Carousel</h2>
        <button @click="prevImage">Previous</button>
        <img :src="images[currentImage]" alt="carousel image" class="carousel-image" />
        <button @click="nextImage">Next</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      boxColor: 'red',
      colors: ['red', 'green', 'blue', 'yellow', 'purple'],
      currentColorIndex: 0,
      images: [
        'https://via.placeholder.com/300x200?text=Image+1',
        'https://via.placeholder.com/300x200?text=Image+2',
        'https://via.placeholder.com/300x200?text=Image+3'
      ],
      currentImage: 0
    };
  },
  methods: {
    incrementCounter() {
      this.count += 1;
    },
    changeColor() {
      this.currentColorIndex = (this.currentColorIndex + 1) % this.colors.length;
      this.boxColor = this.colors[this.currentColorIndex];
    },
    prevImage() {
      this.currentImage = (this.currentImage - 1 + this.images.length) % this.images.length;
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.section {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 400px;
}

button {
  margin: 5px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.carousel-image {
  width: 300px;
  height: 200px;
  object-fit: cover;
  margin: 10px 0;
}
</style>
