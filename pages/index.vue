<template>
  <div class="container mx-auto h-full">
    <div class="flex flex-col h-full justify-center items-center">
      <h1 class="text-6xl tracking-widest font-gradient-2">
        PLAY
      </h1>
      <img class="w-2/3" src="/img/logo.png" alt="melty blood logo" />

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
          <span class="font-gradient">
            Download community version with rollback netcode
          </span>
        </a>
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
        <a
          class="button"
          href="https://discordapp.com/invite/33cskPv"
          target="_"
        >
          <i class="fab fa-discord font-normal mr-1"></i>
          <span class="font-gradient">
            Join the Discord
          </span>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>
#__nuxt {
  background-color: rgba(0, 0, 0, 0.6);
}

body {
  background: url('/img/wallpaper.jpg');
  @apply bg-cover bg-center bg-scroll text-gray-100;
}

.button {
  background-color: rgba(0, 0, 0, 0.9);
  @apply rounded-sm py-2 px-3 border-2 border-gray-100 shadow font-semibold tracking-widest uppercase text-xl text-center m-4 outline-none;
}

.font-gradient {
  background: linear-gradient(rgb(255, 255, 255), rgb(212, 15, 15));
  background-clip: text;
  color: transparent;
}

.font-gradient-2 {
  background: linear-gradient(rgb(0, 0, 0), rgb(219, 0, 0));
  background-clip: text;
  color: transparent;
  -webkit-text-stroke: 2px rgb(255, 255, 255);
  @apply font-black;
}
</style>
