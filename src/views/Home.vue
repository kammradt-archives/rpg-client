<template>
    <v-container fluid>
        <v-row>
            <v-col cols="12" xs="12" md="6" v-for="character in characters" :key="character.id">
                <v-card>
                    <Character :character="character"/>

                    <v-card-actions>
                        <v-spacer></v-spacer>
                        <v-btn text color="primary">text</v-btn>
                        <v-btn text color="primary">text</v-btn>
                    </v-card-actions>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import Character from '@/components/Character'
import axios from 'axios'

export default {
    name: 'Home',
    components: { Character },
    data: () => ({
        characters: []
    }),
    mounted() {
        this.getCharacters()
    },
    methods: {
        getCharacters() {
            axios.get('http://localhost:8080/character/index').then(response => {
                this.characters = response.data
            })
        }
    }
}
</script>
