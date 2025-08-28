<template>
  <div class="card rounded-0 border-0">
    <div class="contact-info-section px-3 py-3">
      <div class="row align-items-center">
        <div class="col-12 col-md-6 col-lg-8">
          <div class="contact-links d-flex flex-column flex-md-row">
            <div class="contact-item mb-2 mb-md-0 me-md-3">
              <i class="bi bi-envelope me-1"></i>
              <a :href="'mailto:' + profile.email" class="text-decoration-none">{{ profile.email }}</a>
            </div> 
            <div class="contact-item">
              <i class="bi bi-telephone me-1"></i>
              <a :href="'tel:' + profile.phone" class="text-decoration-none">{{ profile.phone }}</a>
            </div>
          </div>
        </div>
        <div class="col-12 col-md-6 col-lg-4">
          <div class="user-meta d-flex flex-column flex-sm-row align-items-start align-items-sm-center justify-content-end mt-3 mt-md-0">
            <div class="user-info me-sm-3 mb-2 mb-sm-0">
              <i class="fa-regular fa-circle-user me-1"></i>
              <span class="user-name">{{ item.userName }}</span>
            </div>
            <div class="date-time">
              <i class="bi bi-clock me-1"></i>
              <span class="small">{{ formatDateTime(item.date, item.time) }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="candidate-info-section p-3 p-md-4 small">        
      <div class="row">
        <div class="col-12 col-lg-6">
          <div class="mb-3">
            <div class="row small">
              <div class="col-6 col-md-6 col-lg-4">
              <strong>Current Organization</strong>
              </div>
              <div class="col-6 col-md-6 col-lg-8">
                {{ profile.organization }}
              </div>
            </div>
          </div>
          
          <div class="mb-3">
            <div class="row small">
              <div class="col-6 col-md-6 col-lg-4">
                <strong>Skills</strong>
              </div>
              <div class="col-6 col-md-6 col-lg-8">
                {{ profile.skills }}
              </div>
            </div>
          </div>

          <div class="mb-3">
            <div class="row small">
              <div class="col-6 col-md-6 col-lg-4">
                <strong>Available From</strong>
              </div>
              <div class="col-6 col-md-6 col-lg-8">
                {{ profile.availableFrom }}
              </div>
            </div>
          </div>
          
          <div class="mb-3">
            <div class="row small">
              <div class="col-6 col-md-6 col-lg-4">
                <strong>Current Salary</strong>
              </div>
              <div class="col-6 col-md-6 col-lg-8">
                {{ profile.currentSalary }}
              </div>
            </div>
          </div>

          <div class="mb-3">
            <div class="row small">
              <div class="col-6 col-md-6 col-lg-4">
                <strong>Notice Period</strong>
              </div>
              <div class="col-6 col-md-6 col-lg-8">
                {{ profile.noticePeriod }}
              </div>
            </div>
          </div>
        </div>
        
        <div class="col-12 col-lg-6">
          <div class="mb-3">
            <div class="row small">
              <div class="col-6 col-md-6 col-lg-4">
                <strong>Date of Birth</strong>
              </div>
              <div class="col-6 col-md-6 col-lg-8">
                {{ profile.dob }}
              </div>
            </div>
          </div>

          <div class="mb-3">
            <div class="row small">
              <div class="col-6 col-md-6 col-lg-4">
                <strong>Total Experience</strong>
              </div>
              <div class="col-6 col-md-6 col-lg-8">
                {{ profile.totalExperience }}
              </div>
            </div>
          </div>

          <div class="mb-3">
            <div class="row small">
              <div class="col-6 col-md-6 col-lg-4">
                <strong> Relevant Experience</strong>
              </div>
              <div class="col-6 col-md-6 col-lg-8">
                {{ profile.relevantExperience }}
              </div>
            </div>
          </div>

          <div class="mb-3">
            <div class="row small">
              <div class="col-6 col-md-6 col-lg-4">
                <strong> Salary Expectation</strong>
              </div>
              <div class="col-6 col-md-6 col-lg-8">
                {{ profile.salaryExpectation }}
              </div>
            </div>
          </div>

          <div class="mb-3 ">
            <div class="row small">
              <div class="col-6 col-md-6 col-lg-4">
                <strong> Status</strong>
              </div>
              <div class="col-6 col-md-6 col-lg-8">
                {{ profile.status }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.contact-info-section{border-top:1px solid #cdcdcd;border-bottom:1px solid #cdcdcd}
.contact-links{font-size:.875rem}
.contact-item{display:flex;align-items:center;color:#495057}
.contact-item a{color:#1f5fac;text-decoration:none}
.contact-item a:hover{text-decoration:underline}
.user-meta{font-size:.875rem}
.user-name{color:#495057;font-weight:500}
.date-time{color:#6c757d}
.candidate-info-section{background-color:#fff}
.info-group{border-bottom:1px solid #f1f3f4;padding-bottom:.75rem}
.info-group:last-child{border-bottom:none;padding-bottom:0}
.info-label{margin:0;font-size:.875rem;color:#343a40;font-weight:500}
.info-value{margin:0;font-size:.875rem;color:#495057;word-break:break-word}
@media (max-width:768px){
.contact-info-section{padding:1rem!important}
.candidate-info-section{padding:1rem!important}
.info-group{padding-bottom:1rem}
.info-label,.info-value{font-size:.8rem}
.contact-links{font-size:.8rem}
.user-meta{font-size:.8rem}
}
@media (max-width:576px){
.contact-item{margin-bottom:.5rem}
.user-meta{flex-direction:column;align-items:flex-start!important}
.user-info{margin-bottom:.5rem}
}
</style>


<script>
export default {
  name: "ProfileCard",
  props: {
    item: {
      type: Object,
      default: () => ({
        userName: "Phyllis Yang",
        date: "2025-07-12",  
        time: "11:54",      
      }),
    },
    candidateInfo: {
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
      profile: {
        name: "William Sample",
        title: "Senior Product Manager",
        location: "Dallas, United States",
        email: "williamsample@gmail.com",
        phone: "+1 9021232326",
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
    candidateInfo: {
      handler(newInfo) {
        this.profile = { ...this.profile, ...newInfo };
      },
      deep: true,
      immediate: true,
    },
  },
  methods: {
    formatDateTime(dateStr, timeStr) {
      const dateTimeStr = `${dateStr} ${timeStr}`;
      const dateObj = new Date(dateTimeStr);

      return dateObj.toLocaleString("en-US", {
        month: "short",
        day: "2-digit",
        year: "numeric",
        hour: "numeric",
        minute: "2-digit",
        hour12: true,
      }).replace("AM", "am").replace("PM", "pm");
    },
  },
};
</script>
