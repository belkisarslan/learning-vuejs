<template>
  <div>
    <div class="project">
      <div class="actions">
        <h1 @click="(showDetails = ! showDetails)">{{project.name}}</h1>
      </div>
      <div v-if="showDetails" class="details">
        <p>{{project.email}}</p>
        <p>{{project.info}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:["project"],
  data(){
    return{
      showDetails: false
    }
  }
};
</script>

<style scoped>
.project{
  margin: 20px auto;
  background: #fff;
  padding: 10px 20px;
  border-radius: 5px;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.05);
  border-left: 4px solid rebeccapurple;
}
.actions h1{
  cursor: pointer;
}
</style>
