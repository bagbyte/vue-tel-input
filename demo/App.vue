<template>
  <div id="app">
    <h1>Telephone Input Vue</h1>
    <h2 style="color: #999">made with &#x2764; by Steven.</h2>
    <div style="width: 500px; margin: 20px auto;">
      <vue-tel-input v-model="phoneNumber" @onInput="onInput" :preferredCountries="['de']" :enabledCountryCode="true"></vue-tel-input>
    </div>
    <div v-if="phone.number" style="color: #e83e8c">
      <span>
        Number:
        <strong>{{ phone.formatted }}</strong>,&nbsp;
      </span>
      <span>
        Is valid:
        <strong>{{ phone.isValid }}</strong>,&nbsp;
      </span>
      <span>
        Country:
        <strong>{{ phone.country }}</strong>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      phoneNumber: '',
      phone: {
        number: '',
        isValid: false,
        country: undefined,
        formatted: '',
      },
    };
  },
  methods: {
    onInput({ number, isValid, country, formatted }) {
      this.phone.number = number;
      this.phone.isValid = isValid;
      this.phone.country = country && country.name;
      this.phone.formatted = formatted;
    },
  },
};
</script>
