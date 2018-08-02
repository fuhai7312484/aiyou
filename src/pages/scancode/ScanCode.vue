<template>
  <div id="query">
    <h1>二维码：</h1>
    <canvas id="canvas"></canvas>
  </div>

</template>

<script type='text/ecmascript-6'>
import QRCode from 'qrcode'
  // let scan = null;

  export default {
    name:'ScanCode',
    data() {
      return {
        msg: 'Welcome to Your Vue.js App',
        config: {
            value: 'https://www.baidu.com',
            imagePath: './examples/assets/logo.png',
            filter: 'color'
        },
        downloadButton: false
      }
    },
    mounted() {
      console.log('执行到这了')
      this.useqrcode();
    },
  methods:{
        useqrcode(){ 
      //生成的二维码内容，可以添加变量
　　　　this.QueryDetail='http://www.kspxzx.com/#/guard'+"?unique_code="+this.QueryDetail;var canvas = document.getElementById('canvas')
        QRCode.toCanvas(canvas, this.QueryDetail, function (error) {
        if (error) console.error(error)
        console.log('success!');
        })
    }
    },
    //动态生成二维码
  
    // methods: {
    //   //创建扫描控件
    //   startRecognize() {
    //     let that = this;
    //     if (!window.plus) return;
    //     scan = new plus.barcode.Barcode('bcid');
    //     scan.onmarked = onmarked;

    //     function onmarked(type, result, file) {
    //       switch (type) {
    //         case plus.barcode.QR:
    //           type = 'QR';
    //           break;
    //         case plus.barcode.EAN13:
    //           type = 'EAN13';
    //           break;
    //         case plus.barcode.EAN8:
    //           type = 'EAN8';
    //           break;
    //         default:
    //           type = '其它' + type;
    //           break;
    //       }
    //       result = result.replace(/\n/g, '');
    //       that.codeUrl = result;
    //       alert(result);
    //       that.closeScan();

    //     }
    //   },
    //   //开始扫描
    //   startScan() {
    //     if (!window.plus) return;
    //     scan.start();
    //   },
    //   //关闭扫描
    //   cancelScan() {
    //     if (!window.plus) return;
    //     scan.cancel();
    //   },
    //   //关闭条码识别控件
    //   closeScan() {
    //     if (!window.plus) return;
    //     scan.close();
    //   },
    // }
  }
</script>
<style lang="stylus">
  #canvas{
    width: 80%!important;
    height: auto!important;
  }
</style>