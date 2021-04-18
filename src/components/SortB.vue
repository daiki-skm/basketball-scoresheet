<template>
    <div class="scoresheet-sortB">
        <h1 class="pa-5">{{teamNameB}}</h1>
        <h2 class="pl-7">Quarter {{quarterNowB}}</h2>
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
                    <v-list-item v-on:click="$emit('quarterChangedB',1)">
                        <v-list-item-title>Quarter1</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('quarterChangedB',2)">
                        <v-list-item-title>Quarter2</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('quarterChangedB',3)">
                        <v-list-item-title>Quarter3</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('quarterChangedB',4)">
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
                    <v-list-item v-on:click="$emit('sortChangedB',1)">
                        <v-list-item-title>得点が高い順</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('sortChangedB',2)">
                        <v-list-item-title>FG確率が高い順</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('sortChangedB',3)">
                        <v-list-item-title>3FG確率が高い順</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('sortChangedB',4)">
                        <v-list-item-title>FT確率が高い順</v-list-item-title>
                    </v-list-item>
                    <v-list-item v-on:click="$emit('sortChangedB',5)">
                        <v-list-item-title>背番号順</v-list-item-title>
                    </v-list-item>
                </v-list>
            </v-menu>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SortB',
    props: ['teamNameB','quarterNowB']
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