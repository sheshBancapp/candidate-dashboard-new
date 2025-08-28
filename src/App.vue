<template>
  <div id="app">
    <div class="app-container">
      <!-- Left Sidebar -->
      <SidebarPanel :sidebarOpen="sidebarOpen" @toggle="toggleSidebar" />
      
      <!-- Mobile Backdrop - Only visible on mobile when sidebar is open -->
      <div 
        v-if="sidebarOpen" 
        class="mobile-backdrop d-md-none"
        @click="toggleSidebar"
      ></div>
      
      <!-- Main Content Area -->
      <div class="main-wrapper">
        <!-- Top Header -->
        <TopbarPanel :sidebarOpen="sidebarOpen" @toggle-sidebar="toggleSidebar" />
        
        <!-- Main Content -->
        <main class="main-content">
          <DashboardComponent />
        </main>
      </div>
    </div>
  </div>
</template>

<script>
import SidebarPanel from './components/SidebarPanel.vue'
import TopbarPanel from './components/TopbarPanel.vue'
import DashboardComponent from './views/DashboardComponent.vue'

export default {
  name: 'App',
  components: {
    SidebarPanel,
    TopbarPanel,
    DashboardComponent
  },
  data() {
    return {
      sidebarOpen: false
    }
  },
  methods: {
    toggleSidebar() {
      this.sidebarOpen = !this.sidebarOpen
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f8f9fa;
}

#app {
  height: 100vh;
  overflow: hidden;
}

.app-container {
  display: flex;
  height: 100vh;
  position: relative;
}

.main-wrapper {
  flex: 1;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.main-content {
  flex: 1;
  overflow-y: auto;
  background-color: #f8f9fa;
}

/* Mobile Backdrop Styles */
.mobile-backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 999;
  backdrop-filter: blur(2px);
}

/* Custom scrollbar */
.main-content::-webkit-scrollbar {
  width: 8px;
}

.main-content::-webkit-scrollbar-track {
  background: #f1f1f1;
}

.main-content::-webkit-scrollbar-thumb {
  background: #c1c1c1;
  border-radius: 4px;
}

.main-content::-webkit-scrollbar-thumb:hover {
  background: #a8a8a8;
}

/* Bootstrap overrides */
.btn {
  border-radius: 6px;
  font-weight: 500;
}

.card {
  border: none;
  border-radius: 12px;
}

.form-control {
  border-radius: 8px;
}

.navbar {
  border-radius: 0;
}

/* Mobile Responsive */
@media (max-width: 768px) {
  .app-container {
    position: relative;
  }
  
  .mobile-backdrop {
    display: block;
  }
}

@media (min-width: 769px) {
  .mobile-backdrop {
    display: none !important;
  }
}
</style>
