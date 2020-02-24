<template>
    <v-app-bar v-bind="vtheme['1']" :style="setStyles(datas.options.nav.styles)">
        <div class="app__bar__container">
            <div class="app__bar__name__container">
                <div v-if="datas.options.nav.show_logo" class="app__bar__logo__container">
                    <img :src="datas.logo" :alt="datas.name + ' Logo'" class="app__bar__logo">
                </div>
                <v-toolbar-title v-if="datas.options.nav.show_name">
                    {{ datas.name }}
                </v-toolbar-title>
            </div>
            <ul class="nav__links__no-hambuger" v-if="!datas.options.nav.hamburger">
                <nuxt-link v-for="(item, i) in nav" :key="i" :to="item.link" :style="setStyles(datas.options.nav.styles)">
                        <img v-if="item.icon"/>
                        <p>{{ item.title }}</p>
                </nuxt-link>
            </ul>
            <v-app-bar-nav-icon :class="{'nav__hamburger__hide' : !this.hamburger}" v-bind="vtheme.button" right @click.stop="drawer = !drawer"/>
        </div>
    </v-app-bar>
</template>

<script>
export default {
    props: {
        datas: Object,
        theme: Object,
        hamburger: Boolean
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
            drawer: false,
            vtheme: {
                '1': {
                    clipped: false,
                    fixed: false,
                    dark: false,
                    dense: true,
                    flat: true,
                    "collapse-on-scroll": false
                },
                button: {
                    dark: true
                }
            }
        }
    }
}
</script>

<style>

</style> 