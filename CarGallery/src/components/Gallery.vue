<template>
  <div class="gallery">
    <h1>Card Gallery</h1>
    <div class="gallery-grid">
      <div
        v-for="card in cards"
        :key="card.id"
        :class="['card-wrapper', { flipped: card.flipped }]"
        @click="flipCard(card.id)"
      >
        <transition name="flip">
          <div class="card-inner" :key="card.flipped">
            <div v-if="!card.flipped" class="card-front">
              <Card>
                <template #header>
                  <img :src="`/images/${card.image}`" :alt="card.name" />
                </template>
                <template #title>{{ card.name }}</template>
                <template #content>
                  <p>{{ card.description }}</p>
                </template>
              </Card>
            </div>
            <div v-else class="card-back">
              <Card>
                <template #title>More Info</template>
                <template #content>
                  <p>{{ card.moreInfo }}</p>
                </template>
              </Card>
            </div>
          </div>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
import Card from 'primevue/card';

export default {
  components: {
    Card,
  },
  data() {
    return {
      cards: [
  {
    id: 1,
    name: 'Ferrari F8',
    description: 'A stunning sports car with a powerful V8 engine.',
    moreInfo: 'Top speed: 211 mph',
    image: 'f8.jpg',
    flipped: false,
  },
  {
    id: 2,
    name: 'Lamborghini Huracan',
    description: 'High-performance supercar with sleek design.',
    moreInfo: 'Top speed: 201 mph',
    image: 'huracan.jpg',
    flipped: false,
  },
  {
    id: 3,
    name: 'Porsche 911',
    description: 'An iconic sports car known for its style.',
    moreInfo: 'Top speed: 191 mph',
    image: '911.jpg',
    flipped: false,
  },
  {
    id: 4,
    name: 'Tesla Model S',
    description: 'Luxury EV with cutting-edge technology.',
    moreInfo: 'Top speed: 155 mph',
    image: 'models.jpg',
    flipped: false,
  },
  {
    id: 5,
    name: 'Bugatti Chiron',
    description: 'A hypercar with unmatched speed and luxury.',
    moreInfo: 'Top speed: 261 mph',
    image: 'bugatti.jpg',
    flipped: false,
  },
  {
    id: 6,
    name: 'Pagani Huayra',
    description: 'Exotic design paired with Italian craftsmanship.',
    moreInfo: 'Top speed: 238 mph',
    image: 'huayra.jpg',
    flipped: false,
  },
  {
    id: 7,
    name: 'Koenigsegg Jesko',
    description: 'Track-focused Swedish hypercar engineering.',
    moreInfo: 'Top speed: 278 mph (est)',
    image: 'jesko.jpg',
    flipped: false,
  },
  {
    id: 8,
    name: 'McLaren P1',
    description: 'A hybrid hypercar that blends power and efficiency.',
    moreInfo: 'Top speed: 217 mph',
    image: 'p1.jpg',
    flipped: false,
  }
],

    };
  },
  methods: {
    flipCard(id) {
      const card = this.cards.find((card) => card.id === id);
      card.flipped = !card.flipped;
    },
  },
};
</script>

<style scoped>
.gallery {
  padding: 40px 20px;
  text-align: center;
  background-color: #222;
  color: white;
  min-height: 100vh;
}

h1 {
  margin-bottom: 40px;
  font-size: 3rem;
}

.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 20px;
}



.card-wrapper {
  perspective: 1500px; 
  cursor: pointer;
  height: 380px;
  position: relative;
  transition: transform 0.3s ease-in-out;
}

.card-wrapper:hover {
  transform: scale(1.03);
}

.card-inner {
  width: 100%;
  height: 100%;
  transform-style: preserve-3d;
  transition: transform 0.8s cubic-bezier(0.4, 0.2, 0.2, 1);
  position: relative;
}

.card-wrapper.flipped .card-inner {
  transform: rotateY(180deg);
}

.card-front,
.card-back {
  backface-visibility: hidden;
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  border-radius: 12px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
  overflow: hidden;
  background: white;
  color: black;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  padding: 16px;
  box-sizing: border-box;
}

.card-front {
  z-index: 2;
}

.card-back {
  transform: rotateY(180deg);
  z-index: 1;
}


img {
  width: 100%;
  height: 180px;
  object-fit: cover;
  border-radius: 8px;
  margin-bottom: 15px;
}


.flip-enter-active, .flip-leave-active {
  transition: opacity 0.3s ease;
}
.flip-enter-from, .flip-leave-to {
  opacity: 0;
}


</style>
