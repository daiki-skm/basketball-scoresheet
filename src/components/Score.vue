<template>
    <div class="score">
        <v-list-item>
            <v-list-item-content>
                <v-list-item-title class="font">{{teamNameA}} vs {{teamNameB}}</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <v-list-item class="pl-12">
            <v-list-item-content>
                <v-list-item-title class="font">Q1 {{q1ptsA}} - {{q1ptsB}}</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <v-list-item class="pl-12">
            <v-list-item-content>
                <v-list-item-title class="font">Q2 {{q2ptsA}} - {{q2ptsB}}</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <v-list-item class="pl-12">
            <v-list-item-content>
                <v-list-item-title class="font">Q3 {{q3ptsA}} - {{q3ptsB}}</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <v-list-item class="pl-12">
            <v-list-item-content>
                <v-list-item-title class="font">Q4 {{q4ptsA}} - {{q4ptsB}}</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <v-list-item class="pl-9">
            <v-list-item-content>
                <v-list-item-title class="font">total {{totalA}} - {{totalB}}</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
    </div>
</template>

<script>
export default {
    name: 'Top',
    props: ['teamNameA','teamNameB','q1ptsA','q2ptsA','q3ptsA','q4ptsA','totalA','q1ptsB','q2ptsB','q3ptsB','q4ptsB','totalB']
}
</script>

<style scoped>
.font {
    font-size: x-large;
}
</style>