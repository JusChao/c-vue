<script setup>

import { reactive } from 'vue';

const logoUrl = 'https://img.alicdn.com/imgextra/i2/O1CN0185atxl21LObnbzfiX_!!6000000006968-2-tps-20-20.png';
const linkHoverStates = reactive({
    beianMiit: false,
    beianMps: false
});

const navigateToBeianMiit = () => {
    window.location.href = 'https://beian.miit.gov.cn/';
};

const navigateToBeianMps = () => {
    window.location.href = 'https://beian.mps.gov.cn/#/query/webSearch';
};

import {useRouter} from 'vue-router'
const router = useRouter();
const hub = () => {
    router.push('/hub/')
}

</script>

<template>
    <el-container class="layout-container">
        <el-main>
            <el-button class="button" type="primary" auto-insert-space @click="hub">jupyterhub</el-button>
        </el-main>
        <el-footer class="footer">
            <div class="footer-content">
                <div class="footer-row">
                    <img :src="logoUrl" alt="Logo" @click="navigateToBeianMiit" class="footer-logo" />
                    <p class="footer-text" :style="{ color: linkHoverStates.beianMiit ? '#007bff' : '#999' }"
                        @mouseover="(e) => linkHoverStates.beianMiit = true"
                        @mouseout="(e) => linkHoverStates.beianMiit = false" @click="navigateToBeianMiit">
                        浙ICP备2024067072号</p>
                    <p class="footer-text" :style="{ color: linkHoverStates.beianMps ? '#007bff' : '#999' }"
                        @mouseover="(e) => linkHoverStates.beianMps = true"
                        @mouseout="(e) => linkHoverStates.beianMps = false" @click="navigateToBeianMps">
                        浙公网安备33010202004753号</p>
                </div>
            </div>
        </el-footer>
    </el-container>
</template>

<style lang="scss" scoped>
.layout-container {
    height: 100vh;
}

.home-page {
    // height: 100vh;
    background-color: #fff;
}

.footer {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 20px;
    /* 自定义高度以适应内容 */
    background-color: #f8f8f8;
    /* 可选，设置背景色 */
}

.footer-row {
    display: flex;
    align-items: center;
    gap: 10px;
    /* 图片和文字之间的间距 */
}

.footer-logo {
    width: 15px;
    height: auto;
}

.footer-text {
    cursor: pointer;
    font-size: 14px;
}
</style>