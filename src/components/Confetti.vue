<template>
  <div class="confetti"></div>
</template>

<script>
import confetti from "canvas-confetti";
export default {
  name: "Confetti",
  data() {
    return {
      count:500,
      defaults:{
        origin:{
          y:0.7
        }
      }
    };
  },
  mounted() {
    this.$parent.$on("confettiStart", this.start);
  },
  methods: {
    start() {
      this.fire(0.25, {
        spread: 26,
        startVelocity: 55,
      });
      this.fire(0.2, {
        spread: 60,
      });
      this.fire(0.35, {
        spread: 100,
        decay: 0.91,
        scalar: 0.8,
      });
      this.fire(0.1, {
        spread: 120,
        startVelocity: 25,
        decay: 0.92,
        scalar: 1.2,
      });
      this.fire(0.1, {
        spread: 120,
        startVelocity: 45,
      });
    },
    fire(particleRatio, opts) {
      let th = this;
      confetti(
        Object.assign({}, th.defaults, opts, {
          particleCount: Math.floor(th.count * particleRatio),
        })
      );
    },
  },
};
</script>


