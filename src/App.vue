<script setup lang="ts">
import HeaderBar from './components/HeaderBar.vue'
import ItemBrowser from './components/ItemBrowser.vue'
import FooterBar from './components/FooterBar.vue'
</script>

<template>
  <HeaderBar class="sticky" />
  <img class="background" src="@/assets/images/gameBackground.jpg" alt="Background Image" />
  <div class="content">
    <ItemBrowser class="item-browser" />
  </div>
  <FooterBar />
</template>

<style scoped>
.sticky {
  position: sticky;
  top: 0;
}

.background {
  height: 100%;
  width: 100%;
  filter: grayscale(100%) blur(3px);
  mask-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.1) 50%, transparent 90%);
  position: absolute;
  top: 0;
  z-index: -1000;
}

.content {
  max-width: 1240px;
  margin: 0 auto;
  padding-top: 120px;
}
</style>
