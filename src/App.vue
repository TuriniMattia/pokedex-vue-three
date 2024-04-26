<template>
  <div>
    <AppMain />

  </div>
</template>

<script>
import AppMain from './components/AppMain.vue';
import AppCard from './components/AppCard.vue';
import AppInput from './components/AppInput.vue';
export default {
  components: {
    AppMain,
  },
  data() {


    return {
      AppInput,
      AppCard,
    }
  }
}
</script>

<style lang="scss" scoped></style>
