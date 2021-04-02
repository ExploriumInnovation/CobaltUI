<template>
  <div class="dropdown">
    <div class="dropdown-field">
      <div class="dropdown-t">
        <slot name="selectedItem"></slot>
      </div>
      <div class="dropdown-label"></div>
    </div>
    <div class="dropdown-items">
      <div class="dropdown-item" v-for="item in dropdownItems" :key="item.key">
        <slot name="dropdownItem"></slot>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Dropdown extends Vue {
  dropdownItems = [];
  dropdownCurrent = 0;
  @Prop() private msg!: string;
  @Prop({ default: () => [] }) private items: object[];
  @Prop({ default: 0 }) private current!: number;

  created() {
    this.dropdownItems = [...this.items];
    this.dropdownCurrent = this.current;
  }
}
</script>


<style scoped lang="scss">
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";
</style>
