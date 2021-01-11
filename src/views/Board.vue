<template>
  <div>
    <section class="board_container">
      <span class="info"
        >Musisz mieć więcej niż
        <strong>{{ goodAnswers }} poprawne</strong> odpowiedzi</span
      >

      <div class="dots">
        <div v-for="(item, index) in answersTable" v-bind:key="index">
          <span :class="'dot dot_' + classes[item]"></span>
        </div>
      </div>
      <div class="board">
        <span class="number">{{ num1 }} * {{ num2 }} = </span>
        <input
          type="text"
          id="answer"
          placeholder="odpowiedź"
          :class="answer"
          
          @keyup="Enter"
        />
        <button @click="check">Sprawdź</button>
      </div>
      <History />
      <Face />
      <Confetti />
      
    </section>
  </div>
</template>

<script>
// @ is an alias to /src
import Face from "@/components/Face.vue";
import Confetti from "@/components/Confetti.vue";
import History from "@/components/History.vue";
export default {
  name: "board",
  data() {
    return {
      classes: ["wrong", "success"],
      dir: [-1, 1],
      num1: 1,
      num2: 1,
      val: 0,
      answer: -1,
      answersTable: [],
      goodAnswers: 3,
    };
  },
  components: {
    Face,
    Confetti,
    History,
  },
  mounted() {
    this.$emit("update", this.val);
    this.inputAnswer = document.getElementById("answer");
    this.setRandom();
  },
  watch: {
    answersTable(newValue) {
      if(newValue.length==0)return

      if (newValue.reduce((a, b) => a + b) > this.goodAnswers) {
        this.$emit("confettiStart");
        this.answersTable = [];
      }
    },
  },
  methods: {
    setRandom() {
      this.num1 = this.randomIntFromInterval(1, 10);
      this.num2 = this.randomIntFromInterval(1, 10);
    },
    randomIntFromInterval: (min, max) => {
      return Math.floor(Math.random() * (max - min + 1) + min);
    },
    check() {
      let answer = (this.inputAnswer.value == this.num1 * this.num2) * 1;
      this.answer = this.classes[answer];
      this.val = this.$emit("update", this.dir[answer]);
      this.$emit("add", [this.num1, this.num2, this.inputAnswer.value, answer]);
      this.inputAnswer.value = "";
      this.inputAnswer.focus();
      this.answersTable.push(answer);
      this.setRandom();
    },
    Enter(event) {
      if (event.keyCode === 13) {
        event.preventDefault();
        this.check();
      }
    },
    click: function () {},
  },
};
</script>
<style scoped lang="scss">
.mark {
  width: 17px;
}
.info {
  width: 100%;
  flex-basis: 100%;
  padding: 5px;
  color: #fff;
}
.dots {
  height: 60px;
  display: flex;
  justify-content: center;
}
.dot {
  width: 30px;
  height: 30px;
  border-radius: 100%;
  margin: 15px;
  background: #020202;
  display: inline-block;
}
.board {
  z-index: 1;
  position: relative;
  background: #fff;
      box-shadow: 0 0 0 5px #ffc6e8 inset;
    border: dashed 5px #7cd4df;
  padding: 15px;
  border-radius: 15px;
  width: 90%;
  max-width: 900px;
  margin: auto;
}
.answers_wrong {
  color: red;
}
.answers_success {
  color: green;
}
.dot_wrong {
  background: red;
}
.dot_success {
  background: green;
}
.wrong {
  border-color: red;
}
.success {
  border-color: green;
}
.number {
  font-size: 3em;
}
input,
button {
  padding: 15px;
  border: none;
  border-bottom: 4px solid #020202;
  margin-top: -5px;
  outline-style: none;
  box-shadow: none;
}
input {
  font-size: 3em;
  max-width: 30%;
}
button {
  border: none;
  font-weight: bold;
  background: orange;
  margin-left: 10px;
  color:#fff;
  text-transform: uppercase;
}
</style>
