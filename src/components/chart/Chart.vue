<template>
	<div ref="chartRef" className='es-chart'></div>
</template>

<script setup>
import { onMounted, shallowRef, watch } from 'vue'
import * as echarts from 'echarts'
import { debounce } from 'lodash'

const props = defineProps({
	option: {
		type: Object,
		required: true,
		default: () => ({})
	},
	loading: Boolean
})
const chartRef = shallowRef(null)

const chart = shallowRef(null)
function init() {
	if (props.option) {
		chart.value = echarts.init(chartRef.value)
		setOption(props.option)
	}
}
function setOption(option, notMerge, lazyUpdate) {
	chart.value.setOption(option, notMerge, lazyUpdate)
}

const resize = debounce(() => {
	chart.value?.resize()
}, 500)

watch(() => props.option, () => {
	setOption(props.option)
})

// show loading
watch(() => props.loading, (val) => {
	if (!chart.value) return
	if (val) {
		chart.value.showLoading()
	} else {
		chart.value.hideLoading()
	}
})

onMounted(() => {
	init()
	window.addEventListener("resize", resize);
	resize()
})
onBeforeUnmount(() => {
	window.removeEventListener("resize", resize);
	chart.value = null;
})

defineExpose({
	chart,
	setOption,
	resize
})
</script>

<style lang='scss' scoped>
.es-chart {
	width: 100%;
	height: 100%;
}
</style>
