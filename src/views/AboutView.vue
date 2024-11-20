<script lang="ts">
import { ref, h, reactive } from 'vue'
const count = ref(1)
const obj = reactive({ count })

// ref 会被解包
console.log(obj.count === count.value) // true

// 会更新 `obj.count`
count.value++
console.log(count.value) // 2
console.log(obj.count) // 2

// 也会更新 `count` ref
obj.count++
console.log(obj.count) // 3
console.log(count.value) // 3

export default {
  props: {
    msg: {
      type: String,
      default: 'About Page',
    },
  },
  setup(props) {
    const count = ref(3)

    // 返回渲染函数
    return () => h('div', props.msg + count.value)
    // return () => 'hello world!'
  },
}
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
