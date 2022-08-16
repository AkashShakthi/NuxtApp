<template>
 <div class="container">
        <div class="col-lg-12 text-center">
            <h1 class="page-title">Product List</h1>
        </div>


        <div class="col-lg-12">
            <table class="table table-striped table-dark">
                <thead>
                  <tr>
                    <th scope="col">Id</th>
                    <th scope="col">Name</th>
                   <th scope="col">Price</th>
                    <th scope="col">Status</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="task in tasks">
                    <td scope="row">{{ task.id }}</td>
                    <td>{{ task.name }}</td>
                    <td>{{ task.price }}</td>
                    <td>
                      <span v-if="task.status == 0"  class="badge bg-warning">Inactive</span>
                     <span v-else  class="badge bg-success">Active</span>
                   </td>
                  </tr>
                </tbody>
              </table>
        </div>
   </div>

</template>

<script>
export default {
  name: 'home',
  data(){
    return{
      tasks:[],
    }
  },
  methods: {
    getTasks(){
      this.$axios.get('http://127.0.0.1:8000/api/tasks').then(response =>{
      this.tasks = response.data;
         console.log(response);
      });
    },
  },
  mounted(){
    this.getTasks();
  }
}
</script>


<style>
    .page-title{
        padding-top:2vh;
        font-size: 4rem;
        color:#5471C6;
        padding-bottom:2vh;
    }
</style>
