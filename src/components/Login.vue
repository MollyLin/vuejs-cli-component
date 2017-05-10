<template>
	<div id="login">
		<h2>登入</h2>
		<hr>
			<form>
				<div class="form-group">
					<input type = "text" placeholder = "請輸入身份證號碼" maxlength='10' pattern="[A-Z]{9}" required v-model="user.sid">
				</div>
				<div class="form-group">
					<input type = "text" placeholder = "請輸入生日 例:19841234" pattern="[0-9]{8}" maxlength='8' required v-model="user.bir">
				</div>
				<p>驗證碼</p>
				<button type="submit" class = "btn btn-primary"> 登入 </button >
			</form>
	</div>
</template>

<script>
	export default {
		created () {
			console.log('login')
		},
		data () {
			return {
				user: {
					sid: '',
					bir: ''
				}
			}
		}
	}
</script>
