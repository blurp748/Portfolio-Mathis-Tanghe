<template>
  <div class="big">
    <n-layout has-sider>
      <n-layout-sider
        class="slide"
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
          class="items-menu"
          :collapsed="collapsed"
          :collapsed-width="64"
          :collapsed-icon-size="22"
          :options="menuOptions"
          :render-icon="renderMenuIcon"
        />
      </n-layout-sider>
      <n-layout class="content">
        <PresentationComponent id="presentation" />
        <ProjectsComponent id="projects" />
        <PathComponent id="path" />
        <CvComponent id="cv" />
      </n-layout>
    </n-layout>
  </div>
  <div class="tiny">
    <n-layout>
      <PresentationComponent id="presentation" />
      <ProjectsComponent />
      <PathComponent />
      <CvComponent />
    </n-layout>
    <n-menu class="menuTiny" mode="horizontal" :options="menuOptionsTiny" />
  </div>
</template>

<script lang="ts">
import { defineComponent, h, ref, type Ref } from "vue";
import { NIcon, NLayout, NLayoutSider, NMenu } from "naive-ui";
import type { MenuOption } from "naive-ui";
import {
  BodyOutline,
  Analytics,
  SchoolOutline,
  DocumentOutline,
} from "@vicons/ionicons5";
import PresentationComponent from "./PresentationComponent.vue";
import ProjectsComponent from "./ProjectsComponent.vue";
import PathComponent from "./PathComponent.vue";
import CvComponent from "./CvComponent.vue";

const menuOptions: MenuOption[] = [
  {
    label: () =>
      h(
        'a',
        {
          href: '#presentation',
        },
        'Présentation'
      ),
    key: "presentation",
  },
  {
    label: () =>
      h(
        'a',
        {
          href: '#projects',
        },
        'Mes projets'
      ),
    key: "projects",
  },
  {
    label: () =>
      h(
        'a',
        {
          href: '#path',
        },
        'Mon Parcours'
      ),
    key: "path",
  },
  {
    label: () =>
      h(
        'a',
        {
          href: '#cv',
        },
        'Mon CV'
      ),
    key: "cv",
  },
];

const menuOptionsTiny: MenuOption[] = [
  {
    key: "presentation",
    href: "#presentation",
  },
  {
    key: "path",
  },
  {
    key: "projects",
  },
  {
    key: "cv",
  },
];

export default defineComponent({
  components: {
    NLayout,
    NLayoutSider,
    NMenu,
    PresentationComponent,
    ProjectsComponent,
    PathComponent,
    CvComponent,
  },
  setup() {

    const presRef = ref(null)
    const projectRef = ref(null)
    const pathRef = ref(null)
    const cvRef = ref(null)

    function goto(ref : Ref<any>){
      if(ref.value != null){
        var top = ref.value.offsetTop;
        window.scrollTo(0, top);
      }
    }

    return {
      presRef,
      projectRef,
      pathRef,
      cvRef,
      menuOptions,
      menuOptionsTiny,
      collapsed: ref(true),
      renderMenuIcon(option: MenuOption) {
        if (option.key === "cv")
          return h(NIcon, null, { default: () => h(DocumentOutline) });
        if (option.key === "projects")
          return h(NIcon, null, { default: () => h(Analytics) });
        if (option.key === "path")
          return h(NIcon, null, { default: () => h(SchoolOutline) });
        return h(NIcon, null, { default: () => h(BodyOutline) });
      },
    };
  },
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

@media screen and (min-width: 721px) {
  .items-menu {
    transform: translateY(40vh);
  }
  .tiny {
    display: none;
  }
}

@media screen and (max-width: 720px) {
  .items-menu {
    transform: translateY(35vh);
  }
  .big {
    display: none;
  }

  .menuTiny {
    position: fixed;
  }
}
</style>
