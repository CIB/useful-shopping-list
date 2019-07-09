<template>
  <div class="shopping-list md-elevation-5">
    <div v-for="item in items" v-bind:key="item.id">
      <div
        class="shopping-list-item"
        :key="item.id"
      >
        <md-checkbox
          :disabled="loading[item.name]"
          class="shopping-list-item-checkbox"
          :value="!item.checked"
          :id="item.id"
          v-on:change="$emit('checkbox', item)"
        ></md-checkbox>
        <div
          class="shopping-list-item-name md-layout md-alignment-center-space-between"
        >{{item.name}}</div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class ShoppingList extends Vue {
  @Prop() private items!: any;
  @Prop() private loading!: any;
}
</script>

<style scoped>
  .mdl-checkbox {
    width: 20px;
    min-width: 20px;
    border-radius: 2px;
  }
  .md-checkbox {
    margin: 10px 15px 10px 10px;
  }
  .shopping-list {
    max-width: 180px;
    margin: auto;
    width: 50%;
    padding: 3px 0 3px 3px;
  }
  .shopping-list-item {
    list-style-type: none;
    display: flex;
  }
</style>
