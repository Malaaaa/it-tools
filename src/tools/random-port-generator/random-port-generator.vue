<template>
  <n-card>
    <div class="port">
      {{ port }}
    </div>
    <n-space justify="center">
      <n-button secondary @click="copy"> Copy </n-button>
      <n-button secondary @click="refreshPort"> Refresh </n-button>
    </n-space>
  </n-card>
</template>

<script setup lang="ts">
import { computedRefreshable } from '@/composable/computedRefreshable';
import { useCopy } from '@/composable/copy';
import { generatePort } from './random-port-generator.model';

const [port, refreshPort] = computedRefreshable(() => String(generatePort()));

const { copy } = useCopy({ source: port, text: 'Port copied to the clipboard' });
</script>

<style lang="less" scoped>
.port {
  text-align: center;
  font-size: 26px;
  font-weight: 400;
  margin: 10px 0 25px;
}
</style>
