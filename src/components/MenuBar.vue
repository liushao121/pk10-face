<template lang="pug">
    //-菜单部分
    div.menu
        div.notice
            table
                tr
                    td
                        span(v-bind:style="{fontSize:26*zoomRate.x+'px'}")
                            marquee(v-html='notice.content')
        div.option(@touchend="triggerOption")
        options-dialog(v-bind:game-data="gameData",v-bind:zoom-rate="zoomRate")
</template>
<script>
    import OptionsDialog from './OptionsDialog.vue'
    export default {
        props: ['gameData', 'zoomRate', 'notice'],
        ready() {
            console.log(this.gameData.notice)
        },
        data() {
            return {
                name: 'liu',
                isShowOption: false
            }
        },
        methods: {
            triggerOption() {
                this.$broadcast('triggerOption')
            }
        },
        components: {
            'options-dialog': OptionsDialog
        }
    }
</script>
<style>
    .menu {
        position: relative;
        height: 5%;
        padding: 1% 3% 1% 1%;
        background: url('./../assets/修改切图/通知栏.png');
        z-index: 1;
    }
    
    div.notice {
        height: 100%;
        width: 75%;
        border-radius: 1.5em;
        background: url('./../assets/修改切图/通知栏内.png');
        color: #783a3f;
        float: left;
        text-align: center;
    }
    
    div.option {
        width: 12%;
        height: 100%;
        /*background: black;*/
        float: right;
        /* border:.15em solid #fcd19e;
    border-radius: 0.5em;*/
        /*background: #ff9e40;*/
        background: url(../assets/切图/主界面/菜单.png) 50% 50%;
        background-size: contain;
        background-repeat: no-repeat;
    }
</style>