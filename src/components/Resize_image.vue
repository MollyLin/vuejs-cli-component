<template lang="jade">
  div#resize_image
    h2 Image Upload Preview
    form
      input#js_input-upload(type="file" accept=".png,.jpg,.jpeg" v-on:change="input_onFileChange" v-show="!imgSrc")
      img#js_img-preview(v-bind:src="imgSrc" v-show="imgSrc")
      div(v-show="imgSrc")
        a#js_up.btn.btn-default(href="javascript:void(0);") 上
        a#js_down.btn.btn-default(href="javascript:void(0);") 下
        a#js_left.btn.btn-default(href="javascript:void(0);") 左
        a#js_right.btn.btn-default(href="javascript:void(0);") 右
</template>



<script>
  export default {
		created () {
			console.log('resize_image')
		},
    data () {
      return {
        imgSrc: ''
      }
    },
    methods:{
      input_onFileChange(e) {
        var files = e.target.files || e.dataTransfer.files;
        if (!files.length) return;
        this.input_createImg(files[0]);
      },
      input_createImg(file) {
        var img = new Image();
        var reader = new FileReader();
        var vm = this;
        reader.onload = (e) => {
            vm.imgSrc = e.target.result;
        };
        reader.readAsDataURL(file);
      }
    }
  }
</script>