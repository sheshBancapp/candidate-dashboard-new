<template>
  <aside :class="['sidebar d-flex flex-column py-4 text-white', { open: sidebarOpen }]">
    <div v-if="sidebarOpen" class="mobile-close-btn d-md-none">
      <button 
        class="btn btn-link text-white p-0 border-0"
        @click="$emit('toggle')"
        title="Close Sidebar"
      >
        <i class="bi bi-x-lg fs-4"></i>
      </button>
    </div>

    <div class="sidebar-header mb-4 px-3">
      <div class="d-flex align-items-center">
        <div class="logo-icon me-2">
          <i class="bi bi-briefcase-fill fs-4"></i>
        </div>
        <span v-if="sidebarOpen" class="logo-text fw-bold">Recruit CRM</span>
      </div>
    </div>

    <ul class="nav flex-column flex-grow-1">
      <li class="nav-item mb-2">
        <a href="#" class="nav-link text-white d-flex align-items-center py-2 px-3 rounded">
          <i class="bi bi-house-door-fill fs-5"></i>
          <span v-if="sidebarOpen" class="ms-2">Dashboard</span>
        </a>
      </li>
      
      <li class="nav-item mb-2">
        <a href="#" class="nav-link text-white d-flex align-items-center py-2 px-3 rounded">
          <i class="bi bi-people-fill fs-5"></i>
          <span v-if="sidebarOpen" class="ms-2">Candidates</span>
        </a>
      </li>
      
      <li class="nav-item mb-2">
        <a href="#" class="nav-link text-white d-flex align-items-center py-2 px-3 rounded">
          <i class="bi bi-briefcase fs-5"></i>
          <span v-if="sidebarOpen" class="ms-2">Jobs</span>
        </a>
      </li>
      
      <li class="nav-item mb-2">
        <a href="#" class="nav-link text-white d-flex align-items-center py-2 px-3 rounded">
          <i class="bi bi-building fs-5"></i>
          <span v-if="sidebarOpen" class="ms-2">Companies</span>
        </a>
      </li>
      
      <li class="nav-item mb-2">
        <a href="#" class="nav-link text-white d-flex align-items-center py-2 px-3 rounded">
          <i class="bi bi-calendar-event fs-5"></i>
          <span v-if="sidebarOpen" class="ms-2">Calendar</span>
        </a>
      </li>
      
      <li class="nav-item mb-2">
        <a href="#" class="nav-link text-white d-flex align-items-center py-2 px-3 rounded">
          <i class="bi bi-chat-dots fs-5"></i>
          <span v-if="sidebarOpen" class="ms-2">Messages</span>
        </a>
      </li>
      
      <li class="nav-item mb-2">
        <a href="#" class="nav-link text-white d-flex align-items-center py-2 px-3 rounded">
          <i class="bi bi-file-earmark-text fs-5"></i>
          <span v-if="sidebarOpen" class="ms-2">Reports</span>
        </a>
      </li>
      
      <li class="nav-item mb-2">
        <a href="#" class="text-center nav-link text-white d-flex align-items-center py-2 px-3 rounded">
          <i class="bi bi-gear fs-5"></i>
          <span v-if="sidebarOpen" class="ms-2">Settings</span>
        </a>
      </li>

     
      <li class="nav-item mb-2">
        <a href="#" class="nav-link text-white d-flex align-items-center py-2 px-3 rounded">
          <i class="bi bi bi-three-dots"></i>
         
        </a>
      </li>
    </ul>

  </aside>
</template>

<script>
export default {
  name: "SidebarPanel",
  props: {
    sidebarOpen: {
      type: Boolean,
      default: false
    }
  },
  emits: ['toggle']
};
</script>

<style scoped>
.sidebar{width:60px;background:linear-gradient(180deg,#1f5fac 0,#0b5ed7 100%);transition:all .3s ease;overflow:hidden;flex-shrink:0;position:relative}
.sidebar.open{width:250px}
.logo-text{font-size:1.2rem;color:#fff}
.nav-link{transition:all .2s ease;border-radius:8px}
.nav-link:hover{background-color:#ffffff1a}
.nav-link.active{background-color:#fff3}
.sidebar-footer{border-top:1px solid #ffffff1a;padding-top:1rem}
.user-info{flex:1}
.mobile-close-btn{position:absolute;top:1rem;right:1rem;z-index:1001}
.mobile-close-btn .btn{background:rgba(255,255,255,.1);border-radius:50%;width:40px;height:40px;display:flex;align-items:center;justify-content:center;transition:all .2s ease}
.mobile-close-btn .btn:hover{background:rgba(255,255,255,.2);transform:scale(1.1)}
.mobile-close-btn .btn:active{transform:scale(.95)}
.mobile-close-btn .btn:focus{box-shadow:none;outline:0}
@media (max-width:768px){
.sidebar{width:100%;height:auto;position:fixed;top:0;left:0;z-index:1000;transform:translateX(-100%)}
.sidebar.open{transform:translateX(0);width:280px}
.mobile-close-btn{display:block!important}
}
@media (min-width:769px){
.mobile-close-btn{display:none!important}
}
</style>
