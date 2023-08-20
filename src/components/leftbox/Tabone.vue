<template>
    <div class="box">
        <h2>所有</h2>
        <br>
        <div>
            <ul class="ul1">
                <li v-for="(item, index) in tet2" :key="index">
                    <input type="checkbox" name="" id="" class="che" :value="item.neirong"
                        v-model="selectedItems">&emsp;<span class="sp"
                        :class="{ 'selected': selectedItems.includes(item.neirong) }">{{
                            item.neirong }}</span>
                    <audio ref="audioPlayer" src="../../../public/audio/complete.mp3"></audio>
                    <br>
                    <el-date-picker id="dateinp" v-model="item.create_time" type="date" placeholder="-">
                    </el-date-picker>
                    <span>

                        <svg t="1692519359013" @click="del(index)" class="icon" id="icon2" viewBox="0 0 1024 1024"
                            version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="4669" width="25" height="25">
                            <path
                                d="M840 288H688v-56c0-40-32-72-72-72h-208C368 160 336 192 336 232V288h-152c-12.8 0-24 11.2-24 24s11.2 24 24 24h656c12.8 0 24-11.2 24-24s-11.2-24-24-24zM384 288v-56c0-12.8 11.2-24 24-24h208c12.8 0 24 11.2 24 24V288H384zM758.4 384c-12.8 0-24 11.2-24 24v363.2c0 24-19.2 44.8-44.8 44.8H332.8c-24 0-44.8-19.2-44.8-44.8V408c0-12.8-11.2-24-24-24s-24 11.2-24 24v363.2c0 51.2 41.6 92.8 92.8 92.8h358.4c51.2 0 92.8-41.6 92.8-92.8V408c-1.6-12.8-12.8-24-25.6-24z"
                                fill="white" p-id="4670"></path>
                            <path
                                d="M444.8 744v-336c0-12.8-11.2-24-24-24s-24 11.2-24 24v336c0 12.8 11.2 24 24 24s24-11.2 24-24zM627.2 744v-336c0-12.8-11.2-24-24-24s-24 11.2-24 24v336c0 12.8 11.2 24 24 24s24-11.2 24-24z"
                                fill="white" p-id="4671"></path>
                        </svg>
                        <svg t="1692519275699" id="icon1" class="icon" viewBox="0 0 1024 1024" version="1.1"
                            xmlns="http://www.w3.org/2000/svg" p-id="3641" width="32" height="32">
                            <path d="M288 512m-64 0a64 64 0 1 0 128 0 64 64 0 1 0-128 0Z" fill="white" p-id="3642"></path>
                            <path d="M512 512m-64 0a64 64 0 1 0 128 0 64 64 0 1 0-128 0Z" fill="white" p-id="3643"></path>
                            <path d="M736 512m-64 0a64 64 0 1 0 128 0 64 64 0 1 0-128 0Z" fill="white" p-id="3644"></path>
                        </svg>

                    </span>
                </li>
            </ul>
        </div>
        <div class="rightdata">
            <div class="footer">
                <svg data-v-a22cce3a xmlns="http://www.w3.org/2000/svg" id="svg" viewBox="0 0 1024 1024">
                    <path fill="currentColor"
                        d="M480 480V128a32 32 0 0 1 64 0v352h352a32 32 0 1 1 0 64H544v352a32 32 0 1 1-64 0V544H128a32 32 0 0 1 0-64h352z" />
                </svg>
                <input class="input" type="Text" placeholder="添加任务" v-model="inputValue" @focus="startAnimation"
                    @blur="resetProgress" @keyup.enter="handleEnterKey" />
                <div class="jindu">
                    <el-progress :percentage="progressValue" color="#1089ff" :show-Text="false"
                        :stroke-width="borderHeight"></el-progress>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import audioFile from "../../audio/complete.mp3"

export default {
    name: 'VueTabone',
    data() {
        return {
            inputValue: "",
            progressValue: 0,
            timer: null,
            borderHeight: 2,
            datelist: [],
            selectedItems: [],
            dadada: "123",
            tet2: [
                {
                    neirong: "2222"
                },
                {
                    neirong: "3333"
                },

                {
                    neirong: "4444"
                },
                {
                    neirong: "5555"
                },
            ]
        };
    },

    mounted() {
        // 从本地存储中获取数据
        const storedItems = localStorage.getItem("Text");
        if (storedItems) {
            this.tet2 = JSON.parse(storedItems);
        }
    },

    methods: {
        del(index) {
            if (confirm("确定要删除吗？")) {
                this.tet2.splice(index, 1)
            } else {
                return
            }
            localStorage.setItem("Text", JSON.stringify(this.tet2));
        },
        startAnimation() {
            clearInterval(this.timer); // 清除之前的计时器
            this.progressValue = 0; // 将进度条重置为0
            this.timer = setInterval(() => {
                if (this.progressValue < 100) {
                    this.progressValue += 10; // 每次增加10%
                } else {
                    clearInterval(this.timer); // 达到100%后清除计时器
                }
            }, 100);
        },
        resetProgress() {
            clearInterval(this.timer); // 清除计时器
            this.progressValue = 0; // 将进度条重置为0
        },
        handleEnterKey() {
            let str = {
                neirong: this.inputValue
            }
            this.tet2.push(str)
            localStorage.setItem("Text", JSON.stringify(this.tet2));
        }

    }, watch: {
        selectedItems(newValue) {
            if (newValue) {
                this.audio = new Audio(audioFile);
                this.audio.play();
            } else {
                if (this.audio) {
                    this.audio.pause();
                    this.audio.currentTime = 0;
                }
            }
        }
    },
};
</script>

<style scoped>
.box {
    width: 100%;
    height: 900px;
    margin-left: 30px;
}

h2 {
    color: white;
}

.ul1 li {
    width: 400%;
    height: 60px;
    border-radius: 6px;
    background: #1C1C1E;
    margin-bottom: 10px;
}


.sp {
    color: white;
}

.che {
    margin-left: 10px;
    margin-top: 10px;
}

#icon1 {
    float: right;
    position: relative;
    bottom: 30px;
}

#icon2 {
    float: right;
    position: relative;
    bottom: 25px;
}

.selected {
    Text-decoration: line-through;
    color: rgb(215, 215, 215);
}

.rightdata {
    margin-top: -20px;
    width: 80%;
    float: right;
}

.footer {
    position: fixed;
    bottom: 12px;
    right: 30px;
    width: 74%;
    height: 50px;
    line-height: 40px;
    background-color: #1c1c1e;
    border-top-left-radius: 6px;
    border-top-right-radius: 6px;
    margin: auto;
}



.input {
    position: relative;
    top: -2.5px;
    width: 73%;
    height: 35px;
    outline: none;
    border: none;
    padding-left: 5px;
    background-color: #1c1c1e;
    color: aliceblue;
    border-radius: 6px;
}

#svg {
    width: 16px;
    height: 16px;
    margin-left: 15px;
    color: aliceblue;
}

.progress-bar {
    height: 10px;
    background-color: #ccc;
}
</style>
<style scoped></style>