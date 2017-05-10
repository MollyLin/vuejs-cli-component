<template lang="jade">
  div#contact
    h2 聯絡資訊
    hr
    form
      div.form-group
        input(type="text" placeholder="請輸入您的暱稱" v-model="user.nick")
      div.form-group
        input(id="topic" type="text" placeholder="主題" v-model="user.topic")
      div.form-group
        textarea(id="userPost" rows="5" cols="25" placeholder="描述" v-model="user.desc")
      div.form-group
        input(id="user" type="text" placeholder="姓名" required autocomplete="off" v-model="user.name")
      div.form-group
        input(input id="phone" type="phone" placeholder="聯絡手機" pattern="09[0-9]{8}" maxlength="10" required v-model="user.phone" autocomplete="off")
      div.form-group
        input(id="mail" type="email" required placeholder="Email" v-model="user.email" autocomplete="off")
      div.form-group
        input(id="addr" type="text" required placeholder="請填寫地址"  v-model="user.addr" autocomplete="off")
      div.form-group
        label(for="1")
          input(id="1" type="checkbox" required v-model="user_terms" v-on:click="trans ();!user_terms") 
          | 我已閱讀並同意條款說明
      transition(name="fade")
        div(v-show="trans_terms")
          dl
            dt 個人資料保護事項:
            dd
              ol
                li 依據個人資料保護法，參加本活動者視為瞭解及同意美商3M台灣子公司本於網路省水活動妙招募集及抽獎活動之需要進行蒐集、處理及利用其個人資料(包括電話、e-mail等資訊。具體項目詳如本活動參與頁面及活動辦法內所列事項。) 參加者如欲閱覽、變更、刪除個資或要求美商3M台灣子公司停止蒐集、處理及利用個人資料，請通知美商3M台灣子公司要求辦理。
                li 蒐集個人資料公司: 美商3M台灣子公司及受其委託從事郵寄、運送、活動舉辦、執行研究調查第之第三人。
      div.form-group
        button.btn.btn-primary(type="submit") 送出
</template>

<script>
  export default {
    created () {
      console.log('contact')
    },
    data () {
      return {
        user: {
          nick: '',
          topic: '',
          desc: '',
          name: '',
          phone: '',
          addr: '',
          email: ''
        },
        user_terms: false,
        trans_terms: false
      }
    },
    methods: {
      trans () {
        var vm = this
        if (vm.user_terms === true) {
          vm.trans_terms = true
        } else {
          vm.trans_terms = false
        }
      }
    }
  }
</script>
