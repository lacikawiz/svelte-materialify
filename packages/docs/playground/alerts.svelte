<script>
  import Playground from '@shared/Playground.svelte';
  import { Alert, Icon } from 'svelte-materialify/src';

  const variants = ['dense', 'outlined', 'text', 'tile'];

  const controls = {
    dismissible: { type: 'switch' },
    visible: { type: 'switch' },
    icon: { type: 'switch' },
    coloredBorder: { type: 'switch' },
    border: {
      type: 'select',
      items: ['left', 'top', 'right', 'bottom'],
    },
    color: {
      type: 'select',
      items: ['primary', 'secondary', 'success', 'error', 'info'],
    },
  };

  const formatVariant = (v) => Object.fromEntries(v.map((i) => [i, true]));
  const textColor = (v) => v.some((i) => /^(outlined|text)/.test(i));

  let values = {
    variants: [],
    dismissible: false,
    visible: true,
    icon: false,
    coloredBorder: false,
    border: [],
    color: ['primary'],
  };
</script>

<Playground {variants} {controls} bind:values>
  <Alert
    class="{values.color[0]}-{textColor(values.variants) ? 'text' : 'color'}"
    dismissible={values.dismissible}
    bind:visible={values.visible}
    border={values.border[0]}
    coloredBorder={values.coloredBorder}
    {...formatVariant(values.variants)}>
    <span slot="icon">
      {#if values.icon}
        <Icon class="mdi mdi-home" />
      {/if}
    </span>
    Lorem, ipsum dolor sit amet consectetur adipisicing elit. Omnis itaque excepturi
    suscipit possimus blanditiis, illum libero sequi a deleniti sapiente.
  </Alert>
</Playground>
