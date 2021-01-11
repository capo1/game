<template>
         <span id="history">
         <span class="inner">
        Twoje odpowiedzi:
        <span
          v-for="(item, index) in questions"
          v-bind:key="index">
          {{ item[0] }} * {{ item[1] }} =
          <template v-if="item[3] == 1">{{ item[0] * item[1] }} 
              <svg class="mark"  version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 130.2 130.2">
                <circle class="path circle" fill="none" stroke="#73AF55" stroke-width="8" stroke-miterlimit="10" cx="65.1" cy="65.1" r="62.1"/>
                <polyline class="path check" fill="none" stroke="#73AF55" stroke-width="8" stroke-linecap="round" stroke-miterlimit="10" points="100.2,40.2 51.5,88.8 29.8,67.5 "/>
            </svg>
          </template>
          <template v-else><strike>{{ item[2] }}</strike> {{ item[0] * item[1] }}
            <svg version="1.1" xmlns="http://www.w3.org/2000/svg" class="mark" viewBox="0 0 130.2 130.2">
              <circle class="path circle" fill="none" stroke="#D06079" stroke-width="8" stroke-miterlimit="10" cx="65.1" cy="65.1" r="62.1"/>
              <line class="path line" fill="none" stroke="#D06079" stroke-width="8" stroke-linecap="round" stroke-miterlimit="10" x1="34.4" y1="37.9" x2="95.8" y2="92.3"/>
              <line class="path line" fill="none" stroke="#D06079" stroke-width="8" stroke-linecap="round" stroke-miterlimit="10" x1="95.8" y1="38" x2="34.4" y2="92.2"/>
            </svg>

   
            </template>
            </span>
        </span>
      </span>
</template>

<script>
export default {
  name: "History",
  data() {
    return {
     questions: [],
    };
  },
  mounted() {
    this.$parent.$on("add", this.add);
  },
  methods: {
    add(val){
      this.questions.unshift(val)
    }
  },
};
</script>
<style scoped lang="scss">
.mark{
  width:17px;
}
#history {
  text-align: left;
  width: 300px;
  height: 300px;
  overflow: auto;
  float: left;
  background: #fff;
  padding: 15px;
  border: 3px dotted #ffd45b;
  box-shadow: inset 0 0 0 5px #ccdbf7;
    border: 5px dashed #7cd4df;
  span {
    padding: 3px;
    display: block;
  }
  .inner{
 height: 150px;
 overflow: auto;
  }
}
</style>

