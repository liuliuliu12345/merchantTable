<template>
  <div>
    <Modal v-model="showmodalBind"
           :title="modalTitle"
           @on-cancel="close"
           :width="560"
           class-name="vertical-center-modal">
      <Form ref="modalForm"
            :model="infoModel"
            :rules="rules"
            @keydown.enter.native="save">
        <Row>
          <i-col span="24">
            <FormItem prop="merchantName"
                      label="商品名称："
                      :label-width="210">
              <Input v-model="infoModel.merchantName"
                     placeholder="请输入商品名称"
                     style="width: 200px;" />
            </FormItem>
          </i-col>
        </Row>
        <Row>
          <i-col span="24">
            <FormItem label="商品价格："
                      prop="merchantMoney"
                      :label-width="210">
              <Input v-model="infoModel.merchantMoney"
                     placeholder="请输入商品价格"
                     style="width: 200px;"
                     number />

            </FormItem>
          </i-col>

        </Row>
        <Row>
          <i-col span="24">
            <FormItem label="购买时间："
                      prop="startTime"
                      :label-width="210">
              <Input v-model="infoModel.startTime"
                     placeholder="请输入购买时间"
                     style="width: 200px;" />

            </FormItem>
          </i-col>

        </Row>

      </Form>
      <div slot="footer">
        <Button type="primary"
                size="large"
                :loading="save_loading"
                @click="save">保存</Button>
      </div>

    </Modal>
  </div>
</template>

<script>
import { Modal, Button, Input, Form, Row, FormItem } from "iview";
export default {
  name: "merchantInfo",
  components: {
    Modal,
    Button,
    Input,
    Form,
    Row,
    FormItem
  },
  props: {
    showmodal: {
      type: Boolean,
      default: false
    },
    infoModel: {
      type: Object,
      default: () => {
        return {};
      }
    }
  },
  data() {
    return {
      showmodalBind: this.showmodal,
      modalTitle: "修改账户信息",
      save_loading: false,
      rules: {
        merchantName: [
          {
            required: true,
            message: "请输入商户名称",
            trigger: "blur"
          }
        ],
        merchantMoney: [
          {
            required: true,
            message: "请输入商户价格",
            trigger: "blur",
            type: "number"
          }
        ],
        startTime: [
          {
            required: true,
            message: "请输入购买时间",
            trigger: "blur"
          }
        ]
      }
    };
  },

  watch: {
    showmodal: {
      handler(val) {
        console.log(val);
        this.showmodalBind = val;
      },
      deep: true
    },
    infoModel: {
      handler(val) {
        console.log(val);
      },
      deep: true
    }
  },
  methods: {
    save() {
      this.$refs.modalForm.validate(valid => {
        if (valid) {
          console.log("123");
        }
      });
    },
    close() {
      this.$emit("update:showmodal", false);
    }
  }
};
</script>

<style lang="scss" scoped>
</style>
