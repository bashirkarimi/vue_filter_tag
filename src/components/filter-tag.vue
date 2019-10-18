<template>
  <div class="filter__tag">
    <label class="filter__tag-wrapper">
      <input
        type="radio"
        value=""
        name="showAll"
        @:click="emitToParent"
        v-model="selectedTag"
        class="filter__tag-radio"
      >
      <div class="filter__tag-btn">
        <span class="filter__tag-text">Show all</span>
        <span class="filter__tag-number">{{dataArray.length}}</span>
      </div>
    </label>
    <label v-for="(value, tag, key) in getTags" :key="key" class="filter__tag-wrapper">
      <input
        type="radio"
        :value="tag"
        :name="tag"
        v-model="selectedTag"
        @:click="emitToParent"
        class="filter__tag-radio"
      >
      <div class="filter__tag-btn">
        <span class="filter__tag-text">{{tag}}</span>
        <span class="filter__tag-number">{{value.length}}</span>
      </div>
    </label>
  </div>
</template>

<script>
import { mixins } from "../mixins/mixins";
export default {
  name: "FilterTags",
  mixins: [mixins],
  props: {
    dataArray: {
      type: Array,
      required: true
    },
    tag: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      selectedTag: ""
    };
  },
  computed: {
    emitToParent() {
      return this.$emit("childToParent", this.selectedTag);
    },
    getTags() {
      const tag = this.tag;
      return this.groupBy([...this.dataArray], tag);
    }
  },
};
</script>

<style lang='scss' >
.filter {
  &__tag {
    display: flex;
    flex-wrap: wrap;

    &-radio {
      display: none;

      &:checked {
        + .filter__tag-wrapper {
          color: black;
          border-color: black;
        }
      }
    }

    &-wrapper {
      margin-left: 8px;
      margin-bottom: 8px;
    }

    &-btn {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      padding-left: 12px;
      padding-right: 14px;
      padding-top: 4px;
      padding-bottom: 4px;
      font-size: 13px;
      color: gray;
      font-weight: 500;
      border: 1px solid gray;
      border-radius: 24px;
      cursor: pointer;
      transition: border-color 0.3s ease-in-out;
      transition: color 0.3s ease-in-out;

      &:after {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        border-radius: 24px;
        opacity: 0;
        transition: opacity 0.3s ease-in-out;
        z-index: -100;
      }

      &:hover {
        color: black;
        border-color: black;
      }

      &:hover::after {
        opacity: 1;
      }
    }

    &-number {
      margin-left: 5px;
      font-style: italic;
      opacity: .5;
    }
  }
}
</style>

