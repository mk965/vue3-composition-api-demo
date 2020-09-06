<!--
 * @Author: Mencre
 * @LastEditors: Mencre
 * @email: mencre@163.com
 * @Date: 2020-09-06 17:26:59
 * @LastEditTime: 2020-09-06 17:31:37
 * @Description: Modify here please
-->
<template>
	<div style="margin-top: 20px;">
		<div v-if="api_status === 'FETCHING'">Fetching</div>
		<div v-else-if="api_status === 'FETCHING_ERROR'">Error</div>
		<div v-else-if="api_status === 'FETCHING_SUCCESS'">
			<img
				:src="dogImage"
				style="display: block; max-width: 500px; height: auto; margin: 0 auto;"
			/>
		</div>
		<div v-else>Oops, no dog found</div>
		<button style="margin-top: 20px;" @click.prevent="fetchDog">
			Fetch dog
		</button>
	</div>
</template>

<script>
import { reactive, toRefs } from "vue";
const useApi = (url, options = {}) => {
	const state = reactive({
		data: null,
		api_status: "",
	});

	const initFetch = async () => {
		try {
			// 更改 API 状态
			state.api_status = "FETCHING";
			// 发送请求
			const response = await fetch(url);
			// 格式化返回结果
			const data = await response.json();
			state.data = data.message;
			// 修改 API 状态
			state.api_status = "FETCHING_SUCCESS";
		} catch (error) {
			// 处理错误情况
			state.api_status = "FETCHING_ERROR";
		}
	};
	// 判断有没有 fetchImmediately 属性，并且不为空
	if (
		Object.prototype.hasOwnProperty.call(options, "fetchImmediately") &&
		options.fetchImmediately
	) {
		initFetch();
	}

	return {
		...toRefs(state),
		initFetch,
	};
};
export default {
	setup() {
		const { data, api_status, initFetch } = useApi(
			"https://dog.ceo/api/breeds/image/random",
			{
				fetchImmediately: true,
			}
		);

		return {
			dogImage: data,
			api_status,
			fetchDog: initFetch,
		};
	},
};
</script>

<style lang="stylus" scoped></style>
