<template>
  <div id="app" class="w-50 m-4 ">
    <userForm @formSubmit ="saveForm"
              ref="myFormModel"
              class="border p-4"/>
    <todoList :todoList ="todoList"
              @updateForm="updateForm"
              class="mt-4" />
  </div>
</template>

<script>

import userForm from "@/components/userForm";
import todoList from "@/components/todoList";
export default {
  name: 'App',
  components: {
    userForm,
    todoList
  },
  methods: {
    saveForm(form) {
      if (!form.updateMod ){
        form.id = new Date().getTime();
        this.todoList.push({...form});
      }
      else {
        const index = this.todoList.findIndex(data => data.id === this.$refs.myFormModel.formModel.id);
        this.todoList.splice(index, 1, form)
        form.updateMod = false;

      }

    },
    updateForm(list) {
      this.$refs.myFormModel.formModel = {...list }
    }
  },
  data() {
    return {
      todoList: [],
    }
  },
}
</script>

<style>

</style>
