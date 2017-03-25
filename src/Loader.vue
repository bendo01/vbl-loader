<template>
    <div class="modal background-is-black" :class="{ 'is-active':status }">
        <div class="modal-background"></div>
        <div class="modal-content">
            <div class="loading flex-is-justify-content-center" style="text-align: center;">
              <h2>{{message}}</h2>
              <span></span>
              <span></span>
              <span></span>
              <span></span>
              <span></span>
              <span></span>
              <span></span>
            </div>
        </div>
    </div>
</template>
<script>
'use strict';
var $ = require('jquery/dist/jquery.slim');
export default {
    props: {
        message: {
            type: String,
            default: 'Proses Data'
        },
        isLoading: {
            type: Boolean,
            default: false
        }
    },
    computed: {
        status: function () {
            let returned = false;
            if(this.isLoading) {
                $('html').addClass('is-clipped');
                returned = true;
            }
            else {
                $('html').removeClass('is-clipped');
                returned = false;
            }
            return returned;
        }
    }
};
</script>
<style>
/*
 * Loading Dots
 * Can we use pseudo elements here instead :after?
 */
.loading span {
    display: inline-block;
    vertical-align: middle;
    width: .6em;
    height: .6em;
    margin: .19em;
    background: #007DB6;
    border-radius: .6em;
    animation: loading 1s infinite alternate;
}

/*
 * Dots Colors
 * Smarter targeting vs nth-of-type?
 */
.loading span:nth-of-type(2) {
    background: #008FB2;
    animation-delay: 0.2s;
}
.loading span:nth-of-type(3) {
    background: #009B9E;
    animation-delay: 0.4s;
}
.loading span:nth-of-type(4) {
    background: #00A77D;
    animation-delay: 0.6s;
}
.loading span:nth-of-type(5) {
    background: #00B247;
    animation-delay: 0.8s;
}
.loading span:nth-of-type(6) {
    background: #5AB027;
    animation-delay: 1.0s;
}
.loading span:nth-of-type(7) {
    background: #A0B61E;
    animation-delay: 1.2s;
}

/*
 * Animation keyframes
 * Use transition opacity instead of keyframes?
 */
@keyframes loading {
    0% {
        opacity: 0;
    }
    100% {
        opacity: 1;
    }
}
</style>
