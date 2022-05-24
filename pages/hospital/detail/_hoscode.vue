<template>
  <!-- header -->
  <div class="nav-container page-component">
    <!--左侧导航 #start -->
    <div class="nav left-nav">
      <div class="nav-item ">
        <span class="v-link clickable dark" :onclick="'javascript:window.location=\'/hospital/'+hospital.hoscode+'\''">服务预约 </span>
      </div>
      <div class="nav-item selected">
        <span class="v-link selected dark" :onclick="'javascript:window.location=\'/hospital/detail/'+hospital.hoscode+'\''"> 商家详情 </span>
      </div>
      <div class="nav-item">
        <span class="v-link clickable dark" :onclick="'javascript:window.location=\'/hospital/notice/'+hospital.hoscode+'\''"> 预约须知 </span>
      </div>
      <div class="nav-item "><span
        class="v-link clickable dark"> 商家公告 </span>
      </div>
      <div class="nav-item "><span
        class="v-link clickable dark"> 查询/取消 </span>
      </div>
    </div>
    <!-- 左侧导航 #end -->

    <!-- 右侧内容 #start -->
    <div class="page-container">
      <div class="hospital-detail">
        <div class="common-header">
          <div class="title-wrapper"><span class="hospital-title">{{ hospital.hosname }}</span>
            <div v-if="hospital.param" class="icon-wrapper">
              <span class="iconfont"></span>
              {{ hospital.param.hostypeName }}
            </div>
          </div>
        </div>
        <div class="info-wrapper"><img :src="'data:image/jpeg;base64,'+hospital.logoData" :alt="hospital.hosname" style="width: 80px; height: 80px;">
          <div class="content-wrapper">
            <div></div>
            <div></div>
            <div></div>
            <div>
              <div class="icon-text-wrapper"><span class="iconfont prefix-icon"></span>
                <span class="text"><p>{{ hospital.route }}</p>
              </span><span class="iconfont right-icon"></span></div>
            </div>
          </div>
        </div>
        <div class="title mt40"> 商家介绍</div>
        <div class="detail-content mt40"><p>{{ hospital.intro }}</p></div>
      </div>
    </div>
    <!-- 右侧内容 #end -->
  </div>
  <!-- footer -->
</template>

<script>
import '~/assets/css/hospital_personal.css'
import '~/assets/css/hospital.css'

import hospitalApi from '@/api/hosp'
export default {
  data() {
    return {
      hoscode: null,
      hospital: {}
    }
  },

  created() {
    this.hoscode = this.$route.params.hoscode
    this.init()
  },

  methods: {
    init() {
      hospitalApi.show(this.hoscode).then(response => {
        this.hospital = response.data
      })

    }
  }
}
</script>
<style>
.hospital-detail .info-wrapper {
  width: 100%;
  padding-left: 0;
  padding-top: 0;
  margin-top: 0;
  flex-direction: inherit;
}

.hospital-detail .info-wrapper .text {
  font-size: 14px;

}

.hospital-detail .content-wrapper p {
  text-indent: 0;
}
</style>
