<template>
  <div id="app">

    <div class="container">
      <h2 align="center">Work Shop #2 Preview Image</h2>
      <hr>
    
    <div v-if="!image">
      <input type="file" class="form-control" @change="onFilechange">
      <hr>
    </div>

    <div v-else>
      <img :src="image" class="img-fluid"><hr>
      <button class="btn btn-danger" @click="removeimage">Remove</button>
    </div>
    
    </div>
  </div>

</template>

<script>


export default {
  name: 'App',
  data(){
    return{
      image:''
    }
  },
  methods:{
    // อัพไฟล์รูปเข้ามา
    onFilechange: function(e){
      var files=e.target.files 
      if(!files.length)
        return
      this.createImage(files[0]);
    },
    createImage(files){
      // อ่านไฟล์
      var reader = new FileReader();
      reader.onload=(e) =>{
        this.image=e.target.result;
      }
      reader.readAsDataURL(files);
      console.log(this.image);
    },
    // ลบรูปภาพออก
    removeimage(){
      this.image='';
    }
  }
  
}
</script>

<style>
 *{
   margin:0;
   padding:0;
   box-sizing:border-box;
 }
 .container{
   max-width:960px;
   margin: 0 auto;
 }
 .container h2{
   margin:15px;
   color: gray;
 }
</style>
