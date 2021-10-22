<template>
  <div class="container">
    <div class="blog" v-if="showBlog" @click="stopTimer">
      <p>Click me!</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Blog",
  props: { delay: Number }, //props['delay']
  data() {
    return {
      showBlog: false,
      timer: null,
      reactionTime: 0,
    };
  },

  mounted() {
    //updated() and  unmounted() are also lifecycle methods
    //lifecycle hooks
    setTimeout(() => {
      this.showBlog = true;
      this.startTimer();
    }, this.delay);
    console.log("Component mounted");
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
      
    },
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.$emit('end' , this.reactionTime); //we created end event and parametre 
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
.blog {
  width: 400px;
  height: 300px;
  background: lightgreen;
  border-radius: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.blog p {
  font-size: 50px;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  vertical-align: middle;
}
</style>