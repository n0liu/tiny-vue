<template>
  <tiny-dropdown @visible-change="visibleChange">
    <span>默认插槽</span>

    <template #dropdown>
      <tiny-dropdown-menu>
        <tiny-dropdown-item>黄金糕</tiny-dropdown-item>
        <tiny-dropdown-item>狮子头</tiny-dropdown-item>
        <tiny-dropdown-item>螺蛳粉</tiny-dropdown-item>
        <tiny-dropdown-item disabled>双皮奶</tiny-dropdown-item>
        <tiny-dropdown-item divided>蚵仔煎</tiny-dropdown-item>
      </tiny-dropdown-menu>
    </template>
  </tiny-dropdown>
</template>

<script>
import { iconChevronDown, iconChevronUp } from '@opentiny/vue-icon'
import { Dropdown, DropdownMenu, DropdownItem } from '@opentiny/vue'

export default {
  components: {
    TinyDropdown: Dropdown,
    TinyDropdownMenu: DropdownMenu,
    TinyDropdownItem: DropdownItem,
    IconChevronDown: iconChevronDown(),
    IconChevronUp: iconChevronUp()
  },
  data() {
    return {
      visible: false
    }
  },
  methods: {
    visibleChange(status) {
      this.visible = status
    }
  }
}
</script>
