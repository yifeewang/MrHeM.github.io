<template>
    <div class="wraper">
        <el-form
            label-position="right"
            label-width="100px"
            :model="formLabelAlign"
            style="max-width: 460px"
        >
            <el-form-item label="链接：">
                <el-input v-model="formLabelAlign.linkUrl" />
            </el-form-item>
            <el-form-item label="失效时间：">
                <el-input v-model="formLabelAlign.expireTime" />
            </el-form-item>
            <div>过期时间以分钟计数，比如填 10， 那么该二维码在10分钟后失效</div>
        </el-form>
        <div class="btn">
            <el-button type="primary" @click="generateQrcode">生成二维码</el-button>
        </div>
        <div>
            <img :src="generateUrl" alt="" />
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'
import qrcode from "qrcode";
const formLabelAlign = ref({
    linkUrl: '',
    expireTime: '',
});
const generateUrl = ref('');
async function generateQrcode() {
    const now = new Date();
    const expirationTime = now.getTime() + (formLabelAlign.value.expireTime * 60 * 1000);
    // 构造URL
    const url = `https://MrHe-github-io.pages.dev?expires=${expirationTime}&qrCodeUrl=${encodeURIComponent(formLabelAlign.value.linkUrl)}`;
    try {
        const qrCode = await qrcode.toDataURL(url);
        console.log('QR Code:', url);
        generateUrl.value = qrCode;
        // 在这里你可以将qrCode用于展示或者保存到服务器
    } catch (error) {
        console.error('Error generating QR code:', error);
  }
}
</script>
<style>
.wraper {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-top: 20vh;
    width: 100vw;
    height: 100vh;
}
.btn {
    margin-top: 30px;
}
</style>
