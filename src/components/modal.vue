<template>
    <Modal
        v-model="modal1"
        title="Common Modal dialog box title"
        @on-ok="ok"
        @on-cancel="cancel">
        <p>Content of dialog</p>
        <p>Content of dialog</p>
        <p>Content of dialog</p>
    </Modal>
</template>
<script>
export default {
    props: ["modal"],
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