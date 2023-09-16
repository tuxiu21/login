<template>
<div class="main">
    <img :src="img_src">
    <div class="info">
        <p>
            {{ title }}
        </p>
        <div>
            <CameraOutlined/>
            <span class="text">{{author}}</span>
        </div>
    
    </div>
</div>



</template>


<script setup>

defineProps(['title', 'author', 'img_src'])

import CameraOutlined from '@ant-design/icons-vue/CameraOutlined'



</script>

<style scoped>
.main{
 border: #808080 3px solid;
 border-radius: 15px;
 position: relative;
 transition: all 0.6s;
 z-index: 1;
}
.main:hover{
    transform: scale(1.5);
    z-index: 2;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);

}
.main>img{
    width:100%;
    height: 100%;
    border-radius: 12px 12px 0 0;
    overflow: hidden;
    
}
.info{
    height: 60px;
    background-color: white;
    border-radius:0 0 12px 12px;
}
.info>p{
    position: absolute;
    left: 10px;
    bottom: 10px;
}
.info>div{
    position: absolute;
    right: 10px;
    bottom: 10px;
}


</style>