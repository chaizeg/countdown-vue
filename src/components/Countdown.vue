<template>
  <h1>Hello friends (｡◕‿‿◕｡) </h1>
  Enter number of hours for countdown : 
  <input v-model="hours">
  <br>
  Enter number of minutes for countdown : 
  <input v-model="mins">
  <br>

  Enter number of seconds for countdown : 
  <input v-model="secs">
  <br>
  <br>

  <button @click="launchCountdown">Launching countdown </button>
  <div v-if="show">
    {{countingHr}} : {{countingMin}} : {{countingSec}}
  </div>
</template>
 
<script>
export default {
  name: 'Countdown',
  data(){
    return {
      hours : 0,
      mins: 0,
      secs :0,
      countingMin: 0,
      countingHr : 0,
      countingSec : 0,
      show : false
    }
  },
  methods :{
      async launchCountdown(){
      this.show = true;
      console.log(this.show);
      this.countingMin =this.mins;
      this.countingHr =this.hours;
      this.countingSec =this.secs;
      console.log("here")
      const timer = setInterval(()=>{
        if(this.countingSec > 0){
          this.countingSec=this.countingSec-1;
      }
      else {
        if(this.countingMin > 0){
          this.countingMin=this.countingMin-1;
          this.countingSec = 59;
        }
        else{
          if(this.countingHr> 0){
            this.countingHr= this.countingHr-1;
            this.countingMin= 59;
          }
          else{
            clearInterval(timer);
          }
        }
      }
        console.log(this.countingMin)
        console.log(this.countingHr)
        console.log(this.countingSec)
      },1000);
        console.log("done");
    return this.show;
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
</style>
