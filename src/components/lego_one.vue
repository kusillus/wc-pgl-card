<template>
    <div class="wc-wrapper-card">
        <div class="card-info">
            <div class="header-info">
                <div class="info-name">
                    <!-- <span v-if="parsed.nick.length > 0">
                        {{parsed.nick}}
                    </span> -->
                    {{parsed.name}}
                </div>
                <div class="info-lv-g">
                    Lv {{parsed.level}}
                    <span class="info-gender">
                        <i v-html="parsed.gender == 'M' ? genderM:genderF"></i>
                    </span>
                </div>
            </div>
            <div>
                <img :src='"https://play.pokemonshowdown.com/sprites/dex" + (parsed.shiny == "true" ? "-shiny" : "")+"/" + parsed.name +".png"' :alt='"imgan pokemon " + parsed.name'>
            </div>
        </div>
        <div class="card-stats">
            <div class="header-info">titulo 2</div>
        </div>
    </div>
</template>

<script>
export default {
    props:{
        info:{
            type: String,
            default: "Charizardito,Charizard,M,Aguav Berry,Solar Power,50,false,bug,28 HP / 116 Atk / 24 Def / 24 SpA / 64 SpD / 252 Spe ,27 HP / 25 Atk / 26 Def / 26 SpA / 26 SpD / 25 Spe, Hasty Nature,Acrobatics/Air Slash/Body Slam/Brick Break"
            //TODO:  "nick,name,gender,item,ability,level,shiny,hp,evs,ivs,nature,moves"
        }
    },
    data(){
        return {
            parsed: {},
            genderF: '<svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="13" height="13" viewBox="0 0 477.141 477.141" style="enable-background:new 0 0 477.141 477.141;" xml:space="preserve"><g><path fill="#C33" d="M326.711,341.99h-64.628v-64.634c0-0.686-0.142-1.323-0.213-1.997c65.409-11.119,115.378-68.161,115.378-136.681	C377.249,62.208,315.044,0,238.571,0C162.103,0,99.892,62.208,99.892,138.678c0,68.521,49.973,125.562,115.375,136.681		c-0.059,0.674-0.204,1.312-0.204,1.997v64.634h-64.631c-12.983,0-23.501,10.527-23.501,23.502c0,12.98,10.518,23.507,23.501,23.507 h64.637v64.64c0,12.98,10.524,23.502,23.501,23.502c12.979,0,23.513-10.527,23.513-23.502v-64.64h64.628		c12.986,0,23.508-10.526,23.508-23.507C350.219,352.518,339.698,341.99,326.711,341.99z M146.904,138.678 c0-50.546,41.121-91.673,91.667-91.673c50.549,0,91.676,41.122,91.676,91.673s-41.127,91.667-91.676,91.667C188.031,230.346,146.904,189.224,146.904,138.678z"/></g></svg>',
            genderM: '<svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 462.672 462.672" style="enable-background:new 0 0 462.672 462.672;" xml:space="preserve" width="10" height="10"><g><g><path style="fill:#004689;" d="M167.689,395.964c13.872,0,26.826-2.649,38.862-7.956c12.036-5.304,22.542-12.441,31.519-21.42 c8.975-8.976,16.014-19.479,21.113-31.518c5.1-12.036,7.648-24.99,7.648-38.862c0-13.464-2.551-26.214-7.648-38.25 c-5.102-12.036-12.141-22.542-21.113-31.518c-8.977-8.976-19.482-16.116-31.519-21.42c-12.036-5.304-24.99-7.956-38.862-7.956 c-13.464,0-26.214,2.652-38.25,7.956s-22.542,12.444-31.518,21.42c-8.976,8.976-16.116,19.48-21.42,31.518 c-5.304,12.036-7.956,24.786-7.956,38.25c0,13.872,2.652,26.826,7.956,38.862s12.444,22.542,21.42,31.518 c8.976,8.979,19.482,16.116,31.518,21.42C141.475,393.313,154.225,395.964,167.689,395.964z M460.837,79.56l-0.609-0.612v85.068 c0,8.568-3.063,15.912-9.184,22.032c-6.119,6.12-13.668,9.18-22.643,9.18c-8.568,0-16.32-3.06-23.256-9.18 c-6.121-6.12-9.184-13.464-9.184-22.032v-53.244l-91.188,91.188c9.385,13.464,16.627,28.152,21.727,44.064 c5.102,15.912,7.65,32.64,7.65,50.184c0,22.851-4.387,44.37-13.158,64.566c-8.771,20.193-20.707,37.842-35.803,52.938 c-15.096,15.099-32.742,27.03-52.938,35.805c-20.196,8.771-41.718,13.155-64.566,13.155c-22.848,0-44.37-4.386-64.566-13.155 c-20.196-8.772-37.842-20.706-52.938-35.805c-15.096-15.096-26.928-32.742-35.496-52.938c-8.566-20.196-12.85-41.717-12.85-64.566 c0-22.848,4.284-44.37,12.852-64.566s20.4-37.74,35.496-52.632s32.742-26.724,52.938-35.496s41.718-13.158,64.566-13.158 c17.136,0,33.252,2.346,48.348,7.038c15.096,4.692,29.171,11.322,42.23,19.89l-0.611-0.612l93.021-92.412h-53.854 c-8.979,0-16.32-3.264-22.033-9.792c-3.264-2.856-5.609-6.222-7.037-10.098s-2.143-8.058-2.143-12.546c0-8.976,3.061-16.524,9.18-22.644C280.093,3.06,287.436,0,296.821,0h78.336h20.195h65.483L460.837,79.56L460.837,79.56z"/></g></g></svg>'

        }
    },
    mounted(){
        this.firstLoad(this.info)
    },
    methods:{
        firstLoad(info){
            let vm      = this,
                data    = info.split(','),
                parsed  = {
                    nick: data[0],
                    name: data[1].toLowerCase(),
                    gender: data[2],
                    item: data[3],
                    ability: data[4],
                    level: data[5],
                    shiny: data[6],
                    hp: data[7],
                    evs: data[8],
                    ivs: data[9],
                    nature: data[10],
                    moves: data[11]
                }
            vm.parsed = parsed
        }
    }


}
</script>

<style lang="scss">
$green: #67A72F;
$white: #FFFFFF;
$bg-card: #F6F6F6;
$grey: #CCC;
$orange: #EE5736;
$purple: #753FB5;


$normal: #aa9;
$fire:#f42;
$water:#39f;
$electric: #fc3;
$grass:#7c5;
$ice:#6cf;
$fighting:#b54;
$poison:#a59;
$ground:#db5;
$flying:#89f;
$psychic:#f59;
$bug:#ab2;
$rock:#ba6;
$gost:#66b;
$dragon:#76e;
$dark:#754;
$steel:#aab;
$fairy:#e9e;

:root {
    --font-family: Arial, Helvetica, sans-serif;
    --font-size: 16px;
    --bg-card: rgb(246, 246, 246);
    --bg-title-info: rgb(238, 87, 54);
    --bg-title-stats: rgb(117, 63, 181);
}

.wc-wrapper-card{
    background-color: var(--bg-card);
    max-width: 600px;
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    font-size: var(--font-size);
    font-family: var(--font-family);
    box-sizing: border-box;
    .card-info, .card-stats{
        padding: 4px;
    }
    .card-stats .header-info{
        background-color: var(--bg-title-stats); 
    }

    .header-info{
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 5px;
        background-color: var(--bg-title-info);
        color: #FFF;
        .info-name{
            background-color: var(--bg-title-info);
            text-transform: capitalize;

        }
        .info-lv-g{
            display: flex;
            align-items: center;
        }
        .info-gender{
            height: 100%;
            background: white;
            width: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            justify-content: center;
            position: relative;
            padding-right: 3px;
            margin-left:13px;
            &::before{
                content: '';
                position: absolute;
                left: -9px;
                border: solid;
                border-color: transparent $white transparent transparent;
                border-width: 18px 9px 0px 0px;
            }
        }
    }
}
</style>