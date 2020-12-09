<template>
  <div class="track">
    <h2
      class="track__title"
      :class="{ green: type === 'pickup', red: type === 'delivery' }"
    >
      {{ title }}
    </h2>
    <hr />
    <div class="track__info">
      <p class="track__info-text">{{ zip }}</p>
      <p class="track__info-text">{{ city }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Track",
  props: ["title", "zip", "city", "type"]
};
</script>

<style scoped lang="scss">
.track {
  background-color: #ffffff;
  border-radius: 20px;
  padding: 10px;

  &__title {
    &.green {
      color: green;
    }

    &.red {
      color: red;
    }
  }

  &__info {
    display: flex;
    padding: 0 10px;

    &-text {
      background-color: #939393;
      border-radius: 5px;
      flex-basis: 50%;
      padding: 10px;
      text-align: left;

      &:first-child {
        margin-right: 30px;
      }
    }
  }
}
</style>
