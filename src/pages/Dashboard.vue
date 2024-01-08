<template>
  <div>
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
              <!-- <span class="text-success"
                ><i class="fas fa-long-arrow-alt-down"></i>
              </span> -->
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
              <!-- <span class="text-success"
                ><i class="fas fa-long-arrow-alt-up"></i>
              </span> -->
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
              <!-- <span class="text-success"
                ><i class="fas fa-long-arrow-alt-up"></i>
              </span> -->
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
                <h2><span class="counter">{{ circleTemp }}</span><sub>°C</sub></h2>
                <div class="block_temp" v-for="i in numbers" v-bind:key="getItemStyleTemp(i)" :style="getItemStyleTemp(i)">
                </div>
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
                <h2><span class="counter">{{ circleHum }}</span><sub>%</sub></h2>
                <div class="block_hum" v-for="i in numbers" v-bind:key="getItemStyleHum(i)" :style="getItemStyleHum(i)"></div>
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
                <h2><span :class="getdegTemp">{{ circleSoil }}</span><sub>%</sub></h2>
                <div class="block_soil" v-for="i in numbers" v-bind:key="getItemStyleSoil(i)" :style="getItemStyleSoil(i)">
                </div>
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
                <h2><span class="count">{{ dateDifference }}</span><sub>Days</sub></h2>
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
              {{ startDate }}
            </div>
          </template>
        </stats-card>
      </div>
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-50"
      >
        <md-card>
          <md-card-header data-background-color="orange">
            <h4 class="title">Vase Stats</h4>
            <p class="category">New vase on 15th September, 2023</p>
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
              <md-tab id="tab-home" md-label="Tasks" md-icon="add_task">
                <nav-tabs-table></nav-tabs-table>
              </md-tab>

              <!-- <md-tab id="tab-pages" md-label="Website" md-icon="code">
                <nav-tabs-table></nav-tabs-table>
              </md-tab>

              <md-tab id="tab-posts" md-label="server" md-icon="cloud">
                <nav-tabs-table></nav-tabs-table>
              </md-tab> -->
            </md-tabs>
          </template>
        </nav-tabs-card>
      </div>
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
      startDate: '2023-12-28',
      endDate: '',
      dateDifference: '',
      thingspeak: [],
      numbers: [],
      circleTemp: "",
      circleHum: "",
      circleSoil: "",
      dailyTempChart: {
        data: {
          labels: [],
          series: [[]],
        },
        options: {
          lineSmooth: this.$Chartist.Interpolation.cardinal({
            tension: 0,
          }),
          low: 20,
          high: 30, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
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
          labels: [],
          series: [[]],
        },
        options: {
          lineSmooth: this.$Chartist.Interpolation.cardinal({
            tension: 0,
          }),
          low: 0,
          high: 1100, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
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
          labels: [],
          series: [[]],
        },
        options: {
          lineSmooth: this.$Chartist.Interpolation.cardinal({
            tension: 0,
          }),
          low: 20,
          high: 60, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
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
  computed: {
  },
  methods: {
    fetchData() {
      const url = 'https://api.thingspeak.com/channels/2389978/feeds.json?api_key=7F5ZOP8I2C34NSN9&results=8';
      axios.get(url)
        .then(response => {
          this.thingspeak = response.data.feeds;

          this.circleTemp = this.thingspeak[7].field1.slice(0,4);
          this.circleHum = this.thingspeak[7].field2.slice(0,4);
          this.circleSoil = parseInt((parseInt(this.thingspeak[7].field3))*100/1023);          
          this.endDate = this.thingspeak[7].created_at.slice(0,10);
          this.calculateDateDifference()
          
          for (var i = 0; i < this.thingspeak.length+1; i++) {
            this.dailyTempChart.data.series[0].push(parseInt(this.thingspeak[i].field1));
            this.dailyTempChart.data.labels.push(this.thingspeak[i].created_at.slice(11,16));
            this.dailyHumChart.data.series[0].push(parseInt(this.thingspeak[i].field2));
            this.dailyHumChart.data.labels.push(this.thingspeak[i].created_at.slice(11,16));
            this.dailySoilChart.data.series[0].push(parseInt(this.thingspeak[i].field3));
            this.dailySoilChart.data.labels.push(this.thingspeak[i].created_at.slice(11,16));
          }
        })
        .catch(error => {
          console.error(error);
        });
    },
    getItemStyleTemp(event){
      let circlechild = Math.floor(((parseInt(this.circleTemp))*50)/100);;
      if (event <= circlechild) {
          return {
          transform: `rotate(${7.2*event}deg)`,
          animationDelay: `${event/15}s`,
          background: `rgb(255, 16, 16)`,
        }
      }
      else {
        return {
          transform: `rotate(${7.2*event}deg)`,
          animationDelay: `${event/15}s`,
        }
      }
    },
    getItemStyleHum(event){
      let circlechild = Math.floor(((parseInt(this.circleHum))*50)/100);;
      if (event <= circlechild) {
          return {
          transform: `rotate(${7.2*event}deg)`,
          animationDelay: `${event/15}s`,
          background: `rgb(0, 255, 251)`,
        }
      }
      else {
        return {
          transform: `rotate(${7.2*event}deg)`,
          animationDelay: `${event/15}s`,
        }
      }
    },
    getItemStyleSoil(event){
      let circlechild = Math.floor(((parseInt(this.circleSoil))*50)/100);;
      if (event <= circlechild) {
          return {
          transform: `rotate(${7.2*event}deg)`,
          animationDelay: `${event/15}s`,
          background: `rgb(255, 242, 0)`,
        }
      }
      else {
        return {
          transform: `rotate(${7.2*event}deg)`,
          animationDelay: `${event/15}s`,
        }
      }
    },
    calculateDateDifference() {
      const start = new Date(this.startDate);
      const end = new Date(this.endDate);
      const differenceInTime = end.getTime() - start.getTime();
      const differenceInDays = Math.floor(differenceInTime / (1000 * 3600 * 24));
      this.dateDifference = differenceInDays;
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
.card .rating .block_soil{
  position: absolute;
  width: 2px;
  height: 13px;
  background: #000;
  left: 48%;
  transform-origin: 50% 60px;
  opacity: 0;
  animation: animate 0.1s linear forwards;
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