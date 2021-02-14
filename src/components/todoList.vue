<template>
 <div>
   <div class="form-group d-flex">
     <label for="status" class="mt-1">Show :</label>
     <select class="form-control w-25 ml-2"id="status">
       <option>ALL</option>
       <option>WAITING</option>
       <option>IN PROGRESS</option>
       <option>COMPLETED</option>
     </select>
   </div>
   <div class="card ">
     <div class="card-body row">
       <div class="col-sm-9">
         <h5 class="card-title ">Card title</h5>
         <p class="card-text">With supporting text below as a natural lead-in to additional content.</p>
       </div>
       <div class="col-sm-3  ">
         <a href="#" class="btn btn-primary w-100 mt-4">Edit</a>
       </div>

     </div>

   </div>
 </div>
</template>

<script>
export default {
name: "todoList"
}
</script>

<style scoped>

</style>