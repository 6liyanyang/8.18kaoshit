<template>
    <div class="leftlist">
        <ul>
            <li v-for="(item, index) in list" :key="index" @click="activeTab = index"
                :class="{ 'active': index === activeTab }">
                <span @click="activeTab1 = index" :class="{ 'active1': index === activeTab1 }">
                    <svg data-v-a22cce3a xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
                        viewBox="0 0 24 24">
                        <g fill="none">
                            <path
                                d="M2.75 18h12.5a.75.75 0 0 1 .102 1.493l-.102.007H2.75a.75.75 0 0 1-.102-1.494L2.75 18h12.5h-12.5zm0-6.5h18.5a.75.75 0 0 1 .102 1.493L21.25 13H2.75a.75.75 0 0 1-.102-1.493l.102-.007h18.5h-18.5zm0-6.497h15.5a.75.75 0 0 1 .102 1.493l-.102.007H2.75a.75.75 0 0 1-.102-1.493l.102-.007h15.5h-15.5z"
                                fill="currentColor" />
                        </g>
                    </svg>
                    {{ item.date }}
                    <p>{{ item.num }}</p>
                    <svg t="1692519359013" class="icon" id="icons" @click="del(index)" viewBox="0 0 1024 1024" version="1.1"
                        xmlns="http://www.w3.org/2000/svg" p-id="4669" width="16" height="16">
                        <path
                            d="M840 288H688v-56c0-40-32-72-72-72h-208C368 160 336 192 336 232V288h-152c-12.8 0-24 11.2-24 24s11.2 24 24 24h656c12.8 0 24-11.2 24-24s-11.2-24-24-24zM384 288v-56c0-12.8 11.2-24 24-24h208c12.8 0 24 11.2 24 24V288H384zM758.4 384c-12.8 0-24 11.2-24 24v363.2c0 24-19.2 44.8-44.8 44.8H332.8c-24 0-44.8-19.2-44.8-44.8V408c0-12.8-11.2-24-24-24s-24 11.2-24 24v363.2c0 51.2 41.6 92.8 92.8 92.8h358.4c51.2 0 92.8-41.6 92.8-92.8V408c-1.6-12.8-12.8-24-25.6-24z"
                            fill="#8a8a8a" p-id="4670"></path>
                        <path
                            d="M444.8 744v-336c0-12.8-11.2-24-24-24s-24 11.2-24 24v336c0 12.8 11.2 24 24 24s24-11.2 24-24zM627.2 744v-336c0-12.8-11.2-24-24-24s-24 11.2-24 24v336c0 12.8 11.2 24 24 24s24-11.2 24-24z"
                            fill="#8a8a8a" p-id="4671"></path>
                    </svg>
                </span>
            </li>
        </ul>
        <div class="list-add">
            <a href="#">
                <svg data-v-a22cce3a xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
                    viewBox="0 0 24 24">
                    <g fill="none">
                        <path
                            d="M2.75 18h12.5a.75.75 0 0 1 .102 1.493l-.102.007H2.75a.75.75 0 0 1-.102-1.494L2.75 18h12.5h-12.5zm0-6.5h18.5a.75.75 0 0 1 .102 1.493L21.25 13H2.75a.75.75 0 0 1-.102-1.493l.102-.007h18.5h-18.5zm0-6.497h15.5a.75.75 0 0 1 .102 1.493l-.102.007H2.75a.75.75 0 0 1-.102-1.493l.102-.007h15.5h-15.5z"
                            fill="currentColor" />
                    </g>
                </svg>
                <span @click="add()">新建列表</span>
            </a>
        </div>
    </div>
</template>

<script>
export default {
    name: 'VueLeftbottom',

    data() {

        return {
            lists: [

            ],
            list: [
                {
                    'date': "待办事项",
                    num: 0
                },
                {
                    'date': "待办事项",
                    num: 0
                },
                {
                    'date': "待办事项",
                    num: 0
                },
            ],
            activeTab: null,
            activeTab1: null,
        };
    },
    methods: {
        add() {
            this.list.push({
                date: "待办事项",
                num: "0"
            })
            localStorage.setItem("listdata", JSON.stringify(this.list));
            console.log(this.list);
        },
        del(index) {
            if (confirm("确定要删除吗？")) {
                this.list.splice(index, 1)
            } else {
                return
            }
            localStorage.setItem("lists11", JSON.stringify(this.list));
        },
    },
    mounted() {
        // 从本地存储中获取数据
        const storedItems = localStorage.getItem("lists11");
        if (storedItems) {
            this.list = JSON.parse(storedItems);
        }
    },

}

</script>

<style scoped>
.leftlist {
    position: relative;
    width: 90%;
    margin: auto;
    overflow: hidden;
}

::-webkit-scrollbar {
    display: none;
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
    position: absolute;
    top: 1px;
    right: 5px;
}

img {
    position: relative;
    top: 2px;
}

.active {
    background-color: #1b2835 !important;
    box-shadow: -2px 0px 0px 0px #1089ff;
    border-left: 2px solid #1089ff;
}

svg {
    position: relative;
    top: 3px;
    width: 16px;
    height: 16px;
}

.list-add {
    width: 100px;
    height: 25px;
    margin: auto;
    position: fixed;
    bottom: 12px;
    color: rgba(255, 255, 255, 0.3);
}

a {
    color: rgba(255, 255, 255, 0.3);
}

.list-add:hover a {
    color: rgba(255, 255, 255, 0.822);
}

#icons {
    position: relative;
    left: 90px;
}
</style>