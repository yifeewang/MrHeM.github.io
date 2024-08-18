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
