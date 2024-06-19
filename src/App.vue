<script setup>
import { ref, onMounted, onBeforeUnmount, watchEffect } from "vue";
import "animate.css";
import me from "./img/me.jpg";

const mePicShow = ref(false);

// 裝置監聽
const device = ref("");
const windowWidth = ref(window.innerWidth);
const handleWindowResize = () => {
  windowWidth.value = window.innerWidth;
  if (windowWidth.value >= "768") {
    device.value = "pc";
  } else {
    device.value = "mobile";
  }
};
handleWindowResize();

window.addEventListener("resize", handleWindowResize);

// 彈窗時body滾輪移除
onMounted(() => {
  document.body.classList.remove("overflow-hidden");
});

watchEffect(() => {
  if (mePicShow.value) {
    document.body.classList.add("overflow-hidden");
  } else {
    document.body.classList.remove("overflow-hidden");
  }
});

onBeforeUnmount(() => {
  document.body.classList.remove("overflow-hidden");
});
</script>

<template>
  <div class="relative bg-[#DBC4A7]">
  
    <div
      :class="['max-w-[1240px]  mx-auto min-h-dvh   bg-[#DBC4A7] pt-[10px] pb-[10px]',{
        'flex  pr-[10px]':device=='pc'
      },
      {
        'px-[10px]':device=='mobile'
      }]"
    >
      <!-- 右邊區塊 -->
      <div
        :class="[{
        'w-full':device=='mobile'
      },{
        'w-[30%]':device=='pc'
      },]"
      >
        <div
          @click="mePicShow=true"
          class="w-[90%] aspect-square ml-2 bg-cover bg-center rounded-full cursor-pointer after:content-[''] after:block after:w-[100%] after:aspect-square after:rounded-full after:border after:border-black after:translate-x-2"
          :style="{ 'background-image': `url(${me})` }"
        ></div>
        <div class="p-3">
          <div class="text-center font-bold text-2xl">李庭瑄</div>
          <div
            class="mx-auto w-fit px-5 text-center text-[#735643] border-t border-t-[#735643]"
          >前端工程師</div>
          <div>
            <div class="my-3">
              <div class="font-bold">關於我</div>
              <div class="text-sm my-1 text-[#735643] leading-relaxed">
                我是李庭瑄，個性活潑樂觀，面對挑戰及想做的事情，都會盡力去完成，享受成就感，不害怕失敗，只怕沒有行動而錯失機會。
                <br />
                <br />學生時期透過代辦參加美國打工旅遊計畫，持續進修自我，強化世界觀，透過此機會，加強與累積經驗且建立好人際基礎，學習到與他人溝通與互動及資源找尋之能力，並可將此運用於工作中。
                <br />
                <br />出社會後第一份ERP系統工作，讓我對寫程式產生興趣，並自行進修前端技能，成功轉職為前端工程師，並將所學運用在實務上。我覺得寫程式很有趣，我也很享受寫程式讓我獲得成就感!
                <br />
                <br />平常喜歡健身，利用下班之餘維持身材，認為擁有健康的身體不管是對生活還是工作都是最重要的。
              </div>
            </div>
            <div class="my-3">
              <div class="font-bold">學習歷程</div>
              <div class="text-sm my-1 text-[#735643] leading-relaxed">
                1.高中期間勤奮學習，邏輯觀念好、對數字敏感度高，數理是我的強項，每次段考都獲得全班第一名，每學期都榮獲學校獎學金，也榮獲班上第一名市長獎畢業。
                <br />
                <br />2.大學期間不斷勉勵自己朝多方面發展，積極參與系會活動，同時也考取相關金融專業證照，希望能將自己的知識活用於規劃資產配置上。也利用學生身分這個機會，參與美國政府的打工旅遊計畫，利用這個機會在美國生活了4個月，體驗外國風情，增加世界觀以及獨立的個性，使我擴大視野、增廣見聞對，我受益良多。
                <br />
                <br />3.藉由ERP系統觸寫程式並產生興趣，利用下班之餘自行進修前端技能，上了基本HTML+CSS+Javascript的課程，也上了vue3框架課程來幫助網頁更好維護以及讓工作更有效率，希望能夠轉職前端工程師。
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- 左邊區塊 -->
      <div
        :class="['text-[#735643]',{
        'w-full':device=='mobile'
      },{
        'w-[70%]':device=='pc'
      },]"
      >
        <!-- 左邊區塊:上 -->
        <div class="bg-[#fff] py-5 px-3">
          <div class="text-2xl font-bold mb-5">技能</div>
          <div class="flex flex-wrap gap-1 w-full">
            <div class="w-[40%] rounded bg-[#E4E2E2] text-center px-2">
              <div>前端基本</div>
              <div class="text-sm border border-t-[#735643]">HTML、CSS、SASS、JavaScript</div>
            </div>
            <div class="w-[58%] rounded bg-[#E4E2E2] text-center px-2">
              <div>VueJS</div>
              <div
                class="text-sm border border-t-[#735643]"
              >Vue3、Vue2、Vue Router、Vue-Cil、Vuex、Pinia、Node.js、Ajax、Linux、API串接、Postman</div>
            </div>
            <div class="w-[60%] rounded bg-[#E4E2E2] text-center px-2">
              <div>套件</div>
              <div
                class="text-sm border border-t-[#735643]"
              >Tailwind、Bootstrap、Element Plus、PrimeVue、i18n</div>
            </div>
            <div class="w-[38%] rounded bg-[#E4E2E2] text-center px-2">
              <div>版本控制</div>
              <div class="text-sm border border-t-[#735643]">Git、GitHub、GitLab</div>
            </div>
            <div class="rounded bg-[#E4E2E2] text-center px-2 py-2">
              <div class>RWD</div>
            </div>
          </div>
        </div>
        <!-- 左邊區塊:下 -->
        <div class="bg-[#fff] py-5 px-3 mt-2">
          <div class="text-2xl font-bold mb-5">經驗</div>
          <!-- 經驗一 -->
          <div class="flex">
            <div class="w-[25%]">
              <div
                :class="['text-sm mx-auto  bg-[#C9B49A] text-center font-bold h-fit w-fit px-3 py-1 rounded-2xl',{
        'text-wrap':device=='mobile'
      },{
        'text-nowrap':device=='pc'
      },]"
              >2022/8-2024/7</div>
            </div>
            <div class="w-[5%] mt-3">
              <div class="w-[8px] h-[8px] mx-auto bg-black rounded-full"></div>
              <div class="w-[2px] h-[calc(100%+5px)] mx-auto bg-black rounded-full"></div>
            </div>
            <div class="w-[70%] pb-8">
              <div class="font-bold">神兵資訊(前端工程師)</div>
              <div
                :class="['leading-relaxed',{
                'text-sm':device=='mobile'
              }]"
              >
                1. 使用Vue 進行網站開發。
                <br />2. 串接 API 資料進行使用。
                <br />3. 使用 git 進行版本控制。
                <br />4. RWD
                <br />5.與後端工程師討論製作相關的API資料，或是跨部門企劃、UI討論
                <br />【主要專案】
                <br />專案名稱：區塊鏈遊戲平台開發
                <br />專案內容：
                <br />(1) 以 Vite-Vue 為框架，搭配 PrimeVUE、tailwind、i18n 等套件進行電腦版、手機版前台開發。
                <br />(2)以既有的 Vue2框架建立的後台，搭配Element plus、typescript接手進行新功能開發及維護。
                <br />(3) 利用 Figma 協助處理頁面 UI 規劃與設計。
                <br />(4) 幣安api websocket串接。
                <br />
              </div>
            </div>
          </div>
          <!-- 經驗二 -->
          <div class="flex">
            <div class="w-[25%]">
              <div
                :class="['text-sm mx-auto  bg-[#C9B49A] text-center font-bold h-fit w-fit px-3 py-1 rounded-2xl',{
        'text-wrap':device=='mobile'
      },{
        'text-nowrap':device=='pc'
      },]"
              >2021/8-2022/8</div>
            </div>
            <div class="w-[5%] mt-3">
              <div class="w-[8px] h-[8px] mx-auto bg-black rounded-full"></div>
              <div class="w-[2px] h-[calc(100%+5px)] mx-auto bg-black rounded-full"></div>
            </div>
            <div class="w-[70%] pb-8">
              <div class="font-bold">邑爍資訊(ERP系統輔導專員)</div>
              <div
                :class="['leading-relaxed',{
                'text-sm':device=='mobile'
              },]"
              >
                1.了解勞基法基本法條及知識。
                <br />2.依客戶提供資訊設定系統。
                <br />3.到客戶端安裝系統以及教育訓練。
                <br />4.輔導客戶系統溝通解決問題。
                <br />5.做出客製化系統分析達到客戶需求。
                <br />6.QA，測試系統Bug。
                <br />7.輔導客戶上線，每年更新政府級距資料服務。
                <br />
              </div>
            </div>
          </div>
          <!-- 經驗三 -->
          <div class="flex">
            <div class="w-[25%]">
              <div
                :class="['text-sm mx-auto  bg-[#C9B49A] text-center font-bold h-fit w-fit px-3 py-1 rounded-2xl',{
        'text-wrap':device=='mobile'
      },
      {
        'text-nowrap':device=='pc'
      },]"
              >2019/6-2019/9</div>
            </div>
            <div class="w-[5%] mt-3">
              <div class="w-[8px] h-[8px] mx-auto bg-black rounded-full"></div>
              <div class="w-[2px] h-[calc(100%+5px)] mx-auto bg-black rounded-full"></div>
            </div>
            <div class="w-[70%] pb-8">
              <div class="font-bold">Borgata hotel casino and spa</div>
              <div
                :class="['leading-relaxed',{
                  'text-sm':device=='mobile'
                },]"
              >大學時自行找代辦ciee到美國打工度假，利用遠端視訊與雇主面試，面試上了位於美國西岸紐澤西州的東岸賭城飯店borgata，我負責在賭場內做服務生的角色，也利用這個機會積極與客人對話，練習英文口說，也教了不同國家的朋友。</div>
            </div>
          </div>
          <!-- 經驗四 -->
          <div class="flex">
            <div class="w-[25%]">
              <div
                :class="['text-sm mx-auto  bg-[#C9B49A] text-center font-bold h-fit w-fit px-3 py-1 rounded-2xl',{
        'text-wrap':device=='mobile'
      },{
        'text-nowrap':device=='pc'
      }]"
              >2016-2019</div>
            </div>
            <div class="w-[5%] mt-3">
              <div class="w-[8px] h-[8px] mx-auto bg-black rounded-full"></div>
            </div>
            <div class="w-[70%] pb-8">
              <div class="font-bold">學生時期兼職打工</div>
              <div
                :class="['leading-relaxed',{
                'text-sm':device=='mobile'
              }]"
              >
                1.名貫補習班(數學助教)
                <br />2.Yogilini 瑜珈SPA會館(櫃檯)
                <br />3.一沐日飲料店(櫃檯)
                <br />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- 大頭照 -->
    <template v-if="mePicShow==true">
      <div
        @click.self="mePicShow=false"
        class="cursor-pointer fixed top-0 left-0 w-dvw h-dvh flex items-center justify-center bg-white bg-opacity-60"
      >
        <div
          :class="['animate__animated animate__flipInY  max-w-[600px]   cursor-default  aspect-square bg-cover bg-center rounded-full after:content-[\'\'] after:block after:w-[100%] after:aspect-square after:rounded-full after:border after:border-black after:translate-x-2',{
        'w-[50%] ':device=='pc'
      },{ 'w-[70%] ':device=='mobile'
      }]"
          :style="{ 'background-image': `url(${me})` }"
        ></div>
      </div>
    </template>
  </div>
</template>