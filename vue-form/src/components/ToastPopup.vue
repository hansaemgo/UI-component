<template>
    <div class="toast" v-bind:class="{'animation':open}">
        로그인이 완료되었습니다.
    </div>
</template>

<script>
let timer;

export default {
    props: ['open'],
    watch: {
        open(newValue) {
            if (newValue) {
                console.log('팝업열기');
                clearTimeout(timer);
                timer = setTimeout(() => this.$emit('close'), 2000);
            }
        }
    }
};
</script>

<style scoped>
.toast {
    width: 250px;
    height: 40px;
    background-color: black;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    bottom: -50px;
    left: 10px;
    border-radius:20px;
    transition: bottom .5s ease-in;
}
.animation{
    bottom: 10px;
}

</style>