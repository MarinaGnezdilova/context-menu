<script setup lang="ts">
import Data from "../src/storage/data.json";
import ContextMenu from "./components/ContextMenu.vue";
</script>

<template>
  <main>
    <div class="content-container">
      <div
        v-for="(item, index) in Data.blocks"
        :key="index"
        class="content-container__block"
      >
        <ContextMenu :id="item.id">
          <component
            v-html="item.data.text"
            :is="item.type === 'header' ? `h${item.data.level + 1}` : 'p'"
          >
          </component>
        </ContextMenu>
      </div>
    </div>
  </main>
</template>

<style>
.content-container {
  padding: 30px 30px;
}
.content-container__block {
  width: fit-content;
  position: relative;
}

.content-container__block h2 {
  margin-bottom: 20px;
  padding-right: 25px;
}

.content-container__block h3 {
  margin-bottom: 20px;
  padding-right: 25px;
}

.content-container__block h4 {
  margin-bottom: 20px;
  padding-right: 25px;
}

.content-container__block p {
  margin-bottom: 15px;
  padding-right: 20px;
}
</style>
