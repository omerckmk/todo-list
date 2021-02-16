<template>
  <div>
    <form @submit.prevent="saveForm">
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
        <button type="submit" class="btn btn-primary w-100"  >{{ buttonText }}</button>
      </div>

    </form>

  </div>

</template>

<script>
export default {
  name: "userForm",
  data() {
    return {
      formModel: {
        id : null,
        title: "",
        description: "",
        status: "",
        updateMod : false
      }
    }
  },
  methods: {
    saveForm() {
      this.$emit('formSubmit', {...this.formModel});
      this.clearForm();
    },

    clearForm() {
      this.formModel = {
        title: "",
        description: "",
        status: "",
        updateMod : false
      }
    }
  },
  computed: {
    buttonText() {
      return this.formModel.updateMod === true ? 'Update' : 'Add New' ;
    }
  },

}
</script>

<style scoped>

</style>