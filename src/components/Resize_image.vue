<template lang="jade">
  div#resize_image
    h2 Image Upload Preview
    hr
    form
      div.upload__box
        img#js_img-preview(v-bind:src="imgSrc" v-show="imgSrc")
        input#js_input-upload(type="file" accept=".png,.jpg,.jpeg" v-on:change="input_onFileChange" v-show="!imgSrc")
      div(v-show="imgSrc")
        a#js_up.btn.btn-default(href="javascript:void(0);") 上
        a#js_down.btn.btn-default(href="javascript:void(0);") 下
        a#js_left.btn.btn-default(href="javascript:void(0);") 左
        a#js_right.btn.btn-default(href="javascript:void(0);") 右
        a#js_rotate.btn.btn-default(href="javascript:void(0);") 旋轉
        a.input_upload-re.btn.btn-default(href="javascript:void(0);") 重傳
        input#js_upload-re(type="file" accept=".png,.jpg,.jpeg" v-on:change="input_onFileChange" v-show="input_hide")
        a#js_zoom-in.btn.btn-default(href="javascript:void(0);") ZoomIn
        a#js_zoom-out.btn.btn-default(href="javascript:void(0);") ZoomOut
        a#js_fit.btn.btn-default(href="javascript:void(0);") Fit
</template>

<script>
  import $ from 'jquery'
  import guillotine from 'guillotine'

  $(document).ready(function() {
    $('.input_upload-re').click(function() {
        $('#js_upload-re').trigger("click");
    });
    jQuery(function() {
      var $preview = $('#js_img-preview');
      $preview.on('load', function() {
          $preview.guillotine("remove");
          $preview.guillotine({
              width: 400,
              height: 400
          });
          $preview.guillotine('fit');
          for (var i = 0; i < 5; i++) {
              $preview.guillotine('zoomIn')
          };
          var data = $preview.guillotine('getData');
          for (var key in data) {
              $('#' + key).html(data[key]);
          }
          $('#js_up').click(function() {
              $preview.guillotine('move', {
                  y: 30
              });
          });
          $('#js_down').click(function() {
              $preview.guillotine('move', {
                  y: -30
              });
          });
          $('#js_left').click(function() {
              $preview.guillotine('move', {
                  x: 30
              });
          });
          $('#js_right').click(function() {
              $preview.guillotine('move', {
                  x: -30
              });
          });

          $('#js_rotate').click(function() {
              $preview.guillotine('rotateRight');
          });
          $('#js_zoom-in').click(function() {
              $preview.guillotine('zoomIn');
          });
          $('#js_zoom-out').click(function() {
              $preview.guillotine('zoomOut');
          });
          $('#js_fit').click(function() {
              $preview.guillotine('fit');
          });
          $preview.on('guillotinechange', function(ev, data, action) {
              data.scale = parseFloat(data.scale.toFixed(6));
              for (var k in data) {
                  $('#' + k).html(data[k]);
              }
          });
          //if ($preview.prop('complete')) $preview.trigger('load')
      });
    });
  });

  export default {
		created () {
			console.log('resize_image')
		},
    data () {
      return {
        imgSrc: '',
        input_hide: false
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

<style lang="scss" scoped>
  @import '~guillotine/css/jquery.guillotine.css';
  .upload__box {
    width: 400px;
    height: 400px;
    background-color: #dadada;
    position: relative;
    overflow: hidden;
    margin: 0 10px 10px 10px;
  }
</style>