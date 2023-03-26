<template>
    <div class="wrapper__stopwatch">
        <div class="time">
            <p class="time__el">
                <span v-if="hours > 0">
                    {{ hours }} :
                </span>
                <span v-if="minutes > 0 || seconds > 59 || hours > 0" >
                    {{ minutes < 10 ? "0" + minutes : minutes }} :
                </span>
                <span>
                    {{ seconds < 10 ? "0" + seconds : seconds }}
                </span>
            </p>
        </div>
        <div class="buttons">
            <button @click="pauseStopWatch" v-if="isPause">
                <img src="./../assets/pause.svg" alt="pause" />
            </button>
            <button @click="startStopWatch" v-else>
                <img src="./../assets/start.svg" alt="start" />
            </button>
            <button @click="resetStopWatch">
                <img src="./../assets/stop.svg" alt="stop" />
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: "StopWatch",
    data() {
        return {
            hours: 0,
            minutes: 0,
            seconds: 0,
            interval: null,
            isPause: false
        };
    },
    methods: {
        startCounting() {
            this.seconds++;

            if (this.seconds > 59) {
                this.minutes++;
                this.seconds = 0;
            }

            if (this.minutes > 59) {
                this.hours++;
                this.minutes = 0;
            }
        },
        startStopWatch() {
            clearInterval(this.interval);
            this.interval = setInterval(this.startCounting, 1000);
            this.isPause = !this.isPause
        },
        pauseStopWatch() {
            clearInterval(this.interval);
            this.isPause = !this.isPause
        },
        resetStopWatch() {
            clearInterval(this.interval);
            (this.hours = 0), (this.minutes = 0), (this.seconds = 0);
            this.isPause = false
        },
    },
};
</script>

<style scoped>
.wrapper__stopwatch {
    display: grid;
    grid-template-rows: repeat(2, 1fr);
    width: 225px;
    height: 120px;
    background: #696969;
}
.time {
    display: flex;
    align-items: center;
    justify-content: center;
    border-bottom: 2px solid #9e9e9e;
}
.time__el {
    font-size: 22px;
    color: #9e9e9e;
}
.buttons {
    display: flex;
    gap: 48px;
    align-items: center;
    justify-content: center;
}
</style>
