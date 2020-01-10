<template>
    <div class="progress"></div>
  
</template>

<script>
export default {

}
</script>

<style scoped>
    .progress {
        height: 5px;
        background-color: lime;
        width: 0%;
        /* transition: width .5s ease-in; */
        animation: loading 1s linear;
    }
    .complete {
        width: 100%;
    }
    @keyframes loading {
        0% {
            width:0%;
        }
        50% {
            width:35%;
        }
        100%{
            width:100%;
        }
    }
</style>