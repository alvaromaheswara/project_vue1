<template>
  <div id="app">
    <div class="container">
      <!-- Button Clicker Counter -->
      <div class="counter-section">
        <button @click="incrementCounter" class="btn neon-btn">Click me!</button>
        <p class="count-text neon-text">You've clicked the button <strong>{{ count }}</strong> times.</p>
      </div>

      <!-- Box Color Changer -->
      <div class="color-changer-section">
        <div :style="{ backgroundColor: color }" class="color-box"></div>
        <button @click="changeColor" class="btn neon-btn">Change Color</button>
      </div>

      <!-- Carousel -->
      <div class="carousel-section">
        <div class="carousel">
          <img :src="images[currentIndex]" alt="Carousel Image" />
        </div>
        <div class="carousel-controls">
          <button @click="prevImage" class="btn neon-btn">Previous</button>
          <button @click="nextImage" class="btn neon-btn">Next</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      // Button Clicker Counter
      count: 0,

      // Box Color Changer
      colors: ['#FF5733', '#33FF57', '#3357FF', '#F0F0F0', '#FF33FF'],
      currentColorIndex: 0,

      // Carousel
      images: [
        'https://awsimages.detik.net.id/community/media/visual/2023/05/21/erik-ten-hag-1_169.jpeg?w=1200',
        'https://akcdn.detik.net.id/community/media/visual/2024/08/15/andre-onana_169.jpeg?w=600&q=90',
        'https://i.ytimg.com/vi/_mPDAQm58i8/maxresdefault.jpg'
      ],
      currentIndex: 0
    };
  },
  computed: {
    color() {
      return this.colors[this.currentColorIndex];
    }
  },
  methods: {
    // Button Clicker Counter Methods
    incrementCounter() {
      this.count++;
    },

    // Box Color Changer Methods
    changeColor() {
      this.currentColorIndex = (this.currentColorIndex + 1) % this.colors.length;
    },

    // Carousel Methods
    prevImage() {
      this.currentIndex = (this.currentIndex - 1 + this.images.length) % this.images.length;
    },
    nextImage() {
      this.currentIndex = (this.currentIndex + 1) % this.images.length;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Arial', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  background: #111;
  margin-top: 60px;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 40px;
}

.counter-section, .color-changer-section, .carousel-section {
  width: 100%;
  max-width: 600px;
}

.btn {
  font-size: 16px;
  padding: 10px 20px;
  margin: 10px;
  cursor: pointer;
  border: none;
  border-radius: 5px;
  background-color: #00f;
  color: #fff;
  transition: box-shadow 0.3s ease;
}

.neon-btn {
  position: relative;
  background-color: #ff0055;
  border: 2px solid #ff0055;
  color: #fff;
}

.neon-btn:before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100%;
  height: 100%;
  background: rgba(255, 0, 85, 0.5);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  z-index: -1;
  filter: blur(10px);
}

.btn:hover {
  box-shadow: 0 0 10px rgba(255, 0, 85, 0.8);
}

.count-text {
  font-size: 24px;
  text-shadow: 0 0 10px rgba(255, 0, 85, 1);
}

.color-changer-section .color-box {
  width: 200px;
  height: 200px;
  margin: 0 auto;
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(255, 0, 85, 0.7);
}

.carousel {
  text-align: center;
  margin: 20px auto;
}

.carousel img {
  width: 100%;
  max-width: 600px;
  height: auto;
  border-radius: 10px;
  box-shadow: 0 0 20px rgba(255, 0, 85, 0.7);
}

.carousel-controls {
  margin-top: 10px;
}
</style>
