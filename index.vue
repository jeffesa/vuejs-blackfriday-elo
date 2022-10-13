<template>
  <main class="black-friday is-relative">
    <div class="container">
      <ResponsiveImage :sources="content.body.general.bgTop.src" :alt="content.body.general.bgTop.alt" class="bg top" />
      <ResponsiveImage :sources="content.body.general.bgBottom.src" :alt="content.body.general.bgTop.alt" class="bg bottom" />
      
      <Hero :content="content.body.hero" />

      <BannerContrate id="receber-oferta" :content="content.body.bannerContrate" class="p-t-48 m-b-64 signup" />

      <div class="separator is-flex is-relative p-y-12">
        <LazyImage class="icon-image" :srcset="content.body.general.iconSeparator.src" alt="" />
      </div>

      <Products :content="content.body.products" />

      <div class="separator is-flex is-relative p-b-0 p-t-32">
        <LazyImage class="icon-image" :srcset="content.body.general.iconSeparator.src" alt="" />
      </div>

      <Business :content="content.body.business" />

      <div class="separator is-flex is-relative p-b-0 p-t-32">
        <LazyImage class="icon-image" :srcset="content.body.general.iconSeparator.src" alt="" />
      </div>

      <Sales :content="content.body.sales" />

      <!-- <div class="separator is-flex is-relative p-b-0 p-t-32">
        <LazyImage class="icon-image" :srcset="content.body.general.iconSeparator.src" alt="" />
      </div>

      <DataTechnology :content="content.body.dataTechnology" /> -->

      <div class="logo-black-friday is-relative is-flex p-y-96">
        <LazyImage :srcset="content.body.general.logo" alt="" class="" />
      </div>
    </div>
  </main>
</template>

<script>
import ResponsiveImage from '~/components/shared/ResponsiveImage'
import Hero from '~/partials/BlackFriday2021/Hero'
import Products from '~/partials/BlackFriday2021/Products'
import Business from '~/partials/BlackFriday2021/Business'
import Sales from '~/partials/BlackFriday2021/Sales'
import DataTechnology from '~/partials/BlackFriday2021/DataTechnology'
import BannerContrate from '~/partials/shared/Contrate/Banner'

import { jsonLoader } from '~/utils/jsonLoader.js'

const route = '/black-friday'

export default {
  head () {
    return this.$createHeadFunction(this.content.meta, this.$store.state.headerFooterContent.header.favicon, this.$route.path, JSON.stringify(this.content.dataLayer), this.content.jsonLd);
  },

  components: {
    ResponsiveImage,
    Hero,
    Products,
    Business,
    Sales,
    BannerContrate,
    // DataTechnology
  },

  async asyncData({}) {
    return jsonLoader(route) 
  },

  data(){
    return{}
  }
}
</script>

<style lang="scss" scoped>
@import "~assets/css/abstract/index";

.black-friday {
  background: #050a25;
  overflow: hidden;

  .bg{
    position: absolute;
    display: block;
    left: 0;
    z-index: 0;

    &.top{
      top: 0;
    }

    &.bottom{
      bottom: -306px;
    }
  }

  .signup {
    justify-content: center;
  }

  .separator {
    z-index: 1;
    justify-content: center;

    @include until($desktop) {
      padding-bottom: 56px !important;
    }
  }

  /deep/ {
    .bg {
      &.responsive-image {
        width: 100%;
    
        img {
          width: 100%;
        }
      }
    }

    .icon-number {
      height: 82px;
    }

    .icon-image {
      @include until($desktop) {
        height: 85px;
      }
    }
  }

  .logo-black-friday {
    z-index: 1;
    justify-content: center;
  }
}
</style>
