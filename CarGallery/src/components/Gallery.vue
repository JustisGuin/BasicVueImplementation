<template>
    <div class="gallery">
      <h1>Car Gallery</h1>
      <div class="gallery-grid">
        <div class="gallery-item" v-for="car in cars" :key="car.id">
          <img :src="`/images/${car.image}`" :alt="car.name" />
          <h2>{{ car.name }}</h2>
          <p>{{ car.description }}</p>
        </div>
        </div>
    </div>
  </template>
  <script>
  export default {
    data() {
      return {
        cars: [
          {
            id: 1,
            name: 'Ferrari F8',
            description: 'A stunning sports car with a powerful V8 engine.',
            image: 'f8.jpg',
          },
          {
            id: 2,
            name: 'Lamborghini Huracan',
            description: 'A high-performance supercar with a sleek design.',
            image: 'huracan.jpg',
          },
          {
            id: 3,
            name: 'Porsche 911',
            description: 'An iconic sports car known for its performance and style.',
            image: '911.jpg',
          },
          {
            id: 4,
            name: 'Tesla Model S',
            description: 'An electric car that combines luxury with cutting-edge technology.',
            image: 'models.jpg',
          },
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  .gallery {
    padding: 20px;
    text-align: center;
  }
  
  .gallery-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 20px;
  }
  
  .gallery-item {
    border: 1px solid #ccc;
    border-radius: 8px;
    overflow: hidden;
    transition: transform 0.2s;
  }
  
  .gallery-item:hover {
    transform: scale(1.05);
  }
  
  .gallery-item img {
    width: 100%;
    height: auto;
  }
  
  h1 {
    margin-bottom: 20px;
  }
  </style>