<script setup lang="ts">
defineProps<{
  id: string;
}>();

const copyId = (id: string) => {
  navigator.clipboard.writeText(id).then(
    () => {},
    (err) => {
      console.error("Произошла ошибка при копировании текста: ", err);
    }
  );
};
</script>

<template>
  <div class="dropdown context-menu">
    <button
      class="btn dropdown-toggle context-menu__button"
      type="button"
      data-bs-toggle="dropdown"
      aria-expanded="false"
    >
      <img src="/images/icon-copy.svg" class="context-menu__image" />
    </button>

    <ul class="dropdown-menu context-menu__menu">
      <li class="dropdown-item context-menu__item" @click="copyId(id)">
        Скопировать ссылку
      </li>
    </ul>
    <slot />
  </div>
</template>

<style>
.context-menu__button {
  display: flex;
  opacity: 0;
  justify-content: center;
  align-content: center;
  border: none;
  background-color: transparent;
  border-radius: 5px;
  position: sticky;
  top: 20px;
  left: 100%;
  transition: all 0.3s ease;
}

.content-container__block:hover .context-menu__button {
  opacity: 1;
}

.content-container__block .btn {
  padding: 0;
}


.content-container__block:hover {
  background-color: #ffffff;
}

.context-menu__image {
  position: absolute;
  width: 16px;
  height: 16px;
}

.dropdown-toggle::after {
  display: none;
}

.context-menu__item {
  font-size: 12px;
}

.context-menu__menu {
  padding: 3px;
  inset: 10px auto auto 10px;
}

.context-menu__item:hover {
  background-color: #f0f0f0;
}

.context-menu__menu:hover {
  background-color: #f0f0f0;
}
</style>
