<script>
import canvasResize from "./canvas-resize";
export default {
  methods: {
    imgFilter(fileName) {
      // eslint-disable-next-line
      return /^(?:image\/bmp|image\/cis\-cod|image\/gif|image\/ief|image\/jpeg|image\/jpeg|image\/jpeg|image\/png|image\/pipeg|image\/svg\+xml|image\/tiff|image\/x\-cmu\-raster|image\/x\-cmx|image\/x\-icon|image\/x\-portable\-anymap|image\/x\-portable\-bitmap|image\/x\-portable\-graymap|image\/x\-portable\-pixmap|image\/x\-rgb|image\/x\-xbitmap|image\/x\-xpixmap|image\/x\-xwindowdump)$/i.test(
        `${fileName}`
      )
        ? ""
        : "上传图片格式不正确，请重新上传";
    },
    upload() {
      const target = this.$refs.target;
      const file = target.files[0];
      if (!file) return;
      // 适配中兴手机和部分安卓机型原生浏览器，上传图片后中兴手机自带浏览器会将图片类型的文件的type清空并将文件名后缀去除，部分安卓机型会清空图片类型文件的type
      let fileType = file.type;
      if (!fileType) {
        // type为空时生成一个新的type
        let imgName = file.name;
        let imgType = imgName.split(".").pop().toLowerCase();
        if (imgType === "jpg" || imgName.split(".").length === 1) {
          // 中兴手机会将文件名后缀去除，所以imgName.split(".").length等于1，此时强制将其type设为jpeg
          imgType = "jpeg";
        }
        fileType = "image/" + imgType;
      }
      const error = this.imgFilter(fileType);
      if (error) {
        this.tips = error;
        return;
      }
      if (file.size > "5000000") {
        this.tips = "上传图片不能超过5M, 请重新上传";
        return;
      }
      this.tips = "";
      this.$loading.show();
      const q = new Promise((resolve) => {
        canvasResize(file, {
          width: 1200,
          height: 1200,
          crop: false,
          quality: 80,
          rotate: 0,
          callback: (data) => {
            resolve(data);
          },
        });
      });
      q.then((src) => {
        return Promise.resolve(src);
      })
        .then((src) => {
          return uploadImg(src, this.imgType);
        })
        .then(
          (re) => {
            const url = re.replace(/https?:\/\//, "https://");
            typeof this.callback === "function" && this.callback(url);
            this.init = false;
            this.show = false;
          },
          (e) => {
            this.tips = e.msg || e;
          }
        );
    },
  },
};
</script>