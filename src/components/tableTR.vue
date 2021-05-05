<template>
  <div class="row">
      <div class="col-md-3 mb-4 mb-md-0">
        <div class="covid-card confirmed">
          <div class="covid-card__title mb-5">Vaka Sayısı :</div>
          <div class="covid-card__count">{{ Intl.NumberFormat().format(dataTR[0].confirmed)}}</div>
        </div>
      </div>
      <div class="col-md-3 mb-4 mb-md-0">
        <div class="covid-card critical">
          <div class="covid-card__title mb-5">Ağır Hasta Sayısı :</div>
          <div class="covid-card__count">{{ Intl.NumberFormat().format(dataTR[0].critical)}}</div>
        </div>
      </div>
      <div class="col-md-3 mb-4 mb-md-0">
        <div class="covid-card deaths">
          <div class="covid-card__title mb-5">Vefat Sayısı :</div>
          <div class="covid-card__count">{{ Intl.NumberFormat().format(dataTR[0].deaths)}}</div>
        </div>
      </div>
      <div class="col-md-3 mb-4 mb-md-0">
        <div class="covid-card recovered">
          <div class="covid-card__title mb-5">İyileşen Sayısı :</div>
          <div class="covid-card__count">{{ Intl.NumberFormat().format(dataTR[0].recovered)}}</div>
        </div>
      </div>
    </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      dataTR: null,
    };
  },
  methods: {
    getData() {
      axios
        .get("https://covid-19-data.p.rapidapi.com/country/code?code=tr&format=json", 
        {
          headers: {
            "x-rapidapi-key":
              "76a9939d69msh1745dfee91db31dp1c61d4jsn76452a067b81",
            "x-rapidapi-host": "covid-19-data.p.rapidapi.com",
          },
        })
        .then((response) => (this.dataTR = response.data));
    },
  },
  mounted() {
    this.getData();
  },
};
</script>

<style lang="scss">
$blue: #0465d8;
$orange: #f57a00;
$red: #740400;
$green: #076400;

.covid-card {
  color: #fff;
  padding: 15px;

  &__title {
    font-weight: 600;
    font-size: 18px;
  }

  &__count {
    font-weight: 800;
    font-size: 42px;
    padding: 0px;
    line-height: 1;
    margin: 0px;    
  }

}

.confirmed {
    background-color: $blue;
}

.critical {
    background-color: $orange;
}

.recovered {
    background-color: $green;
}

.deaths {
    background-color: $red;
}

</style>
