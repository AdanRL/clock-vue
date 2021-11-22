<template>
  <div class="clock-container">
    <h1>Hello Clock</h1>
    <div :class="theme" class="clock">
      {{ hours }}:{{ minutes }}:{{ seconds }}
    </div>
  </div>
</template>

<script>
export default {
  name:"VueClock",
  props: {
    theme:{
      type: String,
      default: "red",
      required: true,
      validator: v => {
        return v == "red" || v == "blue" || v == "green" ? true : false;
      }
    } 
  },
  data() {
    return {
      hours: "--",
      minutes: "--",
      seconds: "--"
    }
  },
  methods: {
    getDate() {
      const f = new Date();
      this.hours = this.pad(f.getHours())
      this.minutes = this.pad(f.getMinutes())
      this.seconds = this.pad(f.getSeconds())
    },
    pad(value) {
      return String(value).padStart(2,"0")
    }
  },
  mounted() {

    setInterval(() => this.getDate(), 1000)
  }

}

</script>

<style>
  body {

    margin: auto;

}

.clock-container {

    background: black;
    color:white;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    text-align: center;

}
.clock {

  background: black;
  height: 60px;
  font-size: 20px;
  text-shadow: 0 0 1px rgb(201, 124, 124), 
  0 0 5px rgba(201, 124, 124),
  0 0 10px rgba(201, 124, 124), 
  0 0 20px rgb(161, 72, 72),
  0 0 40px rgba(161, 72, 72), 
  0 0 60px rgba(161, 72, 72),
  0 0 80px rgba(161, 72, 72), 
  0 0 120px rgba(161, 72, 72),
  0 0 150px rgba(161, 72, 72);
  &.blue {
    color: blue;
  }
  &.red {
    color: red;
  }
  &.green {
    color: green;
  }
}
</style>
