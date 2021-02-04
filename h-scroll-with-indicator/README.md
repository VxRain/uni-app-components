Horizontal-Scroll-With-Indicator
---
一个带有滚动距离指示器的水平滚动组件



用法
---

1. 引入组件
  ```vue
  <script>
  import HScrollWithIndicator from "@/components/h-scroll-with-indicator.vue"
  </script>
  ```

2. 注册组件
  ```vue
<script>
import HScrollWithIndicator from "@/components/h-scroll-with-indicator.vue"
export default {
	components: {
		HScrollWithIndicator,
	},
};
</script>
  ```
3. 使用组件

  ```vue
<template>
	<div>
		<HScrollWithIndicator>
			<view class="list">
				<view class="item" v-for="(item, index) of categoryList" :key="index">
					<view class="icon"><image :src="item.icon"></image></view>
					<view class="name">{{ item.name }}</view>
				</view>
			</view>
		</HScrollWithIndicator>
	</div>
</template>

<script>
import HScrollWithIndicator from '@/components/h-scroll-with-indicator.vue';
export default {
	components: {
		HScrollWithIndicator
	}
};
</script>
  ```

  


### props

* color

  指示器颜色

* background

  指示器背景颜色