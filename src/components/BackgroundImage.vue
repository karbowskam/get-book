<template>
  <div class="backgroundImageWrapper">
    <slot />
  </div>
</template>

<script>
export default {
  name: "BackgroundImage",
};
</script>

<style lang="scss" scoped>
.backgroundImageWrapper {
  position: fixed;
  width: 100%;
  height: 100vh;
  background-image: url("../assets/books-gb5e5e6791_1920.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 7% 0%;
  padding: 8px 30px;
}

.backgroundImageWrapper::after {
  content: "";
  background-color: rgb(245, 245, 245);
  opacity: 0.4;
  position: absolute;
  z-index: 2;
  width: 100%;
  height: 100vh;
  top: 0;
  left: 0;
}
</style>
