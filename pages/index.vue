<template>
  <div class="h-full">
    <Play></Play>
  </div>
</template>

<script>
import Play from '~/components/Play'

export default {
  components: {
    Play
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
