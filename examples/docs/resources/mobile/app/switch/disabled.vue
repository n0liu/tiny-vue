<template>
  <div class="switch-wrap">
    <div class="page__hd">
      <h1 class="page__title">Switch</h1>
      <p class="page__desc">Switch开关</p>
    </div>
    <div class="geot">
      <div class="sbody">
        <span class="title">禁用</span>
      </div>
      <tiny-switch v-model="value" disabled></tiny-switch>
    </div>
  </div>
</template>

<script lang="jsx">
import { Switch } from '@opentiny/vue'

export default {
  components: {
    TinySwitch: Switch
  },
  data() {
    return {
      value: true
    }
  }
}
</script>

<style scoped>
.page__hd {
  padding: 40px;
}
.page__title {
  font-weight: 400;
  font-size: 21px;
  text-align: left;
}
.page__desc {
  margin-top: 5px;
  color: #888;
  font-size: 14px;
  text-align: left;
}
.title {
  color: #333;
  font-size: 16px;
}
.switch-wrap {
  padding: 20px;
}
.sbody {
  display: flex;
  flex-direction: column;
  height: 50px;
  justify-content: space-around;
}
.geot {
  display: flex;
  height: 60px;
  width: 100%;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid #ddd;
}
</style>
