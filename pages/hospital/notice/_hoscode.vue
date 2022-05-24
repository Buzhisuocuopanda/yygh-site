<template>
  <!-- header -->
  <div class="nav-container page-component">
    <!--左侧导航 #start -->
    <div class="nav left-nav">
      <div class="nav-item ">
        <span class="v-link clickable dark" :onclick="'javascript:window.location=\'/hospital/'+hospital.hoscode+'\''">服务预约 </span>
      </div>
      <div class="nav-item ">
        <span class="v-link clickable dark" :onclick="'javascript:window.location=\'/hospital/detail/'+hospital.hoscode+'\''"> 商家详情 </span>
      </div>
      <div class="nav-item selected">
        <span class="v-link selected dark" :onclick="'javascript:window.location=\'/hospital/notice/'+hospital.hoscode+'\''"> 预约须知 </span>
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
      <div class="hospital-notice">
        <div class="content"><h2>{{ hospital.hosname }}预约须知</h2>
          <p>为方便您愉快的体验服务，请您认真阅读预约须知：</p>
          <h4 id="一、预约实名制：">一、预约实名制：</h4>
          <p>统一平台电话预约和网上预约均采取实名制注册预约，请您如实提供就诊人员的真实姓名、有效证件号（身份证、护照）、性别、手机号码、社保卡号等基本信息。</p>
          <h4 id="二、预约：">二、预约：</h4>
          <p>按照健康保健预约平台要求，预约规则如下：</p>
          <ul>
            <li>在同一自然日，同一商家，同一服务，同一服务人员，同一预约人，可以预约最多1次；</li>
            <li>在同一自然周，同一预约人，可以预约最多8个；</li>
            <li>在同一自然月，同一预约人，可以预约最多12个；</li>
            <li>在同一自然季度，同一预约人，可以预约最多24个。</li>
          </ul>
          <h4 id="三、取消预约：">三、取消预约：</h4>
          <p>已完成预约的号码，如需办理退号，至少在服务的前一工作日14:00前通过网站、微信公众号、电话等平台预约渠道进行取消预约。</p>
          <h4 id="四、爽约处理：">四、爽约处理：</h4>
          <p>如预约成功后用户未能按时到达且不办理取消预约号视为爽约，同一用户在自然年内爽约规则如下：</p>
          <ul>
            <li>累计爽约3次，自3次爽约日起，90天内不允许通过平台进行预约挂号；</li>
            <li>累计爽约6次，自6次爽约日起，180天内不允许通过平台进行预约挂号。</li>
          </ul>
        </div>

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
