<template>
    <ion-page>
      <ion-header :translucent="true">
        <ion-toolbar>
            <ion-buttons slot="start">
            <ion-back-button default-href="home"></ion-back-button>
            </ion-buttons>
            <ion-title>Registrasi Kolam</ion-title>
        
        </ion-toolbar>
      </ion-header>
      <ion-content :fullscreen="true">
        <ion-header collapse="condense">
            <ion-toolbar>
                <ion-title size="large">Registrasi Kolam</ion-title>
            </ion-toolbar>
        </ion-header>
        <ion-list>
          <ion-item>
              <ion-label position="stacked">Nama Kolam</ion-label>
              <ion-input placeholder="Kolam 1" nama="namaKolam" value="nama" v-model="namaKolam"></ion-input>
           </ion-item>
          <ion-item>
              <ion-label position="stacked">Lokasi Kolam</ion-label>
              <ion-input placeholder="Blok A" name="lokasiKolam" value="Lokasi" v-model="lokasiKolam"></ion-input>
            </ion-item>
            <ion-item>
            <ion-label position="stacked">Material Kolam</ion-label>
            <ion-select interface="action-sheet" v-model="materialKolam">
                <ion-select-option value="tanah">Tanah</ion-select-option>
                <ion-select-option value="beton">Beton</ion-select-option>
                <ion-select-option value="terpal">Terpal</ion-select-option>
            </ion-select>
        </ion-item>
        <ion-item>
            <ion-label position="stacked">Bentuk Kolam</ion-label>
            <ion-select interface="action-sheet" v-model="bentukKolam">
              <ion-select-option value="kotak" name="kotak">Kotak</ion-select-option>
              <ion-select-option value="bundar" name="bundar">Bundar</ion-select-option>
            </ion-select>
          </ion-item>
          
          <ion-button horizontal="center" color="tertiary" type="submit" @click.prevent="submittedForm()">Registrasi</ion-button>
        </ion-list>
       <ion-list>
        {{namaKolam}}
       </ion-list>
        
      </ion-content>
    </ion-page>
  </template>
  
  <script lang="ts">
  import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar,IonInput,IonSelect,IonSelectOption} from '@ionic/vue';
  import { defineComponent } from 'vue';
 

  
  export default defineComponent({
    name: 'HomePage',
    components: {
      IonContent,
      IonHeader,
      IonPage,
      IonTitle,
      IonToolbar,  
      IonInput,
      IonSelect,
      IonSelectOption
    },
    data() {
    return {
      namaKolam: '',
      lokasiKolam: '',
      materialKolam:'',
      bentukKolam:''
      
    }
  },
  methods:{
    submittedForm(){
      let kolam = {
        nama: this.namaKolam,
        lokasi: this.lokasiKolam,
        material: this.materialKolam,
        bentuk: this.bentukKolam

      };
      console.log(kolam);
      // console.log(this.namaKolam)
      // console.log(this.lokasiKolam)
      // console.log(this.materialKolam)
      // console.log(this.bentukKolam)
    },
  }
  });
  </script>
  
  <style scoped>

  </style>
  