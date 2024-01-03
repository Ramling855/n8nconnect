<template>
	<img :src="logoPath" :class="$style.img" alt="n8n.io" />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { mapStores } from 'pinia';
import { useRootStore } from '@/stores/n8nRoot.store';
import { useUIStore } from '@/stores/ui.store';

export default defineComponent({
	computed: {
		...mapStores(useRootStore, useUIStore),
		basePath(): string {
			return this.rootStore.baseUrl;
		},
		isDarkMode() {
            return this.uiStore.appliedTheme === 'dark';
         },

		 
      logoPath() {
      const baseLogoPath = this.basePath;

           return this.isDarkMode
          ? baseLogoPath + 'logo-dark.svg'
          : baseLogoPath + 'logo-light.svg';
      
    },

	},
});
</script>

<style lang="scss" module>
.img {
	height: 32px;
}
</style>