<script setup>
import HelloWorld from '../src/components/HelloWorld.vue'
import Button from '../src/components/ui/Button/index.vue'
</script>

# Docs

This is a .md using a custom component

<HelloWorld />

## More docs

<div class="button-group">
<Button mode="grey" text="grey" />
<Button mode="light" text="light" />
<Button mode="black" text="black" />
</div>

<style lang="scss">
.button-group
  {display: grid;
  gap: 10px; }
</style>
