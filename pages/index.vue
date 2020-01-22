<template>
  <div>
    <div>
      <v-row>
        <v-col class="ma-10"><phone-model></phone-model></v-col>
        <v-col></v-col>
      </v-row>
      
    </div>


  </div>

</template>

<script>
import PhoneModel from '../components/PhoneModel.vue'

export default{
  components: {
    PhoneModel,
  }
}

</script>