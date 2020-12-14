<template>
  <div class="hauls-table">
    <div class="hauls-table__buttons">
      <b-button
        class="hauls-table__button"
        variant="info"
        @click="deleteSelected"
        >Delete</b-button
      >
      <b-button variant="info" @click="addNewRow">Add new row</b-button>
    </div>
    <b-table striped outlined hover :fields="fields" :items="tableRows">
      <template #head(checkbox)>
        <b-form-checkbox
          id="checkbox-head"
          name="checkbox-head"
          value="selected-all"
          v-model="toggleAll"
          @change="toggleAllRows"
        ></b-form-checkbox>
      </template>

      <template #cell(checkbox)="data">
        <b-form-checkbox
          :id="`checkbox-${data.index}`"
          :name="`checkbox-${data.index}`"
          :value="data.index"
          v-model="selected"
        ></b-form-checkbox>
      </template>
    </b-table>
  </div>
</template>

<script>
export default {
  name: "HaulsTable",
  props: ["rows"],
  data() {
    return {
      selected: [],
      fields: ["checkbox", "hu_count", "dimensions", "weight"],
      tableRows: []
    };
  },
  watch: {
    rows() {
      this.tableRows = this.rows.slice(0);
    }
  },
  computed: {
    toggleAll: {
      get() {
        return this.selected.length === this.tableRows.length
          ? "selected-all"
          : "";
      },
      set(newValue) {
        return newValue;
      }
    }
  },
  methods: {
    toggleAllRows() {
      const isSelectedAll = this.selected.length === this.tableRows.length;

      if (!isSelectedAll) {
        this.tableRows.forEach((item, index) => {
          const isSelected = this.selected.indexOf(index) > -1;

          if (!isSelected) {
            this.selected.push(index);
          }
        });
      } else {
        this.selected = [];
      }
    },
    deleteSelected() {
      const newItems = this.tableRows.filter((item, index) => {
        if (!this.selected.includes(index)) {
          return item;
        }
      });

      this.tableRows = newItems;
      this.selected = [];
    },
    addNewRow() {
      const newRow = {
        hu_count: "10 Pallets",
        dimensions: "100.0 x 35.0 x 15.0 inch",
        weight: "15.0 lb"
      };

      this.tableRows.push(newRow);
    }
  }
};
</script>

<style scoped lang="scss">
.hauls-table {
  background-color: #ffffff;
  border-radius: 20px;
  overflow: hidden;

  .table {
    margin-bottom: 0;
  }

  &__buttons {
    background-color: #03034c;
    padding: 15px 10px;
    text-align: left;
  }

  &__button {
    margin-right: 20px;
  }
}
</style>
