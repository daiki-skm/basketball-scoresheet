<template>
    <div class="scoresheet-memberB">
        <h2 class="pa-3">{{teamB.name}}</h2>
        <h2 class="out" v-if="teamB.foul >= 5">退場</h2>
        <div class="btn">
            <v-btn elevation="2" small v-on:click="$emit('memberRemoveB')">メンバーを削除</v-btn>
        </div>
        <v-list-item>
            <v-list-item-content>
                <v-list-item-title class="other">PTS: {{teamB.pts}}</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <li>
            <span>FGA: {{teamB.fga}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusFgaB')"
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
                v-on:click="$emit('minusFgaB')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>FGM: {{teamB.fgm}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusFgmB')"
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
                v-on:click="$emit('minusFgmB')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <v-list-item>
            <v-list-item-content>
                <v-list-item-title class="other">FG percent: {{teamB.fgPer}}%</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <li>
            <span>3FGA: {{teamB.threeFga}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusThreeFgaB')"
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
                v-on:click="$emit('minusThreeFgaB')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>3FGM: {{teamB.threeFgm}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusThreeFgmB')"
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
                v-on:click="$emit('minusThreeFgmB')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <v-list-item>
            <v-list-item-content>
                <v-list-item-title class="other">3FG percent: {{teamB.threeFgPer}}%</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <li>
            <span>FTA: {{teamB.fta}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusFtaB')"
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
                v-on:click="$emit('minusFtaB')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>FTM: {{teamB.ftm}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusFtmB')"
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
                v-on:click="$emit('minusFtmB')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <v-list-item>
            <v-list-item-content>
                <v-list-item-title class="other">FT percent: {{teamB.ftPer}}%</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <li>
            <span>ORB: {{teamB.orb}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusOrbB')"
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
                v-on:click="$emit('minusOrbB')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>DRB: {{teamB.drb}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusDrbB')"
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
                v-on:click="$emit('minusDrbB')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>STL: {{teamB.stl}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusStlB')"
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
                v-on:click="$emit('minusStlB')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>AST: {{teamB.ast}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusAstB')"
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
                v-on:click="$emit('minusAstB')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>BLK: {{teamB.blk}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusBlkB')"
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
                v-on:click="$emit('minusBlkB')"
            >
                <v-icon dark>
                    mdi-minus
                </v-icon>
            </v-btn>
        </li>
        <li>
            <span>FOUL: {{teamB.foul}} </span>
            <v-btn
                class="mx-2"
                fab
                dark
                small
                color="red lighten-3"
                v-on:click="$emit('plusFoulB')"
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
                v-on:click="$emit('minusFoulB')"
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
    name: 'MemberB',
    props: ['teamB']
}
</script>

<style scoped>
li {
    list-style: none;
}
.scoresheet-memberB {
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