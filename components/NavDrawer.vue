<template>
    <v-navigation-drawer v-bind="vtheme['1']" :style="setStyles(sitewide.options.nav.styles)">
        <v-list>
            <v-list-item router exact v-for="(item, i) in datas" :key="i" :to="item.link" :style="setStyles(sitewide.options.nav.styles)">
                <v-list-item-action>
                    <v-icon v-if="item.icon">{{ item.icon }}</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title v-text="item.title" />
                </v-list-item-content>
            </v-list-item>
        </v-list>
    </v-navigation-drawer>
</template>

<script>
export default {
    props: {
        datas: Array,
        theme: Object
    },
    computed: {
        sitewide: function () {
            return this.$store.state.sitewide
        },
        nav: function () {
            return this.$store.state.nav
        },
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
                '1': {
                    fixed: true,
                    right: false,
                    "mini-variant": false,
                    clipped: false
                }
            }
        }
    }
}
</script>

<style>

</style> 