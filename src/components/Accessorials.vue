<template>
  <div class="accessorials">
    <h2 class="accessorials__title">Accessorials</h2>
    <hr />
    <div class="accessorials__options">
      <b-form-group>
        <b-form-checkbox-group
          id="accessorials"
          :options="options"
          name="accessorials"
        ></b-form-checkbox-group>
      </b-form-group>
    </div>
  </div>
</template>

<script>
export default {
  name: "Accessorials",
  data() {
    return {
      options: [
        {
          text: "Hazmat",
          value: "hazmat"
        },
        {
          text: "Bonded",
          value: "bonded"
        },
        {
          text: "Tarps",
          value: "tarps"
        },
        {
          text: "Airport Delivery Non TSA",
          value: "airportDeliveryNonTsa"
        },
        {
          text: "Airport Delivery TSA",
          value: "airportDeliveryTsa"
        },
        {
          text: "Oversize/Overweight Permits",
          value: "oversizeOverweight"
        },
        {
          text: "Escorts",
          value: "escorts"
        },
        {
          text: "Team Drivers",
          value: "teamDrivers"
        },
        {
          text: "Non Stackable",
          value: "nonStackable"
        }
      ]
    };
  }
};
</script>

<style scoped lang="scss">
.accessorials {
  background-color: #ffffff;
  border-radius: 20px;
  padding: 10px;
}
</style>
