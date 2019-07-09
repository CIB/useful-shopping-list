<template>
  <div class="home">
    <ShoppingList
      :items="listItems"
      :loading="{Tomaten: false}"
      @checkbox="toggle($event)"
    ></ShoppingList>
    <md-button class="md-fab bottom-right">
      <md-icon>add</md-icon>
    </md-button>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import { find } from 'lodash';
import ShoppingList from '@/components/ShoppingList.vue'; // @ is an alias to /src

@Component({
  components: {
    ShoppingList,
  },
})
export default class Home extends Vue {
  private listItems: any = {};

  created() {
    console.log('nice!');
    this.listItems = [{
      id: '1',
      name: 'Tomaten',
      checked: false,
    },{
      id: '2',
      name: 'Orangensaft',
      checked: false,
    },{
      id: '3',
      name: 'Wasser',
      checked: true,
    },{
      id: '4',
      name: 'Tofu',
      checked: true,
    }];
  }

  destroyed() {

  }

  toggle(checkbox: any) {
    const checkedItem = find(this.listItems, ['id', checkbox.id]);
    if (checkedItem) {
      checkedItem.checked = !checkedItem.checked;
    }
  }
}
</script>

<style scoped>
.bottom-right {
  position: fixed;
  bottom: 1rem;
  right: 1rem;
}
</style>