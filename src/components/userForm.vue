<template>
  <div>
    <form>
      <div class="form-group">
        <label for="title">Title</label>
        <input type="text"
               v-model="formModel.title"
               class="form-control"
               id="title"
               placeholder="Please enter title">
      </div>
      <div class="form-group">
        <label for="description">Description</label>
        <textarea class="form-control"
                  v-model="formModel.description"
                  id="description"
                  placeholder="Please enter information"
                  rows="2"
        ></textarea>
      </div>
      <div class="form-group">
        <label for="status">Status</label>
        <select class="form-control"
                v-model="formModel.status"
                id="status">
          <option value="" disabled selected>Please select</option>
          <option>WAITING</option>
          <option>IN PROGRESS</option>
          <option>COMPLETED</option>
        </select>
        <br>
        <button type="submit" class="btn btn-primary w-100">Add New</button>
      </div>

    </form>

  </div>

</template>

<script>
export default {
name: "userForm",
  data() {
    return {
      formModel : {
        title : "",
        description : "",
        status : ""
      }
    }
  },
}
</script>

<style scoped>

</style>