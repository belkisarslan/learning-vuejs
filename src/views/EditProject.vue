<template>
   <form @submit.prevent="handleSubmit">
  <label>Name:</label>
   <input type="text" v-model="name" required>
  <label>E-mail</label>
  <input type="text" v-model="email" required/>
  <label>İnfo</label>
  <input type="text" v-model="info" required/>
  <button>Update Project</button>
  </form>
</template>

<script>
export default {
 props:["id"],
 data(){
 return{
    name: "",
    email: "",
    info:"",
    url:"http://localhost:3000/projects/" + this.id
    }
 },
 mounted() {
 fetch(this.url).then(res => res.json()).then((data)=>{
    this.name = data.name,
    this.email = data.email,
    this.info = data.info
 })
 },
 methods:{
 handleSubmit(){
    fetch(this.url, {
        method: "PATCH",
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify({name:this.name, email:this.email, info:this.info})
    }).then(()=>this.$router.push("/")).catch(err=>console.log(err))
 }
 }
}
</script>

<style>
form{
  background: #fff;
  padding: 20px;
  border-radius: 10px;
}
label{
  display: block;
  color: #bbb;
  text-transform: uppercase;
  font-size: 14px;
  font-weight: bold;
  letter-spacing: 1px;
  margin: 20px 0 10px 0;
}
input{
  padding: 10px;
  border: 0;
  border-bottom: 1px solid #ddd;
  width: 100%;
  box-sizing: border-box;
}
form button{
  display: block;
  margin: 20px auto 0;
  background: #76dd78;
  color: #fff;
  padding: 10px;
  border: 0;
  border-radius: 8px;
  font-size: 16px;
  cursor: pointer;
}
</style>