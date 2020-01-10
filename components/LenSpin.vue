<template>
  <div v-if="lenSpin" class="len-spin fixed z-50">
    <img src="/img/lenspin.gif" alt="lenspin" />
  </div>
</template>

<script>
export default {
  data: () => ({
    lenSpin: false
  }),
  mounted() {
    const root = this
    window.addEventListener('keydown', (event) => {
      switch (event.keyCode) {
        case 37:
          root.codeCount = 1
          break
        case 38:
          root.codeCount === 1 ? (root.codeCount = 2) : (root.codeCount = 0)
          break
        case 39:
          root.codeCount === 2 ? (root.codeCount = 3) : (root.codeCount = 0)
          break
        case 40:
          if (root.codeCount === 3) {
            root.codeCount = 0
            root.lenSpin = true
          }
          break
        default:
          root.codeCount = 0
      }
    })
  }
}
</script>

<style>
.len-spin {
  animation: fly-by 5s ease-in;
  top: -10%;
  left: -10%;
}

@keyframes fly-by {
  0% {
    /* transform: translate(0%, 0%); */
    top: -10%;
    left: -10%;
  }
  100% {
    top: 110%;
    left: 110%;
    /* transform: translate(-110%, 110%); */
  }
}
</style>
