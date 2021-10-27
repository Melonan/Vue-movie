<template>
  <div class="home">

      <div class="feature-card">

        <router-link to="/movie/asuka">
          <img src="https://gss3.bdstatic.com/84oSdTum2Q5BphGlnYG/timg?wapp&quality=80&size=b150_150&subsize=20480&cut_x=0&cut_w=0&cut_y=0&cut_h=0&sec=1369815402&srctrace&di=d7a0b45676a92f73b610fd9c2ef181fa&wh_rate=null&src=http%3A%2F%2Ftiebapic.baidu.com%2Fforum%2Fpic%2Fitem%2F4610b912c8fcc3ce7b4607548545d688d53f20d7.jpg" 
          alt="Asuka" class="featured-img">
          <div class="detail">
            <h3>Asuka</h3>
            <p>Asuka , wo zhen de hao xi huan ni a ! wei le ni wo yao ...</p>
          </div>
        </router-link>

      </div>

      <form @submit.prevent="" class="search-box">
        <input type="text" placeholder="What are you looking for" />
        <input type="submit" value="Search">
      </form>

      <div class="movies-list">MOVIES</div>
  </div>
</template>

<script>

import { ref } from 'vue'
// import env from '@/env.js'
export default {
  setup(){
    const search = ref("");
    const movies = ref([]);

    const SearchMovies = () => {
      if(search.value != "")
      {
        fetch(`http://www.omdbapi.com/?apikey=17503e95&s=${search.value}`)
          .then(response => response.json())
          .then(data => {
            // console.log(`${env.apikey}`)
            console.log(data);
          });
      }
    }

    return {
      search,
      movies,
      SearchMovies
    }
  }

}
</script>


<style lang="scss">
.home {
  .feature-card{

    // 生成相对定位的元素，相对于其正常位置进行定位。
    // 因此，"left:20" 会向元素的 LEFT 位置添加 20 像素。

    position: relative;

    .featured-img{
      display: flex;
      width: 100%;
      height: 300px;
      // object-fit 属性指定元素的内容应该如何去适应指定容器的高度与宽度。
      // fill	默认，不保证保持原有的比例，内容拉伸填充整个内容容器。
      // contain	保持原有尺寸比例。内容被缩放。
      // cover	保持原有尺寸比例。但部分内容可能被剪切。
      object-fit: cover;

      position: relative;

      // z-index 属性指定一个元素的堆叠顺序。

      // 拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面。
      z-index: 0;
    }

    .detail{
      // 此处的absolute是相对于父模块, 也就是feature-card的absolute
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      background-color: rgba($color: #000000, $alpha: 0.6);
      padding:16px;
      z-index: 1;

      h3{
        color: #fff;
        margin-bottom: 16px;
      }
      
      p{
        color: white;
      }
    }
  }

  .search-box{
    // 弹性盒子布局
    // 弹性盒子容器中的六个布局
    // flex-direction
    // flex-wrap
    // flex-flow
    // justify-content : 弹性盒子中items在主轴上的对齐方式
    // align-items  : items在交叉轴上如何对齐
    // align-content


    display: flex;
    flex-direction: column;
    justify-content: center;
    
    align-items: center;
    padding: 16px;
    

    input{
      display: block;

      // appearance :展现形式
      // normal	正常呈现元素
      // icon	作为一个小图片的呈现元素
      // window	作为一个视口呈现元素
      // button	作为一个按钮，呈现元素
      // menu	作为一个用户选项设定呈现元素选择
      // field	作为一个输入字段呈现元素
      appearance: none;
      border:none;
      outline: none;
      background: none;

      &[type="text"]{
        width: 100%;
        color: #fff;
        background-color: #496583;
        border-radius: 0px 5px;
        font-size: 20px;
        padding: 10px 16px;
        margin-bottom: 15px;
        transition: 0.4s;

        // 父选择器 后面给俩冒号: 选择他的属性的样式
        &::placeholder{
          color: #f3f3f3;
        }
        //  跟一个冒号: 选择它跟着的方法的样式
        &:focus{
          box-shadow: 3px 3px 6px rgba($color: #000000, $alpha: 0.25);
        }
      }

      &[type="submit"]{
        width: 100%;
        max-width: 300px;
        background-color: #42B883;
        padding: 16px;
        border-radius: 8px;
        color: #fff;
        font-size: 20px;
        // 将文字转化成大写
        text-transform: uppercase;

        transition: 0.4s;

        &:active{
          background-color: #3B8070;
        }

      }
    }

  }
}
</style>