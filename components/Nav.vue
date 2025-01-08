<template>
  <nav class="navbar">
    <div class="navbar-container">
      <div class="logo">Username Dashboard</div>
      <div class="navbar-links">
        <a href="/dashboard" class="navbar-item">Home</a>
        <a href="/CarDisplay" class="navbar-item">Cars</a>
        <a href="/car-handling" class="navbar-item">Car Handling</a>
        <a href="/profile" class="navbar-item">Profile</a>
        <a href="/settings" class="navbar-item">Settings</a>
        <a href="/" class="navbar-item">Log Out</a>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Nav",
};
</script>

<style scoped>
/* .form-container {
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  text-align: center;
  width: 100%;
  max-width: 400px;
} */
/* Main navbar styling */
.navbar {
  /* background-color: rgba(255, 255, 255, 0.8);  */
  background-color: #000000; 
  /* Dark background color */
  padding: 15px 30px; /* Padding for spacing */
}

.navbar-container {
  display: flex;
  justify-content: space-between; /* Space between logo and links */
  align-items: center;
}

.logo {
  font-size: 24px;
  font-weight: bold;
  color: #d46701;
  text-transform: uppercase;
}

.navbar-links {
  display: flex;
  gap: 20px; /* Space between navbar items */
}

.navbar-item {
  color: #d46701;
  text-decoration: none;
  font-size: 16px;
  padding: 10px;
  border-radius: 5px;
  transition: background-color 0.3s ease, color 0.3s ease;
}

/* Hover effect */
.navbar-item:hover {
  background-color: #34495e; /* Lighter shade for hover */
  color: #ecf0f1; /* Lighter text on hover */
}

/* Active link (optional) */
.navbar-item.active {
  background-color: #2980b9; /* Blue background for active link */
  color: #ecf0f1;
}

/* Responsive Design */
@media (max-width: 768px) {
  .navbar-container {
    flex-direction: column; /* Stack items on small screens */
    align-items: flex-start;
  }

  .navbar-links {
    flex-direction: column;
    gap: 10px;
    margin-top: 20px;
  }
}
</style>
