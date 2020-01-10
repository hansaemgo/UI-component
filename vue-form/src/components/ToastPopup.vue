<template>
    <div class="toast" v-bind:class="">
        토스트 팝업
    </div>
</template>

<script>
export default {
    props: ['open'],
    watch: {
        open(newValue) {
            if (newValue) {
                console.log('팝업열기');
            }
        }
    }
};
</script>

<style scoped>
.toast {
    width: 200px;
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
.open{
    bottom: 10px;
}

</style>