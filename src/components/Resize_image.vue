<template lang="jade">
  div#resize_image
    h2 Image Upload Preview
    hr
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
  $(document).ready(function() {
    jQuery(function() {
      var $preview = $('#js_img-preview');
      $preview.on('load', function() {
          $preview.guillotine("remove");
          $preview.guillotine({
              width: 300,
              height: 300
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
              console.log('upup');
              $preview.guillotine('move', {
                  y: -30
              });
          });
          $('#js_down').click(function() {
              $preview.guillotine('move', {
                  y: 30
              });
          });
          $('#js_left').click(function() {
              $preview.guillotine('move', {
                  x: -30
              });
          });
          $('#js_right').click(function() {
              $preview.guillotine('move', {
                  x: 30
              });
          });

          $('#turnRight').click(function() {
              $preview.guillotine('rotateRight');
          });
          $('#turnLeft').click(function() {
              $preview.guillotine('rotateLeft');
          });
          $('#zoomIn').click(function() {
              $preview.guillotine('zoomIn');
          });
          $('#zoomOut').click(function() {
              $preview.guillotine('zoomOut');
          });
          $('#reset').click(function() {
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