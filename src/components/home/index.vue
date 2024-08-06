<template>
    <div class="es-screen-container">
        <div class="es-screen">
            <Header />

            <div class="es-screen-main">
                <div class="es-screen-left">
                    <Left />
                </div>
                <div class="es-screen-center">
                    <Center />
                </div>
                <div class="es-screen-right">
                    <Right />
                </div>
            </div>
        </div>
    </div>

</template>

<script setup>
import Header from './components/Header.vue'
import Left from './components/left/index.vue'
import Right from './components/right/index.vue'
import Center from './components/center/index.vue'

</script>
<style lang='scss' scoped>
.es-screen-container {
    --es-header-height: 72px;
    --es-block-bg: #222733;
    --es-screen-bg: rgb(22, 21, 34);
    --es-screen-text-color: #fff;
    position: relative;
    margin: 0;
    width: 100%;
    height: 100%;
    background-size: 100% 100%;
    overflow: hidden;
    background: var(--es-screen-bg);
    color: var(--es-screen-text-color);
}

.es-screen {
    position: relative;
    user-select: none;
    top: 50%;
    left: 50%;
    width: 100%;
    transform: translate(-50%, -50%);
    background-size: 100% 100%;
    padding: 0 20px;

    &-main {
        position: relative;
        display: flex;
        height: calc(100% - var(--es-header-height));
    }

    &-center {
        flex: 1;
        width: 800px
    }

    &-left,
    &-right {
        flex: 0 0 460px;
    }
}

.light {
    --es-screen-bg: rgb(238, 238, 238);
    --es-block-bg: #fff;
    --es-screen-text-color: rgb(22, 21, 34);
}
</style>
