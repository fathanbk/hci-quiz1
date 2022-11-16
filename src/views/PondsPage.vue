<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-grid>
          <ion-row>
            <ion-col>
              <ion-title>Kolam</ion-title>
            </ion-col>
            <ion-col size="1">
              <ion-icon src="img/Sorting.svg"></ion-icon>
            </ion-col>
            <ion-col size="1">
              <ion-icon src="img/Vector.svg"></ion-icon>
            </ion-col>
          </ion-row>
        </ion-grid>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">

      <ion-list >
        <ion-card color="dark" v-for="(pond,index) in kolam" v-bind:key="index">
          <ion-item lines="none"  color="dark">
            <ion-label><strong>{{pond.alias}}</strong></ion-label>
            <ion-button slot="end" size="medium" color="success">
              <span style="color:white;text-transform: capitalize;"> <strong>{{pond.status}}</strong></span>
            </ion-button>
          </ion-item>
          <ion-card-content>
            <ion-grid>
              <ion-row class="ion-justify-content-start">
                <ion-col size="1">
                  <ion-icon src="img/calendar+.svg"></ion-icon>
                </ion-col>
                <ion-col >
                  <p>{{pond.build_at}}</p>
                </ion-col>
              </ion-row>
              <ion-row class="ion-justify-content-start">
                <ion-col size="1">
                  <ion-icon src="img/TimeSheet.svg"></ion-icon>
                </ion-col>
                <ion-col size="auto">
                  <p>90 Hari</p>
                </ion-col>
              </ion-row>
              <ion-row class="ion-justify-content-start">
                <ion-col size="1">
                  <ion-icon src="img/Whole Fish.svg"></ion-icon>
                </ion-col>
                <ion-col size="auto">
                  <p>{{pond.fish_alive}} <span> Ekor</span></p>
                </ion-col>
              </ion-row>

            </ion-grid>
          </ion-card-content>
        </ion-card>
      </ion-list>
      <ion-fab vertical="bottom" horizontal="end" slot="fixed">
        <ion-fab-button color="tertiary" href="/register">
          <ion-icon src="img/Button+.svg"></ion-icon>
        </ion-fab-button>
      </ion-fab>
    </ion-content>
  </ion-page>
</template>
  
<script lang="ts">
import { IonContent, IonHeader,IonFab, IonPage, IonTitle, IonToolbar, IonItem, IonLabel, IonButton, IonCard, IonGrid, IonRow, IonCol, IonIcon } from '@ionic/vue';
import { defineComponent } from 'vue';
import { onMounted,ref } from 'vue';
import axios from 'axios'

export default defineComponent({
  name: 'PondsPage',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    IonFab
  },
  setup(){
    const kolam = ref()
    onMounted(async () => {
      const response = await axios.get('http://jft.web.id/fishapi/api/ponds')
      kolam.value = response.data
      console.log(kolam.value)
      
    });
    return {kolam}
  },
  methods: {
  }
});
</script>
  
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap%27');

template {
  font-family: 'Poppins';
}

ion-list {
  background-color: #121212;
}
ion-label{
  font-size: 18px;
}
ion-header ion-icon{
  font-size: 21px;
}
ion-item{
  margin-left: 1.2rem;
  margin-right: 1.2rem;
  border-bottom: 4px black solid;
  margin-top: 20px;
}
ion-col p{
  font-size: 16px;
}
ion-button{
  font-size: 16px;
  margin-bottom: 11px;
  border-radius: 20px;
}

ion-card{
  border-radius: 20px;
  margin: 30px;
}
ion-icon {
  font-size: 24px;
}
ion-fab-button ion-icon{
  font-size: 30px;
  font-weight: 900;
}

</style>
  