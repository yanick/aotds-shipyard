<ShipItem {cost} {mass}>
  <Field label="streamlining">
  <div>
    <label>
    <input type="radio" bind:group={type} value="none" />
    none</label>
    <label>

    <input type="radio" bind:group={type} value="partial" />
    partial</label>
    <label>
    <input type="radio" bind:group={type} value="full" />
    full</label>
    </div>
  </Field>
</ShipItem>

  <script>
  import get from 'lodash/get';
  import ShipItem from '~C/ShipItem/index.svelte';
  import Field from '~C/Field/index.svelte';
  import dux from '~/dux/streamlining';

  import {getContext } from 'svelte';

  export let type = 'none';
  export let cost = 0;
  export let mass = 0;
  export let ship_change = getContext('ship_change') || ( () => {} );

  $: ship_change( dux.actions.set_streamlining(type));

  </script>

  <style>
  div { display: flex }
  label {
    margin-left: 1em;
  }
  </style>
