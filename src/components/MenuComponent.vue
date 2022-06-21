<template>
  <n-layout has-sider>
    <n-layout-sider class="slide"
      bordered
      collapse-mode="width"
      :collapsed-width="64"
      :width="240"
      :collapsed="collapsed"
      show-trigger
      @collapse="collapsed = true"
      @expand="collapsed = false"
    >
      <n-menu
        :collapsed="collapsed"
        :collapsed-width="64"
        :collapsed-icon-size="22"
        :options="menuOptions"
        :render-label="renderMenuLabel"
        :render-icon="renderMenuIcon"
      />
    </n-layout-sider>
    <n-layout class="content">
      <PresentationComponent id="presentation" />
      <ProjectsComponent />
      <PathComponent />
    </n-layout>
  </n-layout>
</template>

<script lang="ts">
import { defineComponent, h , ref } from 'vue'
import { NIcon, NLayout, NLayoutSider, NMenu } from 'naive-ui'
import type { MenuOption } from 'naive-ui'
import { BodyOutline, Analytics, SchoolOutline, DocumentOutline } from '@vicons/ionicons5'
import PresentationComponent from "./PresentationComponent.vue";
import ProjectsComponent from "./ProjectsComponent.vue";
import PathComponent from "./PathComponent.vue";

const menuOptions: MenuOption[] = [
  {
    label: 'Presentation',
    key: 'presentation',
    href: '#presentation',
  },
  {
    label: 'Mon Parcours',
    key: 'path',
  },
  {
    label: 'Mes projets',
    key: 'projects',
  },
  {
    label: 'Mon CV',
    key: 'cv',
  }
]

export default defineComponent({
	components: {
		NLayout, 
    NLayoutSider, 
    NMenu,
    PresentationComponent,
    ProjectsComponent,
    PathComponent,
	},
  setup () {
    return {
      menuOptions,
      collapsed: ref(true),
      renderMenuLabel (option: MenuOption) {
        if ('href' in option) {
          return h('a', { href: option.href, target: '_blank' }, [
            option.label as string
          ])
        }
        return option.label as string
      },
      renderMenuIcon (option: MenuOption) {
        // return falsy, don't render icon placeholder
        if (option.key === 'cv') return h(NIcon, null, { default: () => h(DocumentOutline) })
        if (option.key === 'projects') return h(NIcon, null, { default: () => h(Analytics) })
        if (option.key === 'path') return h(NIcon, null, { default: () => h(SchoolOutline) })
        return h(NIcon, null, { default: () => h(BodyOutline) })
      },
    }
  }
});
</script>

<style scoped>
.slide {
  position: fixed;
  height: 100vh;
}
.content {
  margin-left: 65px;
}
</style>