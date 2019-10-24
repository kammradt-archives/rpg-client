<template>
    <v-card height="100">
        <span v-text="itemName"/>   
    </v-card>
</template>

<script>
export default {
    name: 'Item',
    props: {
        item: Object
    },
    computed: {
        itemName() {
            return this.item ? this.item.name : 'X' 
        }
    }
}
</script>