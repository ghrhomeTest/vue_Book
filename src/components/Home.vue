<template>
    <Form ref="formInline" :model="formInline" :rules="ruleInline" inline>
        <FormItem prop="user">
             <InputNumber :max="100" :min="0" :step="1" v-model="formInline.user"></InputNumber>
        </FormItem>
        <FormItem prop="password">
           <InputNumber :max="100" :min="0" :step="1" v-model="formInline.password"></InputNumber>
        </FormItem>
        <FormItem>
            <Button type="primary" @click="handleSubmit('formInline')">登录</Button>
        </FormItem>
        <Button type="primary" @click="showModal()">显示遮罩层</Button>
        <Xmodal :modal="xmodal" @toggleEvent="colseModal()" :userId="formInline.user" :password="formInline.password"></Xmodal>
    </Form>
</template>
<script>
import Xmodal from "@/components/modal";
export default {
  data() {
    const user = (rule, value, callback) => {
      if (value == 0) {
        callback(new Error("用户名不能为空"));
      } else {
        callback();
      }
    };
    const password = (rule, value, callback) => {
      if (value == 0) {
        callback(new Error("密码不能为空"));
      } else {
        callback();
      }
    };
    return {
      xmodal: false,
      formInline: {
        user: 0,
        password: 0
      },
      ruleInline: {
        user: [{ required: true, validator: user, trigger: "change" }],
        password: [{ required: true, validator: password, trigger: "change" }]
      }
    };
  },
  components: {
    Xmodal
  },
  methods: {
    handleSubmit(name) {
      this.$refs[name].validate(valid => {
        if (valid) {
          this.$Message.success("Success!");
        } else {
          this.$Message.error("Fail!");
        }
      });
    },
    showModal() {
            this.xmodal = true; 
    },
    colseModal(){
         this.xmodal = false;
    }
  }
};
</script>