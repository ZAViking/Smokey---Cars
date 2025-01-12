<template><Nav />
    <br><br>
    <div class="car-handling">
      <h2>Calculate FiveM Car Handling</h2>
      <form @submit.prevent="calculateHandling">
        <div class="form-group">
          <label for="car">Select a Car</label>
          <select v-model="selectedCar" @change="updateCarData" id="car" required>
            <option value="" disabled>Select a car</option>
            <option v-for="car in cars" :key="car.name" :value="car.name">{{ car.name }}</option>
          </select>
        </div>
  
        <div v-if="carData" class="car-details">
          <div class="form-group">
            <label>Car Weight (kg)</label>
            <input type="text" v-model="carData.weight" disabled />
          </div>
          <div class="form-group">
            <label>Top Speed (km/h)</label>
            <input type="text" v-model="carData.topSpeed" disabled />
          </div>
          <div class="form-group">
            <label>Braking from 100-0 (seconds)</label>
            <input type="text" v-model="carData.braking" disabled />
          </div>
          <div class="form-group">
            <label>0-100 km/h Acceleration (seconds)</label>
            <input type="text" v-model="carData.acceleration" disabled />
          </div>
        </div>
  
        <button type="submit" class="submit-button">Calculate Handling</button>
      </form>
  
      <div v-if="handlingResult">
        <h3>Car Handling Result</h3>
        <p><strong>Handling Score:</strong> {{ handlingResult }}</p>
      </div>
    </div>
  </template>
  
<script>
export default {
    data() {
      return {
        cars: [
          { name: "Car 1", weight: 1200, topSpeed: 220, braking: 5.6, acceleration: 8.4 },
          { name: "Car 2", weight: 1500, topSpeed: 240, braking: 5.2, acceleration: 7.6 },
          // Add more cars with their handling data
        ],
        selectedCar: null,
        carData: null,
        handlingResult: null,
      };
    },
    methods: {
      updateCarData() {
        const car = this.cars.find(c => c.name === this.selectedCar);
        this.carData = car ? { ...car } : null;
      },
      calculateHandling() {
        if (!this.carData) return;
  
        const { weight, topSpeed, braking, acceleration } = this.carData;
        let score = 0;
  
        // Example calculation based on FiveM data
        score += weight / 1000; // Heavier cars have worse handling
        score += (topSpeed / 100) * 2; // Higher speed can reduce handling
        score -= braking * 2; // Better braking improves handling
        score += acceleration * 1.5; // Faster acceleration improves handling
  
        this.handlingResult = score.toFixed(2);
      },
    },
  };
  </script>
  
  <style scoped>
  .car-handling {
    max-width: 600px;
    margin: 0 auto;
    background-color: rgba(255, 255, 255, 0.8);
    padding: 2rem;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  }
  
  h2 {
    font-size: 2rem;
    text-align: center;
    margin-bottom: 1rem;
  }
  
  .form-group {
    margin-bottom: 1rem;
    text-align: left;
  }
  
  label {
    display: block;
    margin-bottom: 0.5rem;
  }
  
  input {
    width: 100%;
    padding: 0.5rem;
    border: 1px solid #555;
    border-radius: 4px;
    background: #f5f5f5;
    color: #333;
    font-size: 1rem;
  }
  
  .submit-button {
    width: 100%;
    padding: 0.75rem;
    border: none;
    border-radius: 4px;
    background: #ff4500;
    color: white;
    font-size: 1rem;
    cursor: pointer;
    transition: background 0.3s;
  }
  
  .submit-button:hover {
    background: #ff6347;
  }
  
  h3 {
    margin-top: 20px;
    text-align: center;
    color: #333;
  }
  
  .car-details {
    margin-top: 20px;
    padding: 10px;
    background-color: #f0f0f0;
    border-radius: 5px;
  }
  </style>
  