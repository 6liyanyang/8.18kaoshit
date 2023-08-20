<template>
    <div class="leftlist">
        <ul>
            <li v-for="(item, index) in list" :key="index" @click="activeTab = index" class="uls"
                :class="{ 'active': index === activeTab }">
                <span @click="activeTab1 = index" :class="{ 'active1': index === activeTab1 }">
                    <img :src="item.image" alt />
                    {{ item.date }}
                    <p >{{ item.num }}</p>
                </span>
            </li>

        </ul>
        <div v-for="(item, index) in list" :key="index" v-show="index === activeTab" class="tabone">
            <component :is="item.component"></component>
        </div>
    </div>
</template>

<script>
import Tabone from "../leftbox/Tabone.vue";
import Tabtwo from "../leftbox/Tabtwo.vue";
import Tabthree from "../leftbox/Tabthree.vue";
export default {
    name: 'VueLefttab',
    data() {
        return {
            list: [
                {
                    image:
                        "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAAXNSR0IArs4c6QAAAG5JREFUOE9jZKAQMIL0d3d3O/z//z+eVLPKysoSwQZ0dXXNB3GwGYBLrqurKwGkftQAaoYBnih0YGBgOIBFXoGBgWHhaCxQORYO4ogJUCZbiEXOnoGB4SA4Ftrb2xWYmZlB0UU0YGRkfFBaWnoAAFgKgvcfo0+oAAAAAElFTkSuQmCC",
                    date: "所有",
                    num: 3,
                    component: Tabone
                },
                {
                    image:
                        "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAAXNSR0IArs4c6QAAAHpJREFUOE9jZKAQMKLr7+rq+l9WVoYhDlKHTQ6usKuraz8DA4MDkQ56UFZWpghSi2zAfyI1g5XBXIliAC6n4/MmhgEgf8I0/P//v7G8vLxhiBlATEAiRyf1A3Fou2A+AwNDAjFeYGBgOFBWVuaIkpSJ1IihDGuuI8UwAMFfdhEui1guAAAAAElFTkSuQmCC",
                    date: "今天",
                    num: 4,
                    component: Tabtwo
                },
                {
                    image:
                        "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAAAXNSR0IArs4c6QAAAPxJREFUOE+tU8FtwzAQ09VPL9FukmySDGEa/kRpP4bpIZJOkm5SDWLABQ0rUFW7cJHqJ+qOR93xzC0ckgcA177vd8MwhKZpQsTycBOgwHEcL865AGBPcgRgXded9V7X9TliJBW3M7NjVVUfEwHJm5m9CpjvFwBHVTWzIFyJwtKCAF4iwVRx6TtrWFR0J/hLcoxV0f9T8PAXcoK524dZ7jU2MMr/0YM1BSQ/48jSPm0iaNv2uSiKm8aVN1neSX2wOMbUSDkByROAt1+nIAIZSbZOCbz3T2VZegD+kTFO+3K3snPuPa+0Zq55d6Rgny6T15JsdGT4tkwbkxbDvgDzQboRM93XlwAAAABJRU5ErkJggg==",
                    date: "最近7天",
                    num: 4,
                    component: Tabthree
                }
            ],
            activeTab: 0,
            activeTab1: 0,

        };
    },

    mounted() { },

    methods: {}
};

</script>

<style scoped>
.leftlist {
    width: 90%;
    height: 105px;
    margin: auto;
    border-bottom: 1px solid rgba(255, 255, 255, 0.3);
}

ul {
    width: 100%;
    height: 100%;
}

li span {
    display: block;
    width: 95%;
    height: 20px;
    margin: auto;
    position: relative;
    top: 5px;
    color: rgba(255, 255, 255, 0.3);
}

ul li {
    width: 100%;
    height: 30px;
    margin-top: 5px;
    font-size: 14px;
}

ul li:hover {
    background-color: #1b2835;
}

p {
    float: right;
}

img {
    position: relative;
    top: 2px;
}

.active {
    background-color: #1b2835 !important;
    box-shadow: -2px 0px 0px 0px #1089ff;

}

.tabone {
    position: relative;
    left: 250px;
    bottom: 150px;
}
</style>