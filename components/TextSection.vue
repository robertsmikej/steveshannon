<template>
    <div :class="datas.classes" :style="datas.parsedStyles[Object.keys(datas.parsedStyles)[0]]" class="page__text__section" v-html="$md.render(datas.content)">
        {{datas.parsedStyles}}
    </div>
</template>

<script>
export default {
    props: {
        datas: Object,
        theme: Object
    }
}
</script>

<style>
.page__text__section {
    width: 100%;
    max-width: 1200px;
    margin: 20px auto 0;
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    align-content: flex-start;
    justify-content: center;
}
.page__text__section  h2 {
    text-align: center;
    width: 100%;
}
</style> 