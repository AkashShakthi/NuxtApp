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
                  <tr v-for="task in tasks" >


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
  layout: 'dashboard',
  data(){
    return{
      task:[],
    }
  },
  methods: {
    getTasks(){
      this.$axios.get('http://127.0.0.1:8000/api/tasks').then(response =>{
        console.log(response);
        this.tasks = response.data;
      });
    },

     getImgtasks(){
      this.$axios.get('http://127.0.0.1:8000/api/imgtasks').then(response =>{

        this.imgtasks = response.data[0];
        let vdata = response.data;
       consple.log(vdata)


      });
    },
  },
   mounted(){
    this.getTasks();
     this.getImgtasks();
  },
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
