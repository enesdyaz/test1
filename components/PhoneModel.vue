<template>

  <v-card
    class="mx-auto"
    max-width="400"
    shaped
  >
    <v-card-title>
      <h2 class="title"> Device Details</h2>
    </v-card-title>

    <v-divider class="mx-4"></v-divider>

    <v-card-text>
      <span class="subheading">Select your phone</span>


<!-- SELECT 1 -->
      <v-chip-group v-model="select1" active-class="teal white--text"  >
        <v-chip v-for="size in ManufacturerData" :key="size"  :value="size">  {{ size }} </v-chip>
      </v-chip-group>

<!-- SELECT_2 -->
      <div v-if="select1">
         <v-chip-group v-model="select2" active-class="teal white--text" >
            <v-chip v-for="size in ModelData" :key="size" :value="size">  {{ size }} </v-chip>
        </v-chip-group>
      </div>

<!-- SELECT 3 -->
     <div v-if="select2">
         <v-chip-group v-model="select3" multiple active-class="teal white--text" >
            <v-chip v-for="size in ProblemData" :key="size" :value="size"> {{ size }} </v-chip>
        </v-chip-group>
      </div>

    </v-card-text>
<v-divider></v-divider>  
  {{select3}}: {{ValueData}}: {{numberList}}
    <v-card-actions>
      <span class="title"><small>PRICE: $</small>{{ValueData}}</span>
      <v-spacer></v-spacer><v-btn class='blue'> AGREE </v-btn>
    </v-card-actions>
  </v-card>
</template>



<script>
  export default {
    data: () => ({
      select1: '',
      select2: '',
      select3: '',
            Manufacturer: {
                apple: {
                    iphone6: {
                        battery: 59,
                        screen: 69,
                    },
                    iphone7: {
                        battery: 39,
                        dock: 48,
                    }
                },
                samsung: {
                    galaxys8: {
                        battery: 49,
                        screen: 120,
                    },
                    galaxys10: {
                        battery: 133,
                        screen: 422,
                    
                    }
                },
                HTC: {
                  htc10: {
                    battery: 380,
                    dockconnector: 280,
                    screen: 450
                  },
                  htc11: {
                    screen: 310,
                    battery: 210,
                    dock: 110,
                    power: 240,
                    sound: 110,
                    home: 230,
                    wifi: 110,
                    gps: 100
                  }
                }
            }



    }),
    computed: {
        ManufacturerData(){
            return Object.keys(this.Manufacturer)
        },
        ModelData(){
          console.log(this.select1)
            if(this.select1===''){
                return null
            }else{
                return Object.keys(this.Manufacturer[this.select1])
            }
        },
        ProblemData(){
            if(this.select2===''){
                return null
            }else{
                 return Object.keys(this.Manufacturer[this.select1][this.select2])
            }
        },
        ValueData(){
            if(this.select3===''){
                return null
            }else{

                let numberList = []
                // for(var i=0;i<this.select3.length;i++){
                //  numberList.push(Number(Object.values(this.Manufacturer[this.select1][this.select2][this.select3[i]])))
                // }

                for(var i=0; i<this.select3.length;i++){
                numberList += Object.values(this.Manufacturer[this.select1][this.select2][this.select3[i]])
                
                }

                console.log(typeof(numberList))
                console.log(numberList)
                return numberList
              }
        },
        
    },
    methods:{
      add(a, e){
        var total = a + e
        return total
      }
    }
  }
</script>