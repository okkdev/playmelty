<template>
  <div class="h-full">
    <div v-if="!play">working on it :)</div>
    <Play v-if="play"></Play>
  </div>
</template>

<script>
import Play from '~/components/Play'

export default {
  components: {
    Play
  },
  data: () => ({
    play: false
  }),
  mounted() {
    const host = window.location.host
    const parts = host.split('.')

    if (parts[0] === 'play') {
      this.play = true
    } else {
      window.location.replace('https://play.meltyblood.club')
    }
  },
  head() {
    return {
      title: 'Play Melty Blood!',
      meta: [
        { name: 'og:title', content: 'Play Melty Blood you wimp!' },
        {
          name: 'og:description',
          content: 'With the power of friendship and poverty.'
        },
        {
          name: 'og:image',
          content: 'https://meltyblood.club/img/sway.gif'
        },
        { name: 'og:image', content: 'https://play.meltyblood.club' }
      ]
    }
  }
}
</script>
