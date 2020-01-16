<template>
  <!-- Intro -->
  <div
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
</template>

<style>
.static {
  opacity: 0.6;
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
</style>
