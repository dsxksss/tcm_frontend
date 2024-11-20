<template>
	<div class="wedraw">
		<iframe
			ref="wedrawIframe"
			class="m-0 h-full w-full p-0"
			frameborder="0"
			src="/wedraw/index.html"
			@load="onIframeLoad"
		></iframe>
	</div>
</template>

<script setup>
import { ref } from 'vue'

const wedrawIframe = ref(null)

const onIframeLoad = () => {
	if (wedrawIframe.value) {
		wedrawIframe.value.style.height = '100vh'
	}
}
</script>

<style>
.wedraw {
	width: 100%;
	height: calc(100vh - 82px);
}
</style>
