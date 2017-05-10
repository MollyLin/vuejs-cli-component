<template>
  <div id="register">
    <h2>註冊</h2>
    <hr>
    <form>
      <div class="form-group">
        <input type="text" placeholder="請輸入身份證號碼 例:A123456789"   maxlength='10'  title="請填入正確身份證字號" pattern="[A-Z]{9}" autofocus  v-model="sign.sid" required />
      </div>
      <div class="form-group">
        <input type="email" placeholder="E-Mail  例:123@gmail.com" v-model="sign.mail"  pattern="^[a-zA-Z0-9._+-]+&#64;[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$" required />
      </div>
      <div class="form-group">
        <input type="tel" placeholder="手機號碼  例: 0912XXXXXX" pattern="09[0-9]{8}" maxlength='10' title="請填入有效的手機號碼" v-model="sign.phone" required />
      </div>
      <div class="form-group">
        <p>驗證碼</p>
      </div>
      <div class="form-group">
        <button type="submit" class="btn btn-primary">送出</button>
      </div>
    </form>
  </div>
</template>

<script>
  export default {
    created () {
      console.log('register')
    },
    data () {
      return {
        sign: {
          sid: '',
          mail: '',
          phone: ''
        }
      }
    }
  }
</script>
