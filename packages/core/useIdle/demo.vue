<script setup lang="ts">
import { computed } from 'vue-demi'
import { useIdle } from '.'
import { useTimestamp } from '../useTimestamp'

const { idle, lastActive } = useIdle(5000)

const { timestamp: now } = useTimestamp()

const idledFor = computed(() =>
  Math.floor((now.value - lastActive.value) / 1000),
)
</script>

<template>
  <note class="mb-2">
    For demonstraction purpose, the idle timout is set to <b>5s</b> in this
    demo (default 1min).
  </note>
  <div class="mb-2">
    Idle: <code>{{ idle }}</code>
  </div>
  <div>Inactive: <b class="text-primary">{{ idledFor }}s</b></div>
</template>
