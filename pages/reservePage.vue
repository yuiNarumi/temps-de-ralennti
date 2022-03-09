<template>
    <div>
    <SubHeader />
    <div class="reserve">
        <!-- <p class="reserve__pic"><img src="/mv-2.jpg" alt="" class="reserve__img"></p> -->
    <div class="reserve__bg">
    <h2 class="reserve__ttl">Reserve</h2>
    </div>

    <div class="reserve__container">
        <form action="">
            <div class="reserve__selectContainer">
            <p>
            <label for="name">ご利用人数</label>
            <select name="" id="name" v-model="number" class="reserve__labelNumber">
        <option value="" style="display:none;">選択してください</option>
        <option value="1名">1名</option>
        <option value="2名">2名</option>
        <option option value="3名">3名</option>
        <option value="4名">4名</option>
        <option value="5名">5名</option>
        <option option value="6">6名</option>
        <option value="7名">7名</option>
        <option value="8名">8名</option>
        <option option value="9名">9名</option>
        <option option value="10名">10名</option>
            </select>
            </p>

            <p>
            <label for="name">ルーム選択</label>
            <select name="" id="name" v-model="room" class="reserve__labelRoom">
        <option value="" style="display:none;">選択してください</option>
        <option value="Room1">Room1</option>
        <option value="Room2">Room2</option>
        <option option value="Room3">Room3</option>
            </select>
            </p>
            </div>

             <div class="reserve__pickerContainer">


            <div class="reserve__pickerBox">
            <p class="reserve__pTxt">チェックインの日時を選択してください</p>
            <VueCtkDateTimePicker
            inline
            noButtonNow
            v-model="requestDate1"
            :minute-interval="30"
            :format="'YYYY-MM-DD HH:mm'"
            :disabled-hours="['00', '01', '02', '03', '04', '05', '06', '07', '08', '22', '23']"
            :overlay="true"
            :min-date="start"
            :max-date="end"
            ></VueCtkDateTimePicker>
            </div>

            <div class="reserve__pickerBox">
            <p class="reserve__pTxt">チェックアウトの日時を選択してください</p>
            <VueCtkDateTimePicker
            inline
            noButtonNow
            v-model="requestDate2"
            :minute-interval="30"
            :format="'YYYY-MM-DD HH:mm'"
            :disabled-hours="['00', '01', '02', '03', '04', '05', '06', '07', '08', '13','14','15','16','17', '18', '19', '20', '21', '22', '23']"
            :overlay="true"
            :min-date="start"
            :max-date="end"></VueCtkDateTimePicker>
         </div>

            </div>

        </form>

    <div class="reserve__result">
            <div class="reserve__txtBox">
            <p class="reserve__resultTtl">ご予約内容</p>
            <p class="reserve__number">ご利用人数 :<span class="resultTxt">{{number}}</span></p>
            <p class="reserve__room">ルーム :<span class="resultTxt">{{room}}</span></p>
            <p class="reserve__ci">チェックイン :<span class="resultTxt">{{requestDate1}}</span></p>
            <p class="reserve__co">チェックアウト :<span class="resultTxt">{{requestDate2}}</span></p>
            </div>
        <button class="reserve__button">この内容で予約する</button>
        </div>


    </div>

    
    </div>
    
    
    </div>
</template>

<script>
import SubHeader from '@/components/subheader.vue';
import moment from 'moment'
import Datetime from 'vue-ctk-date-time-picker';
import '@/node_modules/vue-ctk-date-time-picker/dist/vue-ctk-date-time-picker.css';

export default {
    layout: "reserve",

    components: {
    SubHeader,
    Datetime
  },

  data() {
      return {
          requestDate1:'',
          requestDate2:'',
          number:'',
          room:''
      }
  },

  mounted() {
      Typekit.load({async: true})
  },

  computed: {
       start() {
      // min-date に明日の9時を指定
      const start = moment().add(1, 'days').hour(8)
      return start.format('YYYY-MM-DDTHH:mm:ss')
    },
    end() {
      // max-date に min-date から3ヶ月後を指定
      const start = moment(this.start)
      const end = start.add(3, 'months').endOf('day')
      return end.format('YYYY-MM-DDTHH:mm:ss')
    }
  }
};
</script>

<style lang="scss">

$font-sub: noto-sans, sans-serif;

$font-ttl:monotype-modern-display, sans-serif;

$font-jp: a-otf-ryumin-pr6n, serif;

@mixin ttlStyle {
    font-size: 96px;
      font-family: $font-ttl;
            font-weight: 400;
            font-style: normal;
            margin-bottom: 130px;
            color: #4c2f21;
}

img {
    width: 100%;
    height: 100%;
    object-fit:cover;
}

.reserve {

    width: 100%;
    padding-bottom: 100px;
     background: rgb(248, 234, 222);

    &__bg {
         width: 100%;
        height: 500px;
        background: url(/mv-2.jpg)center center / cover;
        position: relative;
        margin-bottom: 200px;
    }

    &__ttl {
        @include ttlStyle;
        color: #fff;
        position: absolute;
        bottom: -10%;
        right: 10%;
        z-index:2;
    }

    &__container {
        display: flex;
        justify-content: center;
        gap: 100px;
    }

    &__selectContainer {
        display: flex;
        justify-content: space-between;
        border-bottom:1px solid #000;
        padding:30px;
        margin-bottom: 40px;
    }

    &__pickerContainer {
        display: flex;
        gap: 50px;
    }

    &__pickerBox {
        width: 500px;
        height: 500px;
    }

    &__pTxt {
        font-family: $font-jp;
        font-size: 18px;
        margin-bottom: 30px;
    }

    &__container {
        display: flex;
    }

    &__labelNumber,
    &__labelRoom {
        width: 300px;
        padding:10px;
    }


    &__result {
        width: 500px;
        height: 400px;
        border:1px solid #000;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 20px;
    }

    &__resultTtl {
        font-size: 25px;
        font-family: $font-jp;
        text-align: center;
        margin-bottom: 30px;
    }

    &__txtBox {
        margin-bottom: 30px;
    }

    &__number,
    &__room,
    &__ci,
    &__co {
        font-family: $font-jp;
        font-size: 20px;
        line-height: 1;
        margin-bottom: 15px;
    }

    .resultTxt {
        font-size: 25px;
        font-family: $font-jp;
        font-weight: bold;
        line-height: 1;
        letter-spacing: 0.1rem;
        margin-left: 20px;
    }

    &__button {
        width: 300px;
        padding: 10px;
        font-family: $font-jp;
        font-size: 16px;
    }
}

form {
    /* width: 100%; */
    /* border:1px solid #000; */
    background: rgb(226, 213, 207);
    padding: 30px;
}

label {
    font-family: $font-jp;
    font-size: 20px;
    margin-right: 30px;
}

</style>