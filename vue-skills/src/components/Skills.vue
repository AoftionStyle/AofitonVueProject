<template>
  <div class="hello">
    {{ name }}

    {{ btnState ? 'button is disabled' : 'button is active' }}
    <button v-on:click="changeName" v-bind:disabled="btnState"> ChangeName</button>

    <div class="holder">
      <ul>
        <li v-for="(data, index) in skills" :key='index'>{{index}}.{{data.skill}}</li>
      </ul>

      <p v-if="skills.length > 1"> You have more than 1 skills</p>
      <p v-else> You habe less than or equal to 1 skill</p>

      <div v-bind:class="{ alert: showAlert, 'another-class': showClass }"></div>
      <div v-bind:class="alertObject"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      name: "Aoftion",
      btnState: true,
      skills: [
        {"skill" : "Vue.js"},
        {"skill" : "Frontend Developer"}
      ],
      showAlert: true,
      showClass: true,
      alertObjet: {
        alert: true
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.alert {
  background-color: yellow;
  width: 100%;
  height: 30px;
}
.another-class {
  border: 5px solid black;
}
</style>

<style src="./Skills.css" scoped>

</style>
