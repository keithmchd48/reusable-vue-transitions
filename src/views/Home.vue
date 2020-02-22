<template>
  <div>
    <button v-on:click="show = !show">
      Toggle
    </button>
    Duration:
    <input v-model="duration" type="range" min="100" max="3000">
    {{duration}}ms
    <FadeTransition mode="out-in" :duration="durationNumber">
      <div key="blue" v-if="show" class="box"></div>
      <div key="red" v-else class="red-box"></div>
    </FadeTransition>
  </div>
</template>

<script>
import FadeTransition from "@/components/transitions/FadeTransition";
export default {
  name: 'Home',
  components: {
    FadeTransition
  },
  computed: {
    durationNumber() {
      return parseInt(this.duration);
    }
  },
  data() {
    return {
      show: true,
      duration: 300
    };
  }
}
</script>
<style lang="scss">
  .box {
    width: 200px;
    height: 200px;
    margin-top: 20px;
    background-color: rgb(108, 141, 213);
    box-shadow: rgba(108, 141, 213, 0.5) 0px 6px 20px;
    border-radius: 10px;
  }
  .red-box {
  @extend .box;
    background-color: rgb(251, 17, 116);
    box-shadow: rgba(251, 17, 116, 0.5) 0px 6px 20px;
  }
</style>
