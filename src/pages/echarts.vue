<script setup lang="ts">
import { use } from 'echarts/core'
import { PieChart } from 'echarts/charts'
import { CanvasRenderer } from 'echarts/renderers'
import {
	TitleComponent,
	TooltipComponent,
	LegendComponent,
} from 'echarts/components'
import VChart from 'vue-echarts'
import type { EChartsOption } from 'echarts'
import { GraphChart } from 'echarts/charts'

use([
	CanvasRenderer,
	PieChart,
	TitleComponent,
	TooltipComponent,
	LegendComponent,
	GraphChart,
])

const option = ref<EChartsOption>({
	backgroundColor: '',
	title: {
		text: 'Traffic Sources',
		left: 'center',
	},
	tooltip: {
		show: true,
		formatter: (params) => {
			return `${params.data.name}: ${params.data.value}`
		},
	},
	series: [
		{
			name: '我是标题',
			type: 'graph',
			layout: 'force',
			legendHoverLink: true,
			hoverAnimation: true,
			force: {
				repulsion: 450,
				edgeLength: [150, 200],
				layoutAnimation: true,
			},
			roam: true,
			nodeScaleRatio: 0.6,
			draggable: true,
			focusNodeAdjacency: true,
			edgeSymbol: ['none', 'arrow'],
			symbolSize: 50,
			edgeSymbolSize: 10,
			itemStyle: {
				normal: {
					label: {
						show: true,
					},
				},
				emphasis: {},
			},
			lineStyle: {
				normal: {
					color: '#31354B',
					width: 1,
					type: 'solid',
					curveness: 0,
					opacity: 1,
				},
				emphasis: {},
			},
			label: {
				normal: {
					show: true,
					position: 'bottom',
					textStyle: {
						color: '#2D2F3B',
						fontStyle: 'normal',
						fontWeight: 'bolder',
						fontFamily: 'sans-serif',
						fontSize: 12,
					},
				},
				emphasis: {},
			},
			data: [
				{ name: '节点1', value: 10 },
				{ name: '节点2', value: 20 },
				{ name: '节点3', value: 30 },
				{ name: '节点4', value: 40 },
			],
			links: [
				{ source: '节点1', target: '节点2' },
				{ source: '节点2', target: '节点3' },
				{ source: '节点3', target: '节点1' },
				{ source: '节点4', target: '节点1' },
			],
		},
	],
})
</script>

<template>
	<div>
		<!-- @vue-ignore -->
		<v-chart class="chart" :option="option" autoresize />
	</div>
</template>

<style>
.chart {
	width: 100vw;
	height: calc(100vh - 82px);
}
</style>
