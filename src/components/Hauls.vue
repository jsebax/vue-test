<template>
  <div class="hauls">
    <div class="hauls__track">
      <Track title="Pickup" zip="Zip from" city="City from" type="pickup" />
      <Track title="Delivery" zip="Zip to" city="City to" type="delivery" />
    </div>
    <div class="hauls__accessorials">
      <Accessorials />
    </div>
  </div>
</template>

<script>
import Track from "@/components/Track";
import Accessorials from "@/components/Accessorials";

export default {
  name: "Hauls",
  components: {
    Track,
    Accessorials
  }
};
</script>

<style scoped lang="scss">
.hauls {
  background-color: #b6b6b6;
  padding: 10px 0;
  width: 100vw;

  &__track {
    display: flex;
    margin-bottom: 20px;
    padding: 0 20px;

    .track {
      flex-basis: 50%;

      &:first-child {
        margin-right: 30px;
      }
    }
  }

  &__accessorials {
    padding: 0 20px;
  }
}
</style>
