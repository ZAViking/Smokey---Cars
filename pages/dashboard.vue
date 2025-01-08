<template>
  <Nav /> <!-- Include the Nav component -->
  <div class="dashboard-container">
    <div class="dashboard-main">
      <h1>Welcome to your Dashboard</h1>

      <div class="dashboard-widgets">
        <div class="widget">
          <h3>Recent Activity</h3>
          <ul>
            <li>Logged in at 10:00 AM</li>
            <li>Updated profile</li>
            <li>Completed task #123</li>
          </ul>
        </div>

        <div class="widget">
          <h3>Statistics</h3>
          <p>Sales: 1,250</p>
          <p>Active Users: 50</p>
        </div>

        <div class="widget">
          <h3>Notifications</h3>
          <ul>
            <li>New message from Admin</li>
            <li>Your report was approved</li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
