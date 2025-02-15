<template>
  <label
    :class="[
      'relative outline-0 inline-flex rounded-none cursor-pointer items-center [&:first-of-type_span]:border-l-0.5 sm:[&:first-of-type_span]:border-l [&:first-of-type_span]:rounded-l-sm [&:last-of-type_span]:rounded-r-sm',
      state.size === 'small' ? 'sm:h-6 h-10 text-xs' : 'sm:h-7 sm:leading-7 h-11 leading-[2.75rem] text-sm sm:text-xs',
      !disabled &&
        !state.radioGroup.disabled &&
        state.value === label &&
        'sm:[&:not(:first-of-type)_span]:shadow-[-1px_0_0_0_#0067D1] [&:not(:first-of-type)_span]:shadow-[-0.5px_0_0_0_#0067D1]'
    ]"
    role="radio"
    :aria-checked="state.value === label"
    :aria-disabled="state.isDisabled"
    :tabindex="state.tabIndex"
    @keydown.space.stop.prevent="keydownHandle"
  >
    <input
      ref="radio"
      class="opacity-0 outline-0 absolute -z-10"
      :value="label"
      type="radio"
      v-model="state.value"
      :name="name"
      @change="handleChange"
      :disabled="state.isDisabled"
      tabindex="-1"
      @focus="handleFocus"
      @blur="handleBlur"
    />
    <span
      :class="
        m(
          'relative sm:border-y border-y-0.5 sm:border-r border-r-0.5 border-solid inline-block leading-5 items-center min-w-[2.5rem] max-w-[4.875rem] sm:min-w-[3rem] sm:max-w-[9rem] text-center overflow-hidden text-ellipsis whitespace-nowrap py-[0.1875rem] px-3 cursor-pointer border-color-border box-border',
          state.radioGroup.disabled &&
            state.value === label &&
            'text-color-bg-1 bg-color-brand-disabled border-y-0 cursor-not-allowed border-transparent shadow-none',
          state.radioGroup.disabled &&
            state.value !== label &&
            'bg-color-bg-4 cursor-not-allowed border-color-border-disabled text-color-text-disabled',
          disabled && !state.radioGroup.disabled && 'text-color-text-disabled bg-none cursor-not-allowed',
          state.value === label &&
            !disabled &&
            !state.radioGroup.disabled &&
            'border-color-border-focus text-color-brand-focus',
          state.value !== label &&
            !disabled &&
            !state.radioGroup.disabled &&
            'text-color-text-secondary hover:text-color-brand-hover active:text-color-brand',
          state.size === 'small' ? 'sm:h-6 py-px px-2 h-[1.4375rem]' : 'sm:h-7 h-[1.6875rem]',
          state.showTips && 'sm:pr-7'
        )
      "
      @keydown.stop
    >
      <slot></slot>
      <template v-if="!slots.default"
        >{{ text || label }}
        <tiny-tooltip effect="light" :content="tipContent" placement="top" v-if="state.showTips" class="sm:block hidden"
          ><IconHelpCircle
            class="absolute right-3 top-1.5 bottom-1.5 text-sm cursor-pointer w-3.5 h-3.5 fill-color-border hover:fill-color-brand-focus" /></tiny-tooltip
      ></template>
    </span>
  </label>
</template>

<script lang="ts">
import { renderless, api } from '@opentiny/vue-renderless/radio-button/vue'
import { props, setup, defineComponent } from '@opentiny/vue-common'
import { iconHelpCircle } from '@opentiny/vue-icon'
import Tooltip from '@opentiny/vue-tooltip'

export default defineComponent({
  emits: ['change'],
  props: [...props, 'label', 'events', 'text', 'disabled', 'name', 'tipContent'],
  components: {
    TinyTooltip: Tooltip,
    IconHelpCircle: iconHelpCircle()
  },
  inheritAttrs: false,
  setup(props, context): any {
    return setup({ props, context, renderless, api })
  }
})
</script>
