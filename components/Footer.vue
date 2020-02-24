<template>
    <v-footer app v-bind="vtheme['1']" :style="setStyles(datas.footer.styles)">
        <span>&copy; {{ new Date().getFullYear() }} - {{ datas.name }}</span>
    </v-footer>
</template>

<script>
export default {
    props: {
        datas: Object
    },
    computed: {
        colors: function () {
            return this.$store.state.colors
        } 
    },
    methods: {
        setStyles: function (data) {
            let colors = this.colors;
            let newObj = {};
            for (let s in data) {
                let textColor = data[s];
                if (textColor in colors) {
                    newObj[s] = colors[data[s]].code;
                }
            }
            return newObj
        }
    },
    data () {
        return {
            vtheme: {
                1: {
                    "dark": true,
                    "fixed": false,
                    "absolute": true
                }
            }
        }
    }
}
</script>

<style>

</style> 