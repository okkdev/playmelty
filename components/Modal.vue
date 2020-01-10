<template>
  <div
    v-if="modal"
    @click="modal = false"
    class="fixed h-full w-full modal-background z-20"
  >
    <div class="container h-full mx-auto flex justify-center items-center">
      <div class="modal">
        <portal-target name="modal"></portal-target>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    modal: false
  })
}
</script>
