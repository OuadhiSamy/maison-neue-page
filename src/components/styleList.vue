<template>
  <div class="style-list">
    <h3 class="style-list__title">
      {{ list.title }}
    </h3>
    <span
      v-for="style in list.content"
      :key="style"
      class="style-list__item"
      :style="{
        fontFamily: list.title,
        fontWeight: style.weight,
        fontStyle: style.style,
      }"
    >
      {{ style.name }}
    </span>
  </div>
</template>

<script>
export default {
  component: "style-list",
  props: {
    list: Object,
    default: {},
  },
};
</script>

<style lang="scss">
.style-list {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  &__title {
    font-size: 16px;
    margin-bottom: 24px;
  }

  &__item {
    display: block;
    font-size: 22px;
    margin-bottom: 4px;
    cursor: pointer;
    position: relative;

    &::after {
      content: "Add to cart";
      font-family: "Maison Mono";
      font-weight: bold;
      font-size: 14px;
      position: absolute;
      left: 100%;
      bottom: 0;
      width: 200px;
      opacity: 0;
      transition: 0.2s ease;
    }

    &:hover {
      &::after {
        opacity: 1;
        transform: translateX(12px);
      }
    }
  }
}
</style>
