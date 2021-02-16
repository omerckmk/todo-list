<template>
  <div>
    <ValidationObserver v-slot="{ handleSubmit }">
      <form @submit.prevent="handleSubmit(saveForm)">
        <div class="form-group">
          <label for="title">Title</label>
          <ValidationProvider mode="passive" rules="required" v-slot="{ errors }">
            <input type="text"
                   v-model="formModel.title"
                   class="form-control"
                   id="title"
                   placeholder="Please enter title">
            <span class="text-danger">{{ errors[0] }}</span>
          </ValidationProvider>
        </div>
        <div class="form-group">
          <label for="description">Description</label>
          <ValidationProvider mode="passive" rules="required" v-slot="{ errors }">
        <textarea class="form-control"
                  v-model="formModel.description"
                  id="description"
                  placeholder="Please enter information"
                  rows="2"
        ></textarea>
            <span class="text-danger">{{ errors[0] }}</span>
          </ValidationProvider>
        </div>
        <div class="form-group">
          <label for="status">Status</label>
          <ValidationProvider mode="passive" rules="required" v-slot="{ errors }">
            <select class="form-control"
                    v-model="formModel.status"
                    id="status">
              <option value="" disabled selected>Please select</option>
              <option>WAITING</option>
              <option>IN PROGRESS</option>
              <option>COMPLETED</option>
            </select>
            <span class="text-danger">{{ errors[0] }}</span>
          </ValidationProvider>
          <br>
          <button type="submit" class="btn btn-primary w-100">{{ buttonText }}</button>
        </div>

      </form>
    </ValidationObserver>
  </div>

</template>

<script>
export default {
  name: "userForm",
  data() {
    return {
      formModel: {
        id: null,
        title: "",
        description: "",
        status: "",
        updateMod: false
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
        updateMod: false
      }
    }
  },
  computed: {
    buttonText() {
      return this.formModel.updateMod === true ? 'Update' : 'Add New';
    }
  },

}
</script>

<style scoped>

</style>