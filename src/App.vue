<template>
  {{ obj.list }}
  {{ obj.list2 }}
  <el-button @click="add">add</el-button>
  <el-button @click="add1">add</el-button>
</template>

<script setup lang="ts">
import { reactive, ref, Ref, watch, watchEffect } from "vue";

let obj = reactive({
  list: [123, 123, 1],
  list2: [1, 2, 3, 3],
});

let msg1: Ref<string> = ref("");
let msg2: Ref<string> = ref("");

const stop = watchEffect((oninvalidate) => {
  oninvalidate(() => {
  });

  console.log("msg1", msg1.value);
  console.log("msg2", msg2.value);
},{
    flush:"post",
    onTrigger () {
      console.log(12321312)
    }
});

watch(
  () => obj.list,
  (newVal, oldVal) => {
    console.log(newVal);
  }
);

const add = () => {
  msg1.value = "123";
};
const add1 = () => {
  msg1.value = "321";
};
</script>
