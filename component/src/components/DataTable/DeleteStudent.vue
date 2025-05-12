<template>
    <div class="modal" tabindex="-1" id="exampleModal2" >
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title">Delete Student</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body">
            <form >
              <div class="mb-3">
                <label for="id" class="text-primary form-label">ID</label>
                <input type="text" id="id" class="form-control" v-model="id">
              </div>
            </form>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <button type="button" class="btn btn-primary" data-bs-dismiss="modal" @click="deleteStudent">Delete</button>
                </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data: () => ({
    id:""
  }),
    methods: {
        deleteStudent() {
        const data = {
          id:this.id
        };
        this.$emit("deleteStudent", data);
  
  
      }
    }
  };
  </script>
  