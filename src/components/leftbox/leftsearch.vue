<template>
    <div>
        <input type="text" placeholder="search" v-model="inputValue" @input="inputs" />
        <div class="svger">
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024" v-if="funs" @click="clear" class="icon1">
                <path fill="currentColor"
                    d="m466.752 512-90.496-90.496a32 32 0 0 1 45.248-45.248L512 466.752l90.496-90.496a32 32 0 1 1 45.248 45.248L557.248 512l90.496 90.496a32 32 0 1 1-45.248 45.248L512 557.248l-90.496 90.496a32 32 0 0 1-45.248-45.248L466.752 512z" />
                <path fill="currentColor"
                    d="M512 896a384 384 0 1 0 0-768 384 384 0 0 0 0 768zm0 64a448 448 0 1 1 0-896 448 448 0 0 1 0 896z" />
            </svg>
            <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1024 1024" class="icon">
                <path fill="currentColor"
                    d="m795.904 750.72 124.992 124.928a32 32 0 0 1-45.248 45.248L750.656 795.904a416 416 0 1 1 45.248-45.248zM480 832a352 352 0 1 0 0-704 352 352 0 0 0 0 704z" />
            </svg>
        </div>
    </div>
</template>
  
<script>
export default {
    name: 'VueLeftsearch',

    data() {
        return {
            inputValue: ""
        };
    },

    mounted() { },

    methods: {
        inputs() {
            this.funs = this.inputValue.length > 0;
        },
        clear() {
            this.inputValue = "";
            this.funs = false;
        }
    },
    computed: {
        funs() {
            return this.inputValue.length > 0;
        }
    }
};

</script>

<style scoped>
input {
    width: 88%;
    height: 32px;
    background-color: #25252c;
    border: none;
    outline: none;
    border-radius: 10px;
    padding-left: 10px;
    margin-top: 35px;
    margin-left: 7px;
    color: white;
}

input:hover {
    box-shadow: 0 0 1px 1px rgba(255, 255, 255, 0.3);
}

.icon1 {
    width: 14px;
    height: 14px;
    float: right;
    color: rgba(255, 255, 255, 0.3);

}

.icon {
    width: 14px;
    height: 14px;
    float: right;
    color: rgba(255, 255, 255, 0.3);
}

.svger {
    height: 20px;
    float: right;
    position: relative;
    top: -23px;
    left: -15px;
}
</style>