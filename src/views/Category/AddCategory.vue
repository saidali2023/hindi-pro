<template>
  <div class="container">
      <div class="row">
        <div class="text-center">
          <h3>add cat</h3>
        </div>
      </div>
      <div class="row">
        <div class="col-3">

        </div>
        <div class="col-6">
          <form>
          <div class="form-group">
            <label>Category name</label>
            <input type="text" class="form-control" v-model="categoryName">
          </div>
          <div class="form-group">
            <label>Category desc</label>
            <textarea type="text" class="form-control" v-model="description"></textarea>
          </div>
          <div class="form-group">
            <label>Category image</label>
            <input type="text" class="form-control" v-model="imageUrl">
          </div>

          <button type="button" class="btn btn-primary" @click="addCategory()">Submit</button>
        </form>
        </div>
        <div class="col-3">

        </div>

      </div>
  </div>


</template>
<script>
const axios =require("axios");
const sweetalert =require("sweetalert");
  export default{
    data(){
      return{
        categoryName:"",
        description:"",
        imageUrl:""
      }
    },
    methods: {
       addCategory() {
          console.log(this.categoryName,this.description);
          const newCategory={
            name_ar:this.categoryName,
            description:this.description,
            image:this.imageUrl
          };

          const baseURL="https://elnamat.com/efatora/api/vendors";
          axios({
            method:'post',
            url:`${baseURL}/add-category`,
            data: JSON.stringify(newCategory),
            headers:{
              "Content-Type":"application/json",
            },
          })
          .then(()=>{
            sweetalert({
              text:"category add seccessfully",
              icon:"Seccess"
            });
          })
          .catch((err)=>{
            console.log(err);
          });
      },
    },
  };
</script>
<style scoped="">
</style>
