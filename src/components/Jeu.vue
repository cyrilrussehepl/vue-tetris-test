<template>
  <h1>Jeu</h1>
  <iframe :src="gameUrl" width="800" height="800"></iframe>
</template>

<script>
export default {
  computed: {
    gameUrl() {
      return '/Tetris/index.html'
    }
  }
}
</script>
