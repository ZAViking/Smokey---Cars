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
                'assets/images/cars/car1_2.jpg',     
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
    /* Search bar styleing */
    .search-bar-container{
        padding-top: 15pt;
        padding-right: 15pt;
        display: flex;
        justify-content: right;
        align-items: right;
    }
    .search-bar {
        width: 100%;
        max-width: 400px; /* Limit width */
        padding: 12px 20px;
        font-size: 1rem;
        border-radius: 8px;
        border: 1px solid #000000;
        margin-bottom: 20px;
        transition: all 0.3s ease;
        color: black;
    }
    
    .search-bar:focus {
        outline: none;
        border-color: #27035a;
        box-shadow: 0 0 8px rgba(216, 132, 5, 0.5);
    }

    /* Global Body Styling */
    body {
        font-family: 'Roboto', sans-serif;
        background-color: #f5f7fb;
        margin: 0;
        padding: 0;
    }
    
    /* Container for the tool */
    .car-tool-container {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        padding: 20px;
        max-width: 1200px;
        margin: 0 auto;
    }
    
    /* Car Items Section */
    .car-container {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr)); /* Responsive layout */
        gap: 20px;
        width: 100%;
    }
    
    /* Individual Car Item */
    .car-item {
        background-color: #fff;
        border-radius: 12px;
        overflow: hidden;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        cursor: pointer;
        transition: transform 0.3s ease, box-shadow 0.3s ease;
        text-align: center;
    }
    
    .car-item:hover {
        transform: scale(1.05);
        box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
    }
    
    .car-name {
        font-size: 1.3rem;
        font-weight: 600;
        color: #333;
        margin: 10px 0;
    }
    
    .car-image {
        width: 100%;
        height: 180px;
        object-fit: cover;
        border-bottom: 1px solid #f0f0f0;
    }
    
    .car-spawn-code {
        font-size: 0.9rem;
        color: #888;
        margin: 10px 0;
        padding: 5px 10px;
        background-color: #f0f0f0;
        border-radius: 5px;
    }
    
    /* Car Modal */
    .car-modal {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.7);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 1000;
    }
    
    .modal-content {
        background-color: #fff;
        padding: 20px;
        border-radius: 12px;
        width: 80%;
        max-width: 800px;
        text-align: center;
        box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
    }
    
    .close-btn {
        position: absolute;
        top: 10px;
        right: 10px;
        font-size: 2rem;
        cursor: pointer;
        color: #333;
        transition: color 0.3s ease;
    }
    
    .close-btn:hover {
        color: #6200ea;
    }
    
    .modal-images {
        display: flex;
        justify-content: space-between;
        gap: 10px;
    }
    
    .modal-image {
        width: 32%;
        height: auto;
        border-radius: 8px;
        object-fit: cover;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    }

    .app-container {
        font-family: Arial, sans-serif;
        padding: 20px;
    }
    /* This changes the GRID */

    .car-grid {
        display: grid;
        grid-template-columns: repeat(5, 1fr); /* Max 5 items per row */
        gap: 20px; /* Spacing between items */
    }

    .car-card {
        background-color: #fff;
        border-radius: 8px;
        padding: 16px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        text-align: center;
        transition: transform 0.3s ease;
        cursor: pointer;
    }

    .car-card:hover {
        transform: scale(1.05);
    }

    .car-card img {
        max-width: 100%;
        height: auto;
        border-radius: 4px;
    }

    .car-card h3 {
        margin: 10px 0;
        font-size: 1.2rem;
        color: #333;
    }

    .car-card p {
        font-size: 0.9rem;
        color: #666;
    }

    /* This changes the modal of the selectted image */

    .modal-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.8);
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .modal-content {
        background: #fff;
        padding: 20px;
        border-radius: 8px;
        max-width: 90%;
        text-align: center;
        position: relative;
    }

    .modal-content img {
        max-width: 100%;
        max-height: 60vh;
        border-radius: 5px;
    }

    .close-button {
        position: absolute;
        top: 10px;
        right: 10px;
        background: #ff5c5c;
        border: none;
        color: white;
        font-size: 20px;
        cursor: pointer;
        border-radius: 50%;
        width: 30px;
        height: 30px;
    }

    .slideshow-container {
        position: relative;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .prev-button,
    .next-button {
        background: rgba(0, 0, 0, 0.5);
        color: white;
        border: none;
        font-size: 24px;
        cursor: pointer;
        padding: 10px;
        border-radius: 50%;
        margin: 0 10px;
    }

    .prev-button:hover,
    .next-button:hover {
        background: rgba(0, 0, 0, 0.8);
    }
</style>
  