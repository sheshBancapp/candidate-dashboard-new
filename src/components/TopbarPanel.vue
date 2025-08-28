<template>
  <nav class="navbar navbar-light bg-white border-bottom px-2 py-2">
    <div class="container-fluid d-flex align-items-center justify-content-between flex-wrap">
      
      <div class="d-flex align-items-center">
        <button 
          class="btn btn-link text-muted p-0 border rounded-3 me-2 sidebar-toggle-btn" 
          @click="$emit('toggle-sidebar')"
          title="Toggle Sidebar"
        >
          <i :class="sidebarOpen ? 'bi bi-x-lg' : 'bi bi-list'" class="fs-4"></i>
        </button>
        
        <div class="search-container me-4">
          <div class="input-group border border-secondary-subtle rounded-3 search-input-group">
            <span class="input-group-text border-0">
              <i class="bi bi-search text-muted"></i>
            </span>
            <input
              class="form-control border-0 bg-light"
              type="search"
              placeholder="Search Pipedrive..."
              aria-label="Search"
            />
          </div>
        </div>
      </div>

      <div class="text-center flex-grow-1 d-none d-md-block">
        <img src="@/assets/RCRM-Logo.png" alt="RCRM Logo" class="img-fluid" />
      </div>

      <div class="d-flex align-items-center gap-2 gap-md-3">
        <button class="btn btn-primary rounded-circle p-2 bxround d-none d-sm-block">
          <i class="bi bi-plus-lg text-white"></i>
        </button>
        
        <div class="linv d-none d-md-block"></div>
        
        <div class="position-relative">
          <button class="btn btn-outline-secondary border rounded-circle p-2 position-relative bxround">
            <i class="bi bi-envelope"></i>
          </button>
        </div>

        <div class="position-relative d-none d-sm-block">
          <button class="btn btn-outline-secondary border rounded-circle p-2 position-relative bxround">
            <i class="bi bi-chat-dots"></i>
          </button>
        </div>

        <div class="position-relative d-none d-md-block">
          <button class="btn btn-outline-secondary border rounded-circle p-2 position-relative bxround">
            <i class="bi bi-bell"></i>
          </button>
        </div>

        <div class="dropdown">
          <button class="btn btn-link text-decoration-none dropdown-toggle d-flex align-items-center user-dropdown-btn" 
                  type="button" 
                  data-bs-toggle="dropdown" 
                  aria-expanded="false">
            <img width="40"
              src="@/assets/user-img.png"
              class="rounded-circle me-2 user-avatar"
              alt="User Profile"
            />
            <div class="d-none d-sm-block text-start user-info">
              <div class="fw-semibold text-dark user-name">Phyllis Yang</div>
              <div class="text-muted small user-company">Silicon Links Inc</div>
            </div>
          </button>
          <ul class="dropdown-menu dropdown-menu-end">
            <li><a class="dropdown-item" href="#"><i class="bi bi-person me-2"></i>Profile</a></li>
            <li><a class="dropdown-item" href="#"><i class="bi bi-gear me-2"></i>Settings</a></li>
            <li><hr class="dropdown-divider"></li>
            <li><a class="dropdown-item" href="#"><i class="bi bi-box-arrow-right me-2"></i>Sign Out</a></li>
          </ul>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "TopBar",
  props: {
    sidebarOpen: {
      type: Boolean,
      default: false
    }
  },
  emits: ['toggle-sidebar']
};
</script>

<style scoped>
.linv{height:32px;width:2px;background:#c8ccd2}
.bxround{width:40px;height:40px}
.search-container{position:relative;flex:1;max-width:300px}
.search-input-group{overflow:hidden}
.form-control{border-radius:0;font-size:.9rem}
.form-control::placeholder{font-size:.9rem;color:#6c757d}
.btn-outline-secondary{border-radius:0 25px 25px 0;border:none}
.dropdown-toggle::after{margin-left:.5rem}
.badge{font-size:.6rem;padding:.25em .4em}
.btn-outline-secondary{transition:all .2s ease}
.sidebar-toggle-btn{text-decoration:none;transition:all .2s ease;display:flex;align-items:center;justify-content:center;width:40px;height:38px;border-radius:0 6px 6px 0;border-left:1px solid #dee2e6;background-color:#f8f9fa}
.sidebar-toggle-btn:hover{color:#1f5fac!important;background-color:#e9ecef}
.sidebar-toggle-btn:focus{box-shadow:none;outline:0}
.sidebar-toggle-btn:active{transform:scale(.95)}
.input-group .form-control{border-right:none}
.input-group .sidebar-toggle-btn{border-left:1px solid #dee2e6}
.user-dropdown-btn{padding:.25rem;border:none;background:0 0}
.user-avatar{width:35px;height:35px;object-fit:cover}
.user-info{min-width:120px}
.user-name{font-size:.875rem;margin:0}
.user-company{font-size:.75rem;margin:0}
@media (max-width:768px){
.search-container{max-width:200px}
.search-input-group{width:100%!important}
.sidebar-toggle-btn{width:35px;height:35px}
.sidebar-toggle-btn i{font-size:1rem!important}
.gap-2{gap:.5rem!important}
}
@media (max-width:576px){
.search-container{max-width:150px}
.form-control{font-size:.8rem}
.form-control::placeholder{font-size:.8rem}
.sidebar-toggle-btn{width:32px;height:32px}
.sidebar-toggle-btn i{font-size:.9rem!important}
.gap-2{gap:.25rem!important}
}
@media (max-width:480px){
.search-container{max-width:120px}
.form-control{font-size:.75rem}
.form-control::placeholder{font-size:.75rem}
}
</style>
