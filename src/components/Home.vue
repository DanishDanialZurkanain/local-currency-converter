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
            <b-alert v-if="result" class="text-center" variant="info" show>{{
              result
            }}</b-alert>
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
      cur_to: [
        {
          value: null,
          text: "Please Select",
        },
        {
          value: 0.33,
          text: "SGD",
        },
        {
          value: 3547.39,
          text: "IDR",
        },
        {
          value: 25.46,
          text: "JPY",
        },
        {
          value: 274.7,
          text: "KRW",
        },
        {
          value: 0.34,
          text: "AUD",
        },
      ],
      cur_to_selected: null,
    };
  },
  methods: {
    calculate() {
      if (this.amount != "") {
        this.result = (this.amount * this.cur_to_selected).toFixed(2);
      } else {
        alert("⚠ Enter Some Amount to Proceed");
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
