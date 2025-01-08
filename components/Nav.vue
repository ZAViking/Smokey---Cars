<template>
  <nav class="navbar">
    <div class="navbar-container">
      <div class="logo">My Dashboard</div>
      <div class="navbar-links">
        <a href="/dashboard" class="navbar-item">Home</a>
        <a href="/profile" class="navbar-item">Profile</a>
        <a href="/settings" class="navbar-item">Settings</a>
        <a href="/reports" class="navbar-item">Reports</a>
        <a href="/cars" class="navbar-item">Cars</a>
        <a href="/car-handling" class="navbar-item">Car Handling</a>
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
/* Main navbar styling */
.navbar {
  background-color: #2c3e50; /* Dark background color */
  padding: 15px 30px; /* Padding for spacing */
  color: white;
}

.navbar-container {
  display: flex;
  justify-content: space-between; /* Space between logo and links */
  align-items: center;
}

.logo {
  font-size: 24px;
  font-weight: bold;
  color: white;
  text-transform: uppercase;
}

.navbar-links {
  display: flex;
  gap: 20px; /* Space between navbar items */
}

.navbar-item {
  color: white;
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
