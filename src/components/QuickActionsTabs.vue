<template>
  <div class="quick-actions-tabs">
    <div class="card border-0 h-100 bg-transparent">
     
      <div class="card-body p-0 bg-transparent">
       
        <div class="icons-section p-3  bg-white">
          <div class="d-flex align-items-center">
            <div class="icon-item text-center">
              <div class="icon-circle bg-primary bg-opacity-10 mb-2">
                <i class="bi bi-sticky text-primary fs-5"></i>
              </div>
             
            </div>
            <div class="icon-item text-center">
              <div class="icon-circle bg-success bg-opacity-10 mb-2">
                <i class="bi bi-telephone text-success fs-5"></i>
              </div>
              
            </div>
            <div class="icon-item text-center">
              <div class="icon-circle bg-warning bg-opacity-10 mb-2">
                <i class="bi bi-check-circle text-warning fs-5"></i>
              </div>
              
            </div>
            <div class="icon-item text-center">
              <div class="icon-circle bg-info bg-opacity-10 mb-2">
                <i class="bi bi-calendar text-info fs-5"></i>
              </div>
              
            </div>
          </div>
        </div>
        <ul class="nav nav-tabs nav-fill border-0" id="quickActionsTabs" role="tablist">
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link active" 
              id="all-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#all" 
              type="button" 
              role="tab"
              @click="activeTab = 'all'"
            >
              All
            </button>
          </li>
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link" 
              id="notes-calls-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#notes-calls" 
              type="button" 
              role="tab"
              @click="activeTab = 'notes-calls'"
            >
              Notes & Calls
            </button>
          </li>
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link" 
              id="tasks-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#tasks" 
              type="button" 
              role="tab"
              @click="activeTab = 'tasks'"
            >
              Tasks
            </button>
          </li>
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link" 
              id="meeting-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#meeting" 
              type="button" 
              role="tab"
              @click="activeTab = 'meeting'"
            >
              Meeting
            </button>
          </li>
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link" 
              id="files-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#files" 
              type="button" 
              role="tab"
              @click="activeTab = 'files'"
            >
              Files
            </button>
          </li>
          <li class="nav-item" role="presentation">
            <button 
              class="nav-link" 
              id="details-tab" 
              data-bs-toggle="tab" 
              data-bs-target="#details" 
              type="button" 
              role="tab"
              @click="activeTab = 'details'"
            >
              Details
            </button>
          </li>
        </ul>

        <div class="tab-content" id="quickActionsTabContent">
          
          <div class="tab-pane fade show active " id="all" role="tabpanel">
            <div class="p-3">
              <div v-for="item in allItems" :key="item.id" class="action-card mb-3">
                <div class="card border-0">
                  <div class="card-body p-3">
                    <div class="d-flex align-items-start mb-2">
                      <div class="action-icon me-2">
                        <i :class="item.icon" :style="{ color: item.iconColor }"></i>
                      </div>
                      <div class="flex-grow-1">
                        <span class="action-text">{{ item.text }}</span>
                        <span v-if="item.todo" class="todo-pill ms-2">{{ item.todo }}</span>
                      </div>
                    </div>
                    <div class="action-details">
                      <p class="mb-0" style="font-size: 12px;">{{ item.details }}</p>
                      <span class="mt-2 mb-2 text-blue">1 Association(s)</span>
                    </div>
                    <div class="card-footer bg-transparent border-0 p-0 mt-2">
                      <div class="d-flex justify-content-between align-items-center">
                        <div class="d-flex align-items-center">
                          <i class="fa-regular fa-circle-user me-2 small"></i>
                          <span class="user-name" style="font-size: 12px;">{{ item.userName }}</span>
                        </div>
                        <div class="date-time" style="font-size: 12px;">
                         <i class="bi bi-clock"></i>
                          {{ formatDateTime(item.date, item.time) }}
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="tab-pane fade" id="notes-calls" role="tabpanel">
            <div class="p-3">
              <div v-for="item in notesCallsItems" :key="item.id" class="action-card mb-3">
                <div class="card border-0">
                  <div class="card-body p-3">
                    <div class="d-flex align-items-start mb-2">
                      <div class="action-icon me-2">
                        <i :class="item.icon" :style="{ color: item.iconColor }"></i>
                      </div>
                      <div class="flex-grow-1">
                        <span class="action-text">{{ item.text }}</span>
                        <span v-if="item.todo" class="todo-pill ms-2">{{ item.todo }}</span>
                      </div>
                    </div>
                    <div class="action-details">
                      <p class="mb-0" style="font-size: 12px;">{{ item.details }}</p>
                      <span class="mt-2 mb-2 text-blue">1 Association(s)</span>
                    </div>
                    <div class="card-footer bg-transparent border-0 p-0 mt-2">
                      <div class="d-flex justify-content-between align-items-center">
                        <div class="d-flex align-items-center">
                         <i class="fa-regular fa-circle-user me-2 small"></i>
                          <span class="user-name" style="font-size: 12px;">{{ item.userName }}</span>
                        </div>
                        <div class="date-time" style="font-size: 12px;">
                         <i class="bi bi-clock"></i>
                          {{ formatDateTime(item.date, item.time) }}
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="tab-pane fade" id="tasks" role="tabpanel">
            <div class="p-3">
              <div v-for="item in tasksItems" :key="item.id" class="action-card mb-3">
                <div class="card border-0">
                  <div class="card-body p-3">
                    <div class="d-flex align-items-start mb-2">
                      <div class="action-icon me-2">
                        <i :class="item.icon" :style="{ color: item.iconColor }"></i>
                      </div>
                      <div class="flex-grow-1">
                        <span class="action-text">{{ item.text }}</span>
                        <span v-if="item.todo" class="todo-pill ms-2">{{ item.todo }}</span>
                      </div>
                    </div>
                    <div class="action-details">
                      <p class="mb-0" style="font-size: 12px;">{{ item.details }}</p>
                      <span class="mt-2 mb-2 text-blue">1 Association(s)</span>
                    </div>
                    <div class="card-footer bg-transparent border-0 p-0 mt-2">
                      <div class="d-flex justify-content-between align-items-center">
                        <div class="d-flex align-items-center">
                         <i class="fa-regular fa-circle-user me-2 small"></i>
                          <span class="user-name" style="font-size: 12px;">{{ item.userName }}</span>
                        </div>
                        <div class="date-time" style="font-size: 12px;">
                          <i class="bi bi-clock"></i>
                          {{ formatDateTime(item.date, item.time) }}
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="tab-pane fade" id="meeting" role="tabpanel">
            <div class="p-3">
              <div v-for="item in meetingItems" :key="item.id" class="action-card mb-3">
                <div class="card border-0">
                  <div class="card-body p-3">
                    <div class="d-flex align-items-start mb-2">
                      <div class="action-icon me-2">
                        <i :class="item.icon" :style="{ color: item.iconColor }"></i>
                      </div>
                      <div class="flex-grow-1">
                        <span class="action-text">{{ item.text }}</span>
                        <span v-if="item.todo" class="todo-pill ms-2">{{ item.todo }}</span>
                      </div>
                    </div>
                    <div class="action-details">
                      <p class="mb-0" style="font-size: 12px;">{{ item.details }}</p>
                      <span class="mt-2 mb-2 text-blue">1 Association(s)</span>
                    </div>
                    <div class="card-footer bg-transparent border-0 p-0 mt-2">
                      <div class="d-flex justify-content-between align-items-center">
                        <div class="d-flex align-items-center">
                         <i class="fa-regular fa-circle-user me-2 small"></i>
                          <span class="user-name" style="font-size: 12px;">{{ item.userName }}</span>
                        </div>
                        <div class="date-time" style="font-size: 12px;">
                          <i class="bi bi-clock"></i>
                          {{ formatDateTime(item.date, item.time) }}
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="tab-pane fade" id="files" role="tabpanel">
            <div class="p-3">
              <div v-for="item in filesItems" :key="item.id" class="action-card mb-3">
                <div class="card border-0">
                  <div class="card-body p-3">
                    <div class="d-flex align-items-start mb-2">
                      <div class="action-icon me-2">
                        <i :class="item.icon" :style="{ color: item.iconColor }"></i>
                      </div>
                      <div class="flex-grow-1">
                        <span class="action-text">{{ item.text }}</span>
                        <span v-if="item.todo" class="todo-pill ms-2">{{ item.todo }}</span>
                      </div>
                    </div>
                    <div class="action-details">
                      <p class="mb-0" style="font-size: 12px;">{{ item.details }}</p>
                      <span class="mt-2 mb-2 text-blue">1 Association(s)</span>
                    </div>
                    <div class="card-footer bg-transparent border-0 p-0 mt-2">
                      <div class="d-flex justify-content-between align-items-center">
                        <div class="d-flex align-items-center">
                         <i class="fa-regular fa-circle-user me-2 small"></i>
                          <span class="user-name" style="font-size: 12px;">{{ item.userName }}</span>
                        </div>
                        <div class="date-time" style="font-size: 12px;">
                          <i class="bi bi-clock"></i>
                          {{ formatDateTime(item.date, item.time) }}
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="tab-pane fade" id="details" role="tabpanel">
            <div class="p-3">
              <div v-for="item in detailsItems" :key="item.id" class="action-card mb-3">
                <div class="card border-0">
                  <div class="card-body p-3">
                    <div class="d-flex align-items-start mb-2">
                      <div class="action-icon me-2">
                        <i :class="item.icon" :style="{ color: item.iconColor }"></i>
                      </div>
                      <div class="flex-grow-1">
                        <span class="action-text">{{ item.text }}</span>
                        <span v-if="item.todo" class="todo-pill ms-2">{{ item.todo }}</span>
                      </div>
                    </div>
                    <div class="action-details">
                      <p class="mb-0" style="font-size: 12px;">{{ item.details }}</p>
                      <div class="mt-2 mb-2">
                        <span class="text-blue me-3">{{ item.associations }} Association(s)</span>
                        <span class="text-muted">{{ item.category }}</span>
                      </div>
                      <div class="detail-info mt-2">
                        <div class="row">
                          <div class="col-6">
                            <small class="text-muted">Priority:</small>
                            <div class="priority-badge" :class="item.priority">{{ item.priority }}</div>
                          </div>
                          <div class="col-6">
                            <small class="text-muted">Status:</small>
                            <div class="status-badge" :class="item.status">{{ item.status }}</div>
                          </div>
                        </div>
                        <div class="mt-2">
                          <small class="text-muted">Description:</small>
                          <p class="mb-0 mt-1" style="font-size: 11px;">{{ item.description }}</p>
                        </div>
                      </div>
                    </div>
                    <div class="card-footer bg-transparent border-0 p-0 mt-2">
                      <div class="d-flex justify-content-between align-items-center">
                        <div class="d-flex align-items-center">
                         <i class="fa-regular fa-circle-user me-2 small"></i>
                          <span class="user-name" style="font-size: 12px;">{{ item.userName }}</span>
                        </div>
                        <div class="date-time" style="font-size: 12px;">
                          <i class="bi bi-clock"></i>
                          {{ formatDateTime(item.date, item.time) }}
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
import dayjs from 'dayjs';

export default {
  name: "QuickActionsTabs",
  data() {
    return {
      activeTab: 'all',
      allItems: [
        {
          id: 1,
          icon: 'bi bi-sticky',
          iconColor: '#007bff',
          text: 'Client meeting notes',
          todo: 'Todo',
          details: 'Follow up on project requirements and timeline discussion with the development team.',
          userName: 'William Sample',
          userImage: '',
          date: 'Jul 12',
          time: '11:54 am'
        },
        {
          id: 2,
          icon: 'bi bi-telephone',
          iconColor: '#28a745',
          text: 'Candidate interview call',
          todo: 'Done',
          details: 'Completed initial screening call with Sarah Johnson for Senior Developer position.',
          userName: 'Phyllis Yang',
          userImage: '',
         date: 'Jul 11',
          time: '3:30 pm'
        },
        {
          id: 3,
          icon: 'bi bi-calendar-check',
          iconColor: '#ffc107',
          text: 'Team sync meeting',
          todo: 'Todo',
          details: 'Weekly team alignment meeting to discuss current projects and upcoming deadlines.',
          userName: 'Michael Chen',
          userImage: '',
          date: 'Dec 14',
          time: '3:00 PM'
        },
        {
          id: 4,
          icon: 'bi bi-file-earmark-text',
          iconColor: '#6f42c1',
          text: 'Resume review',
          todo: 'In Progress',
          details: 'Review and evaluate candidate resumes for Product Manager position.',
          userName: 'Emily Rodriguez',
          userImage: '',
          date: 'Dec 14',
          time: '10:30 AM'
        }
      ],
      notesCallsItems: [
        {
          id: 1,
          icon: 'bi bi-sticky',
          iconColor: '#007bff',
          text: 'Client meeting notes',
          todo: 'Todo',
          details: 'Follow up on project requirements and timeline discussion with the development team.',
          userName: 'William Sample',
          userImage: '',
          date: 'Dec 15',
          time: '2:30 PM'
        },
        {
          id: 2,
          icon: 'bi bi-telephone',
          iconColor: '#28a745',
          text: 'Candidate interview call',
          todo: 'Done',
          details: 'Completed initial screening call with Sarah Johnson for Senior Developer position.',
          userName: 'Phyllis Yang',
          userImage: '',
          date: 'Dec 15',
          time: '11:00 AM'
        }
      ],
      tasksItems: [
        {
          id: 1,
          icon: 'bi bi-check-circle',
          iconColor: '#28a745',
          text: 'Review applications',
          todo: 'Todo',
          details: 'Review 15 new job applications received this week and shortlist candidates.',
          userName: 'William Sample',
          userImage: '',
          date: 'Dec 15',
          time: '4:00 PM'
        },
        {
          id: 2,
          icon: 'bi bi-clock',
          iconColor: '#ffc107',
          text: 'Schedule interviews',
          todo: 'In Progress',
          details: 'Schedule second round interviews for shortlisted candidates.',
          userName: 'Phyllis Yang',
          userImage: '',
          date: 'Dec 15',
          time: '1:00 PM'
        }
      ],
      meetingItems: [
        {
          id: 1,
          icon: 'bi bi-calendar-check',
          iconColor: '#ffc107',
          text: 'Team sync meeting',
          todo: 'Todo',
          details: 'Weekly team alignment meeting to discuss current projects and upcoming deadlines.',
          userName: 'Michael Chen',
          userImage: '',
          date: 'Dec 14',
          time: '3:00 PM'
        },
        {
          id: 2,
          icon: 'bi bi-people',
          iconColor: '#17a2b8',
          text: 'Client presentation',
          todo: 'Scheduled',
          details: 'Present recruitment strategy and candidate pipeline to client stakeholders.',
          userName: 'William Sample',
          userImage: '',
          date: 'Dec 16',
          time: '10:00 AM'
        }
      ],
      filesItems: [
        {
          id: 1,
          icon: 'bi bi-file-earmark-text',
          iconColor: '#6f42c1',
          text: 'Resume review',
          todo: 'In Progress',
          details: 'Review and evaluate candidate resumes for Product Manager position.',
          userName: 'Emily Rodriguez',
          userImage: '',
          date: 'Dec 14',
          time: '10:30 AM'
        },
        {
          id: 2,
          icon: 'bi bi-file-earmark-pdf',
          iconColor: '#dc3545',
          text: 'Contract documents',
          todo: 'Pending',
          details: 'Prepare employment contracts for newly hired candidates.',
          userName: 'Phyllis Yang',
          userImage: '',
          date: 'Dec 13',
          time: '2:00 PM'
        }
      ],
      detailsItems: [
        {
          id: 1,
          icon: 'bi bi-file-earmark-text',
          iconColor: '#6f42c1',
          text: 'Resume review',
          todo: 'In Progress',
          details: 'Review and evaluate candidate resumes for Product Manager position.',
          userName: 'Emily Rodriguez',
          userImage: '',
          date: 'Dec 14',
          time: '10:30 AM',
          associations: 1,
          category: 'Job Application',
          priority: 'High',
          status: 'In Progress',
          description: 'Detailed review of resumes for the Product Manager position. Need to finalize shortlist by tomorrow.'
        },
        {
          id: 2,
          icon: 'bi bi-file-earmark-pdf',
          iconColor: '#dc3545',
          text: 'Contract documents',
          todo: 'Pending',
          details: 'Prepare employment contracts for newly hired candidates.',
          userName: 'Phyllis Yang',
          userImage: '',
          date: 'Dec 13',
          time: '2:00 PM',
          associations: 1,
          category: 'HR',
          priority: 'Medium',
          status: 'Pending',
          description: 'Finalize and send employment contracts to the legal department for review.'
        },
        {
          id: 3,
          icon: 'bi bi-sticky',
          iconColor: '#007bff',
          text: 'Client meeting notes',
          todo: 'Todo',
          details: 'Follow up on project requirements and timeline discussion with the development team.',
          userName: 'William Sample',
          userImage: '',
          date: 'Jul 12',
          time: '11:54 am',
          associations: 2,
          category: 'Client Communication',
          priority: 'High',
          status: 'Todo',
          description: 'Comprehensive meeting notes from client discussion covering project scope, timeline, and resource requirements.'
        },
        {
          id: 4,
          icon: 'bi bi-telephone',
          iconColor: '#28a745',
          text: 'Candidate interview call',
          todo: 'Done',
          details: 'Completed initial screening call with Sarah Johnson for Senior Developer position.',
          userName: 'Phyllis Yang',
          userImage: '',
          date: 'Jul 11',
          time: '3:30 pm',
          associations: 1,
          category: 'Recruitment',
          priority: 'Medium',
          status: 'Done',
          description: 'Successfully completed initial screening interview. Candidate shows strong technical skills and cultural fit.'
        },
        {
          id: 5,
          icon: 'bi bi-calendar-check',
          iconColor: '#ffc107',
          text: 'Team sync meeting',
          todo: 'Todo',
          details: 'Weekly team alignment meeting to discuss current projects and upcoming deadlines.',
          userName: 'Michael Chen',
          userImage: '',
          date: 'Dec 14',
          time: '3:00 PM',
          associations: 3,
          category: 'Team Management',
          priority: 'Medium',
          status: 'Scheduled',
          description: 'Weekly team alignment meeting to review project progress, discuss blockers, and plan upcoming sprints.'
        }
      ]
    };
  },
   methods: {
    handleTabChange(tabName) {
      this.activeTab = tabName;
    },
    formatDateTime(dateStr, timeStr) {
      const fullDateStr = `${dateStr}, ${new Date().getFullYear()} ${timeStr}`;
      const parsed = dayjs(fullDateStr);
      return parsed.isValid()
        ? parsed.format('MMM D, YYYY, h:mm a')
        : `${dateStr} • ${timeStr}`;
    }
  }
};
</script>

<style scoped>
.text-blue{color:#1f5fac;font-size:12px}
.quick-actions-tabs{height:100%}
.icons-section{background-color:#f8f9fa}
.icon-item{flex:1;max-width:80px}
.icon-circle{width:40px;height:40px;border-radius:50%;display:flex;align-items:center;justify-content:center;margin:0 auto;transition:all .2s ease}
.icon-item small{display:block;font-weight:500}
.nav-tabs{background-color:#e9ecef;border:0}
.nav-tabs .nav-link{border:none;color:#6c757d;font-weight:500;padding:.75rem 1rem;border-radius:0;transition:all .2s ease;font-size:12px}
.nav-tabs .nav-link:hover{color:#495057;border:none}
.nav-tabs .nav-link.active{color:#1f5fac;background:0 0;font-weight:600}
.tab-content{min-height:300px}
.tab-pane{padding:0}
.action-icon{width:24px;height:24px;display:flex;align-items:center;justify-content:center;font-size:14px}
.action-text{font-weight:500;font-size:12px}
.todo-pill{background-color:#e9ecef;color:#6c757d;padding:.25rem .5rem;border-radius:12px;font-size:10px;font-weight:500}
.user-avatar{width:24px;height:24px;border-radius:50%;object-fit:cover}
.user-name{color:#495057;font-weight:500}
.date-time{color:#6c757d}
.priority-badge{display:inline-block;padding:4px 8px;border-radius:12px;font-size:10px;font-weight:500;color:#fff}
.priority-badge.High{background-color:#dc3545}
.priority-badge.Medium{background-color:#ffc107}
.priority-badge.Low{background-color:#28a745}
.status-badge{display:inline-block;padding:4px 8px;border-radius:12px;font-size:10px;font-weight:500;color:#fff}
.status-badge.Todo{background-color:#007bff}
.status-badge.In Progress{background-color:#ffc107}
.status-badge.Done{background-color:#28a745}
.status-badge.Pending{background-color:#6c757d}
.status-badge.Scheduled{background-color:#17a2b8}
.detail-info .row{margin-bottom:8px}
.detail-info .text-muted{font-size:11px;color:#6c757d}
.detail-info .priority-badge,.detail-info .status-badge{display:inline-block;padding:4px 8px;border-radius:12px;font-size:10px;font-weight:500;color:#fff}
.detail-info .mt-1{margin-top:4px}
@media (max-width:768px){
.nav-tabs .nav-link{padding:.5rem .75rem;font-size:11px}
.action-card .card-body{padding:.75rem}
}

</style>
