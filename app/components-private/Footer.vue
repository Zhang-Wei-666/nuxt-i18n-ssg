<template>
  <div class="footer flex justify-center mt-6">
    <!-- 回到首页 -->
    <button :title="t('home')" @click="navigateTo('/')">
      <i-vaadin-home-o />
    </button>

    <!-- 切换语言 -->
    <el-dropdown class="c-inherit!" :title="t('toggle-language')" @command="code => setLocale(code)">
      <button>
        <i-ion-language />
      </button>

      <template #dropdown>
        <el-dropdown-menu>
          <template v-for="item in locales" :key="item.code">
            <el-dropdown-item :command="item.code" :disabled="item.code === locale">{{ item.name }}</el-dropdown-item>
          </template>
        </el-dropdown-menu>
      </template>
    </el-dropdown>

    <!-- 跳转到 Github -->
    <button :title="t('github')">
      <a href="https://github.com/Zhang-Wei-666/nuxt-i18n-ssg" target="_blank" rel="noopener noreferrer">
        <i-mdi-github />
      </a>
    </button>
  </div>
</template>

<script lang="ts" setup>
  const { t, locale, locales, setLocale } = useI18n({ useScope: 'local' });
</script>

<style lang="scss" scoped>
  .footer button {
    --uno: text-(2xl center) outline-none opacity-60 hover:text-blue-5 hover:opacity-100 bg-transparent transition-(all duration-300) mx-2;
  }
</style>

<i18n lang="yaml">
zh-CN:
  home: 首页
  toggle-dark-mode: 切换深色模式
  toggle-language: 切换语言
  github: 跳转到 Github
en-US:
  home: Home
  toggle-dark-mode: Toggle Dark Mode
  toggle-language: Toggle Language
  github: Go to Github
</i18n>
