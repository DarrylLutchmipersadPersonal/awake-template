<template>
  <div class="logo-wrapper">
    <div
      :class="{
        'logo-inner': true,
        blink: blinking
      }"
    >
      <img
        v-for="x in frames"
        :key="x"
        :src="`/logo-frames/BeefCo_Logo.svg`"
      />
      <img
        v-for="x in frames"
        :key="`${x}-r`"
        :src="`/logo-frames/BeefCo_Logo.svg`"
      />
    </div>
  </div>
</template>
<script>
export default {
  name: 'SiteLogo',
  data() {
    return {
      frames: 1,
      currentFrame: 1,
      blinking: true
    }
  },
  mounted() {
    setInterval(() => {
      const rand = Math.ceil(Math.random() * 10)
      this.blinking = rand % 2
    }, 1000)
  }
}
</script>
<style lang="scss">
@keyframes logoBlink {
  100% {
    transform: translateY(-360px);
  }
}
.logo-wrapper {
  position: relative;
  height: 100px;
  overflow: hidden;
  width: 400px;
  vertical-align: middle;
  .logo-inner {
    position: absolute;
    height: 500px;
    img {
      display: block;
      height: 80px;
      margin: 5px;
      max-height: initial;
    }
    &.blink {
      animation: logoBlink 0.2s steps(8, end) alternate;
    }
  }
}
</style>
