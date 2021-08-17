<template>
  <div class="h-full">
    <!-- Background Video -->
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
    <div v-if="!content" @click="content = true" class="h-full">
      <Intro></Intro>
    </div>

    <!-- Modal -->
    <div
      v-if="modal"
      @click.self="modal = false"
      class="fixed h-full w-full modal-background z-20"
    >
      <div
        @click.self="modal = false"
        class="container h-full mx-auto flex justify-center items-center"
      >
        <div class="modal">
          <portal-target name="modal"></portal-target>
        </div>
      </div>
    </div>

    <!-- Main content div -->
    <div v-if="content" class="content container mx-auto h-full flex flex-col">
      <!-- Background video toggle -->
      <div class="fixed right-0 m-3 opacity-75">
        <div class="hidden md:flex flex-row">
          <div class="mr-2 tracking-widest uppercase">Video</div>
          <div
            v-if="video"
            @click="toggleVideo"
            class="border rounded-full border-gray-300 flex items-center cursor-pointer w-10 bg-red-700 justify-end shadow-inner shadow"
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

      <!-- Centered Content -->
      <div class="flex flex-col h-full justify-center items-center">
        <!-- Play text with dancing necos -->
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

        <!-- Melty logo image -->
        <img class="w-2/3" src="/img/logo.png" alt="melty blood logo" />

        <!-- Resource Buttons -->
        <div class="flex flex-col justify-center">
          <div class="flex flex-col md:flex-row justify-center">
            <!-- Get the Game Button -->
            <div
              @click="openModal('get')"
              class="button text-center flex flex-col md:w-56 flex-1 cursor-pointer"
            >
              <div><i class="fas fa-gamepad"></i></div>
              <div>Get Melty</div>
              <Portal v-if="modalContent === 'get'" to="modal">
                <div class="flex justify-between">
                  <div class="title">
                    Get Melty
                  </div>
                  <div @click="modal = false" class="cursor-pointer z-50">
                    <svg
                      class="fill-current"
                      xmlns="http://www.w3.org/2000/svg"
                      width="32"
                      height="32"
                      viewBox="0 0 18 18"
                    >
                      <path
                        d="M14.53 4.53l-1.06-1.06L9 7.94 4.53 3.47 3.47 4.53 7.94 9l-4.47 4.47 1.06 1.06L9 10.06l4.47 4.47 1.06-1.06L10.06 9z"
                      ></path>
                    </svg>
                  </div>
                </div>
                <p class="mb-2">
                  Buy the game on Steam to support the developer.
                </p>
                <p class="mb-6">
                  Play the game with the free "community edition" which includes
                  many features and fixes as well as the fan made CCCaster
                  program which adds rollback netcode. If you want to play
                  online definitely use the community edition.
                </p>
                <div class="flex flex-col md:flex-row justify-center flex-wrap">
                  <a
                    class="button"
                    href="https://store.steampowered.com/app/411370/Melty_Blood_Actress_Again_Current_Code/"
                    target="_"
                  >
                    <i class="fab fa-steam-square font-normal mr-1"></i>
                    <span class="font-gradient">Steam Version</span>
                  </a>
                  <a
                    class="button"
                    href="https://github.com/okkdev/melty-installer/releases/latest/download/MeltyInstaller.exe"
                  >
                    <i class="fas fa-cloud-download-alt mr-1"></i>
                    <span class="font-gradient">Community Edition</span>
                  </a>
                </div>
                <p class="my-2 text-center text-lg">
                  CCCaster guide:
                </p>
                <!-- Youtube Intro to Melty -->
                <div class="mx-auto youtube-video">
                  <iframe
                    src="https://www.youtube.com/embed/aMxwkPb5kOM"
                    frameborder="0"
                    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen
                  ></iframe>
                </div>
              </Portal>
            </div>
            <!-- About the Game -->
            <div
              @click="openModal('about')"
              class="button text-center flex flex-col md:w-56 flex-1 cursor-pointer"
            >
              <div><i class="fas fa-info-circle"></i></div>
              <div>About Melty</div>
              <Portal v-if="modalContent === 'about'" to="modal">
                <div class="flex justify-between">
                  <div class="title">
                    About Melty
                  </div>
                  <div @click="modal = false" class="cursor-pointer z-50">
                    <svg
                      class="fill-current"
                      xmlns="http://www.w3.org/2000/svg"
                      width="32"
                      height="32"
                      viewBox="0 0 18 18"
                    >
                      <path
                        d="M14.53 4.53l-1.06-1.06L9 7.94 4.53 3.47 3.47 4.53 7.94 9l-4.47 4.47 1.06 1.06L9 10.06l4.47 4.47 1.06-1.06L10.06 9z"
                      ></path>
                    </svg>
                  </div>
                </div>
                <p class="mb-3">
                  Melty Blood is a fighting game developed by
                  <a
                    href="https://en.wikipedia.org/wiki/French_Bread_(game_developer)"
                    target="_"
                    >French Bread</a
                  >. It is based on
                  <a href="https://en.wikipedia.org/wiki/Type-Moon" target="_"
                    >Type Moon</a
                  >'s hit visual novel "<a
                    href="https://en.wikipedia.org/wiki/Tsukihime"
                    target="_"
                    >Tsukihime</a
                  >". Since release at
                  <a href="https://en.wikipedia.org/wiki/Comiket" target="_"
                    >Comiket</a
                  >
                  in December 2002 there were 4 major updates. The current
                  version being "Melty Blood Actress Again Current Code Ver.
                  1.07".
                </p>
                <p class="mb-4">
                  With a cast of 31 characters with 3 forms (Moons) each the
                  game has a total of <i>93</i> playable characters.
                </p>
                <p class="text-right mb-6">
                  Source:
                  <a href="https://en.wikipedia.org/wiki/Melty_Blood"
                    >Wikipedia</a
                  >
                </p>
                <p class="mb-2 text-center text-lg">
                  Nice intro by
                  <a
                    href="https://www.youtube.com/channel/UCL45vmk8Jx3Pa3q0xUbZWtw"
                    target="_"
                    >novriltataki</a
                  >:
                </p>
                <!-- Youtube Intro to Melty -->
                <div class="mx-auto youtube-video">
                  <iframe
                    src="https://www.youtube.com/embed/Zz4L7uy3zj8"
                    frameborder="0"
                    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen
                  ></iframe>
                </div>
              </Portal>
            </div>
            <!-- Learning Resources -->
            <div
              @click="openModal('learn')"
              class="button text-center flex flex-col md:w-56 flex-1 cursor-pointer"
            >
              <div><i class="fas fa-graduation-cap"></i></div>
              <div>Learn Melty</div>
              <Portal v-if="modalContent === 'learn'" to="modal">
                <div class="flex justify-between">
                  <div class="title">
                    Learn Melty
                  </div>
                  <div @click="modal = false" class="cursor-pointer z-50">
                    <svg
                      class="fill-current"
                      xmlns="http://www.w3.org/2000/svg"
                      width="32"
                      height="32"
                      viewBox="0 0 18 18"
                    >
                      <path
                        d="M14.53 4.53l-1.06-1.06L9 7.94 4.53 3.47 3.47 4.53 7.94 9l-4.47 4.47 1.06 1.06L9 10.06l4.47 4.47 1.06-1.06L10.06 9z"
                      ></path>
                    </svg>
                  </div>
                </div>
                <p class="mb-2 text-center text-lg">
                  General guide by
                  <a href="https://twitter.com/Fimbulvetr090" target="_">Alps</a
                  >:
                </p>
                <!-- Youtube Complete Guide to melty -->
                <div class="mx-auto youtube-video">
                  <iframe
                    src="https://www.youtube.com/embed/yKPJWNZ8Idw"
                    frameborder="0"
                    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen
                  ></iframe>
                </div>
                <p class="mb-1 mt-6 text-center text-lg">
                  Recommended characters for beginners guide by
                  <a href="https://twitter.com/OnemiESESEBEME" target="_"
                    >Onemi</a
                  >:
                </p>
                <div class="flex flex-col md:flex-row flex-wrap justify-center">
                  <a
                    class="button"
                    href="https://www.evernote.com/shard/s622/sh/24574c5c-22ad-4853-9cb0-d53630d33fca/d97c8677816f7693"
                    target="_"
                  >
                    <i class="fas fa-book mr-1"></i>
                    <span class="font-gradient">Beginner Characters</span>
                  </a>
                </div>
                <p class="mt-3 mb-1 text-center">
                  The Mizuumi wiki is the best place for info about poverty
                  fighting games.
                </p>
                <div class="flex flex-col md:flex-row flex-wrap justify-center">
                  <a
                    class="button"
                    href="https://wiki.gbl.gg/w/Melty_Blood/MBAACC"
                    target="_"
                  >
                    <i class="fas fa-book mr-1"></i>
                    <span class="font-gradient">Mizuumi Wiki</span>
                  </a>
                </div>
                <p class="mt-3 mb-1 text-center">
                  If you want to watch matches with specific characters, there's
                  melty.games and meltydb.
                </p>
                <div class="flex flex-col md:flex-row flex-wrap justify-center">
                  <a class="button" href="http://melty.games/" target="_">
                    <i class="fas fa-tv mr-1"></i>
                    <span class="font-gradient">Melty.Games</span>
                  </a>
                </div>
              </Portal>
            </div>
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
import Intro from '~/components/Intro'

export default {
  components: {
    LenSpin,
    Intro
  },
  data: () => ({
    video: true,
    content: false,
    neco: false,
    modal: false,
    modalContent: ''
  }),
  mounted() {
    if (window.innerWidth <= 768) {
      this.video = false
      this.content = true
    }

    if (this.$route.query.video === 'false') {
      this.video = false
    }

    setTimeout(() => (this.content = true), 3000)
  },
  methods: {
    toggleVideo() {
      this.video = !this.video
      this.$router.push({ path: '/', query: { video: this.video } })
    },
    openModal(content) {
      this.modalContent = content
      this.modal = true
    }
  }
}
</script>

<style>
body {
  background: url('/img/wallpaper.jpg');
  @apply bg-cover bg-center bg-scroll text-gray-100;
}

p {
  @apply text-lg font-medium tracking-wide;
}

.youtube-video {
  padding-top: 55%;
  @apply max-w-4xl relative;
}

.youtube-video iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.title {
  @apply text-3xl uppercase tracking-widest font-black mb-4;
}

.modal a {
  @apply text-red-400;
}
.modal a:hover {
  @apply text-red-600;
}

.button {
  background-color: rgba(0, 0, 0, 0.9);
  @apply rounded-sm py-2 px-3 border-2 border-gray-100 shadow font-semibold tracking-widest uppercase text-xl text-center m-4 outline-none;
}

.modal {
  background-color: rgba(0, 0, 0, 0.9);
  @apply rounded-sm p-8 mx-3 max-w-4xl border-2 border-gray-100 shadow max-h-full overflow-y-auto;
  animation: fade-in 0.5s;
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

.font-gradient {
  background: linear-gradient(rgb(255, 255, 255), rgb(212, 15, 15));
  background-clip: text;
  color: transparent;
}

.modal-background {
  background-color: rgba(0, 0, 0, 0.5);
}

.font-gradient-2 {
  background: linear-gradient(rgb(0, 0, 0), rgb(219, 0, 0));
  background-clip: text;
  color: transparent;
  -webkit-text-stroke: 0.03rem rgb(255, 255, 255);
  @apply font-black;
}

#__nuxt {
  background-color: rgba(0, 0, 0, 0.7);
}

#__layout {
  background-image: url('/img/topo.svg');
}
</style>
