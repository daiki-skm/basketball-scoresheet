<template>
    <div class="scoresheet-sortA">
        <h1 class="pa-5">{{teamNameA}}</h1>
        <h2 class="pl-7">Quarter {{quarterNowA}}</h2>
        <div class="quarterChange">
            <v-menu transition="scale-transition" origin="center center">
                <template v-slot:activator="{ on, attrs }">
                    <v-btn
                        color="primary lighten-3"
                        v-bind="attrs"
                        v-on="on"
                    >
                    Quarter change
                    </v-btn>
                </template>
                <v-list>
                    <v-list-item v-on:click="$emit('quarterChangedA',1)">
                        <v-list-item-title>Quarter1</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('quarterChangedA',2)">
                        <v-list-item-title>Quarter2</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('quarterChangedA',3)">
                        <v-list-item-title>Quarter3</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('quarterChangedA',4)">
                        <v-list-item-title>Quarter4</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>
        </div>
        <div class="sortChange">
            <v-menu transition="scale-transition" origin="center center">
                <template v-slot:activator="{ on, attrs }">
                    <v-btn
                        color="primary lighten-3"
                        v-bind="attrs"
                        v-on="on"
                    >
                    Sort change
                    </v-btn>
                </template>
                <v-list>
                    <v-list-item v-on:click="$emit('sortChangedA',1)">
                        <v-list-item-title>得点が高い順</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('sortChangedA',2)">
                        <v-list-item-title>FG確率が高い順</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('sortChangedA',3)">
                        <v-list-item-title>3FG確率が高い順</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('sortChangedA',4)">
                        <v-list-item-title>FT確率が高い順</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('sortChangedA',5)">
                        <v-list-item-title>背番号順</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SortA',
    props: ['teamNameA','quarterNowA']
}
</script>

<style scoped>
.quarterChange {
    padding-top: 10px;
    padding-left: 30px;
}
.sortChange {
    padding-top: 10px;
    padding-left: 30px;
}
</style>