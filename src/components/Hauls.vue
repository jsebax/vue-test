<template>
  <div class="hauls">
    <div class="hauls__track">
      <Track title="Pickup" zip="Zip from" city="City from" type="pickup" />
      <Track title="Delivery" zip="Zip to" city="City to" type="delivery" />
    </div>
  </div>
</template>

<script>
import Track from "@/components/Track";

export default {
  name: "Hauls",
  components: {
    Track
  }
};
</script>

<style scoped lang="scss">
.hauls {
  background-color: #b6b6b6;
  width: 100vw;

  &__track {
    display: flex;
    padding: 10px 20px;

    .track {
      flex-basis: 50%;

      &:first-child {
        margin-right: 30px;
      }
    }
  }
}
</style>
