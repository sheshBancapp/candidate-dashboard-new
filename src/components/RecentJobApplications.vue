<template>
  <div class="recent-job-applications">
    <div class="card border-0">
      <div class="card-header bg-transparent border-0 pb-0">
        <div class="d-flex justify-content-between align-items-center">
          <h5 class="mb-0 fw-bold">Recent Job Applications</h5>
          <div class="d-flex gap-2">
            <select 
              v-model="selectedStatus" 
              class="form-select form-select-sm" 
              style="width: auto;"
              @change="filterApplications"
            >
              <option value="">All Status</option>
              <option value="Applied">Applied</option>
              <option value="In Review">In Review</option>
              <option value="Interview">Interview</option>
              <option value="Hired">Hired</option>
              <option value="Rejected">Rejected</option>
            </select>
            <button class="btn btn-outline-primary btn-sm" @click="exportData">
              <i class="bi bi-download me-1"></i>Export
            </button>
          </div>
        </div>
      </div>
      
      <div class="card-body p-0">
        <div class="table-responsive">
          <table class="table table-hover mb-0">
            <thead class="table-light">
              <tr>
                <th class="border-0">Position</th>
                <th class="border-0">Company</th>
                <th class="border-0">Applied Date</th>
                <th class="border-0">Status</th>
                <th class="border-0">Actions</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="application in filteredApplications" :key="application.id">
                <td>
                  <div class="d-flex align-items-center">
                    <div class="profile-initial me-3">
                      <span class="initial-text">{{ getProfileInitial(application.position) }}</span>
                    </div>
                    <div>
                      <h6 class="mb-0">{{ application.position }}</h6>
                      <small class="text-muted">{{ application.type }}</small>
                    </div>
                  </div>
                </td>
                <td>
                  <div class="d-flex align-items-center">
                    <div class="company-logo me-2">
                      <img :src="application.companyLogo" :alt="application.company" class="rounded" />
                    </div>
                    <span class="fw-medium">{{ application.company }}</span>
                  </div>
                </td>
                <td>
                  <div class="d-flex flex-column">
                    <span class="fw-medium">{{ application.appliedDate }}</span>
                    <small class="text-muted">{{ application.daysAgo }}</small>
                  </div>
                </td>
                <td>
                  <span :class="`badge bg-${application.statusColor}`">
                    {{ application.status }}
                  </span>
                </td>
                <td>
                  <div class="btn-group btn-group-sm">
                    <button class="btn btn-outline-primary" @click="viewApplication(application)">
                      <i class="bi bi-eye me-1"></i>View
                    </button>
                    <button class="btn btn-outline-secondary" @click="editApplication(application)">
                      <i class="bi bi-pencil me-1"></i>Edit
                    </button>
                    <button class="btn btn-outline-danger" @click="deleteApplication(application)">
                      <i class="bi bi-trash me-1"></i>
                    </button>
                  </div>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      
        <div v-if="filteredApplications.length === 0" class="text-center py-5">
          <div class="empty-state">
            <i class="bi bi-briefcase fs-1 text-muted mb-3"></i>
            <h6 class="text-muted">No job applications found</h6>
            <p class="text-muted small">Try adjusting your filters or add a new application</p>
            <button class="btn btn-primary btn-sm" @click="addNewApplication">
              <i class="bi bi-plus me-1"></i>Add Application
            </button>
          </div>
        </div>
      </div>
      
     
      <div v-if="filteredApplications.length > 0" class="card-footer bg-transparent border-0">
        <div class="d-flex justify-content-between align-items-center">
          <small class="text-muted">
            Showing {{ startIndex + 1 }}-{{ endIndex }} of {{ filteredApplications.length }} applications
          </small>
          <nav aria-label="Job applications pagination">
            <ul class="pagination pagination-sm mb-0">
              <li class="page-item" :class="{ disabled: currentPage === 1 }">
                <button class="page-link" @click="changePage(currentPage - 1)">
                  <i class="bi bi-chevron-left"></i>
                </button>
              </li>
              <li 
                v-for="page in visiblePages" 
                :key="page" 
                class="page-item"
                :class="{ active: page === currentPage }"
              >
                <button class="page-link" @click="changePage(page)">{{ page }}</button>
              </li>
              <li class="page-item" :class="{ disabled: currentPage === totalPages }">
                <button class="page-link" @click="changePage(currentPage + 1)">
                  <i class="bi bi-chevron-right"></i>
                </button>
              </li>
            </ul>
          </nav>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "RecentJobApplications",
  data() {
    return {
      selectedStatus: "",
      currentPage: 1,
      itemsPerPage: 5,
      applications: [
        {
          id: 1,
          position: "Senior Product Manager",
          type: "Full-time",
          company: "TechCorp Inc.",
          companyLogo: "",
          appliedDate: "Dec 15, 2024",
          daysAgo: "2 days ago",
          status: "In Review",
          statusColor: "warning"
        },
        {
          id: 2,
          position: "Product Lead",
          type: "Full-time",
          company: "InnovateTech",
          companyLogo: "",
          appliedDate: "Dec 12, 2024",
          daysAgo: "5 days ago",
          status: "Hired",
          statusColor: "success"
        },
        {
          id: 3,
          position: "Product Strategy",
          type: "Contract",
          company: "StrategyCorp",
          companyLogo: "",
          appliedDate: "Dec 10, 2024",
          daysAgo: "1 week ago",
          status: "Interview",
          statusColor: "primary"
        },
        {
          id: 4,
          position: "UX Designer",
          type: "Full-time",
          company: "DesignHub",
          companyLogo: "",
          appliedDate: "Dec 8, 2024",
          daysAgo: "1 week ago",
          status: "Applied",
          statusColor: "info"
        },
        {
          id: 5,
          position: "Frontend Developer",
          type: "Part-time",
          company: "CodeWorks",
          companyLogo: "",
          appliedDate: "Dec 5, 2024",
          daysAgo: "2 weeks ago",
          status: "Rejected",
          statusColor: "danger"
        }
      ]
    };
  },
  computed: {
    filteredApplications() {
      if (!this.selectedStatus) {
        return this.applications;
      }
      return this.applications.filter(app => app.status === this.selectedStatus);
    },
    totalPages() {
      return Math.ceil(this.filteredApplications.length / this.itemsPerPage);
    },
    startIndex() {
      return (this.currentPage - 1) * this.itemsPerPage;
    },
    endIndex() {
      return Math.min(this.startIndex + this.itemsPerPage, this.filteredApplications.length);
    },
    visiblePages() {
      const pages = [];
      const maxVisible = 5;
      let start = Math.max(1, this.currentPage - Math.floor(maxVisible / 2));
      let end = Math.min(this.totalPages, start + maxVisible - 1);
      
      if (end - start + 1 < maxVisible) {
        start = Math.max(1, end - maxVisible + 1);
      }
      
      for (let i = start; i <= end; i++) {
        pages.push(i);
      }
      
      return pages;
    }
  },
  methods: {
    filterApplications() {
      this.currentPage = 1;
    },
    changePage(page) {
      if (page >= 1 && page <= this.totalPages) {
        this.currentPage = page;
      }
    },
    viewApplication(application) {
      this.$emit('view-application', application);
      console.log('Viewing application:', application);
    },
    editApplication(application) {
      this.$emit('edit-application', application);
      console.log('Editing application:', application);
    },
    deleteApplication(application) {
      if (confirm(`Are you sure you want to delete the application for ${application.position}?`)) {
        this.applications = this.applications.filter(app => app.id !== application.id);
        this.$emit('delete-application', application);
        console.log('Deleted application:', application);
      }
    },
    addNewApplication() {
      this.$emit('add-application');
      console.log('Adding new application');
    },
    exportData() {
      const data = this.filteredApplications.map(app => ({
        Position: app.position,
        Company: app.company,
        'Applied Date': app.appliedDate,
        Status: app.status,
        Type: app.type
      }));
      
      const csv = this.convertToCSV(data);
      const blob = new Blob([csv], { type: 'text/csv' });
      const url = window.URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = 'job-applications.csv';
      a.click();
      window.URL.revokeObjectURL(url);
      
      this.$emit('export-data', data);
    },
    convertToCSV(data) {
      const headers = Object.keys(data[0]);
      const csvRows = [headers.join(',')];
      
      for (const row of data) {
        const values = headers.map(header => {
          const value = row[header];
          return `"${value}"`;
        });
        csvRows.push(values.join(','));
      }
      
      return csvRows.join('\n');
    },
    getProfileInitial(position) {
      if (!position) return '';
      return position.split(' ').map(word => word[0]).join('').toUpperCase();
    }
  }
};
</script>

<style scoped>
.recent-job-applications{margin-top:2rem}
.company-logo img{width:32px;height:32px;object-fit:cover}
.profile-initial{width:32px;height:32px;background-color:#007bff;border-radius:50%;display:flex;align-items:center;justify-content:center;color:#fff;font-weight:700;font-size:.875rem}
.initial-text{display:block;text-align:center;width:100%}
.empty-state{padding:2rem}
.empty-state i{display:block;margin:0 auto}
.table th{font-weight:600;color:#495057;border-bottom:2px solid #dee2e6}
.table td{vertical-align:middle;padding:1rem .75rem}
.btn-group .btn{border-radius:.375rem;margin-right:.25rem}
.btn-group .btn:last-child{margin-right:0}
.pagination .page-link{border-radius:.375rem;margin:0 .125rem;border:1px solid #dee2e6}
.pagination .page-item.active .page-link{background-color:#1F5FAC;border-color:#1F5FAC}
.card-footer{background-color:#f8f9fa;border-top:1px solid #dee2e6}
@media (max-width: 768px) {
.card-header .d-flex{flex-direction:column;gap:1rem;align-items:stretch}
.btn-group{flex-direction:column;width:100%}
.btn-group .btn{margin-right:0;margin-bottom:.25rem}
.table-responsive{font-size:.875rem}
.company-logo img{width:24px;height:24px}
}
</style>
