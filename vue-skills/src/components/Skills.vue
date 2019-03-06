<template>
  <div class="hello">
    <div class="holder">
      {{ name }}

      {{ btnState ? 'button is disabled' : 'button is active' }}
      <button v-on:click="clickMe" v-bind:disabled="btnState"> ChangeName</button>
      <br>
      <form @submit.prevent="addSkill">
        <input type="text" placeholder="Enter a skill you have.." v-model="skill" v-validate="'min:5'" name="skill">

        <transition name="alert-in">
        <p class="alert" v-if="errors.has('skill')">{{ error.first('skill') }}</p>
        </transition>

        <input type="checkbox" id="checkbox" v-model="checked">
      </form> 

    
      <ul>
        <li v-for="(data, index) in skills" :key='index'>{{index}}.{{data.skill}}</li>
      </ul>

      <!-- <p v-if="skills.length > 1"> You have more than 1 skills</p>
      <p v-else> You habe less than or equal to 1 skill</p> -->

      <!-- <div v-bind:class="{ alert: showAlert, 'another-class': showClass }"></div>
      <div v-bind:class="alertObject"></div>
      <div v-bind:style="{ backgroundColor: bgColor, width: bgWidth, height: bgHeight }"></div> -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      checked: false,
      name: "Aoftion",
      btnState: true,
      skill: '',
      skills: [
        {"skill" : "Vue.js"},
        {"skill" : "Frontend Developer"}
      ],
      showAlert: true,
      showClass: true,
      alertObject: {
        alert: true
      },
      bgColor: "blue",
      bgWidth: "100%",
      bgHeight: '30px',
      clickMe: "clickme!!",
    }
  },
  methods: {
    addSkill() {
      this.$validator.validateAll().then((result) => {
        if(result) {
          this.skills.push({skill: this.skill})
          this.skill = '';
        } else {
          console.log('Not valid')
        }
      });
      
      console.log('This checkcbox value is: '+ this.checked);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
a {
  color: #42b983;
}

</style>

<style src="./Skills.css" scoped>

</style>
