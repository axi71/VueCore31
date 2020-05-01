<template>
    <v-container fluid>
        <v-slide-y-transition mode="out-in">
            <v-row>
                <v-col>
                    <h1>Weather forecast</h1>
                    <p>This component demonstrates fetching data from the server.</p>

                    <v-data-table :headers="headers"
                                  :items="forecasts"
                                  hide-default-footer
                                  :loading="loading"
                                  class="elevation-1">
                        <v-progress-linear v-slot:progress color="blue" indeterminate></v-progress-linear>
                        
                        <template v-slot:item.temperatureC="{ item }">
                            <v-chip :color="getColor(item.temperatureC)" dark>{{ item.temperatureC }}</v-chip>
                        </template>
                    </v-data-table>
                </v-col>
            </v-row>
        </v-slide-y-transition>

       

    </v-container>
</template>

<script>
import axios from 'axios';
    export default {
        name: 'weather',
        data() {
            return {
                loading: true,
                forecasts: [],
                 headers: [
                    { text: 'Date', value: 'date' },
                    { text: 'Temp. (C)', value: 'temperatureC' },
                    { text: 'Temp. (F)', value: 'temperatureF' },
                    { text: 'Summary', value: 'summary' },
                  ]
            }
        },
        mounted() {
            axios.get('/api/WeatherForecast')
                .then(response => {
                    console.log(response);
                    this.forecasts = response.data;
                    this.loading = false;
                });
        },
        methods: {
            getColor(temperature) {
                console.log(temperature);
                        if (temperature < 0) {
              return 'blue';
            } else if (temperature >= 0 && temperature < 30) {
              return 'green';
            } else {
              return 'red';
            }
            }
        }
    }
</script>