<template>
    <v-container fluid>
        <v-row>
            <v-col cols="12" md="6" v-for="character in characters" :key="character.id">
                <Character :character="character"/>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import axios from 'axios'
import Character from '@/components/Character'

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
