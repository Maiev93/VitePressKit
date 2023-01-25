<template>
  <a
    v-if="link !== ''"
    class="base-btn"
    :class="btnClass"
    :href="link"
    target="_blank"
  >
    <slot />
  </a>
  <button
    v-else
    class="base-btn"
    :class="btnClass"
    :type="isSubmit ? 'submit' : 'button'"
    @click="$emit('click', $event)"
  >
    {{ text }}
    <span
      v-if="$slots.left"
      class="icon icon-btn_left"
    >
      <slot name="left" />
    </span>
    <slot />
    <span
      v-if="$slots.right"
      class="icon icon-btn_right"
    >
      <slot name="right" />
    </span>
  </button>
</template>
<script>
export default {
  props: {
    link: {
      type: String,
      default: '',
    },
    isSubmit: {
      type: Boolean,
      default: true,
    },
    disabled: {
      type: [Boolean, String],
      default: false,
    },
    mode: {
      type: String,
      default: '',
    },
    text: {
      type: String,
      default: '',
    },
    padding: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    btnClass() {
      const { mode, disabled } = this;
      return [
        { 'base-btn_disabled': disabled },
        { 'base-btn_light': mode === 'light' },
        { 'base-btn_grey': mode === 'grey' },
        { 'base-btn_black': mode === 'black' },
        { 'base-btn_padding': this.padding }
      ];
    },
  },
};
</script>
<style lang="scss" scoped>
.icon {
  &-btn {
    &_left {
      padding-right: 5px;
    }
    &_right {
      padding-left: 5px;
    }
  }
}
.base-btn {
  user-select: none;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 46px;
  color: #ffffff;
  font-family: 'Inter', sans-serif;
  font-style: normal;
  font-weight: normal;
  font-size: 16px;
  line-height: 130%;
  text-align: center;
  transition: .3s;
  background: blue;
  border-radius: 6px;
  &:hover {
    background: #103D7C;
  }
  &_padding {
    padding: 0 10px;
  }
  &_black {
    background: black;
    color: white;
    &:hover {
      background: gray;
    }
  }
  &_grey {
    background-color: LightGray;
    &:hover {
      background: Silver;
    }
  }
  &_disabled {
    pointer-events: none;
    color: gray;
    background: LightGray;
  }
  &_light {
    background: #FFFFFF;
    color: black;
    transition: 0.5s;
    &:hover {
      background: DimGray;
    }
  }
}
</style>
