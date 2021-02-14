<template>
  <div id="app" class="w-50 m-4 ">
    <userForm class="border p-4"/>
    <todoList class="mt-4" />
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
  data() {
    return {
      todoList: []
    }
  },
}
</script>

<style>

</style>
