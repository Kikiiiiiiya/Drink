<template>
  <div>
    <swiper
      :indicator-dots="indicatorDots"
      :autoplay="autoplay"
      :interval="interval"
      :duration="duration"
    >
      <block v-for="img in imgUrls" :key="img">
        <swiper-item>
          <image :src="img" style="width:100%" />
        </swiper-item>
      </block>
    </swiper>
    <i-grid i-class="no-border">
    <i-grid-item @click="goType(grid)" v-for="grid in grids" :key="grid" i-class="no-border">
        <i-grid-icon>
            <image :src="grid.image" />
        </i-grid-icon>
        <i-grid-label>{{grid.title}}</i-grid-label>
    </i-grid-item>
  </i-grid>
  <i-panel :title="title_name">
    <view style="padding: 15px;">
      <i-card v-for="item in top" :key="item" i-class="split" :extra="item.name" :thumb="item.image">
          <view slot="content">{{item.remark}}</view>
          <view slot="footer">{{item.address}}</view>
      </i-card>
    </view>
  </i-panel>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title_name: "热门店铺",
      grids: [
        {title:"饮料",image:"/static/images/1.jpg"},
        {title:"牛奶",image:"/static/images/2.jpg"},
        {title:"咖啡",image:"/static/images/3.jpg"},
        {title:"茶",image:"/static/images/4.jpg"}
      ],
      top: [
        {name:"百事",address:"徐东大街梨园小路",image:"http://img.zcool.cn/community/0174c2554358260000019ae9885e6d.jpg@1280w_1l_2o_100sh.png",remark:"百事，新一代的选择"},
        {name:"旺仔牛奶",address:"暂无实体店，敬请期待",image:"https://graph.baidu.com/resource/1215b70fb72bac5b6e5cb01578328800.jpg",remark:"在看我？在看我？还在看我？再看，我就把你喝掉！"},
        {name:"星巴克",address:"和平大道730号村福星惠誉水岸国际三号楼一层",image:"https://graph.baidu.com/thumb/v2/120462370,707526853.jpg",remark:"认真对待每一位顾客，一次只烹调顾客那一杯咖啡"},
        {name:"奈雪的茶",address:"徐东大街120号群星城1F层",image:"http://img.mp.itc.cn/upload/20170620/7bc26b2c66f0499f97392cf644255543_th.jpg",remark:"高山云雾出好茶，明前绿茶，叶子嫩的可以直接吃"}
      ],
      imgUrls: [
        'https://graph.baidu.com/resource/12125069a2e75995348a701578328977.jpg',
        'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=4184875832,632365737&fm=26&gp=0.jpg',
        'https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=624279544,4142658441&fm=26&gp=0.jpg'
      ],
      indicatorDots: false,
      autoplay: false,
      interval: 5000,
      duration: 1000
    }
  },

  methods: {
    goType(type){
      console.log(type)
      let url = '../list/main?type=' + type.title
      mpvue.navigateTo({ url })
    }
  },

  created () {
  }
}
</script>

<style scoped>
div >>> .no-border {
  border-width: 0pt;
}
div >>> .split {
  margin-bottom: 10pt;
}
</style>
