<script setup>
import { reactive, onMounted } from 'vue';
import { StorageService, StorageService } from '@/services/StorageService';

//스토리지서비스 클래스 내에 있는 생성자 호출
//생성자 호출할때는 new 키워드가 앞에 꼭 있어야함
const storageService = new StorageService('myMemo'); 

const state = reactive ({
  memos: {}
});

onMounted(()=> state.memos = storageService.getItems() );

</script>

<template>
  <div class = "memo-list">
    <router-link class="item" v-for = "item in state.memos" :to="`/memos/${item.id}`">

    </router-link>
  </div>
</template>
