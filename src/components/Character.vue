<template>
    <v-card elevation="12">
        <v-card-title primary-title>
            <span class="headline mb-0" v-text="character.name" />
        </v-card-title>
        <v-card-text>
            <v-row>
                <v-col class="mx-auto" cols="4">
                    <Item :item="character.helmet" />
                </v-col>
            </v-row>
            <v-row>
                <v-col cols="4">
                    <v-card height="100">
                        <Item :item="character.primaryWeapon" />
                    </v-card>
                </v-col>
                <v-col cols="4">
                    <v-card height="100">
                        <Item :item="character.armor" />
                    </v-card>
                </v-col>
                <v-col cols="4">
                    <v-card height="100">
                        <Item :item="character.secondaryWeapon" />
                    </v-card>
                </v-col>
            </v-row>
            <v-row>
                <v-col cols="4" offset="4">
                    <v-card height="100">
                        <Item :item="character.pants" />
                    </v-card>
                </v-col>
                <v-col cols="4" >
                    <v-card height="100">
                        <Item :item="character.gloves" />
                    </v-card>
                </v-col>
            </v-row>
            <v-row>
                <v-col class="mx-auto" cols="4" >
                    <v-card height="100">
                        <Item :item="character.shoes" />
                    </v-card>
                </v-col>
            </v-row>
        </v-card-text>
    </v-card>
</template>

<script>
import Item from './Item';

export default {
    name: 'Character',
    components: { Item },
    props: {
        character: Object
    }
}
</script>
