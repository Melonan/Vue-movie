<template>
  <div class="home">

      <div class="feature-card">

        <router-link to="/">
          <img src="https://gss3.bdstatic.com/84oSdTum2Q5BphGlnYG/timg?wapp&quality=80&size=b150_150&subsize=20480&cut_x=0&cut_w=0&cut_y=0&cut_h=0&sec=1369815402&srctrace&di=d7a0b45676a92f73b610fd9c2ef181fa&wh_rate=null&src=http%3A%2F%2Ftiebapic.baidu.com%2Fforum%2Fpic%2Fitem%2F4610b912c8fcc3ce7b4607548545d688d53f20d7.jpg" 
          alt="Asuka" class="featured-img">
          <div class="detail">
            <h3>Asuka</h3>
            <p>Asuka , wo zhende haoxi huanni a ! wei le ni wo yao ...</p>
          </div>
        </router-link>

      </div>


  </div>
</template>

<script>

export default {

}
</script>


<style lang="scss">
.home {
  .feature-card{
    position: relative;

    .featured-img{
      display: flex;
      width: 100%;
      height: 300px;
      object-fit: cover;

      position: relative;
      z-index: 0;
    }



  }
}
</style>