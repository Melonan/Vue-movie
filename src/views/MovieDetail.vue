<template>
  <div class="movie-detail">
      <!-- 可以在这里直接用setup里面的变量 -->
      <h2>{{movie.Title}}</h2>
      <p>{{movie.Year}}</p>

      <img :src="movie.Poster" alt="Movie Poster" class="featured-img">

      <p>{{movie.Plot}}</p>
      <p class="movie-release">{{movie.Released}}</p>
  </div>
</template>

<script>

// setup实际上就是create() 生命周期钩子函数 在这个时候还没有data对象 ,
// 想要使用变量的话就不得不自己定义, 想要变成响应式就不得不使用ref
// ref 将括号内的东西变成响应式的, 
import { ref, onBeforeMount } from 'vue';
import { useRoute } from 'vue-router'
import env from '@/env.js'
export default {
    setup()
    {
        const movie = ref({});
        const route = useRoute();


        onBeforeMount(()=>{
            // 这里必须使用useRoute获取route对象
            fetch(`http://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`)
            .then(response => response.json())
            .then(data => {
                console.log(data);
                movie.value=data;
            }) 
        })

        return {
            movie,
        }
    }
}
</script>

<style lang="scss">
    .movie-detail{
        display: flex;
        // position: relative;
        flex-direction: column;
        // justify-items: center;
        align-items: center;
        // align-content: center;
        padding: 8px 16px;
        width: 100%;
        color: rgb(23, 160, 223);

        h2{
            color: #fff;
            font-family: '';
            font-size: 28px;
            font-weight: 500;
            margin-bottom: 16px;
        }

        .featured-img{
            position: relative;
            display: block;
            max-width: 300px;
            margin-top: 10px;
            margin-bottom: 20px;
        }

        p{
            // color: #fff;
            font-size: 18px;
            font-weight: 200;
            line-height: 1.4;

            
        }
        .movie-release{
            color: #0c040431;
            font-size: 20px;
            font-weight: 700;
        }

    }
</style>