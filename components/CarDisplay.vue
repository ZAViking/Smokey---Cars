<template>        
<!-- Search Bar -->
    <div class="search-bar-container">
        <input
            type="text"
            v-model="searchQuery"
            placeholder="Search cars..."
            class="search-bar"
        />
    </div>
    <div class="app-container">
        <!-- Car Grid -->
        <div class="car-grid">
            <div
            class="car-card"
            v-for="car in filteredCars"
            :key="car.id"
            @click="openCarModal(car)"
            >
            <h3>{{ car.name }}</h3>
            <img :src="car.image" alt="Car image" />
            <p>Spawn Code: {{ car.spawnCode }}</p>
            </div>
        </div>
  
      <!-- Modal -->
      <div v-if="isModalOpen" class="modal-overlay" @click="closeCarModal">
        <div class="modal-content" @click.stop>
          <button class="close-button" @click="closeCarModal">✖</button>
          <h2>{{ selectedCar.name }}</h2>
          <div class="slideshow-container">
            <button class="prev-button" @click="prevSlide">❮</button>
            <img :src="selectedCar.images[currentSlide]" alt="Car image" />
            <button class="next-button" @click="nextSlide">❯</button>
          </div>
          <p>Spawn Code: {{ selectedCar.spawnCode }}</p>
        </div>
      </div>
    </div>
  </template>
  
  
  <script>
  export default {
    data() {
      return {
        searchQuery: '',
        cars: [
          { id: 1, 
            name: 'Nissian GTR R35 Monster', 
            image: '/car-assets/Nissian-GTR-R35-Monster.jpg', 
            spawnCode: 'spawn1',  
            images: [
                '/car-assets/Nissian-GTR-R35-Monster.jpg',     
                '/car-assets/Capture.png',     
                'assets/images/cars/car1_3.jpg' 
            ] },
          { id: 2, name: 'Car 2', image: 'path/to/car2.jpg', spawnCode: 'spawn2', images: ['path/to/car2.jpg', 'path/to/car2_2.jpg', 'path/to/car2_3.jpg'] },
          { id: 2, name: 'Car 2', image: 'path/to/car2.jpg', spawnCode: 'spawn2', images: ['path/to/car2.jpg', 'path/to/car2_2.jpg', 'path/to/car2_3.jpg'] },
          { id: 2, name: 'Car 2', image: 'path/to/car2.jpg', spawnCode: 'spawn2', images: ['path/to/car2.jpg', 'path/to/car2_2.jpg', 'path/to/car2_3.jpg'] },
          { id: 2, name: 'Car 2', image: 'path/to/car2.jpg', spawnCode: 'spawn2', images: ['path/to/car2.jpg', 'path/to/car2_2.jpg', 'path/to/car2_3.jpg'] },
          { id: 2, name: 'Car 2', image: 'path/to/car2.jpg', spawnCode: 'spawn2', images: ['path/to/car2.jpg', 'path/to/car2_2.jpg', 'path/to/car2_3.jpg'] },
          { id: 2, name: 'Car 2', image: 'path/to/car2.jpg', spawnCode: 'spawn2', images: ['path/to/car2.jpg', 'path/to/car2_2.jpg', 'path/to/car2_3.jpg'] },
          { id: 2, name: 'Car 2', image: 'path/to/car2.jpg', spawnCode: 'spawn2', images: ['path/to/car2.jpg', 'path/to/car2_2.jpg', 'path/to/car2_3.jpg'] },
          // Add more cars as needed
        ],
        isModalOpen: false,
        selectedCar: null,
        currentSlide: 0,
      };
    },
    computed: {
    filteredCars() {
      return this.cars.filter((car) =>
        car.name.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
  methods: {
    openCarModal(car) {
      this.selectedCar = car;
      this.currentSlide = 0;
      this.isModalOpen = true;
    },
    closeCarModal() {
      this.isModalOpen = false;
      this.selectedCar = null;
    },
    nextSlide() {
      if (this.currentSlide < this.selectedCar.images.length - 1) {
        this.currentSlide++;
      } else {
        this.currentSlide = 0; // Loop back to the first slide
      }
    },
    prevSlide() {
      if (this.currentSlide > 0) {
        this.currentSlide--;
      } else {
        this.currentSlide = this.selectedCar.images.length - 1; // Loop back to the last slide
      }
    },
  },
};
</script>
  
<style scoped>
</style>
  