

<template>
    <div id="container">
      <header>
        <nav>
          <p>欢迎来到图库</p>
          <div>
            <RouterLink to="/login">登录</RouterLink>
            <RouterLink to="/reg">免费注册</RouterLink>
            <a href="#">购物车</a>
            <a href="#">我的订单</a>
          </div>
        </nav>
        <div class="down">
          <img src="../assets/images/logo.png" >

          <div class="search_bar">
            <div class="search_bar_top">
              <input type="input" placeholder="请输入...">
              <button>搜索</button>
            </div>
            <div class="search_bar_bottom">
              <a href="#">山川</a>
              <a href="#">河流</a>
              <a href="#">星空</a>
              <a href="#">山川</a>
            </div>
          </div>
          <img src="../assets/images/code.jpg" style="width:70px;">

        </div>
      </header>
      <main>
        <nav>
          <a href="">首页</a>
          <a >最新图片</a>
          <a >最热图片</a>
          <a >山川湖海</a> 
          <a >大漠孤烟</a> 
          <a>人像精选</a>
        </nav>
        
        <div class="slideshow">
          <img v-for="(image, index) in images" :src="image" :key="index" :class="{active:currentIndex===index}" />
          <div class="pagination">
          <span v-for="(image, index) in images" :key="index" :class="{active:currentIndex===index}" @mouseover="changeSlide(index)" @mouseout="startChange()">{{ index + 1 }}</span>
          <!-- 对每一个span子元素添加事件 当鼠标滑过对应的span 就向changeSlide 函数传入对应的index -->
          </div>
        </div>

        <div class="gallery">
          <nav>
            <p>
              <span>精选图片 </span>
              <span>总有一幅让你怦然心动</span>
            </p>
          </nav>
          <div class="img_list">
            <ImgItem
              v-for="(image,index) in image_gallery"
              title="name"
              author="pig"
              :img_src="image"
              :key="index"
              
            />
          </div>
        </div>
        
        
      </main>
      <footer>
        Copyright © 1999 - 2020 LZH. All Rights Reserved.
      </footer>
  </div>
  
</template>
<script setup>
import '../assets/IndexView.css'
import {ref} from'vue'

import ImgItem from '../components/ImgItem.vue';


const images=[]
for (let index = 0; index < 5; index++) {
  images.push('/src/assets/images/banner/'+(index+1)+'.jpg')
}
// console.log(images);

var intervalId=setInterval(() => {
  currentIndex.value = (currentIndex.value + 1) % images.length;
}, 3000);

const currentIndex = ref(0);
function changeSlide(index) {
  clearInterval(intervalId)
  currentIndex.value = index;
}
function startChange(){
  intervalId=setInterval(() => {
  currentIndex.value = (currentIndex.value + 1) % images.length;
}, 3000);
}


const image_gallery = Array.from({length: 15}, (_, i) => 
  `/src/assets/images/gallery/${String(i + 1).padStart(2, '0')}.jpg`
);
console.log(image_gallery)
</script>