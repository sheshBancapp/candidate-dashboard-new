<template>
  <div class="recent-jobs-section">
    <div class="card border-0">
      
      
      <div class="card-body p-0">
        <ul class="nav nav-tabs nav-fill border-0" id="recentJobsTabs" role="tablist">
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link active" 
              id="add-details-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#add-details" 
              type="button" 
              role="tab"
              @click="activeTab = 'add-details'"
            >
              Add Details
            </button>
          </li>
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link" 
              id="assigned-jobs-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#assigned-jobs" 
              type="button" 
              role="tab"
              @click="activeTab = 'assigned-jobs'"
            >
              Assigned Jobs
            </button>
          </li>
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link" 
              id="related-emails-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#related-emails" 
              type="button" 
              role="tab"
              @click="activeTab = 'related-emails'"
            >
              Related Emails
            </button>
          </li>
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link" 
              id="candidate-questions-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#candidate-questions" 
              type="button" 
              role="tab"
              @click="activeTab = 'candidate-questions'"
            >
              Candidate Questions
            </button>
          </li>
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link" 
              id="hotlists-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#hotlists" 
              type="button" 
              role="tab"
              @click="activeTab = 'hotlists'"
            >
              Hotlists
            </button>
          </li>
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link" 
              id="related-deals-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#related-deals" 
              type="button" 
              role="tab"
              @click="activeTab = 'related-deals'"
            >
              Related Deals
            </button>
          </li>
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link" 
              id="contacts-pitched-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#contacts-pitched" 
              type="button" 
              role="tab"
              @click="activeTab = 'contacts-pitched'"
            >
              Contact(s) Pitched
            </button>
          </li>
        </ul>
        <div class="tab-content" id="recentJobsTabContent">
          
         
          <div class="tab-pane fade show active" id="add-details" role="tabpanel">
            <div class="p-2">
              <div class="d-flex justify-content-between align-items-center mb-4">
                <div>
                  <h4 class="mb-1 fw-semibold small">Details of the job</h4>
                </div>
                
              </div>
              <div class="row g-3">
                <div v-for="job in assignedJobs" :key="job.id" class="col-12">
                  <div class="card">
                    <div class="card-body small">
                      <div class="row align-items-center">
                        <div class="col-md-4">
                          <div class="d-flex align-items-center">
                            <div class="profile-initial me-3">
                              <span class="initial-text">{{ getProfileInitial(job.profileName) }}</span>
                            </div>
                            <div>
                              <h6 class="mb-0 fw-bold small">{{ job.profileName }}</h6>
                              <small class="text-muted">{{ job.subHeading }}</small>
                            </div>
                          </div>
                        </div>

                        <div class="col-md-3">
                          <div class="d-flex flex-column">
                            <span class="fw-normal small"><i class="fa-regular fa-circle-user me-2 small"></i>{{ job.userName }}</span>
                            <small class="text-muted"><i class="bi bi-clock me-2"></i>{{ job.date }}</small>
                          </div>
                        </div>

                        <div class="col-md-2">
                          <span class="badge text-bg-light">{{ job.assignedPills }}</span>
                        </div>

                        <div class="col-md-2">
                          <button class="btn btn-outline-secondary btn-sm bg-white text-black">
                            View Files
                          </button>
                        </div>

                        <div class="col-md-1 d-flex justify-content-center justify-md-content-end">
                         <div class="form-check form-switch">
                          <input 
                            class="form-check-input" 
                            type="checkbox" 
                            :id="'toggle-' + job.id" 
                            :checked="job.isActive"
                          />
                        </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="tab-pane fade" id="assigned-jobs" role="tabpanel">
            <div class="p-2">
              <div class="d-flex justify-content-between align-items-center mb-4">
                <div>
                  <h4 class="mb-1 fw-semibold small">Assigned jobs to William Sample</h4>
                </div>
                <div class="d-flex gap-2">
                  <button class="btn btn-primary btn-sm p-2">
                   Assign to Jobs
                  </button>
                  <button class="btn btn-outline-secondary btn-sm p-2">
                    View All Assigned Jobs
                  </button>
                </div>
              </div>
              <div class="row g-3">
                <div v-for="job in assignedJobs" :key="job.id" class="col-12">
                  <div class="card">
                    <div class="card-body small">
                      <div class="row align-items-center">
                        <div class="col-md-4">
                          <div class="d-flex align-items-center">
                            <div class="profile-initial me-3">
                              <span class="initial-text">{{ getProfileInitial(job.profileName) }}</span>
                            </div>
                            <div>
                              <h6 class="mb-0 fw-bold small">{{ job.profileName }}</h6>
                              <small class="text-muted">{{ job.subHeading }}</small>
                            </div>
                          </div>
                        </div>

                        <div class="col-md-3">
                          <div class="d-flex flex-column">
                            <span class="fw-normal small"><i class="fa-regular fa-circle-user me-2 small"></i>{{ job.userName }}</span>
                            <small class="text-muted"><i class="bi bi-clock me-2"></i>{{ job.date }}</small>
                          </div>
                        </div>

                        <div class="col-md-2">
                          <span class="badge text-bg-light">{{ job.assignedPills }}</span>
                        </div>

                        <div class="col-md-2">
                          <button class="btn btn-outline-secondary btn-sm bg-white text-black">
                            View Files
                          </button>
                        </div>

                        <div class="col-md-1 d-flex justify-content-center justify-md-content-end">
                         <div class="form-check form-switch">
                          <input 
                            class="form-check-input" 
                            type="checkbox" 
                            :id="'toggle-' + job.id" 
                            :checked="job.isActive"
                          />
                        </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          
          <div class="tab-pane fade" id="related-emails" role="tabpanel">
            <div class="p-4">
              <div class="text-center py-5">
               
                <h5>Related Emails</h5>
                <p class="text-muted">View and manage emails related to job applications</p>
               
              </div>
            </div>
          </div>

         
          <div class="tab-pane fade" id="candidate-questions" role="tabpanel">
            <div class="p-4">
              <div class="text-center py-5">
                
                <h5>Candidate Questions</h5>
                <p class="text-muted">Review and answer questions from candidates</p>
               
              </div>
            </div>
          </div>

          <div class="tab-pane fade" id="hotlists" role="tabpanel">
            <div class="p-4">
              <div class="text-center py-5">
               
                <h5>Hotlists</h5>
                <p class="text-muted">Manage priority candidate lists</p>
                
              </div>
            </div>
          </div>

          <div class="tab-pane fade" id="related-deals" role="tabpanel">
            <div class="p-4">
              <div class="text-center py-5">
                
                <h5>Related Deals</h5>
                <p class="text-muted">Track deals and opportunities related to jobs</p>
               
              </div>
            </div>
          </div>

          <div class="tab-pane fade" id="contacts-pitched" role="tabpanel">
            <div class="p-4">
              <div class="text-center py-5">
               
                <h5>Contact(s) Pitched</h5>
                <p class="text-muted">Manage contacts that have been pitched for jobs</p>
                
              </div>
            </div>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "RecentJobsSection",
  data() {
    return {
      activeTab: 'add-details',
      assignedJobs: [
        {
          id: 1,
          profileName: "Senior Product Manager",
          subHeading: "Recruit CRM",
          userName: "William Sample",
          date: "Jul 10, 2023",
          assignedPills: "Assigned",
          isActive: true,
        },
        {
          id: 2,
          profileName: "Product Manager",
          subHeading: "Product Manager",
          userName: "William Demo",
          date: "Jul 14, 2024",
          assignedPills: "Assigned",
          isActive: true,
        },
        {
          id: 3,
          profileName: "Marketing Manager",
          subHeading: "UX Designer",
          userName: "Will Sample",
          date: "Jul 10, 2025",
          assignedPills: "Assigned",
          isActive: false,
        },
        {
          id: 4,
          profileName: "Development Manager",
          subHeading: "Backend Developer",
          userName: "david.kim",
          date: "Jul 20, 2025",
          assignedPills: "Assigned",
          isActive: true,
        }
      ]
    };
  },
  methods: {
    handleTabChange(tabName) {
      this.activeTab = tabName;
    },
    getProfileInitial(name) {
        return name
          .split(' ')
          .filter(word => word.length > 0)          
          .slice(0, 2)                              
          .map(word => word[0])                     
          .join('')
          .toUpperCase();
      }
  }
};
</script>

<style scoped>
.nav-tabs{background-color:#E9ECEF;border:0;flex-wrap:nowrap;display:flex;align-items:start;justify-content:flex-start;white-space:nowrap}
.nav-tabs .nav-link{border:none;color:#6c757d;font-weight:500;font-size:12px;padding:1rem .8rem;border-radius:0;transition:all .2s ease;white-space:nowrap;flex-shrink:0;min-width:fit-content;border-bottom:3px solid transparent}
.nav-tabs .nav-link:hover{color:#495057;background-color:#e9ecef;border-bottom:3px solid #1F5FAC}
.nav-tabs .nav-link.active{color:#1F5FAC;background-color:#fff;border-bottom:3px solid #1F5FAC;font-weight:600}
.tab-content{min-height:400px}
.tab-pane{padding:1rem}
.badge{font-size:.75rem;padding:.5em .75em}
.form-check-input:checked{background-color:#1F5FAC;border-color:#1F5FAC}
.btn{transition:all .2s ease-in-out}
.profile-initial{width:40px;height:40px;border-radius:50%;display:flex;align-items:center;justify-content:center;background:#FBDDB3;color:#F08C00;font-weight:600;font-size:1rem}
.initial-text{line-height:1;text-align:center}
@media (max-width: 768px) {
.nav-tabs .nav-link{padding:.75rem 1rem;font-size:.875rem;white-space:nowrap;flex-shrink:0}
.card-body .row{flex-direction:column;gap:1rem}
.col-md-2,.col-md-3{text-align:center}
.d-flex.justify-content-between{flex-direction:column;gap:1rem;align-items:stretch}
.btn-group{flex-direction:column;width:100%}
}
@media (max-width: 576px) {
.nav-tabs{flex-wrap:nowrap;overflow-x:auto}
.nav-tabs .nav-link{flex-shrink:0;min-width:fit-content;white-space:nowrap}
}
</style>
