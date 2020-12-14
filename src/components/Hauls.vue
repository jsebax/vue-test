<template>
  <div class="hauls">
    <div class="hauls__track">
      <Track title="Pickup" :zip="zipFrom" :city="cityFrom" type="pickup" />
      <Track title="Delivery" :zip="zipTo" :city="cityTo" type="delivery" />
    </div>
    <div class="hauls__accessorials">
      <Accessorials :selectedOptions="accessorials" />
    </div>
    <div class="hauls__table">
      <HaulsTable :rows="haulsTable" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Track from "@/components/Track";
import Accessorials from "@/components/Accessorials";
import HaulsTable from "@/components/HaulsTable";

export default {
  name: "Hauls",
  components: {
    Track,
    Accessorials,
    HaulsTable
  },
  data() {
    return {
      hauls: {},
      zipFrom: "",
      cityFrom: "",
      zipTo: "",
      cityTo: "",
      accessorials: [],
      haulsTable: []
    };
  },
  mounted() {
    axios
      .get("https://tt.guane.com.co/api/loads/1")
      .then(response => {
        if (response.data && response.data.hauls.length > 0) {
          this.hauls = response.data.hauls[0];
          this.zipFrom = `Zip from: ${this.hauls.zip_from}`;
          this.cityFrom = `City from: ${this.hauls.city_from}`;
          this.zipTo = `Zip to: ${this.hauls.zip_to}`;
          this.cityTo = `City to: ${this.hauls.city_to}`;
          this.accessorials = this.hauls.accessorials;
          this.haulsTable = this.hauls.commodity;
        }
      })
      .catch(error => {
        console.log(error);
      });
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
    margin-bottom: 20px;
    padding: 0 20px;
  }

  &__table {
    padding: 0 10px;
  }
}
</style>
