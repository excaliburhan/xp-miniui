<template>
  <div class="mnui-list" :class="className">
    <div class="mnui-listItem" v-for="(item, index) in data" :key="index">
      <a class="mnui-listItem__link" v-if="item.link" :href="item.link">
        <div class="mnui-listItem__wrap">
          <img class="mnui-listItem__icon" v-if="item.icon" :src="item.icon">
          <span class="mnui-listItem__title" v-if="item.title">{{item.title}}</span>
          <span class="mnui-listItem__desc" v-if="item.desc">{{item.desc}}</span>
          <div class="mnui-listItem__arrow" v-if="item.link"></div>
        </div>
      </a>
      <div v-else class="mnui-listItem__wrap" @click="onClick(item)">
        <img class="mnui-listItem__icon" v-if="item.icon" :src="item.icon">
        <span class="mnui-listItem__title" v-if="item.title">{{item.title}}</span>
        <span class="mnui-listItem__desc" v-if="item.desc">{{item.desc}}</span>
        <div class="mnui-listItem__arrow" v-if="item.arrow"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'list',
  props: {
    className: {
      type: String,
      default: ''
    },
    data: {
      type: Array,
      default: () => {
        return []
      }
    }
  },

  methods: {
    onClick(item) {
      this.$emit('click', item)
    }
  }
}
</script>

<style scoped>
.mnui-list {
  margin-top: 20px;
  width: 100%;
  background: #fff;
}
.mnui-listItem {
  border-top: 1px solid rgba(0, 0, 0, 0.1);
}
.mnui-listItem:first-child {
  border: none;
}
.mnui-listItem {
  box-sizing: border-box;
  /* width: calc(100% - 32px); */
  margin-left: 32px;
  padding-right: 32px;
}
.mnui-listItem__link {
  width: 100%;
}
.mnui-listItem__wrap {
  box-sizing: border-box;
  display: flex;
  align-items: center;
  width: 100%;
  height: 92px;
}
.mnui-listItem__icon {
  width: 36px;
  height: 36px;
  margin-right: 16px;
}
.mnui-listItem__title {
  flex: 1;
  color: #333;
}
.mnui-listItem__desc {
  min-width: 112px;
  text-align: right;
  color: #333;
}
.mnui-listItem__arrow {
  width: 15px;
  height: 15px;
  border-top: 3px solid #666;
  border-right: 3px solid #666;
  transform: rotate(45deg);
}
</style>
