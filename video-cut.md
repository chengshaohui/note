```vue
<template>

</template>

<script>
  import Hls from 'my-hls.js'
  import Server from '@/common/js/request.js'

  let $ = require('jquery')
  // 进度条长度
  const progressWidth = 680
  export default {
    name: 'video-cut',
    props: {
      viewData: {
        type: Object
      },
      allSplitJobs: {
        type: Array
      },
      maskData: {
        type: Array
      }
    },
    data() {
      return {
        videoId: this.viewData.fileId,
        videoType: true, // false m3u8, true mp4
        showTileEdit: false,
        appName: this.$root.$data.userInfo.appName,
        activeIndex: -1,
        canvasWidth: 0,
        videoWidth: 0,
        videoHeight: 0,
        vHeight: 386,
        isPlay: false,
        videoEle: null,
        timer: null,
        nowTime: 0,
        allTime: 0,
        currentX: 0,
        startX: 0,
        startY: 0,
        endX: 0,
        endY: 0,
        progressItemWidth: 0,
        progressCutIntoTime: 0,
        progressCutOutTime: 0,
        progressCutIntoLeft: 0,
        progressCutOutLeft: 0,
        progressCutOutWidth: 0,
        maskName: '',
        videoUrl: '',
        maskList: [],
        canvasImg: '',
        activeMaskItem: null
      }
    },
    computed: {},
    methods: {
      // 上一帧
      videoBack() {
        this.pause()
        this.videoEle.currentTime -= 0.04
      },
      // 下一帧
      videoAdvance() {
        this.videoEle.currentTime += 0.04
      },
      // 播放
      startPlay() {
        this.isPlay = true
        this.videoEle.play()
      },
      // 暂停
      pause() {
        this.isPlay = false
        this.videoEle.pause()
      },
      // 基础信息
      baseInfo() {
        setTimeout(() => {
          if (this.maskData.length) {
            this.maskData.forEach(item => {
              let obj = {}
              obj.name = item.name
              obj.left = (item.markTime / this.allTime) * progressWidth
              obj.markTime = item.markTime
              obj.id = item.id
              this.maskList.push(obj)
            })
          }
        }, 500)
        this.videoEle = this.$refs.video
        if (this.viewData.format === 'm3u8') {
          this.videoType = false
          let hls = new Hls()
          hls.loadSource(this.videoUrl)
          hls.attachMedia(this.videoEle)
        } else {
          this.videoType = true
        }
        this.videoEle.load()
        this.videoEle.addEventListener('timeupdate', e => {
          this.nowTime = this.videoEle.currentTime * 1000
          this.progressItemWidth = (this.nowTime / this.allTime) * progressWidth
        })
        this.videoEle.addEventListener('loadedmetadata', e => {
          this.videoWidth = this.videoEle.videoWidth
          this.videoHeight = this.videoEle.videoHeight
          this.canvasWidth = this.videoWidth / this.videoHeight * this.vHeight
        })
      },
      // 拖动进度条
      drag() {
        $('.controls').delegate(this.$refs.progressDot, 'mousedown', (e) => {
          let tempX
          let renderX
          if (this.$refs.progressDot) {
            this.currentX = this.$refs.progressDot.offsetLeft
          }
          this.startX = e.clientX
          this.startY = e.clientY
          $(document).bind('mousemove', (e) => {
            this.endX = e.clientX
            this.endY = e.clientY
            if (Math.abs(this.endY - this.startY) > 10) {
              $(document).unbind('mousemove')
            }
            tempX = this.currentX + (this.endX - this.startX)
            renderX = Math.min(progressWidth - 7, Math.max(0, tempX))
            this.progressItemWidth = renderX
            this.videoEle.currentTime = (renderX / progressWidth * this.allTime) / 1000
          })
          $(document).bind('mouseup', (e) => {
            $(document).unbind('mousemove')
            $(document).unbind('mouseup')
          })
        })
      },
      // 打入点
      progressInto() {
        clearInterval(this.timer)
        this.progressCutIntoTime = this.nowTime
        this.progressCutIntoLeft = (this.nowTime / this.allTime) * progressWidth
        this.timer = setInterval(() => {
          this.progressCutOutWidth = (this.nowTime - this.progressCutIntoTime) / this.allTime * progressWidth
        }, 100)
      },
      // 打出点
      progressOut() {
        clearInterval(this.timer)
        this.progressCutOutWidth = (this.nowTime - this.progressCutIntoTime) / this.allTime * progressWidth
        this.progressCutOutTime = this.nowTime
      },
      // 选段
      doSplit() {
        let param = {}
        param.videoId = this.videoId  // 视频id
        param.name = '片段' + (this.allSplitJobs.length + 1)  // 片段名
        param.startTime = parseInt(this.progressCutIntoTime) // 入点毫秒值
        param.endTime = parseInt(this.progressCutOutTime) // 出点毫秒值
        Server.request('/cloud/split/paragraph', param, () => {
          this.$emit('splitSuccess', true)
        })
      },
      showMask(index, item) {
        this.activeMaskItem = item
        let noneVideo = this.$refs.noneVideo
        noneVideo.currentTime = item.markTime / 1000
        noneVideo.oncanplay = () => {
          this.$refs.canvas.getContext('2d').drawImage(noneVideo, 0, 0, this.canvasWidth, this.vHeight)
          this.canvasImg = this.$refs.canvas.toDataURL('image/png')
          this.activeIndex = index
        }
      },
      // 抓帧
      mask() {
        let param = {}
        let left
        let name
        left = (this.nowTime - this.progressCutIntoTime) / this.allTime * progressWidth
        name = '片段' + (this.maskList.length + 1)
        this.maskList.push({left: left, name: name, markTime: this.nowTime})
        this.showMask(this.maskList.length - 1, this.nowTime)
        param.splitId = this.videoId  // 视频id
        param.name = name  // 关键帧名
        param.markTime = parseInt(this.nowTime)  // 关键帧所在毫秒值
        param.content = ''   // 其它要存的信息(字符串格式)
        Server.request('/cloud/split/doMark', param, (value) => {
          this.$emit('editMarkSuccess', true)
        })
      },
      // mask() {
      //   let param = {}
      //   let left
      //   let name
      //   let canvas
      //   let ctx
      //   let img
      //   canvas = this.$refs.canvas
      //   ctx = canvas.getContext('2d')
      //   ctx.drawImage(this.videoEle, 0, 0, this.canvasWidth, this.vHeight)
      //   img = canvas.toDataURL('image/png')
      //   let blob = this.dataURLtoBlob(img)
      //   this.uploadFile(blob, (imgUrl) => {
      //     left = (this.nowTime - this.progressCutIntoTime) / this.allTime * progressWidth
      //     name = '片段' + (this.maskList.length + 1)
      //     this.maskList.push({left: left, img: img, name: name})
      //     this.activeIndex = this.maskList.length - 1
      //     param.splitId = this.videoId  // 视频id
      //     param.name = name  // 关键帧名
      //     console.log(this.nowTime)
      //     param.markTime = parseInt(this.nowTime)  // 关键帧所在毫秒值
      //     param.content = imgUrl   // 其它要存的信息(字符串格式)
      //     Server.request('/cloud/split/doMark', param, (value) => {
      //       this.$emit('editMarkSuccess', true)
      //     })
      //   })
      // },
      uploadFile(data, completeCallback) {
        Server.request('/cloud/upload/getImgKeyset', {name: 'image.png'}, res => {
          this.upload(res, data, completeCallback)
        })
      },
      upload(keyset, data, completeCallback) {
        let fd = new FormData()
        let key = 'image/cloud/' + keyset.fileName + '.png'
        fd.append('key', key)
        if (keyset.type === 'oss') {
          fd.append('Content-Type', 'image/png')
          fd.append('OSSAccessKeyId', keyset.id)
          fd.append('policy', keyset.policy)
          fd.append('signature', keyset.signature)
        } else {
          fd.append('Signature', keyset.signature)
          fd.append('success_action_status', '200')
        }
        fd.append('file', data)
        let xhr = new XMLHttpRequest()
        xhr.addEventListener('load', () => {
          let result = this.$root.$data.globalSetting.ossVideoUri + key
          completeCallback(result)
        }, false)
        xhr.open('POST', keyset.url, true)
        xhr.send(fd)
      },
      dataURLtoBlob(dataurl) {
        let arr = dataurl.split(',')
        let mime = arr[0].match(/:(.*?);/)[1]
        let bstr = atob(arr[1])
        let n = bstr.length
        let u8arr = new Uint8Array(n)
        while (n--) {
          u8arr[n] = bstr.charCodeAt(n)
        }
        return new Blob([u8arr], {type: mime})
      },
      // 编辑片段名
      confirmEdit() {
        Server.request('/cloud/split/mark/edit', {markId: this.activeMaskItem.id, name: this.maskName}, (res) => {
          this.$emit('editMarkSuccess', true)
          this.showTileEdit = false
        })
      },
      // 编辑标记名称
      titleEdit(name) {
        this.maskName = name
        this.showTileEdit = true
      },
      // 删除编辑
      deleteMask(item) {
        Server.request('/cloud/split/deleteMark', {markId: item.id}, (res) => {
          this.$emit('editMarkSuccess', true)
          this.maskList = this.maskList.filter(val => val !== item)
          this.activeIndex = -1
        })
      }
    },
    mounted() {
      this.baseInfo()
      this.drag()
    },
    created() {
      this.allTime = this.viewData.duration
      this.videoUrl = this.$root.$data.globalSetting.ossDownLoadUri + this.viewData.filePath
    },
    beforeDestroy() {
      clearInterval(this.timer)
    }
  }
</script>

<style scoped lang="scss">
  .video-cut {
    width: 100%;
    background-color: #2B303A;
    .video {
      display: block;
      width: 100%;
      height: 386px;
    }
    .controls {
      position: relative;
      height: 64px;
      text-align: center;
      border-top: 1px solid #6A6A6A;
      .progress {
        position: relative;
        display: inline-block;
        width: 680px;
        height: 6px;
        margin-top: 15px;
        border-radius: 3px;
        background-color: #4c5362;
        .progress-item {
          position: absolute;
          width: 0;
          height: 6px;
          left: 0;
          top: 0;
          background-color: #ff5813;
        }
        .progress-cut-out {
          position: absolute;
          height: 6px;
          top: 0;
          left: 0;
          background-color: #FF9B83;
        }
        .progress-dot {
          position: absolute;
          z-index: 11;
          display: inline-block;
          left: 0;
          top: -5px;
          width: 16px;
          height: 16px;
          border-radius: 50%;
          background-color: #fff;
          border: 2px solid #ff5b1f;
          box-sizing: border-box;
          box-shadow: 0 0 10px rgba(0, 0, 0, .4);
          cursor: pointer;
          &:hover {
            background-color: #ff5b1f;
            border-color: #fff;
          }
        }
        .mask-wrapper {
          position: absolute;
          left: 0;
          top: 0;
          width: 100%;
          .mask-li {
            position: absolute;
            width: 10px;
            height: 20px;
            bottom: -6px;
            background: url("~assets/cut_icon.png") no-repeat -458px -71px;
            .mask-box {
              position: absolute;
              z-index: 100;
              bottom: 20px;
              left: -80px;
              width: 160px;
              padding: 10px;
              background-color: #fff;
              border-radius: 3px;
              .img-area {
                position: relative;
                .delete {
                  position: absolute;
                  top: 0;
                  right: 0;
                  width: 20px;
                  height: 20px;
                  cursor: pointer;
                  background: red url("~assets/cut_icon.png") no-repeat -339px -20px;
                }
              }
              .title-edit {
                display: flex;
                justify-content: space-between;
                .name {
                  font-size: 14px;
                  color: #333;
                  overflow: hidden;
                  display: inline-block;
                  width: 135px;
                  text-overflow: ellipsis;
                  white-space: nowrap;
                  height: 25px;
                  line-height: 25px;
                }
              }
              .mask-name {
                font-size: 12px;
                color: #999;
              }
            }
          }
        }
      }
      .bottom {
        display: flex;
        justify-content: space-between;
        padding: 0 14px;
        box-sizing: border-box;
        .ctl-btn-box {
          display: flex;
          justify-content: space-between;
          width: 160px;
          color: #fff;
          font-size: 26px;
          .ctl-btn {
            display: inline-block;
            cursor: pointer;
            &:hover {
              color: #ff5b1f;
            }
            &.icon-video-mask {
              margin-left: 20px;
            }
          }
        }
        .videoTime {
          color: #fff;
          .nowTime {
            color: #ff5b1f;
          }
        }
      }
    }
  }
  .options {
    display: flex;
    justify-content: space-between;
    margin-top: 12px;
    .left {
      display: flex;
      align-items: center;
      .xgbtn {
        margin: 0;
        &.pitching {
          margin-left: 30px;
        }
      }
      .time-box {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 28px;
        padding: 0 20px;
        margin-left: 8px;
        border: 1px solid #BFBFBF;
        font-size: 14px;
      }
      .opt-line {
        width: 20px;
        height: 0;
        border-top: 1px solid #BFBFBF;
        margin: 0 20px;
      }
    }
  }
  .edit-title {
    background-color: rgba(0, 0, 0, .4);
    .tips {
      margin-top: 12px;
      margin-left: 2px;
      color: #48576a;
      font-size: 14px;
    }
  }
</style>

```

