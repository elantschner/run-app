<template>
  <v-container class="my-md-8 py-8 blur white--text elevation-10">
    <v-row class="text-center">
      <v-col cols="12" class="mb-4 my-3">
        <h2 class="font-weight-bold mb-3">
          Wettkampfzeitenrechner
        </h2>
        <p class="subheading font-weight-regular">
          Maximal mögliche Zeiten auf Nachbardistanzen
        </p>
      </v-col>
      <v-col sm="4" offset-sm="2" class="white--text">
        <v-text-field v-model="test1500m" label="1.500 m" dark></v-text-field>
        <v-text-field v-model="test3000m" label="3.000 m" dark></v-text-field>
        <v-text-field v-model="test5k" label="5.000 m" dark></v-text-field>
        <v-text-field v-model="test10k" label="10.000 m" dark></v-text-field>
        <v-text-field v-model="test10k" label="10.000 m" dark></v-text-field>
        <v-text-field v-model="test21k" label="Halbmarathon" dark></v-text-field>
      </v-col>      
      <v-col sm="4">
        <v-text-field :value="formatieren(berechnen(test1500m)*2+20)" label="3.000 m" disabled dark></v-text-field>
        <v-text-field :value="formatieren((berechnen(test3000m)+20)*1.666)" label="5.000 m" disabled dark></v-text-field>
        <v-text-field :value="formatieren(berechnen(test5k)*2+60)" label="10.000 m" disabled dark></v-text-field>
        <v-text-field :value="formatieren(berechnen(test10k)*2.21)" label="Halbmarathon" disabled dark></v-text-field>
        <v-text-field :value="formatieren(berechnen(test10k)*4.666)" label="Marathon" disabled dark></v-text-field>
        <v-text-field :value="formatieren(berechnen(test21k)*2.11)" label="Marathon" disabled dark></v-text-field>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'Wettkampfzeiten',

    data(){
      return {
        test1500m: '',
        test3000m: '',
        test5k: '',
        test10k: '',
        test21k: '',
      };
    },
    methods: {     
      berechnen(value){
        const regex = /^(?:(?:([01]?\d|2[0-3]):)?([0-5]?\d):)([0-5]?\d)$/g;
        if (value.match(regex) !== null){
          let arr = value.split(':');
          if (arr.length<3){
            arr.unshift(0);
          }
          return arr[0]*60*60 + arr[1]*60 + arr[2]*1;
        }
      },
      formatieren(sec){
        if (sec){
        const hours = Math.floor(sec/3600);
        const minutes = Math.floor((sec%3600) / 60);
        const seconds = Math.floor((sec%60));
        return `${hours}:${minutes>9 ? minutes : '0'+minutes}:${seconds>9 ? seconds : '0'+seconds}`;
        }
      },      
    }
  }
</script>

<style>
  .blur{
    background-color: rgb(200, 0, 0, 0.7);
    backdrop-filter: blur(8px);
  }
</style>