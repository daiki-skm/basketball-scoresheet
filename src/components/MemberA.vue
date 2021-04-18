<template>
    <div class="scoresheet-memberA">
        <h2 class="pa-3">{{teamA.name}}</h2>
        <h2 class="out" v-if="teamA.foul >= 5">退場</h2>
        <div class="btn">
            <v-btn elevation="2" small v-on:click="$emit('memberRemoveA')">メンバーを削除</v-btn>
        </div>
        <v-list-item>
            <v-list-item-content>
                <v-list-item-title class="other">PTS: {{teamA.pts}}</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <li>
            <span>FGA: {{teamA.fga}}</span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusFgaA')"
            >
                <v-icon dark>
                    mdi-plus
                </v-icon>
            </v-btn>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="cyan lighten-3"
                v-on:click="$emit('minusFgaA')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>FGM: {{teamA.fgm}}</span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusFgmA')"
            >
                <v-icon dark>
                    mdi-plus
                </v-icon>
            </v-btn>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="cyan lighten-3"
                v-on:click="$emit('minusFgmA')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <v-list-item>
            <v-list-item-content>
                <v-list-item-title class="other">FG percent: {{teamA.fgPer}}%</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <li>
            <span>3FGA: {{teamA.threeFga}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusThreeFgaA')"
            >
                <v-icon dark>
                    mdi-plus
                </v-icon>
            </v-btn>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="cyan lighten-3"
                v-on:click="$emit('minusThreeFgaA')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>3FGM: {{teamA.threeFgm}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusThreeFgmA')"
            >
                <v-icon dark>
                    mdi-plus
                </v-icon>
            </v-btn>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="cyan lighten-3"
                v-on:click="$emit('minusThreeFgmA')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <v-list-item>
            <v-list-item-content>
                <v-list-item-title class="other">3FG percent: {{teamA.threeFgPer}}%</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <li>
            <span>FTA: {{teamA.fta}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusFtaA')"
            >
                <v-icon dark>
                    mdi-plus
                </v-icon>
            </v-btn>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="cyan lighten-3"
                v-on:click="$emit('minusFtaA')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>FTM: {{teamA.ftm}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusFtmA')"
            >
                <v-icon dark>
                    mdi-plus
                </v-icon>
            </v-btn>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="cyan lighten-3"
                v-on:click="$emit('minusFtmA')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <v-list-item>
            <v-list-item-content>
                <v-list-item-title class="other">FT percent: {{teamA.ftPer}}%</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <li>
            <span>ORB: {{teamA.orb}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusOrbA')"
            >
                <v-icon dark>
                    mdi-plus
                </v-icon>
            </v-btn>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="cyan lighten-3"
                v-on:click="$emit('minusOrbA')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>DRB: {{teamA.drb}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusDrbA')"
            >
                <v-icon dark>
                    mdi-plus
                </v-icon>
            </v-btn>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="cyan lighten-3"
                v-on:click="$emit('minusDrbA')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>STL: {{teamA.stl}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusStlA')"
            >
                <v-icon dark>
                    mdi-plus
                </v-icon>
            </v-btn>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="cyan lighten-3"
                v-on:click="$emit('minusStlA')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>AST: {{teamA.ast}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusAstA')"
            >
                <v-icon dark>
                    mdi-plus
                </v-icon>
            </v-btn>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="cyan lighten-3"
                v-on:click="$emit('minusAstA')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>BLK: {{teamA.blk}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusBlkA')"
            >
                <v-icon dark>
                    mdi-plus
                </v-icon>
            </v-btn>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="cyan lighten-3"
                v-on:click="$emit('minusBlkA')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>FOUL: {{teamA.foul}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusFoulA')"
            >
                <v-icon dark>
                    mdi-plus
                </v-icon>
            </v-btn>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="cyan lighten-3"
                v-on:click="$emit('minusFoulA')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
    </div>
</template>

<script>
export default {
    name: 'MemberA',
    props: ['teamA']
}
</script>

<style scoped>
li {
    list-style: none;
}
.scoresheet-memberA {
    padding-left: 20px;
    float: left;
}
span {
    padding-left: 15px;
    font-size: larger;
}
.out {
    padding-left: 10px;
    padding-bottom: 10px;
    color: crimson;
}
.btn {
    padding-left: 15px;
}
.other {
    font-size: larger;
}
</style>