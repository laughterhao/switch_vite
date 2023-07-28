<template>
  <div class="container position-relative" style="padding-top: 56px">
    <div class="row justify-content-md-center">
      <div class="col-md-auto">
        <h3>插件說明</h3>
      </div>
    </div>
    <div class="row row-cols-1 row-cols-md-3 " style="padding-top: 30px;">
      <div v-for="item in items" :key="item.id" class="col" style="padding-top: 30px">
        <div class="card h-100">
          <img src="https://fakeimg.pl/300x200/200" />
          <div class="card-body">
            <h5 class="card-title text-center">{{ item.title }}</h5>
            <p class="card-text text-truncate "  style="padding-bottom: 50px;">
              {{ item.content }}
            </p>
            <a href="#" class="btn btn-primary position-absolute bottom-0 start-0" style="margin: 10px">閱讀更多...</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<style>
</style>
<script setup lang="ts">
import { ref } from 'vue'
let id = 0
const items = ref([
  { id : id++, title: 'DBI應用', content: '目前來看，大氣層的USB直裝遊戲未來應該是趨向於Tinfoil和DBI方式了，也省去了關機拔記憶卡動作。主要介紹DBI的USB遊戲安裝，卸載補丁，重置遊戲所需最低系統版本等。' },

  { id : id++, title: 'JKSV', content: '常用存檔導入匯出功能的人應該知道兩款插件程式：JKSV和CheckPoint。JKSV除了存檔導入、匯出、批量備份、功能以外，更常用的一個功能是BCAT的恢復，常玩動物之森和怪物獵人崛起的人可能會用到當然還有一些比較少用到的功能，比如刪除本機已下載的系統升級包。' },

  { id : id++, title: 'DayBreak', content: '離線升級系統，對於破解設備來說是很有必要的，畢竟隨著遊戲更新，系統版本的要求也會隨之遞增。鑒於大白兔很久沒有更新了，而大氣層官方推薦使用Daybreak來離線升級主機系統。所以，今天就來說一下大氣層 Atmosphere 如何離線升降級系統。' },

  { id : id++, title: 'Linkalho', content: '有部分遊戲，如暗黑3，真人快打、重裝機兵等，啟動遊戲均需要本地帳戶有綁定任天堂的帳戶才行，但是破解系統又不能正常連線去任天堂做帳戶的綁定(會被ban)所以國外大神rdmrocha開發了一款名為Linkalho的工具，可以實現離線模式下關聯全部帳戶，一鍵關聯全部帳戶，一鍵解除關聯全部帳戶，支援當前所有Switch設備SX軟破、硬破設備和大氣層設備。' },

  { id : id++, title: '大氣層包升級', content: '由於任天堂,會不斷的更新韌體版本,為了要讓大氣層可以支援最新的韌體,我們必須更新更新大氣層包' },

  { id : id++, title: 'Tesle側邊選單', content: 'Tesla側邊快捷選單為一個可快速開啟特定功能的選單可自訂義想加入的功能，可達到快速開啟及關閉的作用選單可以在系統啟動後於主頁面或是遊戲內按下左搖桿的 L 鍵 + 方向下鍵來啟動' },
])
</script>
