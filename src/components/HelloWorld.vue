<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <!-- <hello :infoMethods.sync="infoMethods" /> -->
    <div class="inputBox">
      <div class="inlineBlock">
        商品名称：
        <Input clearable
               type="text"
               style="width: 160px;"
               placeholder="请输入商品名称" />
      </div>
      <div class="inlineBlock mleft20">
        商品价格：
        <Input clearable
               type="text"
               style="width: 160px;"
               placeholder="请输入商品价格" />
      </div>
      <div class="inlineBlock mleft20">
        购买日期：
        <DatePicker type="date"
                    style="width: 160px"
                    placeholder="请选择购买日期"></DatePicker>
      </div>

      <div class="inlineBlock mleft20">
        <Button type="primary"
                icon="ios-loading">保存</Button>
      </div>
    </div>

    <div class="tableBox">
      <Card style="height: 400px">
        <Table stripe
               :height="screenHeight"
               :columns="columns"
               :data="reqDataList"
               ref="table"
               size="small">
          <template slot-scope="{ row }"
                    slot="name">
            <strong>{{ row.name }}</strong>
          </template>
          <template slot-scope="{ row }"
                    slot="action">
            <Button type="primary"
                    size="small"
                    style="margin-right: 5px"
                    @click="editOperate(row)">修改</Button>

            <Button @click="deleteData(row)"
                    type="warning"
                    size="small">删除</Button>
          </template>

        </Table>
      </Card>
    </div>
  </div>
</template>

<script>
import { columnTable } from "./columns";
import { Input, DatePicker, Button, Card, Table } from "iview";
// import hello from "./hello";
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  components: {
    // hello,
    Input,
    DatePicker,
    Card,
    Table,
    Button
  },
  data() {
    return {
      screenHeight: 368,
      infoMethods: "hello,vue",
      columns: columnTable(),
      reqDataList: [
        {
          merchantName: "John Brown",
          merchantMonth: 18,
          startTime: "2019-6-7"
        },
        {
          merchantName: "John Brown",
          merchantMonth: 18,
          startTime: "2019-6-7"
        },
        {
          merchantName: "John Brown",
          merchantMonth: 18,
          startTime: "2019-6-7"
        },
        {
          merchantName: "John Brown",
          merchantMonth: 18,
          startTime: "2019-6-7"
        },
        {
          merchantName: "John Brown",
          merchantMonth: 18,
          startTime: "2019-6-7"
        },
        {
          merchantName: "John Brown",
          merchantMonth: 18,
          startTime: "2019-6-7"
        },
        {
          merchantName: "John Brown",
          merchantMonth: 18,
          startTime: "2019-6-7"
        },
        {
          merchantName: "John Brown",
          merchantMonth: 18,
          startTime: "2019-6-7"
        },
        {
          merchantName: "John Brown",
          merchantMonth: 18,
          startTime: "2019-6-7"
        },
        {
          merchantName: "John Brown",
          merchantMonth: 18,
          startTime: "2019-6-7"
        }
      ]
    };
  },
  methods: {
    deleteData() {},
    editOperate(index) {
      this.data.splice(index, 1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.inlineBlock {
  display: inline-block;
  /* width: 200px; */
}

.mleft20 {
  margin-left: 20px;
}
.inputBox {
  margin-top: 30px;
}
.tableBox {
  margin-top: 30px;
  margin-left: 5%;
  width: 90%;
}
</style>
