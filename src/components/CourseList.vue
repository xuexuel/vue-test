<template>
  <div>
    <!-- 列表渲染 -->
    <p v-if="courses.length == 0">没有任何课程信息</p>
    <!-- <div v-for="c in courses" :key="c.name" 
                    :class="{ active:selectedCourse === c}" @click="selectedCourse = c">
                        {{ c }}
                    </div> -->
    <div class="course-list" v-else>
      <div
        v-for="c in courses"
        :key="c.name"
        :style="{
          backgroundColor: selectedCourse === c ? '#ddd' : 'transparent',
        }"
        @click="selectedCourse = c"
      >
        {{ c.name }}-{{ c.price | currency("$") }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    courses: {
      type: Array,
      default: function(){
          return []
      },
    },
  },
  data() {
    return {
      selectedCourse: "",
    };
  },

  filters: {
    currency(value, symbol = "￥") {
      return symbol + value;
    },
  },
};
</script>

<style scoped>
.active {
  background-color: #ddd;
}
</style>
