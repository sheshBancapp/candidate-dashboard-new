<template>
  <div class="user-profile-section">
    <div class="card border-0">
      <div class="card-body p-4">
        <div class="row align-items-start">
          <div class="col-md-12 col-lg-7 mb-3 mb-md-0">
            <div class="user-info-container d-flex align-items-center">
              <div class="user-image-container me-3 me-md-4">
                <img
                  src="@/assets/user-icon.png"
                  alt="User Profile"
                  class="user-image rounded-circle"
                />
              </div>
              <div class="user-details flex-grow-1">
                <div class="user-header d-flex flex-column flex-sm-row align-items-start align-items-sm-center mb-2">
                  <h4 class="fs-5 user-name mb-0 me-sm-3">William Sample</h4>
                  <div class="social-icons d-flex align-items-center mt-2 mt-sm-0">
                    <i class="bi bi-linkedin text-primary fs-6 me-2"></i>
                    <i class="fa-brands fa-square-facebook fs-6 me-2"></i>
                    <i class="fa-brands fa-linkedin fs-6"></i>
                  </div>
                </div>
                <p class="user-title small mb-0">
                  Senior Product Manager
                  <span class="location-info ms-2 ms-sm-3">United States</span>
                  <span class="location-info ms-2 ms-sm-3">Dallas</span>
                </p>
              </div>
            </div>
          </div>

          
          <div class="col-md-12 col-lg-5">
            <div class="action-buttons-container d-flex w-100 flex-wrap gap-3">
              <div class="action-buttons d-flex  w-100 gap-2 justify-content-start justify-content-lg-end">
                <button class="btn btn-outline-danger btn-sm action-btn">
                  <span class="btn-text">Contact Linked</span>
                </button>
                
               
                <div class="icon-buttons d-flex gap-1">
                  <button class="btn btn-outline-secondary btn-sm action-btn">
                    <i class="bi bi-star"></i>
                  </button>

                  <button class="btn btn-outline-secondary btn-sm action-btn">
                    <i class="bi bi-fire"></i>
                  </button>
                  
                 
                  <button 
                    class="btn btn-outline-secondary btn-sm action-btn"
                    @click="openEditModal"
                    title="Edit Profile"
                  >
                    <i class="bi bi-pencil"></i>
                  </button>

                
                  <div class="dropdown">
                    <button
                      class="btn btn-outline-secondary btn-sm action-btn dropdown-toggle"
                      type="button"
                      data-bs-toggle="dropdown"
                      aria-expanded="false"
                    >
                      <i class="bi bi-three-dots"></i>
                    </button>
                    <ul class="dropdown-menu dropdown-menu-end">
                      <li>
                        <a class="dropdown-item" href="#">
                          <i class="bi bi-share me-2"></i>Share Profile
                        </a>
                      </li>
                      <li>
                        <a class="dropdown-item" href="#">
                          <i class="bi bi-download me-2"></i>Export Data
                        </a>
                      </li>
                      <li>
                        <a class="dropdown-item" href="#">
                          <i class="bi bi-archive me-2"></i>Archive
                        </a>
                      </li>
                      <li><hr class="dropdown-divider" /></li>
                      <li>
                        <a class="dropdown-item text-danger" href="#">
                          <i class="bi bi-trash me-2"></i>Delete
                        </a>
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    
    <div v-if="editModal" class="modal fade show d-block" style="background: rgba(0,0,0,0.5); z-index: 1050;">
      <div class="modal-dialog modal-dialog-centered modal-fullscreen-sm-down">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title">Edit Candidate Information</h5>
            <button type="button" class="btn-close" @click="closeEditModal"></button>
          </div>
          <div class="modal-body">
            <div class="row">
              <div class="col-12 col-md-6">
                <div class="mb-3">
                  <label class="form-label">Current Organization</label>
                  <input v-model="form.organization" type="text" class="form-control" />
                </div>
                <div class="mb-3">
                  <label class="form-label">Skills</label>
                  <input v-model="form.skills" type="text" class="form-control" />
                </div>
                <div class="mb-3">
                  <label class="form-label">Available From</label>
                  <input v-model="form.availableFrom" type="text" class="form-control" />
                </div>
                <div class="mb-3">
                  <label class="form-label">Current Salary</label>
                  <input v-model="form.currentSalary" type="text" class="form-control" />
                </div>
                <div class="mb-3">
                  <label class="form-label">Notice Period</label>
                  <input v-model="form.noticePeriod" type="text" class="form-control" />
                </div>
              </div>
              <div class="col-12 col-md-6">
                <div class="mb-3">
                  <label class="form-label">Date of Birth</label>
                  <input v-model="form.dob" type="text" class="form-control" />
                </div>
                <div class="mb-3">
                  <label class="form-label">Total Experience</label>
                  <input v-model="form.totalExperience" type="text" class="form-control" />
                </div>
                <div class="mb-3">
                  <label class="form-label">Relevant Experience</label>
                  <input v-model="form.relevantExperience" type="text" class="form-control" />
                </div>
                <div class="mb-3">
                  <label class="form-label">Salary Expectation</label>
                  <input v-model="form.salaryExpectation" type="text" class="form-control" />
                </div>
                <div class="mb-3">
                  <label class="form-label">Status</label>
                  <input v-model="form.status" type="text" class="form-control" />
                </div>
              </div>
            </div>
          </div>
          <div class="modal-footer">
            <button class="btn btn-secondary" @click="closeEditModal">Cancel</button>
            <button class="btn btn-primary" @click="saveEdit">Save Changes</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserProfileSection",
  props: {
    currentCandidateInfo: {
      type: Object,
      default: () => ({
        organization: "World Bank Group",
        skills: "HTML, CSS, Javascript",
        availableFrom: "Jul 14, 2023",
        currentSalary: "$6000",
        noticePeriod: "90 Days",
        dob: "15 June 1993",
        totalExperience: "5 Years",
        relevantExperience: "7 Years",
        salaryExpectation: "$9000",
        status: "Submitted to Client",
      }),
    },
  },
  data() {
    return {
      editModal: false,
      form: {
        organization: "World Bank Group",
        skills: "HTML, CSS, Javascript",
        availableFrom: "Jul 14, 2023",
        currentSalary: "$6000",
        noticePeriod: "90 Days",
        dob: "15 June 1993",
        totalExperience: "5 Years",
        relevantExperience: "7 Years",
        salaryExpectation: "$9000",
        status: "Submitted to Client",
      },
    };
  },
  watch: {
    currentCandidateInfo: {
      handler(newInfo) {
      
        this.form = { ...this.form, ...newInfo };
      },
      deep: true,
      immediate: true,
    },
  },
  methods: {
    openEditModal() {
     
      this.form = { ...this.currentCandidateInfo };
      this.editModal = true;
    },
    closeEditModal() {
      this.editModal = false;
    },
    saveEdit() {
   
      this.$emit('update-candidate-info', this.form);
      this.closeEditModal();
    },
  },
};
</script>

<style scoped>
.user-profile-section{position:relative}
.user-image{width:60px;height:60px;object-fit:cover}
.user-name{color:#343a40;font-weight:600}
.user-title{color:#6c757d}
.location-info{color:#6c757d}
.social-icons i{cursor:pointer;transition:color .2s ease}
.social-icons i:hover{color:#007bff}
.action-buttons-container{display:flex;justify-content:flex-end;width:100%}
.action-btn{transition:all .2s ease;border-radius:6px;font-size:.875rem;padding:.375rem .75rem}
.action-btn:hover{transform:translateY(-1px);box-shadow:0 2px 4px rgba(0,0,0,.1)}
.icon-buttons .action-btn{width:36px;height:36px;padding:0;display:flex;align-items:center;justify-content:center}
.modal{backdrop-filter:blur(5px)}
.modal-dialog{max-width:800px}
.modal-content{border-radius:8px;box-shadow:0 10px 30px rgba(0,0,0,.3)}
.modal-header{border-bottom:1px solid #dee2e6;background-color:#f8f9fa;border-radius:8px 8px 0 0}
.modal-footer{border-top:1px solid #dee2e6;background-color:#f8f9fa;border-radius:0 0 8px 8px}
.form-label{font-weight:500;color:#495057;margin-bottom:.5rem}
.form-control{border:1px solid #ced4da;border-radius:4px;padding:.5rem .75rem;transition:border-color .15s ease-in-out,box-shadow .15s ease-in-out}
.form-control:focus{border-color:#007bff;box-shadow:0 0 0 .2rem rgba(0,123,255,.25)}
@media (max-width:768px){
.user-image{width:50px;height:50px}
.user-name{font-size:1.1rem!important}
.user-title{font-size:.8rem}
.location-info{display:block;margin-top:.25rem}
.modal-dialog{margin:.5rem;max-width:calc(100% - 1rem)}
.modal-body{padding:1rem}
.modal-footer{padding:1rem}
.form-control{font-size:16px}
}
@media (max-width:576px){
.user-info-container{flex-direction:column;text-align:center}
.user-image-container{margin-bottom:1rem;margin-right:0!important}
.user-header{flex-direction:column!important;align-items:center!important}
.user-name{margin-bottom:.5rem!important;margin-right:0!important}
.social-icons{justify-content:center}
.action-buttons{flex-direction:column;align-items:stretch}
.icon-buttons{justify-content:center;margin-top:.5rem}
.modal-dialog{margin:0;max-width:100%;height:100%}
.modal-content{border-radius:0;height:100%;display:flex;flex-direction:column}
.modal-body{flex:1;overflow-y:auto}
}
@media (min-width:769px) and (max-width:1024px){
.action-buttons{gap:.75rem!important}
.user-image{width:55px;height:55px}
}
</style>

