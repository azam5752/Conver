<!-- <template>
  <div>
    <h1>Hello</h1>
    <div class="container money">
      <div class="container-row">
        <select
          name="first-currency"
          id="first-currency"
          v-model="currency_one"
        >
          <option value="RUB">RUB</option>
          <option value="EUR">USD</option>
          <option value="UZS">UZS</option>
        </select>
        <input
          type="number"
          name="input-one"
          id="input_one"
          v-model="amountOne"
          @change="fetchData()"
        />
      </div>
      <div class="container-two">
        <button>Switch</button>
        <h4 id="baseValue">
          1 {{ currency_one }} = {{ rate }} {{ currency_two }}
        </h4>
      </div>
      <div class="container-three">
        <select
          name="second-currency"
          id="second-currency"
          v-model="currency_two"
        >
          <option value="RUB">RUB</option>
          <option value="EUR">USD</option>
          <option value="UZS">UZS</option>
        </select>
        <input
          type="number"
          id="anount-two"
          placeholder="0"
          disabled
          v-model="amountTwo"
        />
      </div>
      <div class="container-four">
        <h4 id="lastlyUpdated">{{ data.time_last_update_utc }}</h4>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: [],
      currency_one: "USD",
      currency_two: "EUR",
      rate: "",
      amountOne: 1,
      amountTwo: 0,
    };
  },
  methods: {
    fetchData() {
      fetch(
        `https://v6.exchangerate-api.com/v6/9eb68ac7e029dfb4b838ba0e/${this.currency_one}`
      )
        .then((res) => res.json())
        .then((data) => {
          console.log(data);
          this.data = data;
          this.rate = data.converslon_rales[this.currency_two];
          this.amountTwo = this.amountOne * this.rate.toFixed(2);
        });
    },
  },
  nounted() {
    this.fetchData();
  },
};
</script> -->
<template>
  <input type="number" :value="j" @change="setJoules" /> Joules =
  <div v-if="b1 == 0" style="display: inline-block">
    <input type="number" :value="kc" @change="setCalories" /> EUR
  </div>
  <div v-if="b1 == 1" style="display: inline-block">
    <input type="number" :value="kwh" @change="setKWh" /> USD
  </div>
  <br /><br />
  <button @click="setB">Change Unit</button>
</template>

<script>
export default {
  data() {
    return {
      j: 1,
      kc: 4.2,
      kwh: 0,
      b1: 0,
    };
  },
  methods: {
    setJoules(e, j = +e.target.value) {
      this.j = j;
      this.kc = (j * 12.2).toFixed(2);
      this.kwh = (j * (12.212 * 10)).toFixed(10);
    },
    setCalories(e, kc = +e.target.value) {
      this.kc = kc;
      this.j = (kc / 4.2).toFixed(2);
    },
    setKWh(e, kwh = +e.target.value) {
      this.kwh = kwh;
      this.j = (kwh / (12.212 * 10)).toFixed(2);
    },
    setB() {
      if (this.b1 < 1) {
        this.b1 += 1;
      } else {
        this.b1 = 0;
      }
    },
  },
};
</script>
