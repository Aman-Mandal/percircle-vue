<template>
  <div class="hello">
    <h3>Percircle (Custom colors and reactive percents)</h3>
    <pre>
      <code> 
        { 
          percent: {{percent}},
          displayTextAtZero: true,
          progressBarColor: "#1B75BC"
        } 
      </code>
    </pre>
    <percircle :percent="percent" progressBarColor="#1B75BC" />

    <div class="buttons">
      <button class="button" @click="add(10)">+10</button>
      <button class="button" @click="add(-10)">-10</button>
    </div>

    <h3>
      Percircle (Text based, small size, dark background, uses same percent as
      above but translates it to a letter grade)
    </h3>
    <pre>
      <code> 
        class="small dark"

        { 
          percent: {{percent}},
          displayTextAtZero: true,
          text: {{letterGrade}}
        } 
      </code>
    </pre>
    <div class="dark-background">
      <percircle class="small dark" :percent="percent" :text="letterGrade" />
    </div>

    <div class="buttons">
      <button class="button" @click="add(10)">+10</button>
      <button class="button" @click="add(-10)">-10</button>
    </div>

    <h3>Perdown (Countdown timer, big size, clicking resets it)</h3>
    <pre>
      <code> 
        class="big"

        { 
          perdown: true,
          secs: {{secs}},
          timeUpText: "Done",
          resetOnClick: true
        } 
      </code>
    </pre>
    <percircle class="big" perdown :secs="secs" timeUpText="Done" />

    <h3>Perclock (Clock)</h3>
    <pre>
      <code> 
        { 
          perclock: true
        } 
      </code>
    </pre>
    <percircle perclock />

    <h3>Percircle (Animate on scroll)</h3>
    <pre>
      <code> 
        { 
          percent: {{percent}},
          displayTextAtZero: true,
          progressBarColor: "#1B75BC",
          animateOnScroll: true
        } 
      </code>
    </pre>
    <percircle :percent="percent" progressBarColor="#1B75BC" animateOnScroll />

    <div class="buttons">
      <button class="button" @click="add(10)">+10</button>
      <button class="button" @click="add(-10)">-10</button>
    </div>

    <h3>Percircle (Animation off)</h3>
    <pre>
      <code> 
        { 
          percent: {{percent}},
          displayTextAtZero: true,
          animate: false
        } 
      </code>
    </pre>
    <percircle :percent="percent" :animate="animate" />

    <div class="buttons">
      <button class="button" @click="add(10)">+10</button>
      <button class="button" @click="add(-10)">-10</button>
    </div>
  </div>
</template>

<script>
import Percircle from "./percircle.vue";
export default {
  name: "HelloWorld",

  components: {
    Percircle,
  },

  data() {
    return {
      percent: 60,
      secs: 35,
      animate: false,
    };
  },

  computed: {
    letterGrade() {
      if (this.percent >= 90) {
        return "A";
      }

      if (this.percent >= 80) {
        return "B";
      }

      if (this.percent >= 70) {
        return "C";
      }

      if (this.percent >= 60) {
        return "D";
      }

      return "F";
    },
  },

  methods: {
    add(amount) {
      this.percent += amount;
    },
  },
};
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

pre code {
  background-color: #eee;
  border: 1px solid #999;
  display: block;
  padding: 20px;
}

.button {
  cursor: pointer;
  margin-left: 10px;
}

.dark-background {
  background-color: black;
  margin-bottom: 20px;
  padding: 20px;
}
</style>
