<template>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in projects">
        <h1>{{project.name}}</h1>
        <p>{{project.email}}</p>
        <p>{{project.info}}</p>
      </div>
    </div>
  </div>
</template>

<script>


export default {
  name: 'Home',
  components: {},
  data(){
    return{
      projects: []
    }
  },
  mounted() {
    fetch("http://localhost:3000/projects")
    .then(res => res.json())
    .then(data => this.projects = data)
    .catch(err => console.log(err.message))
  },
}
</script>
