<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <label>Huidige leeftijd?
      <input
        type="number"
        v-model="age"
        v-on:input="calculatePension">
    </label>

    <label>Pensioen leeftijd?
      <input
        type="number"
        v-model="retireAge"
        v-on:input="calculatePension">
    </label>
    <button
      v-on:click="startCounter"
    >Start</button>
    <h1>{{secondsTillPension }}</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Time To Pension',
      age: 0,
      retireAge: 67,
      secondsTillPension: 0,
      hasStarted: false
    }
  },
  methods: {
    startCounter () {
      this.hasStarted = true
      setInterval(() => {
        if (this.secondsTillPension === 0) {
          clearInterval()
          this.hasStarted = false
        }
        this.secondsTillPension--
      }, 1000)
    },
    calculatePension () {
      this.secondsTillPension = (this.retireAge - this.age) * 365 * 24 * 60 * 60
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
</style>
