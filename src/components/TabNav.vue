<template>
  <div class="row">
    <div class="col-12 d-flex justify-content-between align-items-center mb-3 mt-3 flex-wrap">
    
      <nav aria-label="breadcrumb" class="d-flex align-items-center gap-2 mb-4 mb-md-0">
        <ol class="breadcrumb mb-0 small">
          <li class="breadcrumb-item">
            <a href="#" class="text-decoration-none">Candidates</a>
          </li>
         
          <li class="breadcrumb-item active" aria-current="page">
            {{ currentPage }}
          </li>
        </ol>
        <span class="badge text-bg-light p-1 fw-normal border border-secondary-subtle">ID: {{ candidateId }}</span>
      </nav>
      
      <div class="d-flex gap-2">
        <button class="btn btn-outline-secondary btn-sm bg-white text-black" @click="$emit('request-update')">         
          Request Profile Update
        </button>
        <button class="btn btn-outline-secondary btn-sm bg-white text-black" @click="$emit('previous')">
         
          Previous
        </button>
        <button class="btn btn-outline-secondary btn-sm bg-white text-black" @click="$emit('next')">
          Next
         
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabNav",
  props: {
    currentPage: {
      type: String,
      default: "Robert Hardy",
    },
    candidateId: {
      type: String,
      default: "id-231",
    },
  },
};
</script>

<style scoped>
.breadcrumb a {
  color: #1F5FAC;
}
</style>
