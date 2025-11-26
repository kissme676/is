<template>
  <button :class="$style.button" :data-layout="props.layout" :data-size="props.size" :disabled="props.isDisabled" :type="props.type">
    <slot></slot>
  </button>
</template>

<script setup lang="ts">
interface IProps {
  layout?: 'primary' | 'secondary';
  type?: 'submit' | 'button';
  isDisabled?: boolean;
  size?: 'm' | 'l';
}

const props = withDefaults(defineProps<IProps>(), {
  layout: 'primary',
  type: 'button',
  size: 'm'
});
</script>

<style module lang="scss">
.button {
  position: relative;
  display: inline-flex;
  gap: 8px;
  align-items: center;
  justify-content: center;
  height: 40px;
  padding: 16px 32px;
  font-size: 1rem;
  line-height: 1.5;
  color: var(--color-white);
  background: var(--color-primary);
  border-radius: 16px;

  &[data-size='l'] {
    height: 48px;
    padding: 20px 40px;
    font-size: 1.125rem;
  }

  &[data-layout='secondary'] {
    color: var(--color-primary);
    background-color: var(--color-transparent);
    border-color: var(--color-primary);
  }
}
</style>
