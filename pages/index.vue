<template>
  <div class="container mx-auto h-full">
    <div class="flex flex-col h-full justify-center items-center">
      <h1 class="text-6xl">
        PLAY
      </h1>
      <img class="w-2/3" src="/img/logo.png" alt="melty blood logo" />

      <div class="flex flex-wrap justify-center">
        <a class="button" href="https://www.youtube.com/watch?v=Zz4L7uy3zj8">
          <span class="font-gradient">Intro to Melty</span>
        </a>
        <a class="button" href="https://www.youtube.com/watch?v=yKPJWNZ8Idw">
          <span class="font-gradient">Complete Guide to Melty</span>
        </a>
        <a class="button" href="http://wiki.mizuumi.net/w/Melty_Blood">
          <span class="font-gradient">Wiki</span>
        </a>
        <a
          class="button"
          href="https://store.steampowered.com/app/411370/Melty_Blood_Actress_Again_Current_Code/"
        >
          <span class="font-gradient">Buy the Game</span>
        </a>
        <a
          class="button"
          href="https://mega.nz/#!qRMTHK6A!QCBOqnH91TynUqQjddgm8omGBeIG5Yp_-iT-Q5QmTas"
        >
          <span class="font-gradient"
            >Download the community version with rollback netcode</span
          >
        </a>
        <a class="button" href="https://discordapp.com/invite/33cskPv">
          <span class="font-gradient">Join the Discord</span>
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
  @apply rounded-sm py-2 px-3 border-2 border-gray-100 shadow font-bold tracking-widest uppercase text-xl m-4;
}

.font-gradient {
  background: linear-gradient(rgb(255, 255, 255), rgb(184, 14, 14));
  background-clip: text;
  color: transparent;
}
</style>
