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
        <PathComponent id="path" />
        <ProjectsComponent id="project" />
        <CvComponent id="cv" />
      </n-layout>
    </n-layout>
  </div>
  <div class="tiny">
    <n-layout>
      <PresentationComponent />
      <PathComponent />
      <ProjectsComponent />
      <CvComponent />
    </n-layout>
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
          href: '#project',
        },
        'Mes projets'
      ),
    key: "project",
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

    function goto(ref : Ref<any>){
      if(ref.value != null){
        var top = ref.value.offsetTop;
        window.scrollTo(0, top);
      }
    }

    return {
      menuOptions,
      collapsed: ref(true),
      renderMenuIcon(option: MenuOption) {
        if (option.key === "cv")
          return h(NIcon, null, { default: () => h(DocumentOutline) });
        if (option.key === "project")
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
.content {
  margin-left: 65px;
}

@media screen and (min-width: 721px) {
  .slide {
    position: fixed;
    height: 100vh;
  }
  .items-menu {
    transform: translateY(40vh);
  }
  .tiny {
    display: none;
  }

  .content {
    background: linear-gradient(-45deg, #000000, #222222, #444444, #666666);
    background-size: 400% 400%;
    background-attachment: fixed;
    animation: gradient 30s ease infinite;
  }

  @keyframes gradient {
    0% {
      background-position: 0% 50%;
    }
    50% {
      background-position: 100% 50%;
    }
    100% {
      background-position: 0% 50%;
    }
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
