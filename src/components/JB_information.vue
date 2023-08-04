<template>
  <div class="container">
    <div class="row">
      <h2 class="fw-bold text-center pt-4">安裝原理</h2>
      <p class="fs-5 lh-base font-monospace pt-4">{{ installmsg }}</p>
      <div class="col-sm-5 text-center">
        <img :src="JBimg" class="img-thumbnail border-0" />
      </div>
      <div class="col-sm-7">
        <div v-for="item in jb_detail">
          <p class="fs-5 lh-base font-monospace">{{ item.area }}</p>
          <p class="fs-5 lh-base font-monospace">{{ item.content }}</p>
        </div>
      </div>
      <p class="pt-3 fs-5 lh-base font-monospace">{{ endmsg }}</p>
    </div>
    <h2 class="fw-bold text-center pt-4">機器開機方式</h2>
    <div class="row pt-4">
      <div v-for="item of jb_difference" class="col-sm-6">
        <h3 class="text-center">{{ item.title }}</h3>
        <p class="fs-5 lh-base font-monospace">{{ item.content }}</p>
      </div>
      <div v-for="item of JB_pic" class="col-sm-6 text-center">
        <p class="fs-6 lh-base font-monospace">{{ item.detail }}</p>
        <img class="img-thumbnail border-0 rounded" :src='item.pic' />

      </div>
    </div>
    <div class="row pt-4">
      <div  v-for="(item, id) of startoptions " :key="item.id" class="col-lg-4 h-auto">
        <!-- 這邊必須要給一個id 讓toggleShowContent去做使用 -->
        <div class="h-100">
          <img class="rounded-circle rounded mx-auto d-block" :src="optionimg">
          <div class="accordion pt-5 h-auto">
            <div class="accordion-item h-100">
              <h2 class="accordion-header">
                <button @click="toggleShowContent(id)"  class="accordion-button" type="button" >
                  <h3 class="text-center pt-4"> {{ item.title }} </h3>
                </button>
              </h2>
              <div v-show="ShowContent[id]" class="accordion-collapse collapse show" >
                <div class="accordion-body">
                  <p class="fs-5 lh-base font-monospace"> {{ item.content }} </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref , reactive} from "vue"
let id = (0)
const ShowContent = reactive([false]);

function toggleShowContent(id){
  console.log(ShowContent)
  ShowContent[id] = !ShowContent[id]
}

const startoptions = ref([
  { id: id++, title: '正版系統(無破解)', content: '該系統為本機原有的正版系統，如要使用Nintendo Switch Online服務(例如動物森友會或是魔物獵人)，則必須使用該系統才能享受原本Switch主機連線的樂趣喔。點選後會讀取機器本身記憶模塊的正版系統，所有功能都跟未改機之前是一模一樣的。' },
  { id: id++, title: '正版系統(帶破解)', content: '該系統為本機原有的正版系統，但額外附帶了大氣層的相簿內所有功能 可以用來修改存檔或是開金手指遊玩喔。點選後會讀取機器本身記憶模塊的正版系統，所有功能都跟未改機之前是一模一樣的，但相簿功能加載了額外的所有插件。' },
  { id: id++, title: '虛擬系統(帶破解)', content: '該系統即為本機的虛擬系統，建立在記憶卡上，可用來遊玩各類第三方程序,點選後會讀取記憶卡上的虛擬系統' }
])

const JBimg = new URL('https://fakeimg.pl/400x200/200').href
const optionimg = new URL('https://fakeimg.pl/200x200/200').href
const installmsg = ref(`Switch的破解概念其實跟iPhone拿去JB是非常相近的，都是透過破解後取得系統的控制權，從而可以加載各式不同的程式及插件,Switch目前主流的破解系統有SX系統跟Atmosphere系統差異`)
const endmsg = ref(`所以雙系統就是所謂的正版系統跟虛擬系統，是分別儲存在不同位置的系統，這概念其實也跟桌上型電腦很像一開始電腦只裝了一個硬碟C槽(即A點)，所以開機後都是直接進入C槽的系統(正版系統)那麼破解之後，加裝第二顆硬碟D槽(即B點)，並在D槽上也安裝一個系統(虛擬系統)之後在機器開機的時候做個選單讓你選擇要進入C槽的系統(正版系統)或是D槽的系統(虛擬系統)這樣一台電腦的雙系統就完成了也因為是分別獨立空間的系統，所以系統的升級兩邊也是分開來的喔`)


const JB_pic = ref([
  { id: id++, detail: '螢幕底部會有一個跑條向右跑，如未按下音量小聲鍵則會自動進入虛擬系統', pic: ('https://fakeimg.pl/400x300/200') },
  { id: id++, detail: '進入開機選單後的畫面', pic: ('https://fakeimg.pl/400x300/200') }
])

const jb_detail = ref([
  { id: id++, area: 'A區域', content: '該模塊為eMMC模塊，是Switch機器原裝內置的儲存模塊，大小為32G(OLED機型為64G)預裝Switch的操作系統，也可以稱為正版系統' },
  { id: id++, area: 'B區域', content: '該記憶卡為Switch可額外插入的擴充儲存媒介，在Switch破解後，所有的資料都必須放在該記憶卡上可為破解系安裝虛擬系統，遊戲及各類插件' }
])

const jb_difference = ref([
  { id: id++, title: '接注入器版本(軟破機)', content: '按照原本方式，右搖桿滑軌插入短接器，下方插入注入器，按住音量 +後再按電源鍵開機 (電源鍵按了之後就可一起放開)' },
  { id: id++, title: '焊接晶片版本(硬破機)', content: '直接按電源鍵開機，等待機器背面下方進氣孔處的燈號轉綠燈第一次開機啟動後，當看見第一個Logo畫面時去按住音量小聲鍵即可進到開機選單畫面(有3秒的時間可以按)' }
])

</script>

