<template>
  <div class="dashboard-container">
    <div class="row g-0">
      <!-- Main Content Column -->
      <div class="col-12 col-xl-8 p-0 m-0">
        <TabNav
          currentPage="William"
          candidateId="id-231"
          @request-update="handleRequestUpdate"
          @previous="handlePrevious"
          @next="handleNext"
        />
       
        <UserProfileSection 
          :currentCandidateInfo="candidateInfo" 
          @update-candidate-info="handleUpdateCandidateInfo" 
        />
       
        <div class="profile-card-container">
          <ProfileCard :candidateInfo="candidateInfo" />
        </div>
        
        <!-- Recent Jobs Section with Tabs -->
        <RecentJobsSection />
      </div>

      <!-- Right Column: Quick Actions -->
      <div class="col-12 col-xl-4 p-0 m-0">
        <QuickActionsTabs />
      </div>
    </div>
  </div>
</template>

<script>
import RecentJobsSection from '../components/RecentJobsSection.vue'
import QuickActionsTabs from '../components/QuickActionsTabs.vue'
import UserProfileSection from '../components/UserProfileSection.vue'
import ProfileCard from '../components/ProfileCard.vue'
import TabNav from "../components/TabNav.vue";

export default {
  name: "DashboardComponent",
  components: {
    RecentJobsSection,
    QuickActionsTabs,
    UserProfileSection,
    ProfileCard,
    TabNav,
  },
  data() {
    return {
      candidateInfo: {
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
  methods: {
    handleRequestUpdate() {
    },
    handlePrevious() {
    },
    handleNext() {
    },
    handleUpdateCandidateInfo(updatedInfo) {
      // Update the candidate info when modal saves changes
      this.candidateInfo = { ...this.candidateInfo, ...updatedInfo };
    },
  },
};
</script>

<style scoped>
.dashboard-container {
  padding: 0;
  overflow-x: hidden;
  max-width: 100%;
}

.profile-card-container {
  margin-bottom: 1rem;
}

.timeline-marker {
  width: 12px;
  height: 12px;
  margin-top: 6px;
}

.timeline-item {
  position: relative;
}

.timeline-item:not(:last-child)::after {
  content: '';
  position: absolute;
  left: 5px;
  top: 24px;
  bottom: -12px;
  width: 2px;
  background-color: #e9ecef;
}

.card {
  transition: transform 0.2s ease-in-out;
  max-width: 100%;
}

.btn {
  transition: all 0.2s ease-in-out;
}

.bg-opacity-10 {
  --bs-bg-opacity: 0.1;
}

.row {
  margin-left: 0;
  margin-right: 0;
}

.col-xl-8,
.col-xl-4 {
  padding-left: 1rem;
  padding-right: 1rem;
}

.card-body {
  word-wrap: break-word;
  overflow-wrap: break-word;
}

/* Mobile Responsive Styles */
@media (max-width: 1200px) {
  .col-xl-8,
  .col-xl-4 {
    padding-left: 0.75rem;
    padding-right: 0.75rem;
  }
}

@media (max-width: 768px) {
  .dashboard-container {
    padding: 0;
  }
  
  .col-xl-8,
  .col-xl-4 {
    padding-left: 0.5rem;
    padding-right: 0.5rem;
  }
  
  .profile-card-container {
    margin-bottom: 0.75rem;
  }
}

@media (max-width: 576px) {
  .col-xl-8,
  .col-xl-4 {
    padding-left: 0.25rem;
    padding-right: 0.25rem;
  }
  
  .profile-card-container {
    margin-bottom: 0.5rem;
  }
}

/* Tablet adjustments */
@media (min-width: 769px) and (max-width: 1024px) {
  .col-xl-8,
  .col-xl-4 {
    padding-left: 0.75rem;
    padding-right: 0.75rem;
  }
}
</style>
