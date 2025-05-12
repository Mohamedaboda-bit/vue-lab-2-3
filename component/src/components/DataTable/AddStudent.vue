<template>
  <div class="modal" tabindex="-1" id="exampleModal" >
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">Add Student</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <form >
            <div class="mb-3">
              <label for="name" class="text-primary form-label">Name</label>
              <input type="text" id="name" class="form-control" v-model="name">
            </div>
            <div class="mb-3">
              <label for="city" class="text-primary form-label">City</label>
              <input type="text" id="city" class="form-control" v-model="city">
            </div>
          </form>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
          <button type="button" class="btn btn-primary" data-bs-dismiss="modal" @click="addStudent">Save</button>
              </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    name: "",
    city: ""
  }),
  methods: {
    addStudent() {
      const data = {
        name: this.name,
        city: this.city
      };
      this.$emit("addNewStudent", data);


    }
  }
};
</script>
