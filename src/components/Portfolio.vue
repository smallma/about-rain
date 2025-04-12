<template>
  <div id="portfolio">
    <div class="portfolio-bg" >
      <img v-bind:src="background" :class="'img_bg ' + bgClass"/>
      <div class="img_mask"></div>
    </div>
    <div class="center_line"></div>

    <HistoryCard 
      v-for="history in historys"
      :history="history"
      :key="history.id"
      @changeBackground="updateBackground"
    />

  </div>
</template>

<script>
  import HistoryCard from './HistoryCard.vue'

  export default {
    name: 'Profolio',
    components: {
      HistoryCard
    },
    data () {
      return {
        historys: [
          {
            'id': 18,
            'type': 'asus',
            'from': 'rogphone',
            'bgHeightFull': false,
            'year': '~ now',
            'title': 'ROG Phone Series',
            'info': 'ROG Phone 6, 7 都是大量使用 ScrollTrigger 特效, 是主流風格的網頁特效, 再搭配大量的影片播放控制, 調整最佳的網頁效能, 讓網頁都能順暢的瀏覽, 也符合 WCAL 2.1 Level AA 的無障礙標準, 也透過 Lighthouse 檢測 LCP 與 CLS 指標是否合格, 在 GA 與 SEO 上也是有符合華碩規範.',
            'links': [
              {
                'name': 'ROG Phone 9',
                'url': 'https://rog.asus.com/phones/rog-phone-9/'
              },
              {
                'name': 'ROG Phone 7',
                'url': 'https://rog.asus.com/phones/rog-phone-7/'
              },
              
              {
                'name': 'ROG Phone 6',
                'url': 'https://rog.asus.com/phones/rog-phone-6-model/'
              },
              {
                'name': 'ROG Phone 5',
                'url': 'https://rog.asus.com/phones/rog-phone-5s-pro-model/'
              },
              {
                'name': 'ROG Phone 3',
                'url': 'https://rog.asus.com/phones/rog-phone-3-strix-edition-model/'
              },
              {
                'name': 'ROG Phone 2',
                'url': 'https://rog.asus.com/phones/rog-phone-ii-model/'
              }
            ]
          },
          {
            'id': 17,
            'type': 'asus',
            'from': 'accessory',
            'bgHeightFull': false,
            'year': '~ now',
            'title': 'Accessory',
            'info': '有負責過 ZenWatch, ZenPower, Phone Case 等產品網頁, 其中包含許多模組化網頁, 透過開發各種模組加速網頁開發效率, 透過 PUG/SCSS 開發模組',
            'links': [
              {
                'name': 'ROG Phone 5 - KUNAI 3',
                'url': 'https://rog.asus.com/controllers/rog-kunai-3-bumper-for-rog-phone-5-model/'
              },
              {
                'name': 'ZenPower Duo',
                'url': 'https://www.asus.com/Accessories/Power-Banks/ASUS-Power-Bank/ZenPower-Duo/'
              },
              {
                'name': 'ZenFone 9 Connex',
                'url': 'https://www.asus.com/accessories/cases-and-protection/zenfone/zenfone-9-connex-accessories-set/'
              }
            ]
          },
          {
            'id': 16,
            'type': 'asus',
            'from': 'notebook',
            'bgHeightFull': false,
            'year': '~ now',
            'title': 'NoteBook',
            'info': '從 2015 年至今不斷開發 Zenbook, Vivobook, Expertbook 等 notebook, 其中導入各種 CSS/JS/Canvas 特效, 圖片也導入 Next Gen Image Webp 格式, GA Tracking 埋設與 SEO 相關設定, 完成呈現 RWD 網頁開發, 確保網頁流量都能符合部門規範',
            'links': [
              {
                'name': 'ASUS Vivobook Pro 16X OLED (K6604)',
                'url': 'https://www.asus.com/laptops/for-creators/vivobook/vivobook-pro-16x-oled-k6604/'
              },
              {
                'name': 'ASUS Zenbook Pro 14 UX8402',
                'url': 'https://www.asus.com/laptops/for-creators/zenbook/zenbook-pro-14-duo-oled-ux8402/'
              },
              {
                'name': 'ASUS Expertbook B5 Flip b5602f',
                'url': 'https://www.asus.com/laptops/for-work/expertbook/expertbook-b5-flip-b5602f-12th-gen-intel/'
              }
            ]
          },

          {
            'id': 15,
            'type': 'asus',
            'from': 'zenfone',
            'bgHeightFull': false,
            'year': '~ now',
            'title': 'ZenFone',
            'info': '2015 年開始的第一個產品就是 ZenFone Zoom, 當時實現了華碩內部自製第一個 RWD 網頁, 並開發各種 CSS/JS 特效, 其中包含當下最熱門的滾動視差特效, 開發接近 Apple 等級的網頁水準, 至今所有的 ZenFone 系列都是我們開發的產品網頁, 不乏也有不少 tw 語系也是委託我們開發',
            'links': [
              {
                'name': 'ZenFone 12',
                'url': 'https://www.asus.com/mobile-handhelds/phones/zenfone/zenfone-12-ultra/'
              },
              {
                'name': 'ZenFone 6',
                'url': 'https://www.asus.com/mobile/phones/zenfone/zenfone-6/'
              },
              {
                'name': 'ZenFone 4 Selfie',
                'url': 'https://www.asus.com/mobile/phones/all-series/zenfone-4-selfie-zd553kl/'
              },
              {
                'name': 'ZenFone 2 Laser',
                'url': 'https://www.asus.com/mobile/phones/all-series/zenfone-2-laser-ze550kl/'
              }
            ]
          },
          {
            'id': 14,
            'type': 'asus',
            'from': 'cmd',
            'bgHeightFull': true,
            'year': '2015',
            'title': 'ASUS Creative Web Design',
            'info': '進入華碩網頁開發團隊後, 開始著手架設 git 環境, WiFi 環境, 網頁測試前後台, 前端網頁開發框架, 定義網頁檢測標準, 前端開發規範等, 2015 年從前端 1 人至今已擴展至 5 人, 從當初的 ZenFone 產品網頁以拓展到 ROG Phone, ZenFone, Zenbook, Vivobook, ROG Laptop 與各種 Accessory 網頁, 其中也包含些許串接 API 元件與一個 Vue2 多國語系網站.' 
          },
          {
            'id': 13,
            'type': 'quanta',
            'from': 'jaybo',
            'bgHeightFull': false,
            'year': '2015',
            'title': 'QRI - Jaybo Parse API',
            'info': 'Jaybo 是一個 Noticifation APP, 可以自行加入平台上頻道, 接收對應頻道的即時推播資訊, 過去曾和雲門舞集合作園區導覽, 棒球與籃球賽實況推播, 樂透號碼推播等, 這邊我是使用 Parse.com 快速開發 Restful API'
          },
          {
            'id': 12,
            'type': 'quanta',
            'from': 'qoca',
            'bgHeightFull': false,
            'year': '2014',
            'title': 'QRI - QOCA Messenger',
            'info': 'QOCA Messenger 是一個整合於 QOCA 醫療系統的聊天軟體, 提供簡易的介面與 Private Messenge 的功能, 提升年長者使用 Messenger 的意願, 這是使用 Sencha Touch 開發的 Hybrid APP'
          },
          {
            'id': 11,
            'type': 'quanta',
            'from': 'phollow',
            'bgHeightFull': false,
            'year': '2013',
            'title': 'QRI - Phollow APP',
            'info': 'Phollow 是一個 Breadcrumb 地圖社交軟體, 是透過使用者或商家在某個地點加入 Breadcrumb, 當使用者靠近附近時會自動跳出當地的 Breadcrum 資訊, 讓使用者只能在特地地點中獲取特殊訊息, 訊息是限時限地, 請內容可為私人訊息, 或是商家推廣 coupon, 後續還嘗試要整合了美國當地的支付系統, 可在店家中進行 coupon 扣款支付, 這邊是透過 Cordova 開發 Hybrid APP'
          },
          
          {
            'id': 10,
            'type': 'quanta',
            'from': 'qri',
            'bgHeightFull': false,
            'year': '2013',
            'title': 'Quanta Research Institute',
            'info': '因部門重組後, 加入廣達研究院, 這個單位配置前端, 後端, Android App, iOS App 與設計 Team, 在這邊加入前端 Team, 並學習使用 Agile 開發, 其中也參與 Garage Startup Meetings, Phollow, QOCA 醫療系統, Jaybo 等相關案子, 接觸的技術有 HTML, Javascript, React, Sencha Touch, Parse.com Promise API 等'
          },
          
          {
            'id': 9,
            'type': 'quanta',
            'from': 'filesystem',
            'bgHeightFull': false,
            'year': '2012',
            'title': 'CCBU - Server 新增硬碟自動整合機制',
            'info': '過往 Server 如插入硬碟時需要手動找到硬碟, 格式化, 再掛載到對應的位置, 這個機制提供系統偵測到新增硬碟, 自動格式化硬碟成 ZFS 加入到 Zpool 中使用, 這邊是使用 Python 開發'
          },
          
          {
            'id': 8,
            'type': 'quanta',
            'from': 'glance',
            'bgHeightFull': false,
            'year': '2011',
            'title': 'CCBU - OpenStack Glance Management System',
            'info': 'Glance 替 OpenStack 提供映像檔服務, 透過 Glance 可以上傳, 檢視與修改映像檔, 我開發的 Glance Management System 可透過 GUI 介面操作與檢視 Glance 相關功能, 自動化管理 Glance, 這邊是使用 Python 開發'
          },
          
          {
            'id': 7,
            'type': 'quanta',
            'from': 'memcached',
            'bgHeightFull': false,
            'year': '2010',
            'title': 'CCBU - Memcached Automatic Failback System',
            'info': 'Memecached 是一個分散式快取系統, 透過這個 service 可以減少 server request, 並增加 response 效率, 我們在自己的伺服器上開發 Memcached failover system, 透過伺服器自動偵測 memcached vm 服務狀態是否正常, 當系統偵測某一台 memcached 斷線時, 會即時啟動另一個備援的 memcached 替補, 這邊是使用 Shell Script / PHP 開發'
          },

          {
            'id': 6,
            'type': 'quanta',
            'from': 'ccbu',
            'bgHeightFull': false,
            'year': '2010',
            'title': 'Quanta CCBU',
            'info': '退役後面試進入廣達電腦, 並於 CCBU 內學習與開發多個與 Linux 系統相關的服務, 其中曾使用的技術為 Shell Script, PHP, Python, 並對 Memcached 與 Openstack Glance 有實際的操作與開發相關輔助系統經驗, 並實作出伺服器硬碟格式與建制 ZFS 的自動化流程, 讓系統能自動的整合新插入的硬碟'
          },

          {
            'id': 5,
            'type': 'education',
            'from': 'aea',
            'bgHeightFull': false,
            'year': '2009',
            'title': '兵役 - 行政執行處',
            'info': '在替代役時期於台北行政執行處統計處服兵役, 並於同年被擢升為管理幹部, 負責管理處內 60 位役男生活起居相關內容, 在行政執行處時期因大量案件需要處理, 且要再點時間內確實且正確的完成, 這樣的環境也確實磨煉了個人的耐性與細心程度'
          },

          {
            'id': 4,
            'type': 'education',
            'from': 'ieee',
            'bgHeightFull': false,
            'year': '2009',
            'title': 'IEEE 最佳學生論文',
            'info': '2008 年以論文 KML 技術實現台灣遙測地理平台獲得 IEEE 最佳學生論文殊榮, 論文中透過 JSP 語法開發遙測資訊平台, 整合分類言算法與平行運算, 提升計算效率, 並即時針對高光譜影像計算不同的分類影像, 並使用 KML 技術將分類影像疊蓋到 Goolgle Earth 做 3D 檢視, 透過這個系統可以提升分類影像的辨別率與操作體驗'
          },

          {
            'id': 3,
            'type': 'education',
            'from': 'ntut',
            'bgHeightFull': true,
            'year': '2007',
            'title': 'NTUT 電機工程研究所',
            'info': '透過甄試考進北科大電機工程所, 並加入遙測與影像辨識實驗室, 在研究所時期深入研究叢集電腦架設, 平行演算法, Linux 系統伺服器架設, 電子學, 影像辨識演算法等相關知識, 並擔任電子電路課程助教, 輔助學生學習使用 VHDL, 並連續兩年都與研究室成員積極參與偏鄉志工團, 教導宜蘭與新竹偏鄉孩子電腦相關知識, 在寒暑假時陪伴他們學習電腦技能, 以期減少減少偏鄉差距'
          },

          {
            'id': 2,
            'type': 'education',
            'from': 'innoserve',
            'bgHeightFull': false,
            'year': '2006',
            'title': '全國大專院校專題競賽',
            'info': '畢業專題以產學合作的 POS 機開發無人借還書系統, 透過 JSP 語法開發圖書館借還書功能, 並使用 RFID 實現自動化偵測借還數量與書籍對應 ID, 可有效提升借還書效率, 並於 2006 年全國大專院校專題競賽中獲得佳作(第四名)殊榮'
          },
          {
            'id': 1,
            'type': 'education',
            'from': 'ntub',
            'bgHeightFull': true,
            'year': '2004',
            'title': 'NTUB 資訊管理系',
            'info': '在 2005 年二技聯招時以全國 101 名進入北商資管系, 在北商就讀資管系時期繼續研習資料庫, 資料結構, 演算法, 軟體工程, 多媒體應用, C++, JAVA 等電腦相關知識, '
          },
        ],
        background: '',
        bgClass: ''
      }
    },
    methods: {
      updateBackground: function(src, bgClass) {
        console.log('updateBackground', src, bgClass);
        this.background = src;
        this.bgClass = bgClass;
        return;
      }
    }
  }
</script>

<style lang="scss" scoped>
#portfolio {
  display: block;
  position: relative;
  padding-top: 258px;
  background: rgb(36 36 36 / 80%);
  min-height: 100vh;

  .portfolio-bg {
    display: flex;
    overflow: clip;
    align-items: center;
    justify-content: center;

    .img_bg {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;

      // &.width-first {

      // }

      // &.height-first {
      //   // height: 100%;

      // flex-shrink: 0;
      // min-width: 100%;
      // min-height: 100%
      // }
    }

    .img_mask {
      display: block;
      position: fixed;
      top: 0;
      width: 100%;
      height: 100%;
      background: rgb(0 0 0 / 50%);
      content: '';

    }
  }
}

.center_line {
  position: absolute;
  top: 0;
  left: 50%;
  width: 4px;
  height: 100%;
  background-color: #7f7f7f;
  transform: translateX(-50%);
}


@media all and (max-width: 730.4px) {
  #portfolio {
    padding-top: 32px;

    .portfolio-bg {

      img {
        width:100%; 
        height:100%;
        object-fit: cover;
      }
    }
  }

  .center_line {
    left: 22px;
    transform: none;
  }
  
}
</style>