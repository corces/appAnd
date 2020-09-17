<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Blank</ion-title>
        </ion-toolbar>
      </ion-header>
    
      <div id="container">
          <table border="1">
            <thead>
            <tr>
                <th>Nombre</th>
                <th>Rut</th>
                <th>Correo</th>
                <th>Con</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="item in todos" :key="item">
                <td>{{item.nombre}}</td>
                <td>{{item.rut}}</td>
                <td>{{item.correo}}</td>
                <td>{{item.confirmado}}</td>
            </tr>
            </tbody>
        </table>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar } from '@ionic/vue';
import { defineComponent } from 'vue';
import axios from 'axios';
export default defineComponent({
     mounted(){
		this.created();
    },
    
    name: 'Home',
    components: {
        IonContent,
        IonHeader,
        IonPage,
        IonTitle,
        IonToolbar
    },
   

    data() {
        return {
            todos: []
        }
    },
    methods: {
        created() {
            axios.get('http://localhost:8000/api/usuario').then(res => this.todos = res.data)
            console.log(this.todos);
        }
    },
  
    
});




</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>