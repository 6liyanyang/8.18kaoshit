<template>
    <div class="leftbox">
        <leftone></leftone>
        <lefttwo></lefttwo>
        <bottom></bottom>

    </div>
</template>
<script>
import leftone from "../leftbox/leftsearch.vue";
import lefttwo from "../leftbox/lefttab.vue";
import bottom from "../leftbox/leftbottom.vue"
export default {
    name: 'VueLeftbox',


    data() {
        return {

        };
    },

    mounted() {

    },

    methods: {

    },
    components: {
        leftone,
        lefttwo,
        bottom
    },
};
</script>

<style scoped>
.leftbox {
    width: 20%;
    height: 100%;
    border-top-left-radius: 10px;
    border-bottom-left-radius: 10px;
    background-color: #1c1c1e;
}
</style>