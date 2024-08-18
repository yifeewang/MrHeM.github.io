<template>
    <div class="outer-wrap">
        <div class="outer-content">
            <div class="wap-nav-bar">
                <div class="wap-nav-bar__left">
                    <a href="/">
                        <img src="https://t3.chei.com.cn/chsi/assets/gb/wap/images/logo.png" alt="学信网" class="logo">
                    </a>
                    <span class="logo-dot"></span>
                    <span class="logo-text"><a href="/xlrz/index.jsp">学历认证</a></span>
                </div>
                <div class="wap-nav-bar__center"></div>
                <div class="wap-nav-bar__right">
                    <span class="ch-nav">
                        <img class="ch-nav-img" alt="" src="./assets/nav.jpg">
                    </span>
                </div>
            </div>
            <div class="res bg-result-container">
                <div class="bg-white">
                    <div class="top-change clearfix">
                        <div class="fl lang-div change-language-box">
                            <div class="switch">
                                <span class="cg-bgyz-title">报告语种</span>
                                <a href="/xlrz/bgcx.jsp?v=11554658-11-F82B58B8&amp;wp=zh" class="current">中文</a>
                            </div>
                        </div>
                        <div class="fr pdf-div down-pdf-box">
                            <a @click="getpdf" class="down-bg-pdf"></a>
                        </div>
                    </div>
                </div>
                <div class="bg-white base-info-box gd-base-info-box">
                    <h3>中国高等教育学历认证报告</h3>
                    <div class="img-div clearfix"></div>
                </div>
                <div class="collection card">
                    <div class="row collection-item">
                        <div class="col s4 bolder">姓名</div>
                        <div class="col s8 namtFamily">方国学</div>
                    </div>
                    <div class="row collection-item">
                        <div class="col s4 bolder">性别</div>
                        <div class="col s8">男</div>
                    </div>
                    <div class="row collection-item">
                        <div class="col s4 bolder">身份证号</div>
                        <div class="col s8">420881196502054816</div>
                    </div>
                    <div class="row collection-item">
                        <div class="col s4 bolder">学历类别</div>
                        <div class="col s8">高等教育自学考试</div>
                    </div>
                    <div class="row collection-item">
                        <div class="col s4 bolder">层次</div>
                        <div class="col s8">专科</div>
                    </div>
                    <div class="row collection-item">
                        <div class="col s4 bolder">省级考委</div>
                        <div class="col s8">湖北省</div>
                    </div>
                    <div class="row collection-item">
                        <div class="col s4 bolder">主考院校</div>
                        <div class="col s8">华中师范大学</div>
                    </div>
                    <div class="row collection-item">
                        <div class="col s4 bolder">专业名称</div>
                        <div class="col s8">政治教育</div>
                    </div>
                    <div class="row collection-item">
                        <div class="col s4 bolder">毕业日期</div>
                        <div class="col s8">1999年12月</div>
                    </div>
                    <div class="row collection-item">
                        <div class="col s4 bolder">毕结业</div>
                        <div class="col s8">毕业</div>
                    </div>
                    <div class="row collection-item">
                        <div class="col s4 bolder">证书编号</div>
                        <div class="col s8">27040045</div>
                    </div>
                    <div class="row collection-item ">
                        <div class="col s4 bolder">报告编号</div>
                        <div class="col s8">11554658</div>
                    </div>
                    <div class="row collection-item ">
                        <div class="col s4 bolder">打印日期</div>
                        <div class="col s8">2021-04-20</div>
                    </div>
                </div>
                <div class="collection card zcrz-collection">
                    <div class="collection-item zcrz-box">
                        以上学历情况属实，专此认证
                        <span class="zcrz-icon"></span>
                    </div>
                </div>
                <div class="collection card zs-list">
                    <div class="row collection-item">
                        <div class="col s4 bolder">毕业证书</div>
                        <div class="col s8 materialboxed"><img
                                src="./assets/member.png" data-caption="毕业证书"
                                width="60" height="40"> <i class="iconfont"></i></div>
                    </div>
                </div>
            </div>
        </div>
        <div class="wap-footer wap-footer2">
            主办单位：<a href="https://chesicc.chsi.com.cn/">教育部学生服务与素质发展中心</a><br>
            Copyright © 2003-2024 <a href="https://www.chsi.com.cn/" target="_blank">学信网</a> All Rights Reserved
        </div>
    </div>
</template>

<script setup>
// import { ref } from 'vue';
import axios from 'axios';
function getpdf() {
    axios('/certificate.pdf', {//pdf的位置
        responseType: 'blob', //重要代码
    }).then(res => {
        const url = window.URL.createObjectURL(new Blob([res.data]));
        const link = document.createElement('a');
        link.href = url;
        let fileName = "陈洪谦的pdf.pdf" //保存到本地的文件名称
        link.setAttribute('download', fileName);
        document.body.appendChild(link);
        link.click();
        console.log(link);
        link.remove();
    })
}
</script>

<style>
*, body {
    margin: 0;
    padding: 0;
}
.outer-wrap {
    width: 100vw;
    height: 100vh;
    min-height: 100vh;
    color: #2a3839;
    background-color: #fff;
    word-wrap: break-word;
    margin: 0 auto;
    position: relative;
    font-size: 12px;
}
.outer-content {
    /* padding-bottom: 1.813rem; */
}
.wap-nav-bar {
    position: relative;
    z-index: 1;
    height: 1.173rem;
    display: flex;
    align-items: center;
    background: #fff;
    border-bottom: 1px solid #E8EAED;
}
.ch-icon {
    position: relative;
    font: normal normal normal 14px / 1 'ch-icon';
    font-size: inherit;
    text-rendering: auto;
    font-size: 0.533rem;
    -webkit-font-smoothing: antialiased;
}
.ch-icon-wap-nav:before {
    display: inline-block;
    content: "\F0DD";
    cursor: pointer;
}
.wap-nav-bar__left {
    padding: 0 0.427rem;
    display: flex;
    align-items: center;
}
.logo {
    display: block;
    height: 0.704rem;
}
.logo-dot {
    display: block;
    height: 0.533rem;
    width: 0.027rem;
    background: #E8EAED;
    margin: 0 0.213rem;
}
.wap-nav-bar__center {
    flex: 1;
    height: 1.173rem;
    display: flex;
    align-items: center;
    justify-content: flex-end;
}
.wap-nav-bar__right {
    padding: 0 0.427rem;
    display: flex;
    align-items: center;
}
.ch-nav-img {
    width: 0.36rem;
    height: 0.32rem;
}
.collection {
    margin: 0;
    padding: .53rem 0;
    background-color: #fff;
    border-bottom: .01rem solid #ebebeb;
}
.zcrz-collection {
    margin: 0;
    padding: 0;
}
.res .collection .collection-item:last-child {
    border-bottom: none;
}
.collection-item {
    line-height: .53rem;
    padding: .2rem .44rem;
    background-color: #fff;
    line-height: .533rem;
    padding: .346rem .427rem;
    margin: 0;
}
.bg-result-container .collection .collection-item:not(.course-tit) .col:first-child.s4 {
    color: #889098;
    text-align: right;
    padding-right: .37rem;
}
.res .row .col.s4 {
    width: 33%;
    margin-left: auto;
    left: auto;
    right: auto;
    padding-right: 1%;
    color: #999;
}
.res .row .col {
    float: left;
    min-height: 1px;
    box-sizing: border-box;
}
.res .row .col.s8 {
    width: 66%;
    margin-left: auto;
    left: auto;
    right: auto;
}
.res .zs-list .s8 img {
    width: 1.6rem;
    height: 1.067rem;
    vertical-align: text-top;
}

.res .zs-list .s8 .iconfont {
    float: right;
    line-height: 1.067rem;
    color: #999;
}
</style>

<style>
    @font-face {
        font-style: normal;
        font-weight: 400;
        font-family: 'ch-icon';
        src: url(https://t3.chei.com.cn/gaokao/wap/assets/font/vant-icon.woff2) format("woff2"), url(https://t3.chei.com.cn/gaokao/wap/assets/font/vant-icon.woff) format("woff"), url(https://t3.chei.com.cn/gaokao/wap/assets/font/vant-icon.ttf) format("truetype")
    }

    .ch-nav {
        display: flex;
        align-items: center;
    }

    .ch-icon {
        position: relative;
        font: normal normal normal 14px/1 'ch-icon';
        font-size: inherit;
        text-rendering: auto;
        font-size: 0.533rem;
        -webkit-font-smoothing: antialiased;
    }

    .ch-icon-cross:before {
        display: inline-block;
        content: '\F042';
        cursor: pointer;
    }

    .ch-icon-right {
        cursor: pointer;
        font-size: 0.4rem;
        font-weight: 400;
        color: #666666;
        line-height: 0.43rem;
    }

    .van-overflow-hidden {
        overflow: hidden !important;
    }

    .ch-common-nav-popup .van-popup {
        position: fixed;
        width: 100%;
        max-width: 750px;
        margin: 0 auto;
        max-height: 100%;
        overflow-y: auto;
        background-color: #fff;
        transition: transform 0.3s;
        -webkit-overflow-scrolling: touch;
    }

    .ch-van-overlay {
        position: fixed;
        top: 0;
        left: 0;
        z-index: 1;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.7);
    }

    .ch-common-nav-popup .van-popup--center {
        top: 50%;
        left: 50%;
        transform: translate3d(-50%, -50%, 0);
    }

    .ch-common-nav-popup .close-bar {
        height: 1.173rem;
        padding: 0 0.427rem;
        display: flex;
        -ms-flex-align: center;
        align-items: center;
        -ms-flex-pack: end;
        justify-content: space-between;
    }

    .ch-common-nav-popup .ch-van-overlay {
        top: 0;
        left: auto;
        max-width: 750px;
        margin: 0 auto;
    }

    .ch-common-nav-popup .van-popup {
        top: 0;
        left: auto;
    }

    .ch-common-nav-popup .van-popup::after {
        position: absolute;
        box-sizing: border-box;
        content: ' ';
        pointer-events: none;
        top: -50%;
        right: -50%;
        bottom: -50%;
        left: -50%;
        border: 0 solid #e5e5e5;
        transform: scale(0.5);
        border-top-width: 1px;
        border-color: #d5d5d5;
    }

    .ch-common-nav-popup .van-popup--center {
        transform: none;
    }

    .ch-common-nav-popup .van-row {
        padding: 0.267rem 0.28rem;
        text-align: center;
    }

    .ch-common-nav-popup .van-row .active {
        background: #f5f5f5;
    }

    .ch-common-nav-popup .van-row a {
        display: block;
        height: 0.96rem;
        line-height: 0.96rem;
        border-radius: 0.107rem;
        margin: 0 0.147rem 0.293rem;
        font-size: 0.373rem;
        color: #333;
        background: #f5f5f5;
        text-decoration: none;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;

    }

    .ch-common-nav-popup .van-row .van-col:nth-child(6) a {
        padding-left: 0.133rem;
    }

    .ch-icon-wap-nav:before {
        display: inline-block;
        content: "\F0DD";
        cursor: pointer;
    }

    .close-bar .logo {
        display: block;
        height: 0.704rem;
    }

    .gk-top-navlist-item {
        font-size: 0.43rem;
        font-weight: 700;
        color: #333333;
        line-height: 0.43rem;
        padding: 0.267rem 0.427rem;
    }

    /* wap-top-nav */
    .wap-nav-bar {
        position: relative;
        z-index: 1;
        height: 1.173rem;
        display: flex;
        align-items: center;
        background: #fff;
        border-bottom: 1px solid #E8EAED;
    }

    /* .wap-nav-bar:after {
    position: absolute;
    box-sizing: border-box;
    content: " ";
    pointer-events: none;
    top: -50%;
    right: -50%;
    bottom: -50%;
    left: -50%;
    border-bottom: 1px solid #E8EAED;
    transform: scale(.5);
} */
    .wap-nav-bar.no-border {
        border-bottom: none;
    }

    .wap-nav-bar .wap-nav-bar__left {
        padding: 0 0.427rem;
        display: flex;
        align-items: center;
    }

    .wap-nav-bar .logo {
        display: block;
        height: 0.704rem;
    }

    .wap-nav-bar__center {
        flex: 1;
        height: 1.173rem;
        display: flex;
        align-items: center;
        justify-content: flex-end;
    }

    .wap-nav-bar .wap-nav-bar__right {
        padding: 0 0.427rem;
        display: flex;
        align-items: center;
    }

    .logo-text {
        font-size: 0.373rem;
        color: #60656E;
        margin-bottom: -0.0534rem;
    }

    .logo-text a {
        color: #60656E;
    }

    .logo-dot {
        display: block;
        height: 0.533rem;
        width: 0.027rem;
        background: #E8EAED;
        margin: 0 0.213rem;
    }
</style>
