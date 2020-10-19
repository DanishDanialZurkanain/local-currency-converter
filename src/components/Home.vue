<template>
  <div class="d-flex align-items-center min-vh-100">
    <div class="container">
      <b-card header="💷 Malaysia Currency Converter">
        <b-form>
          <div class="row">
            <div class="col-5">
              <b-form-input
                type="number"
                required
                placeholder="MYR"
                v-model="amount"
              ></b-form-input>
            </div>
            <div class="col-2 text-center">
              <span class="align-middle">to</span>
            </div>
            <div class="col-5">
              <b-form-select
                required
                v-model="cur_to_selected"
                :options="cur_to"
              ></b-form-select>
            </div>
          </div>
          <div class="my-3">
            <b-alert v-if="result" class="text-center" variant="info" show
              >{{ result_currency }} {{ result }}</b-alert
            >
          </div>
          <b-button @click="calculate" block variant="outline-primary"
            >Calculate</b-button
          >
        </b-form>
      </b-card>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      amount: "",
      result: "",
      result_currency: "",
      cur_to: [
        {
          value: null,
          text: "Please Select",
        },
        {
          value: {
            currency: 0.33,
            label: "SGD",
          },
          text: "Singapore",
        },
        {
          value: {
            currency: 3547.39,
            label: "IDR",
          },
          text: "Indonesia",
        },
        {
          value: {
            currency: 25.46,
            label: "JPY",
          },
          text: "Japan",
        },
        {
          value: {
            currency: 274.7,
            label: "KRW",
          },
          text: "Korean",
        },
        {
          value: {
            currency: 0.34,
            label: "AUD",
          },
          text: "Australia",
        },
      ],
      cur_to_selected: null,
    };
  },
  methods: {
    calculate() {
      if (this.amount != "") {
        this.result = (this.amount * this.cur_to_selected.currency).toFixed(2);
        this.result_currency = this.cur_to_selected.label;
      } else {
        alert("⚠ Enter Some Amount to Proceed");
      }
    },
  },
};
</script>

<style scoped>
</style>
