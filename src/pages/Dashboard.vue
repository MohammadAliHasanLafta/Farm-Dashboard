<template>
  <div class="content">
    <div class="md-layout">
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-33"
      >
        <chart-card
          :chart-data="dailyTempChart.data"
          :chart-options="dailyTempChart.options"
          :chart-type="'Line'"
          data-background-color="blue"
        >
          <template slot="content">
            <h4 class="title">Temperature</h4>
            <p class="category">
              <span class="text-success"
                ><i class="fas fa-long-arrow-alt-down"></i> 10%
              </span>
              decrease in today temperature.
            </p>
          </template>

          <template slot="footer">
            <div class="stats">
              <md-icon>access_time</md-icon>
              updated 4 minutes ago
            </div>
          </template>
        </chart-card>
      </div>
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-33"
      >
      <chart-card
          :chart-data="dailyHumChart.data"
          :chart-options="dailyHumChart.options"
          :chart-type="'Line'"
          data-background-color="red"
        >
          <template slot="content">
            <h4 class="title">Humidity</h4>
            <p class="category">
              <span class="text-success"
                ><i class="fas fa-long-arrow-alt-up"></i> 9%
              </span>
              increase in today temperature.
            </p>
          </template>

          <template slot="footer">
            <div class="stats">
              <md-icon>access_time</md-icon>
              updated 4 minutes ago
            </div>
          </template>
        </chart-card>
      </div>
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-33"
      >
      <chart-card
          :chart-data="dailySoilChart.data"
          :chart-options="dailySoilChart.options"
          :chart-type="'Line'"
          data-background-color="green"
        >
          <template slot="content">
            <h4 class="title">Soil Moisture</h4>
            <p class="category">
              <span class="text-success"
                ><i class="fas fa-long-arrow-alt-up"></i> 9%
              </span>
              increase in today temperature.
            </p>
          </template>

          <template slot="footer">
            <div class="stats">
              <md-icon>access_time</md-icon>
              updated 4 minutes ago
            </div>
          </template>
        </chart-card>
      </div>
      <div
        class="md-layout-item md-medium-size-50 md-xsmall-size-100 md-size-25"
      >
        <stats-card data-background-color="green">
          <template slot="header">
            <md-icon>thermostat</md-icon>
            <div class="card">
              <div class="rating">
                <h2><span class="counter">{{ thingspeak[7].field1 }}</span><sub>°C</sub></h2>
                <div class="block_temp" v-for="i in numbers" v-bind:key="getItemStyle(i)" :style="getItemStyle(i)"></div>
              </div>
            </div>
          </template>
          <template>
            
          </template>

          <template slot="content">
            <h5 class="category">Temperature</h5>
            <h3 class="title"></h3>
          </template>

          <template slot="footer">
            <div class="stats">
              <md-icon>date_range</md-icon>
              Last 3 Min.
            </div>
          </template>
        </stats-card>
      </div>
      <div
        class="md-layout-item md-medium-size-50 md-xsmall-size-100 md-size-25"
      >
        <stats-card data-background-color="orange">
          <template slot="header">
            <md-icon>opacity</md-icon>
            <div class="card">
              <div class="rating">
                <h2><span class="counter">{{ thingspeak[7].field2 }}</span><sub>%</sub></h2>
                <div class="block_hum" v-for="i in numbers" v-bind:key="getItemStyle(i)" :style="getItemStyle(i)"></div>
              </div>
            </div>
          </template>

          <template slot="content">
            <h5 class="category">Humidity</h5>
            <h3 class="title"></h3>
          </template>
       
          <template slot="footer">
            <div class="stats">
              <md-icon>date_range</md-icon>
              Last 3 Min.
            </div>
          </template>
        </stats-card>
      </div>
      <div
        class="md-layout-item md-medium-size-50 md-xsmall-size-100 md-size-25"
      >
        <stats-card data-background-color="red">
          <template slot="header">
            <md-icon>eco</md-icon>
            <div class="card">
              <div class="rating">
                <h2><span class="counter">{{ thingspeak[7].field3 }}</span></h2>
                <div class="block_eco" v-for="i in numbers" v-bind:key="getItemStyle(i)" :style="getItemStyle(i)"></div>
              </div>
            </div>
          </template>

          <template slot="content">
            <h5 class="category">Soil Moisture</h5>
            <h3 class="title"></h3>
          </template>

          <template slot="footer">
            <div class="stats">
              <md-icon>date_range</md-icon>
              Last 3 Min.
            </div>
          </template>
        </stats-card>
      </div>
      <div
        class="md-layout-item md-medium-size-50 md-xsmall-size-100 md-size-25"
      >
        <stats-card data-background-color="blue">
          <template slot="header">
            <md-icon>local_florist</md-icon>
            <div class="card">
              <div class="rating">
                <h2><span class="count">67</span><sub>Days</sub></h2>
              </div>
            </div>
          </template>

          <template slot="content">
            <h5 class="category">Life of vase</h5>
            <h3 class="title"></h3>
          </template>

          <template slot="footer">
            <div class="stats">
              <md-icon>update</md-icon>
              2023/10/20
            </div>
          </template>
        </stats-card>
      </div>
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-50"
      >
        <md-card>
          <md-card-header data-background-color="orange">
            <h4 class="title">Employees Stats</h4>
            <p class="category">New employees on 15th September, 2016</p>
          </md-card-header>
          <md-card-content>
            <ordered-table table-header-color="orange"></ordered-table>
          </md-card-content>
        </md-card>
      </div>
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-50"
      >
        <nav-tabs-card>
          <template slot="content">
            <span class="md-nav-tabs-title">Tasks:</span>
            <md-tabs class="md-success" md-alignment="left">
              <md-tab id="tab-home" md-label="Bugs" md-icon="bug_report">
                <nav-tabs-table></nav-tabs-table>
              </md-tab>

              <md-tab id="tab-pages" md-label="Website" md-icon="code">
                <nav-tabs-table></nav-tabs-table>
              </md-tab>

              <md-tab id="tab-posts" md-label="server" md-icon="cloud">
                <nav-tabs-table></nav-tabs-table>
              </md-tab>
            </md-tabs>
          </template>
        </nav-tabs-card>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import {
  StatsCard,
  ChartCard,
  NavTabsCard,
  NavTabsTable,
  OrderedTable,
} from "@/components";

export default {
  components: {
    StatsCard,
    ChartCard,
    NavTabsCard,
    NavTabsTable,
    OrderedTable,
  },
  data() {
    return {
      thingspeak: [],
      numbers: [],
      dailyTempChart: {
        data: {
          labels: ["M", "T", "W", "T", "F", "S", "S"],
          series: [[]],
        },
        options: {
          lineSmooth: this.$Chartist.Interpolation.cardinal({
            tension: 0,
          }),
          low: 0,
          high: 50, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
          chartPadding: {
            top: 0,
            right: 0,
            bottom: 0,
            left: 0,
          },
        },
      },
      dailySoilChart: {
        data: {
          labels: ["M", "T", "W", "T", "F", "S", "S"],
          series: [[]],
        },
        options: {
          lineSmooth: this.$Chartist.Interpolation.cardinal({
            tension: 0,
          }),
          low: 0,
          high: 800, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
          chartPadding: {
            top: 0,
            right: 0,
            bottom: 0,
            left: 0,
          },
        },
      },
      dailyHumChart: {
        data: {
          labels: ["M", "T", "W", "T", "F", "S", "S"],
          series: [[]],
        },
        options: {
          lineSmooth: this.$Chartist.Interpolation.cardinal({
            tension: 0,
          }),
          low: 0,
          high: 100, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
          chartPadding: {
            top: 0,
            right: 0,
            bottom: 0,
            left: 0,
          },
        },
      },
    };
  },
  mounted() {
  },
  created() {
    this.fetchData();
    this.numbers = Array.from(Array(51).keys());
  },
  methods: {
    fetchData() {
      const url = 'https://api.thingspeak.com/channels/2389978/feeds.json?api_key=7F5ZOP8I2C34NSN9&results=8';
      axios.get(url)
        .then(response => {
          this.thingspeak = response.data.feeds;
          // this.dailyTempChart.data.series.pop();
          for (var i = 1; i < this.thingspeak.length+2; i++) {
            this.dailyTempChart.data.series[0].push(parseInt(this.thingspeak[i].field1));
            this.dailyHumChart.data.series[0].push(parseInt(this.thingspeak[i].field2));
            this.dailySoilChart.data.series[0].push(parseInt(this.thingspeak[i].field3));
          }
        })
        .catch(error => {
          console.error(error);
        });
    },
    getItemStyle(event){
      return {
        transform: `rotate(${7.2*event}deg)`,
        animationDelay: `${event/15}s`
      }
    },
  },
};
</script>

<style scoped>
.card {
  position: relative;
  width: 100px;
  height: 110px;
}
.card .rating{
  position: relative;
  width: 100%;
  height: 100%;
}
.card .rating .block_temp{
  position: absolute;
  width: 2px;
  height: 13px;
  background: #000;
  left: 48%;
  transform-origin: 50% 60px;
  opacity: 0;
  animation: animate 0.1s linear forwards;
}
.card .rating .block_temp:nth-child(-n+13){
  background: rgb(255, 16, 16);
  box-shadow: 0 0 15px rgb(255, 16, 16), 0 0 30px rgb(255, 16, 16);
}
.card .rating .block_hum{
  position: absolute;
  width: 2px;
  height: 13px;
  background: #000;
  left: 48%;
  transform-origin: 50% 60px;
  opacity: 0;
  animation: animate 0.1s linear forwards;
}
.card .rating .block_hum:nth-child(-n+23){
  background: rgb(0, 255, 251);
  box-shadow: 0 0 15px rgb(0, 255, 251), 0 0 30px rgb(0, 255, 251);
}
.card .rating .block_eco{
  position: absolute;
  width: 2px;
  height: 13px;
  background: #000;
  left: 48%;
  transform-origin: 50% 60px;
  opacity: 0;
  animation: animate 0.1s linear forwards;
}
.card .rating .block_eco:nth-child(-n+20){
  background: rgb(255, 242, 0);
  box-shadow: 0 0 15px rgb(255, 242, 0), 0 0 30px rgb(255, 242, 0);
}
@keyframes animate{
  to{
    opacity: 1;
  }
}
.card .rating h2{
  position: absolute;
  top: 45%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: #fff;
  font-size: 1em;
  font-weight: 250;
  text-align: center;
}
.card .rating h2 span{
  font-size: 2.5em;
  font-weight: 700;

}
</style>