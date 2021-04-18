<template>
    <div class="pa-5">
        <v-text-field
            label="Please write the name of Team A"
            v-model="teamNameA"
            hide-details="auto"
        ></v-text-field>
        <div class="py-2">
            <v-btn elevation="2" small v-on:click="clickHandlerA">確定</v-btn>
        </div>
        <v-text-field
            label="Please write the name of Team B"
            v-model="teamNameB"
            hide-details="auto"
        ></v-text-field>
        <div class="py-2">
            <v-btn elevation="2" small v-on:click="clickHandlerB">確定</v-btn>
        </div>
        <v-text-field
            label="Please write the uniform number of the player of Team A"
            v-model="nameA"
            hide-details="auto"
        ></v-text-field>
        <div class="py-2">
            <v-btn elevation="2" small v-on:click="clickHandlerAddA">メンバーを追加</v-btn>
        </div>
        <v-text-field
            label="Please write the uniform number of the player of Team B"
            v-model="nameB"
            hide-details="auto"
        ></v-text-field>
        <div class="py-2">
            <v-btn elevation="2" small v-on:click="clickHandlerAddB">メンバーを追加</v-btn>
        </div>
    </div>
</template>

<script>
export default {
    name: 'InputArea',
    data: function(){
        return {
            teamNameA: '',
            teamNameB: '',
            nameA: '',
            nameB: '',
        }
    },
    methods: {
        clickHandlerA: function(){
            var name = ''
            name = this.teamNameA
            this.$emit('teamNameDecisionA',name)
        },
        clickHandlerB: function(){
            var name = ''
            name = this.teamNameB
            this.$emit('teamNameDecisionB',name)
        },
        clickHandlerAddA: function(){
            var name = ''
            name = this.nameA
            this.$emit('memberAddA',name)
        },
        clickHandlerAddB: function(){
            var name = ''
            name = this.nameB
            this.$emit('memberAddB',name)
        }
    }
}
</script>