<script setup lang="ts">
import { ref } from 'vue'

const x = ref(0)
const y = ref(0)
let animationFrameId: number

const updatePosition = (event: MouseEvent) => {
	x.value = event.clientX - 5
	y.value = event.clientY - 60
}

const onMouseMove = (event: MouseEvent) => {
	// 使用 requestAnimationFrame 来优化性能
	if (!animationFrameId) {
		animationFrameId = requestAnimationFrame(() => {
			updatePosition(event)
			animationFrameId = null // 重置动画帧 ID
		})
	}
}
</script>

<template>
	<div class="relative h-screen w-screen" @mousemove="onMouseMove">
		<div class="absolute">
			<div>x坐标 {{ x }}</div>
			<div>y坐标 {{ y }}</div>
		</div>
		<div
			class="cursor"
			:style="`transform: translate3d(${x}px, ${y}px, 0)`"
		></div>
	</div>
</template>

<style scoped>
.cursor {
	width: 20px; /* 自定义光标宽度 */
	height: 20px; /* 自定义光标高度 */
	background-color: red; /* 自定义光标颜色 */
	border-radius: 50%; /* 使光标为圆形 */
	position: absolute; /* 绝对定位 */
	transition: transform 0.1s ease; /* 减少过渡时间以提高响应性 */
	pointer-events: none; /* 使光标不影响鼠标事件 */
}
</style>
