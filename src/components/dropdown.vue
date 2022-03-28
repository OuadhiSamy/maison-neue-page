<template>
  <div class="dropdown">
    <div class="dropdown__header" @click="showOptions = !showOptions">
      <span>{{ currentStyle }}</span
      ><svg
        :style="[showOptions ? {transform: 'rotate(0)'} : {transform: 'rotate(180deg)'}]"
        width="15"
        height="11"
        viewBox="0 0 15 11"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path d="M0 11L7.5 0L15 11H0Z" fill="black" />
      </svg>
    </div>
    <div v-if="showOptions" class="dropdown__content">
      <template v-for="styleList in list">
        <div
          v-for="style in styleList.content"
          :key="style"
          class="dropdown__item"
          :style="{
            fontFamily: styleList.title,
            fontWeight: style.weight,
            fontStyle: style.style,
          }"
          @click="
            selectStyle({
              fontName: style.name,
              fontFamily: styleList.title,
              fontWeight: style.weight,
              fontStyle: style.style,
            })
          "
        >
          {{ style.name }}
        </div>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  component: "dropdown",
  props: {
    list: Array,
    default: [],
  },
  data: () => {
    return {
      currentStyle: "Medium",
      showOptions: false,
    };
  },
  methods: {
    selectStyle(payload) {
      this.currentStyle = payload.fontName;
      this.$emit("onStyleChange", payload);
      this.showOptions = false;
    },
  },
};
</script>

<style lang="scss">
.dropdown {
  z-index: 1;
  position: relative;
  &__header {
    display: flex;
    justify-content: space-between;
    width: 250px;
    gap: 12px;
    cursor: pointer;
    padding: 8px 0 8px 8px;

    svg {
        transform: rotate(180deg);
        transition: 0.3s ease;
    }
  }

  &__content {
    position: absolute;
    top: 40px;
    width: 250px;
    height: 200px;
    overflow-y: scroll;
    background: white;
  }

  &__item {
    padding: 8px;
    cursor: pointer;

    &:hover {
      color: white;
      background: black;
    }
  }
}
</style>
