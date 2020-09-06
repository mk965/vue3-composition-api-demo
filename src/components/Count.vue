<!--
 * @Author: Mencre
 * @LastEditors: Mencre
 * @email: mencre@163.com
 * @Date: 2020-09-06 17:04:55
 * @LastEditTime: 2020-09-06 17:26:04
 * @Description: Count.vue
-->
<template>
	<div class="count">
		<h1>Count is: {{ state.count }}, double is: {{ state.double }}</h1>
		<button @click="increment">Click Me</button>
	</div>
</template>

<script>
import { reactive, computed } from "vue";

export default {
	setup() {
		const state = reactive({
			count: 0,
			double: computed(() => state.count * 2),
		});
		const increment = () => state.count++;
		return {
			state,
			increment,
		};
	},
};
</script>
