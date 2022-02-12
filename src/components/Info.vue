<template>
  <div class="infoWrapper">
    <h1 class="heading">GET BOOK</h1>
    <p class="first-paragraph">
      Get Book is a simple book finder. Discover and broaden your horizons.
    </p>
    <p class="second-paragraph">Type title or author to start</p>
  </div>
</template>

<script>
export default {
  name: "Info",
};
</script>

<style lang="scss" scoped>
.infoWrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;

  .heading {
    font-size: 48px;
    letter-spacing: 2px;
    font-weight: 700;
    margin: 15px 0;
  }

  .first-paragraph {
    margin: 5px;
    font-size: 20px;
    font-weight: 300;
  }

  .second-paragraph {
    margin: 25px 0 0 0;
    font-size: 15px;
    font-weight: 300;
  }
}
</style>
