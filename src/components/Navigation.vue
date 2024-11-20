<script setup lang="ts">
import { useI18n } from 'vue-i18n'

// Setup i18n
const { te, t } = useI18n()
</script>

<template>
	<nav
		aria-label="Site Nav"
		class="h-60px max-w-100vw flex items-center justify-center p-4"
	>
		<ul class="flex items-center gap-2 text-sm font-medium">
			<el-menu
				:default-active="`/`"
				mode="horizontal"
				:ellipsis="false"
				:router="true"
				@select="handleSelect"
			>
				<el-menu-item :key="`/`" :index="`/`">
					{{ 'Home' }}
				</el-menu-item>
				<el-menu-item :key="`browse`" index="1">
					<el-sub-menu :index="main">
						<template #title>Browse</template>
						<el-menu-item v-for="sub in subItems" :key="sub" :index="sub">
							{{ te(sub) ? t(sub) : sub }}
						</el-menu-item>
					</el-sub-menu>
				</el-menu-item>
				<el-menu-item :key="`/analyze`" :index="`/analyze`">
					{{ te('analyze') ? te('analyze') : 'Analyze' }}
				</el-menu-item>
				<el-menu-item :key="`/download`" :index="`/download`">
					{{ te('download') ? te('download') : 'Download' }}
				</el-menu-item>
				<el-menu-item :key="`/docs`" :index="`/docs`">
					{{ te('docs') ? te('docs') : 'Docs' }}
				</el-menu-item>
			</el-menu>
		</ul>
	</nav>
</template>
<style>
.el-menu--horizontal > .el-menu-item:nth-child(1) {
	margin-right: auto;
}
</style>
