<template>
    <div>
        <v-card-title primary-title>
            <span class="headline mb-0" v-text="character.name" />
        </v-card-title>
        <v-card-text>
            <v-row>
                <v-col class="mx-auto" sm="4" md="2">
                    <v-card height="100">
                        {{character.helmet ? character.helmet.name : 'No helmet'}}                                    
                    </v-card>
                </v-col>
            </v-row>
            <v-row>
                <v-col sm="4" md="2" offset-md="3">
                    <v-card height="100">
                        {{character.primaryWeapon ? character.primaryWeapon.name : 'No Primary weapon'}}                                    
                    </v-card>
                </v-col>
                <v-col sm="4" md="2" >
                    <v-card height="100">
                        {{character.armor ? character.armor.name : 'No armor'}}                                    
                    </v-card>
                </v-col>
                <v-col sm="4" md="2">
                    <v-card height="100">
                        {{character.secondaryWeapon ? character.secondaryWeapon.name : 'No Secondary weapon'}}                                    
                    </v-card>
                </v-col>
            </v-row>
            <v-row>
                <v-col sm="4" md="2" offset-md="3">
                    <v-card height="100">
                        {{character.pants ? character.pants.name : 'No pants'}}                                    
                    </v-card>
                </v-col>
                <v-col sm="4" md="2">
                    <v-card height="100">
                        {{character.gloves ? character.gloves.name : 'No gloves'}}                                    
                    </v-card>
                </v-col>
            </v-row>
            <v-row>
                <v-col class="mx-auto" sm="4" md="2">
                    <v-card height="100">
                        {{character.shoes ? character.shoes.name : 'No shoes'}}                                    
                    </v-card>
                </v-col>
            </v-row>
        </v-card-text>
    </div>
</template>

<script>
export default {
    name: 'Character',
    props: {
        character: Object
    }
}
</script>
