<template>
  <div>
    <div>
      <v-row>
        <v-col class="ma-10">
          <no-ssr />
          <phone-model></phone-model></v-col>
        <v-col><phone-list></phone-list></v-col>
      </v-row>
      
    </div>


  </div>

</template>

<script>
import PhoneModel from '../components/PhoneModel.vue'
import PhoneList from '../components/PhoneList.vue'

export default{
  components: {
    PhoneModel, PhoneList
  }
}

</script>