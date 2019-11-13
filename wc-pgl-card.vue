<template>
    <div class="wc-lego-wrapper">
        Raiz del components
        <h5>{{user}}</h5>
        <lego-one></lego-one>
    </div>
</template>

<script>
import LegoOne from './src/components/lego_one.vue'

export default {
    props: {
        user: {
            type: String,
            default: 'Mark'
        }
    },
    components: {
        'lego-one': LegoOne
    }
}
</script>

<style lang="scss">
@import url('./src/styles/main.scss');
</style>