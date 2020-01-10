<template>
  <div class="h-full">
    <div
      v-if="video && content"
      class="hidden md:block"
      style="position: fixed; z-index: -99; width: 100%; height: 100%"
    >
      <iframe
        frameborder="0"
        height="100%"
        width="100%"
        src="https://youtube.com/embed/bWq6xVyKYqA?autoplay=1&loop=1&disablekb=1&controls=0&showinfo=0&mute=1&start=8&end=90&playlist=bWq6xVyKYqA"
      ></iframe>
    </div>

    <!-- Len spin easter egg -->
    <LenSpin></LenSpin>

    <!-- Intro -->
    <div
      v-if="!content"
      @click="content = true"
      class="fixed h-full w-full z-30 flex justify-center items-center cursor-pointer"
    >
      <div class="fixed new-challenger pointer-events-none z-40">
        <div class="flex flex-col items-end">
          <div>Here comes a New challenger!</div>
          <div class="text-5xl">Recalculation Interrupted Now ...</div>
        </div>
      </div>
      <img
        class="w-full a-bit-transparent static pointer-events-none"
        src="/img/static.gif"
        alt="static"
      />
    </div>

    <!-- Modal -->
    <Modal></Modal>

    <div v-if="content" class="content container mx-auto h-full flex flex-col">
      <div class="fixed right-0 m-3 opacity-75">
        <div class="hidden md:flex flex-row">
          <div class="mr-2 tracking-widest uppercase">Video</div>
          <div
            v-if="video"
            @click="toggleVideo"
            class="border rounded-full border-gray-300 flex items-center cursor-pointer w-10 bg-purple-700 justify-end shadow-inner shadow"
          >
            <div
              class="rounded-full border w-5 h-5 border-gray-300 shadow-inner bg-gray-200 shadow"
            ></div>
          </div>
          <div
            v-else
            @click="toggleVideo"
            class="border rounded-full border-gray-300 flex items-center cursor-pointer w-10 justify-start shadow"
          >
            <div
              class="rounded-full border w-5 h-5 border-gray-300 shadow-inner bg-gray-200 shadow"
            ></div>
          </div>
        </div>
      </div>

      <div class="flex flex-col h-full justify-center items-center">
        <div class="flex">
          <img v-if="neco" class="mr-5" src="/img/sway.gif" alt="neco sway" />
          <h1
            @click="neco = !neco"
            class="text-6xl tracking-widest font-gradient-2 cursor-pointer"
          >
            PLAY
          </h1>
          <img v-if="neco" class="ml-6" src="/img/happy.gif" alt="neco happy" />
        </div>
        <img class="w-2/3" src="/img/logo.png" alt="melty blood logo" />

        <div class="flex flex-col justify-center">
          <div class="flex flex-col md:flex-row flex-wrap justify-center">
            <a
              class="button"
              href="https://store.steampowered.com/app/411370/Melty_Blood_Actress_Again_Current_Code/"
              target="_"
            >
              <i class="fab fa-steam-square font-normal mr-1"></i>
              <span class="font-gradient">Buy the Game</span>
            </a>
            <a
              class="button"
              href="https://mega.nz/#!qRMTHK6A!QCBOqnH91TynUqQjddgm8omGBeIG5Yp_-iT-Q5QmTas"
              target="_"
            >
              <i class="fas fa-cloud-download-alt mr-1"></i>
              <span class="font-gradient"
                >Download community version with rollback netcode</span
              >
            </a>
          </div>
          <div class="flex flex-col md:flex-row flex-wrap justify-center">
            <a
              class="button"
              href="https://www.youtube.com/watch?v=Zz4L7uy3zj8"
              target="_"
            >
              <i class="fab fa-youtube font-normal mr-1"></i>
              <span class="font-gradient">Intro to Melty</span>
            </a>
            <a
              class="button"
              href="https://www.youtube.com/watch?v=yKPJWNZ8Idw"
              target="_"
            >
              <i class="fab fa-youtube font-normal mr-1"></i>
              <span class="font-gradient">Complete Guide to Melty</span>
            </a>
            <a
              class="button"
              href="http://wiki.mizuumi.net/w/Melty_Blood"
              target="_"
            >
              <i class="fas fa-book mr-1"></i>
              <span class="font-gradient">Mizuumi Wiki</span>
            </a>
            <a class="button" href="http://melty.games/" target="_">
              <i class="fas fa-tv mr-1"></i>
              <span class="font-gradient">Match Videos</span>
            </a>
          </div>
          <div class="flex flex-col md:flex-row flex-wrap justify-center">
            <a
              class="button"
              href="https://discordapp.com/invite/33cskPv"
              target="_"
            >
              <i class="fab fa-discord font-normal mr-1"></i>
              <span class="font-gradient">Join the Discord</span>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import LenSpin from '~/components/LenSpin'
import Modal from '~/components/Modal'

export default {
  components: {
    LenSpin,
    Modal
  },
  data: () => ({
    video: true,
    content: false,
    neco: false
  }),
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
          content: 'https://play.meltyblood.club/img/sway.gif'
        },
        { name: 'og:image', content: 'https://play.meltyblood.club' }
      ]
    }
  },
  mounted() {
    if (window.innerWidth <= 768) {
      this.video = false
      this.content = true
    }

    if (this.$route.query.video === 'false') {
      this.video = false
    }
  },
  methods: {
    toggleVideo() {
      this.video = !this.video
      this.$router.push({ path: '/', query: { video: this.video } })
    }
  }
}
</script>

<style>
body {
  background: url('/img/wallpaper.jpg');
  @apply bg-cover bg-center bg-scroll text-gray-100;
}

.button {
  background-color: rgba(0, 0, 0, 0.9);
  @apply rounded-sm py-2 px-3 border-2 border-gray-100 shadow font-semibold tracking-widest uppercase text-xl text-center m-4 outline-none;
}

.modal {
  background-color: rgba(0, 0, 0, 0.9);
  @apply rounded-sm p-8 border-2 border-gray-100 shadow;
}

.content {
  animation: fade-in 2s;
}

@keyframes fade-in {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.static {
  animation: static-grow 1s ease-in;
  height: 24rem;
}

@keyframes static-grow {
  0% {
    height: 0rem;
  }
  100% {
    height: 24rem;
  }
}

.new-challenger {
  /* purgecss ignore current */
  font-family: 'Crmson Text', serif;
  font-size: 5rem;
  font-weight: 900;
  -webkit-text-stroke: 0.15rem rgb(255, 255, 255);
  background: linear-gradient(to right, rgb(245, 168, 168), rgb(189, 7, 7));
  background-clip: text;
  color: transparent;
  animation: new-challenger-move 1.2s ease-out;
}

@keyframes new-challenger-move {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(0%);
  }
}

.font-gradient {
  background: linear-gradient(rgb(255, 255, 255), rgb(212, 15, 15));
  background-clip: text;
  color: transparent;
}

.a-bit-transparent {
  opacity: 0.6;
}

.modal-background {
  background-color: rgba(0, 0, 0, 0.8);
}

.font-gradient-2 {
  background: linear-gradient(rgb(0, 0, 0), rgb(219, 0, 0));
  background-clip: text;
  color: transparent;
  -webkit-text-stroke: 0.05rem rgb(255, 255, 255);
  @apply font-black;
}

#__nuxt {
  background-color: rgba(0, 0, 0, 0.7);
}

#__layout {
  background-image: url('/img/topo.svg');
}
</style>
