<template>
  <div>
    <div class="form-group d-flex">
      <label for="status" class="mt-1">Show :</label>
      <select class="form-control w-25 ml-2"
              id="status"
              v-model="selected">
        <option>ALL</option>
        <option>WAITING</option>
        <option>IN PROGRESS</option>
        <option>COMPLETED</option>
      </select>
    </div>
    <div :class="{'bg-danger' : list.status === 'WAITING', 'bg-success' : list.status === 'IN PROGRESS',
    'bg-primary' : list.status === 'COMPLETED'}"
        class="card mt-2"
         v-for="list  in listShow" :key="list.id" >
      <div class="card-body row  ">
        <div class="col-sm-9">
          <h5 class="card-title ">{{list.title }}</h5>
          <p class="card-text">{{list.description}}</p>
        </div>
        <div class="col-sm-3  ">
          <a href="#" @click="updateForm(list)" class="btn btn-info w-100 mt-w">Edit</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "todoList",
  methods: {
    updateForm(list) {
      list.updateMod = true ;
      return this.$emit('updateForm' , list);
    }
  },
  data() {
    return {
      selected: "ALL"
    }
  },
  computed: {
    listShow() {
      if (this.selected !== 'ALL'){
        return this.todoList.filter( item => item.status === this.selected);
      }
      else {
        return this.todoList;
      }
    },
  },
  props: {
    todoList: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>

</style>