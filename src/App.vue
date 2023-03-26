<template>
    <div class="main">
        <StopWatch v-for="stopWatch in stopWatches" v-bind:key="stopWatch" />
        <div class="wrapper__add">
            <button @click="addStopWatch" >
                <img src="./assets/plus.svg" alt="add stop watch" />
            </button>
        </div>
    </div>
</template>

<script>
import StopWatch from "./components/StopWatch.vue";

export default {
    name: "App",
    components: {
        StopWatch,
    },
    data() {
        return {
            stopWatches: 1,
        };
    },
    methods: {
        addStopWatch() {
            this.stopWatches++;
        },
    },
};
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
#app {
    font-family: "Gotham Pro", sans-serif;
    background: #353638;
    height: 100vh;
    padding: 72px 10%;
}
.main {
    display: grid;
    grid-template-rows: repeat(auto, 1fr);
    gap: 45px;
    align-items: center;
    justify-items: center;
    height: max-content;
    background: transparent;
}
@media (min-width: 768px) {
    .main {
        grid-template-columns: repeat(2, 1fr);
    }
}
@media (min-width: 1024px) {
    .main {
        grid-template-columns: repeat(3, 1fr);
    }
}
.wrapper__add {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 225px;
    height: 120px;
    background: #696969;
}
button {
    cursor: pointer;
    background: transparent;
    border: none;
}
</style>
