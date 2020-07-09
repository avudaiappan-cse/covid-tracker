<template>
  <div>
    <div
      v-if="dataLoaded !== true"
      style="text-align:center;color:white;font-size:3rem;height:100vh;"
    >
      <h2>Loading....</h2>
    </div>
    <div v-else>
      <div class="report">
        <div class="report__container total">
          <h5>Total</h5>
          <br />
          <h2>{{formatNumber(totalCases)}}</h2>
        </div>
        <div class="report__container">
          <h5>Active</h5>
          <br />
          <h2>{{formatNumber(activeCases)}}</h2>
        </div>
        <div class="report__container good">
          <h5>Recovered</h5>
          <br />
          <h2>{{formatNumber(recoveredCases)}}</h2>
        </div>
        <div class="report__container warn">
          <h5>Deceased</h5>
          <br />
          <h2>{{formatNumber(deathCases)}}</h2>
        </div>
      </div>
      <table class="table-data">
        <th>Region</th>
        <th>Total</th>
        <th>Recovered</th>
        <th>Deceased</th>
        <TableData
          v-for="(region,index) in regions"
          v-bind:key="index"
          :region="region.loc"
          :recovered="region.discharged"
          :confirmed="region.totalConfirmed"
          :deceased="region.deaths"
        />
      </table>
      <br />
    </div>
  </div>
</template>

<script>
import TableData from "./MainPageTable";
export default {
  name: "Container",
  components: {
    TableData
  },
  data: function() {
    return {
      totalCases: 0,
      activeCases: 0,
      recoveredCases: 0,
      deathCases: 0,
      regions: [],
      dataLoaded: false
    };
  },
  methods: {
    formatNumber: function(val) {
      return val.toLocaleString("en-IN");
    }
  },
  mounted: async function() {
    const response = await fetch(
      "https://api.rootnet.in/covid19-in/stats/latest"
    );
    const data = await response.json();
    this.totalCases = data.data["unofficial-summary"][0].total;
    this.activeCases = data.data["unofficial-summary"][0].active;
    this.recoveredCases = data.data["unofficial-summary"][0].recovered;
    this.deathCases = data.data["unofficial-summary"][0].deaths;
    this.regions = data.data.regional;
    this.dataLoaded = true;
  }
};
</script>

<style scoped>
.report {
  display: flex;
  margin: 0 auto;
  text-align: center;
  width: fit-content;
}
.report__container {
  padding: 1rem;
  background: #212121;
  color: rgb(201, 5, 201);
  font-size: 1.5rem;
}
.total {
  color: white;
}
.good {
  color: lime;
}
.warn {
  color: red;
}
table {
  border-collapse: unset;
  border-spacing: 0px;
}
.table-data {
  margin: 0 auto;
  width: fit-content;
  background: purple;
  color: white;
  font-size: 1.2rem;
  margin-top: 1rem;
}
th {
  padding: 0.3rem;
}
@media only screen and (max-width: 720px) {
  .report {
    display: flex;
    flex-direction: column;
    margin: 0 auto;
    width: auto;
  }
  .table-data {
    margin: 0 auto;
    width: auto;
    background: purple;
    color: white;
    font-size: 1rem;
    margin-top: 1rem;
  }
}
</style>