<template>
    <Modal
        v-model="modal1"
        title="输入的信息"
        @on-ok="ok"
        @on-cancel="cancel">
        <p>用户名：{{userId}}</p>
        <p>密码：{{password}}</p>
    </Modal>
</template>
<script>
export default {
    props: ["modal","userId","password"],
  data() {
    return {
      modal1: false
    };
  },
  methods: {
    ok() {
      this.$Message.info("Clicked ok");
      this.$emit('toggleEvent')
    },
    cancel() {
      this.$Message.info("Clicked cancel");
      this.$emit('toggleEvent')
    }
  },
  watch:{
      'modal' (val){
          if(val){
              this.modal1=true;
          }else{
              this.modal1=false;
          }
      }
  }
};
</script>