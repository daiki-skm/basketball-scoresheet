<template>
    <v-app>
        <v-card>
            <v-toolbar color="cyan" dark flat>
                <v-toolbar-title>Scoresheet</v-toolbar-title>
                <template v-slot:extension>
                    <v-tabs v-model="tab" align-with-title>
                        <v-tabs-slider color="yellow"></v-tabs-slider>
                        <v-tab v-for="item in items" :key="item">
                            {{ item }}
                        </v-tab>
                    </v-tabs>
                </template>
            </v-toolbar>

            <v-tabs-items v-model="tab">
                <v-tab-item>
                    <v-card flat>
                        <v-card-text>
                            <InputArea
                            v-on:teamNameDecisionA="teamNameDecisionA"
                            v-on:teamNameDecisionB="teamNameDecisionB"
                            v-on:memberAddA="memberAddA"
                            v-on:memberAddB="memberAddB"
                            ></InputArea>
                        </v-card-text>
                    </v-card>
                </v-tab-item>

                <v-tab-item>
                    <v-card flat>
                        <v-card-text>
                            <Score
                            v-bind:teamNameA="teamNameA"
                            v-bind:teamNameB="teamNameB"
                            v-bind:q1ptsA="q1ptsA"
                            v-bind:q2ptsA="q2ptsA"
                            v-bind:q3ptsA="q3ptsA"
                            v-bind:q4ptsA="q4ptsA"
                            v-bind:totalA="totalA"
                            v-bind:q1ptsB="q1ptsB"
                            v-bind:q2ptsB="q2ptsB"
                            v-bind:q3ptsB="q3ptsB"
                            v-bind:q4ptsB="q4ptsB"
                            v-bind:totalB="totalB"
                            ></Score>
                        </v-card-text>
                    </v-card>
                </v-tab-item>

                <v-tab-item>
                    <v-card flat>
                        <v-card-text>
                            <SortA
                            v-bind:teamNameA="teamNameA"
                            v-bind:quarterNowA="quarterNowA"
                            v-on:quarterChangedA="quarterChangedA"
                            v-on:sortChangedA="sortChangedA"
                            ></SortA>

                            <div class="member">
                                <MemberA 
                                v-for="(teamA, index) in filteredTeamA"
                                v-bind:key="teamA.id"
                                v-bind:teamA="teamA"
                                v-on:memberRemoveA="memberRemoveA(index)"
                                v-on:plusFgaA="plusFgaA(teamA.id)"
                                v-on:plusFgmA="plusFgmA(teamA.id)"
                                v-on:plusThreeFgaA="plusThreeFgaA(teamA.id)"
                                v-on:plusThreeFgmA="plusThreeFgmA(teamA.id)"
                                v-on:plusFtaA="plusFtaA(teamA.id)"
                                v-on:plusFtmA="plusFtmA(teamA.id)"
                                v-on:plusOrbA="plusOrbA(teamA.id)"
                                v-on:plusDrbA="plusDrbA(teamA.id)"
                                v-on:plusStlA="plusStlA(teamA.id)"
                                v-on:plusAstA="plusAstA(teamA.id)"
                                v-on:plusBlkA="plusBlkA(teamA.id)"
                                v-on:plusFoulA="plusFoulA(teamA.id)"
                                v-on:minusFgaA="minusFgaA(teamA.id)"
                                v-on:minusFgmA="minusFgmA(teamA.id)"
                                v-on:minusThreeFgaA="minusThreeFgaA(teamA.id)"
                                v-on:minusThreeFgmA="minusThreeFgmA(teamA.id)"
                                v-on:minusFtaA="minusFtaA(teamA.id)"
                                v-on:minusFtmA="minusFtmA(teamA.id)"
                                v-on:minusOrbA="minusOrbA(teamA.id)"
                                v-on:minusDrbA="minusDrbA(teamA.id)"
                                v-on:minusStlA="minusStlA(teamA.id)"
                                v-on:minusAstA="minusAstA(teamA.id)"
                                v-on:minusBlkA="minusBlkA(teamA.id)"
                                v-on:minusFoulA="minusFoulA(teamA.id)"
                                ></MemberA>
                            </div>
                        </v-card-text>
                    </v-card>
                </v-tab-item>

                <v-tab-item>
                    <v-card flat>
                        <v-card-text>
                            <SortB
                            v-bind:teamNameB="teamNameB"
                            v-bind:quarterNowB="quarterNowB"
                            v-on:quarterChangedB="quarterChangedB"
                            v-on:sortChangedB="sortChangedB"
                            ></SortB>

                            <div class="member">
                                <MemberB 
                                v-for="(teamB, index) in filteredTeamB"
                                v-bind:key="teamB.id"
                                v-bind:teamB="teamB"
                                v-on:memberRemoveB="memberRemoveB(index)"
                                v-on:plusFgaB="plusFgaB(teamB.id)"
                                v-on:plusFgmB="plusFgmB(teamB.id)"
                                v-on:plusThreeFgaB="plusThreeFgaB(teamB.id)"
                                v-on:plusThreeFgmB="plusThreeFgmB(teamB.id)"
                                v-on:plusFtaB="plusFtaB(teamB.id)"
                                v-on:plusFtmB="plusFtmB(teamB.id)"
                                v-on:plusOrbB="plusOrbB(teamB.id)"
                                v-on:plusDrbB="plusDrbB(teamB.id)"
                                v-on:plusStlB="plusStlB(teamB.id)"
                                v-on:plusAstB="plusAstB(teamB.id)"
                                v-on:plusBlkB="plusBlkB(teamB.id)"
                                v-on:plusFoulB="plusFoulB(teamB.id)"
                                v-on:minusFgaB="minusFgaB(teamB.id)"
                                v-on:minusFgmB="minusFgmB(teamB.id)"
                                v-on:minusThreeFgaB="minusThreeFgaB(teamB.id)"
                                v-on:minusThreeFgmB="minusThreeFgmB(teamB.id)"
                                v-on:minusFtaB="minusFtaB(teamB.id)"
                                v-on:minusFtmB="minusFtmB(teamB.id)"
                                v-on:minusOrbB="minusOrbB(teamB.id)"
                                v-on:minusDrbB="minusDrbB(teamB.id)"
                                v-on:minusStlB="minusStlB(teamB.id)"
                                v-on:minusAstB="minusAstB(teamB.id)"
                                v-on:minusBlkB="minusBlkB(teamB.id)"
                                v-on:minusFoulB="minusFoulB(teamB.id)"
                                ></MemberB>
                            </div>
                        </v-card-text>
                    </v-card>
                </v-tab-item>
                
                <v-tab-item>
                    <v-card flat>
                        <v-card-text>
                            <div class="graph">
                                <h1 class="pa-8">グラフ</h1>
                                <div class="pl-10">
                                    <v-btn elevation="2" small v-on:click="fillData()">確定</v-btn>
                                </div>
                                <Chart v-bind:chartData="datacollection"></Chart>
                            </div>
                        </v-card-text>
                    </v-card>
                </v-tab-item>
            </v-tabs-items>
        </v-card>
    </v-app>
</template>

<script>
import InputArea from './Input.vue';
import Score from './Score.vue';
import SortA from './SortA.vue';
import MemberA from './MemberA.vue';
import SortB from './SortB.vue';
import MemberB from './MemberB.vue';
import Chart from './Chart.vue';

export default {
    name: 'Scoresheet',
    props: [],
    components: {
        InputArea,
        Score,
        SortA,
        MemberA,
        SortB,
        MemberB,
        Chart
    },
    data: function(){
        return {
            tab: null,
            items: [
            'input', 'score', 'statistics of player of Team A', 'statistics of player of Team B', 'graph',
            ],
            text: 'a',
            teamNameA: 'Team A',
            teamNameB: 'Team B',
            q1ptsA: 0,
            q2ptsA: 0,
            q3ptsA: 0,
            q4ptsA: 0,
            totalA: 0,
            q1ptsB: 0,
            q2ptsB: 0,
            q3ptsB: 0,
            q4ptsB: 0,
            totalB: 0,
            quarterNowA: 1,
            quarterNowB: 1,
            sortOrderA: 0,
            sortOrderB: 0,
            teamA: [],
            teamB: [],
            datacollection: null,
        }
    },
    computed: {
        totalQ1ptsA: function(){
            var pts = 0
            for(var i=0; i<this.teamA.length; i++){
                pts += this.teamA[i].q1pts;
            }
            return pts
        },
        totalQ2ptsA: function(){
            var pts = 0
            for(var i=0; i<this.teamA.length; i++){
                pts += this.teamA[i].q2pts;
            }
            return pts
        },
        totalQ3ptsA: function(){
            var pts = 0
            for(var i=0; i<this.teamA.length; i++){
                pts += this.teamA[i].q3pts;
            }
            return pts
        },
        totalQ4ptsA: function(){
            var pts = 0
            for(var i=0; i<this.teamA.length; i++){
                pts += this.teamA[i].q4pts;
            }
            return pts
        },
        totalPtsA: function(){
            var pts = 0
            pts = this.q1ptsA + this.q2ptsA + this.q3ptsA + this.q4ptsA
            return pts
        },
        totalQ1ptsB: function(){
            var pts = 0
            for(var i=0; i<this.teamB.length; i++){
                pts += this.teamB[i].q1pts;
            }
            return pts
        },
        totalQ2ptsB: function(){
            var pts = 0
            for(var i=0; i<this.teamB.length; i++){
                pts += this.teamB[i].q2pts;
            }
            return pts
        },
        totalQ3ptsB: function(){
            var pts = 0
            for(var i=0; i<this.teamB.length; i++){
                pts += this.teamB[i].q3pts;
            }
            return pts
        },
        totalQ4ptsB: function(){
            var pts = 0
            for(var i=0; i<this.teamB.length; i++){
                pts += this.teamB[i].q4pts;
            }
            return pts
        },
        totalPtsB: function(){
            var pts = 0;
            pts = this.q1ptsB + this.q2ptsB + this.q3ptsB + this.q4ptsB
            return pts
        },
        filteredTeamA: function(){
            var newTeam = [];
            for(var i=0; i<this.teamA.length; i++){
                newTeam.push(this.teamA[i]);
            }
            if(this.sortOrderA == 1){
                newTeam.sort(function(a,b){
                    return b.pts - a.pts;
                });
            }
            else if(this.sortOrderA == 2){
                newTeam.sort(function(a,b){
                    return b.fgPer - a.fgPer;
                });
            }
            else if(this.sortOrderA == 3){
                newTeam.sort(function(a,b){
                    return b.threeFgPer - a.threeFgPer;
                });
            }
            else if(this.sortOrderA == 4){
                newTeam.sort(function(a,b){
                    return b.ftPer - a.ftPer;
                });
            }
            else if(this.sortOrderA == 5){
                newTeam.sort(function(a,b){
                    return a.name - b.name;
                });
            }
            return newTeam
        },
        filteredTeamB: function(){
            var newTeam = [];
            for(var i=0; i<this.teamB.length; i++){
                newTeam.push(this.teamB[i]);
            }
            if(this.sortOrderB == 1){
                newTeam.sort(function(a,b){
                    return b.pts - a.pts;
                });
            }
            else if(this.sortOrderB == 2){
                newTeam.sort(function(a,b){
                    return b.fgPer - a.fgPer;
                });
            }
            else if(this.sortOrderB == 3){
                newTeam.sort(function(a,b){
                    return b.threeFgPer - a.threeFgPer;
                });
            }
            else if(this.sortOrderB == 4){
                newTeam.sort(function(a,b){
                    return b.ftPer - a.ftPer;
                });
            }
            else if(this.sortOrderB == 5){
                newTeam.sort(function(a,b){
                    return a.name - b.name;
                });
            }
            return newTeam
        },
        fgA: function(){
            var fg = [];
            for(var i=0; i<this.teamA.length; i++){
                if(this.teamA[i].fgm != 0) fg[i] = Math.round(this.teamA[i].fga/this.teamA[i].fgm*100);
                else fg[i] = 0;
            }
            return fg;
        },
        threeFgA: function(){
            var fg = [];
            for(var i=0; i<this.teamA.length; i++){
                if(this.teamA[i].threeFgm != 0) fg[i] = Math.round(this.teamA[i].threeFga/this.teamA[i].threeFgm*100);
                else fg[i] = 0;
            }
            return fg;
        },
        ftA: function(){
            var ft = [];
            for(var i=0; i<this.teamA.length; i++){
                if(this.teamA[i].ftm != 0) ft[i] = Math.round(this.teamA[i].fta/this.teamA[i].ftm*100);
                else ft[i] = 0;
            }
            return ft;
        },
        fgB: function(){
            var fg = [];
            for(var i=0; i<this.teamB.length; i++){
                if(this.teamB[i].fgm != 0) fg[i] = Math.round(this.teamB[i].fga/this.teamB[i].fgm*100);
                else fg[i] = 0;
            }
            return fg;
        },
        threeFgB: function(){
            var fg = [];
            for(var i=0; i<this.teamB.length; i++){
                if(this.teamB[i].threeFgm != 0) fg[i] = Math.round(this.teamB[i].threeFga/this.teamB[i].threeFgm*100);
                else fg[i] = 0;
            }
            return fg;
        },
        ftB: function(){
            var ft = [];
            for(var i=0; i<this.teamB.length; i++){
                if(this.teamB[i].ftm != 0) ft[i] = Math.round(this.teamB[i].fta/this.teamB[i].ftm*100);
                else ft[i] = 0;
            }
            return ft;
        },
    },
    created(){
        this.fillData()
    },
    methods: {
        teamNameDecisionA: function(name){
            this.teamNameA = name
        },
        teamNameDecisionB: function(name){
            this.teamNameB = name
        },
        memberAddA: function(nameA){
            var max = this.teamA.reduce(function(a,b){
                return a > b.id ? a : b.id
            },0)
            this.teamA.push({
                id: max+1,
                name: nameA,
                pts: 0,
                q1pts: 0,
                q2pts: 0,
                q3pts: 0,
                q4pts: 0,
                fga: 0,
                fgm: 0,
                threeFga: 0,
                threeFgm: 0,
                fta: 0,
                ftm: 0,
                fgPer: 0,
                threeFgPer: 0,
                ftPer: 0,
                orb: 0,
                drb: 0,
                stl: 0,
                ast: 0,
                blk: 0,
                foul: 0
            })
        },
        memberAddB: function(nameB){
            var max = this.teamB.reduce(function(a,b){
                return a > b.id ? a : b.id
            },0)
            this.teamB.push({
                id: max+1,
                name: nameB,
                pts: 0,
                q1pts: 0,
                q2pts: 0,
                q3pts: 0,
                q4pts: 0,
                fga: 0,
                fgm: 0,
                threeFga: 0,
                threeFgm: 0,
                fta: 0,
                ftm: 0,
                fgPer: 0,
                threeFgPer: 0,
                ftPer: 0,
                orb: 0,
                drb: 0,
                stl: 0,
                ast: 0,
                blk: 0,
                foul: 0
            })
        },
        quarterChangedA: function(num){
            this.quarterNowA = num
        },
        quarterChangedB: function(num){
            this.quarterNowB = num
        },
        sortChangedA: function(num){
            this.sortOrderA = num
        },
        sortChangedB: function(num){
            this.sortOrderB = num
        },
        memberRemoveA: function(index){
            this.teamA.splice(index,1);
        },
        plusFgaA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                this.teamA[index].fga++
                this.teamA[index].fgm++
                this.teamA[index].pts += 2
                if(this.quarterNowA == 1){
                    this.teamA[index].q1pts += 2
                }
                else if(this.quarterNowA == 2){
                    this.teamA[index].q2pts += 2
                }
                else if(this.quarterNowA == 3){
                    this.teamA[index].q3pts += 2
                }
                else if(this.quarterNowA == 4){
                    this.teamA[index].q4pts += 2
                }
            }
        },
        plusFgmA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                this.teamA[index].fgm++
            }
        },
        plusThreeFgaA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                this.teamA[index].threeFga++
                this.teamA[index].threeFgm++
                this.teamA[index].pts += 3
                if(this.quarterNowA == 1){
                    this.teamA[index].q1pts += 3
                }
                else if(this.quarterNowA == 2){
                    this.teamA[index].q2pts += 3
                }
                else if(this.quarterNowA == 3){
                    this.teamA[index].q3pts += 3
                }
                else if(this.quarterNowA == 4){
                    this.teamA[index].q4pts += 3
                }
            }
        },
        plusThreeFgmA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                this.teamA[index].threeFgm++
            }
        },
        plusFtaA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                this.teamA[index].fta++
                this.teamA[index].ftm++
                this.teamA[index].pts += 1
                if(this.quarterNowA == 1){
                    this.teamA[index].q1pts += 1
                }
                else if(this.quarterNowA == 2){
                    this.teamA[index].q2pts += 1
                }
                else if(this.quarterNowA == 3){
                    this.teamA[index].q3pts += 1
                }
                else if(this.quarterNowA == 4){
                    this.teamA[index].q4pts += 1
                }
            }
        },
        plusFtmA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                this.teamA[index].ftm++
            }
        },
        plusOrbA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                this.teamA[index].orb++
            }
        },
        plusDrbA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                this.teamA[index].drb++
            }
        },
        plusStlA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                this.teamA[index].stl++
            }
        },
        plusAstA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                this.teamA[index].ast++
            }
        },
        plusBlkA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                this.teamA[index].blk++
            }
        },
        plusFoulA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                this.teamA[index].foul++
            }
        },
        minusFgaA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                if(this.teamA[index].fga > 0){
                    if(this.quarterNowA == 1 && this.q1ptsA > 0){
                        if(this.teamA[index].q1pts > 0){
                            this.teamA[index].pts -= 2
                            this.teamA[index].fga--
                            this.teamA[index].fgm--
                            this.teamA[index].q1pts -= 2
                        }
                    }
                    else if(this.quarterNowA == 2 && this.q2ptsA > 0){
                        if(this.teamA[index].q2pts > 0){
                            this.teamA[index].pts -= 2
                            this.teamA[index].fga--
                            this.teamA[index].fgm--
                            this.teamA[index].q2pts -= 2
                        }
                    }
                    else if(this.quarterNowA == 3 && this.q3ptsA > 0){
                        if(this.teamA[index].q3pts > 0){
                            this.teamA[index].pts -= 2
                            this.teamA[index].fga--
                            this.teamA[index].fgm--
                            this.teamA[index].q3pts -= 2
                        }
                    }
                    else if(this.quarterNowA == 4 && this.q4ptsA > 0){
                        if(this.teamA[index].q4pts > 0){
                            this.teamA[index].pts -= 2
                            this.teamA[index].fga--
                            this.teamA[index].fgm--
                            this.teamA[index].q4pts -= 2
                        }
                    }
                }
            }
        },
        minusFgmA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                if(this.teamA[index].fgm > 0 && this.teamA[index].fgm > this.teamA[index].fga){
                    this.teamA[index].fgm--
                }
            }
        },
        minusThreeFgaA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                if(this.teamA[index].threeFga > 0){
                    if(this.quarterNowA == 1 && this.q1ptsA > 0){
                        if(this.teamA[index].q1pts > 0){
                            this.teamA[index].pts -= 3
                            this.teamA[index].threeFga--
                            this.teamA[index].threeFgm--
                            this.teamA[index].q1pts -= 3
                        }
                    }
                    else if(this.quarterNowA == 2 && this.q2ptsA > 0){
                        if(this.teamA[index].q2pts > 0){
                            this.teamA[index].pts -= 3
                            this.teamA[index].threeFga--
                            this.teamA[index].threeFgm--
                            this.teamA[index].q2pts -= 3
                        }
                    }
                    else if(this.quarterNowA == 3 && this.q3ptsA > 0){
                        if(this.teamA[index].q3pts > 0){
                            this.teamA[index].pts -= 3
                            this.teamA[index].threeFga--
                            this.teamA[index].threeFgm--
                            this.teamA[index].q3pts -= 3
                        }
                    }
                    else if(this.quarterNowA == 4 && this.q4ptsA > 0){
                        if(this.teamA[index].q4pts > 0){
                            this.teamA[index].pts -= 3
                            this.teamA[index].threeFga--
                            this.teamA[index].threeFgm--
                            this.teamA[index].q4pts -= 3
                        }
                    }
                }
            }
        },
        minusThreeFgmA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                if(this.teamA[index].threeFgm > 0 && this.teamA[index].threeFgm > this.teamA[index].threeFga){
                    this.teamA[index].threeFgm--
                }
            }
        },
        minusFtaA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                if(this.teamA[index].fta > 0){
                    if(this.quarterNowA == 1 && this.q1ptsA > 0){
                        if(this.teamA[index].q1pts > 0){
                            this.teamA[index].pts -= 1
                            this.teamA[index].fta--
                            this.teamA[index].ftm--
                            this.teamA[index].q1pts -= 1
                        }
                    }
                    else if(this.quarterNowA == 2 && this.q2ptsA > 0){
                        if(this.teamA[index].q2pts > 0){
                            this.teamA[index].pts -= 1
                            this.teamA[index].fta--
                            this.teamA[index].ftm--
                            this.teamA[index].q2pts -= 1
                        }
                    }
                    else if(this.quarterNowA == 3 && this.q3ptsA > 0){
                        if(this.teamA[index].q3pts > 0){
                            this.teamA[index].pts -= 1
                            this.teamA[index].fta--
                            this.teamA[index].ftm--
                            this.teamA[index].q3pts -= 1
                        }
                    }
                    else if(this.quarterNowA == 4 && this.q4ptsA > 0){
                        if(this.teamA[index].q4pts > 0){
                            this.teamA[index].pts -= 1
                            this.teamA[index].fta--
                            this.teamA[index].ftm--
                            this.teamA[index].q4pts -= 1
                        }
                    }
                }
            }
        },
        minusFtmA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                if(this.teamA[index].ftm > 0 && this.teamA[index].ftm > this.teamA[index].fta){
                    this.teamA[index].ftm--
                }
            }
        },
        minusOrbA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                if(this.teamA[index].orb > 0){
                    this.teamA[index].orb--
                }
            }
        },
        minusDrbA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                if(this.teamA[index].drb > 0){
                    this.teamA[index].drb--
                }
            }
        },
        minusStlA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                if(this.teamA[index].stl > 0){
                    this.teamA[index].stl--
                }
            }
        },
        minusAstA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                if(this.teamA[index].ast > 0){
                    this.teamA[index].ast--
                }
            }
        },
        minusBlkA: function(id){
            var index = id-1
            if(this.teamA[index].foul < 5){
                if(this.teamA[index].blk > 0){
                    this.teamA[index].blk--
                }
            }
        },
        minusFoulA: function(id){
            var index = id-1
            if(this.teamA[index].foul > 0){
                this.teamA[index].foul--
            }
        },
        memberRemoveB: function(index){
            this.teamB.splice(index,1)
        },
        plusFgaB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                this.teamB[index].fga++
                this.teamB[index].fgm++
                this.teamB[index].pts += 2
                if(this.quarterNowB == 1){
                    this.teamB[index].q1pts += 2
                }
                else if(this.quarterNowB == 2){
                    this.teamB[index].q2pts += 2
                }
                else if(this.quarterNowB == 3){
                    this.teamB[index].q3pts += 2
                }
                else if(this.quarterNowB == 4){
                    this.teamB[index].q4pts += 2
                }
            }
        },
        plusFgmB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                this.teamB[index].fgm++
            }
        },
        plusThreeFgaB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                this.teamB[index].threeFga++
                this.teamB[index].threeFgm++
                this.teamB[index].pts += 3
                if(this.quarterNowB == 1){
                    this.teamB[index].q1pts += 3
                }
                else if(this.quarterNowB == 2){
                    this.teamB[index].q2pts += 3
                }
                else if(this.quarterNowB == 3){
                    this.teamB[index].q3pts += 3
                }
                else if(this.quarterNowB == 4){
                    this.teamB[index].q4pts += 3
                }
            }
        },
        plusThreeFgmB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                this.teamB[index].threeFgm++
            }
        },
        plusFtaB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                this.teamB[index].fta++
                this.teamB[index].ftm++
                this.teamB[index].pts += 1
                if(this.quarterNowB == 1){
                    this.teamB[index].q1pts += 1
                }
                else if(this.quarterNowB == 2){
                    this.teamB[index].q2pts += 1
                }
                else if(this.quarterNowB == 3){
                    this.teamB[index].q3pts += 1
                }
                else if(this.quarterNowB == 4){
                    this.teamB[index].q4pts += 1
                }
            }
        },
        plusFtmB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                this.teamB[index].ftm++
            }
        },
        plusOrbB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                this.teamB[index].orb++
            }
        },
        plusDrbB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                this.teamB[index].drb++
            }
        },
        plusStlB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                this.teamB[index].stl++
            }
        },
        plusAstB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                this.teamB[index].ast++
            }
        },
        plusBlkB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                this.teamB[index].blk++
            }
        },
        plusFoulB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                this.teamB[index].foul++
            }
        },
        minusFgaB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                if(this.teamB[index].fga > 0){
                    if(this.quarterNowB == 1 && this.q1ptsB > 0){
                        if(this.teamB[index].q1pts > 0){
                            this.teamB[index].pts -= 2
                            this.teamB[index].fga--
                            this.teamB[index].fgm--
                            this.teamB[index].q1pts -= 2
                        }
                    }
                    else if(this.quarterNowB == 2 && this.q2ptsB > 0){
                        if(this.teamB[index].q2pts > 0){
                            this.teamB[index].pts -= 2
                            this.teamB[index].fga--
                            this.teamB[index].fgm--
                            this.teamB[index].q2pts -= 2
                        }
                    }
                    else if(this.quarterNowB == 3 && this.q3ptsB > 0){
                        if(this.teamB[index].q3pts > 0){
                            this.teamB[index].pts -= 2
                            this.teamB[index].fga--
                            this.teamB[index].fgm--
                            this.teamB[index].q3pts -= 2
                        }
                    }
                    else if(this.quarterNowB == 4 && this.q4ptsB > 0){
                        if(this.teamB[index].q4pts > 0){
                            this.teamB[index].pts -= 2
                            this.teamB[index].fga--
                            this.teamB[index].fgm--
                            this.teamB[index].q4pts -= 2
                        }
                    }
                }
            }
        },
        minusFgmB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                if(this.teamB[index].fgm > 0 && this.teamB[index].fgm > this.teamB[index].fga){
                    this.teamB[index].fgm--
                }
            }
        },
        minusThreeFgaB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                if(this.teamB[index].threeFga > 0){
                    if(this.quarterNowB == 1 && this.q1ptsB > 0){
                        if(this.teamB[index].q1pts > 0){
                            this.teamB[index].pts -= 3
                            this.teamB[index].threeFga--
                            this.teamB[index].threeFgm--
                            this.teamB[index].q1pts -= 3
                        }
                    }
                    else if(this.quarterNowB == 2 && this.q2ptsB > 0){
                        if(this.teamB[index].q2pts > 0){
                            this.teamB[index].pts -= 3
                            this.teamB[index].threeFga--
                            this.teamB[index].threeFgm--
                            this.teamB[index].q2pts -= 3
                        }
                    }
                    else if(this.quarterNowB == 3 && this.q3ptsB > 0){
                        if(this.teamB[index].q3pts > 0){
                            this.teamB[index].pts -= 3
                            this.teamB[index].threeFga--
                            this.teamB[index].threeFgm--
                            this.teamB[index].q3pts -= 3
                        }
                    }
                    else if(this.quarterNowB == 4 && this.q4ptsB > 0){
                        if(this.teamB[index].q4pts > 0){
                            this.teamB[index].pts -= 3
                            this.teamB[index].threeFga--
                            this.teamB[index].threeFgm--
                            this.teamB[index].q4pts -= 3
                        }
                    }
                }
            }
        },
        minusThreeFgmB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                if(this.teamB[index].threeFgm > 0 && this.teamB[index].threeFgm > this.teamB[index].threeFga){
                    this.teamB[index].threeFgm--
                }
            }
        },
        minusFtaB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                if(this.teamB[index].fta > 0){
                    if(this.quarterNowB == 1 && this.q1ptsB > 0){
                        if(this.teamB[index].q1pts > 0){
                            this.teamB[index].pts -= 1
                            this.teamB[index].fta--
                            this.teamB[index].ftm--
                            this.teamB[index].q1pts -= 1
                        }
                    }
                    else if(this.quarterNowB == 2 && this.q2ptsB > 0){
                        if(this.teamB[index].q2pts > 0){
                            this.teamB[index].pts -= 1
                            this.teamB[index].fta--
                            this.teamB[index].ftm--
                            this.teamB[index].q2pts -= 1
                        }
                    }
                    else if(this.quarterNowB == 3 && this.q3ptsB > 0){
                        if(this.teamB[index].q3pts > 0){
                            this.teamB[index].pts -= 1
                            this.teamB[index].fta--
                            this.teamB[index].ftm--
                            this.teamB[index].q3pts -= 1
                        }
                    }
                    else if(this.quarterNowB == 4 && this.q4ptsB > 0){
                        if(this.teamB[index].q4pts > 0){
                            this.teamB[index].pts -= 1
                            this.teamB[index].fta--
                            this.teamB[index].ftm--
                            this.teamB[index].q4pts -= 1
                        }
                    }
                }
            }
        },
        minusFtmB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                if(this.teamB[index].ftm > 0 && this.teamB[index].ftm > this.teamB[index].fta){
                    this.teamB[index].ftm--
                }
            }
        },
        minusOrbB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                if(this.teamB[index].orb > 0){
                    this.teamB[index].orb--
                }
            }
        },
        minusDrbB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                if(this.teamB[index].drb > 0){
                    this.teamB[index].drb--
                }
            }
        },
        minusStlB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                if(this.teamB[index].stl > 0){
                    this.teamB[index].stl--
                }
            }
        },
        minusAstB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                if(this.teamB[index].ast > 0){
                    this.teamB[index].ast--
                }
            }
        },
        minusBlkB: function(id){
            var index = id-1
            if(this.teamB[index].foul < 5){
                if(this.teamB[index].blk > 0){
                    this.teamB[index].blk--
                }
            }
        },
        minusFoulB: function(id){
            var index = id-1
            if(this.teamB[index].foul > 0){
                this.teamB[index].foul--
            }
        },
        getFgPerA: function(){
            var fgPer = 0;
            var num = 0;
            for(var i=0; i<this.teamA.length; i++){
                if(this.teamA[i].fgm !== 0){
                fgPer += this.teamA[i].fgPer;
                num++;
                }
            }
            return Math.round(fgPer/num)
        },
        getThreeFgPerA: function(){
            var fgPer = 0;
            var num = 0;
            for(var i=0; i<this.teamA.length; i++){
                if(this.teamA[i].threeFgm !== 0){
                fgPer += this.teamA[i].threeFgPer;
                num++;
                }
            }
            return Math.round(fgPer/num)
        },
        getFtPerA: function(){
            var ftPer = 0;
            var num = 0;
            for(var i=0; i<this.teamA.length; i++){
                if(this.teamA[i].ftm !== 0){
                    ftPer += this.teamA[i].ftPer;
                    num++;
                }
            }
            return Math.round(ftPer/num)
        },
        getFgPerB: function(){
            var fgPer = 0;
            var num = 0;
            for(var i=0; i<this.teamB.length; i++){
                if(this.teamB[i].fgm !== 0){
                    fgPer += this.teamB[i].fgPer;
                    num++;
                }
            }
            return Math.round(fgPer/num)
        },
        getThreeFgPerB: function(){
            var fgPer = 0;
            var num = 0;
            for(var i=0; i<this.teamB.length; i++){
                if(this.teamB[i].threeFgm !== 0){
                fgPer += this.teamB[i].threeFgPer;
                num++;
                }
            }
            return Math.round(fgPer/num)
        },
        getFtPerB: function(){
            var ftPer = 0;
            var num = 0;
            for(var i=0; i<this.teamB.length; i++){
                if(this.teamB[i].ftm !== 0){
                    ftPer += this.teamB[i].ftPer;
                    num++;
                }
            }
            return Math.round(ftPer/num)
        },
        fillData: function(){
            this.datacollection = {
                labels: [this.teamNameA+' FG %',this.teamNameB+' FG %',this.teamNameA+' 3FG %',this.teamNameB+' 3FG %',this.teamNameA+' FT %',this.teamNameB+' FT %'],
                datasets: [
                {
                    data: [this.getFgPerA(),this.getFgPerB(),this.getThreeFgPerA(),this.getThreeFgPerB(),this.getFtPerA(),this.getFtPerB()],
                    label: 'percent',
                    backgroundColor: [
                        'rgba(255, 99, 132, 0.2)',
                        'rgba(54, 162, 235, 0.2)',
                        'rgba(255, 99, 132, 0.2)',
                        'rgba(54, 162, 235, 0.2)',
                        'rgba(255, 99, 132, 0.2)',
                        'rgba(54, 162, 235, 0.2)'
                    ],
                    borderColor: [
                        'rgba(255, 99, 132, 1)',
                        'rgba(54, 162, 235, 1)',
                        'rgba(255, 99, 132, 1)',
                        'rgba(54, 162, 235, 1)',
                        'rgba(255, 99, 132, 1)',
                        'rgba(54, 162, 235, 1)'
                    ],
                    borderWidth: 1,
                }
                ]
            }
        },
    },
    watch: {
        totalQ1ptsA: function(newVal,oldVal){
            this.q1ptsA -= oldVal;
            this.q1ptsA += newVal;
        },
        totalQ2ptsA: function(newVal,oldVal){
            this.q2ptsA -= oldVal;
            this.q2ptsA += newVal;
        },
        totalQ3ptsA: function(newVal,oldVal){
            this.q3ptsA -= oldVal;
            this.q3ptsA += newVal;
        },
        totalQ4ptsA: function(newVal,oldVal){
            this.q4ptsA -= oldVal;
            this.q4ptsA += newVal;
        },
        totalPtsA: function(newVal,oldVal){
            this.totalA -= oldVal;
            this.totalA += newVal;
        },
        totalQ1ptsB: function(newVal,oldVal){
            this.q1ptsB -= oldVal;
            this.q1ptsB += newVal;
        },
        totalQ2ptsB: function(newVal,oldVal){
            this.q2ptsB -= oldVal;
            this.q2ptsB += newVal;
        },
        totalQ3ptsB: function(newVal,oldVal){
            this.q3ptsB -= oldVal;
            this.q3ptsB += newVal;
        },
        totalQ4ptsB: function(newVal,oldVal){
            this.q4ptsB -= oldVal;
            this.q4ptsB += newVal;
        },
        totalPtsB: function(newVal,oldVal){
            this.totalB -= oldVal;
            this.totalB += newVal;
        },
        fgA: function(val){
            for(var i=0; i<val.length; i++){
                this.teamA[i].fgPer = val[i];
            }
        },
        threeFgA: function(val){
            for(var i=0; i<val.length; i++){
                this.teamA[i].threeFgPer = val[i];
            }
        },
        ftA: function(val){
            for(var i=0; i<val.length; i++){
                this.teamA[i].ftPer = val[i];
            }
        },
        fgB: function(val){
            for(var i=0; i<val.length; i++){
                this.teamB[i].fgPer = val[i];
            }
        },
        threeFgB: function(val){
            for(var i=0; i<val.length; i++){
                this.teamB[i].threeFgPer = val[i];
            }
        },
        ftB: function(val){
            for(var i=0; i<val.length; i++){
                this.teamB[i].ftPer = val[i];
            }
        }
    }
}

</script>

<style scoped>
.graph {
    clear: left;
}
</style>