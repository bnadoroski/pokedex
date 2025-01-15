<template>
  <footer class="bg-blue-lighten-1">
    <div>
        Feito em {{ new Date().getFullYear() }}
    </div>
  </footer>
</template>

<script>
export default {

}
</script>

<style lang="sass">
footer
    position: fixed
    bottom: 0
    width: 100%
    display: flex
    align-items: center
    justify-content: center
</style>