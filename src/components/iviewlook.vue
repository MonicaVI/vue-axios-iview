<template>
    <div>
      <div>
        <Select v-model="model8" clearable style="width:200px">
          <Option v-for="item in cityList" :value="item.value" :key="item.value">{{ item.label }}</Option>
        </Select>
        <Button type="primary" shape="circle" icon="ios-search" @click="getmessage"></Button>
      </div>
      <!--<p v-for="re in results">{{re.title}}<br/>{{re.text}}</p>-->
      <div class="columns medium-3" v-for="result in results">
        <div class="card">
          <div class="card-divider">
            {{ result.title }}
          </div>
          <div class="card-section">
            <p>{{ result.text }}</p>
          </div>
        </div>
      </div>
    </div>
</template>
<style>

</style>
<script>

    export default {
      name: 'iviewlook',
      data() {
        return {
          cityList: [
            {
              value: 'cmccgx',
              label: '中国移动'
            },
            {
              value: '10010',
              label: '中国联通'
            },
            {
              value: '96301',
              label: '中国电信'
            }
          ],
          model8: '',
          results: ''
        }
      },
      methods:{
        formatterDateTime() {
          var date=new Date()
          var month=date.getMonth() + 1
          var datetime = date.getFullYear()
            + ""// "年"
            + (month >= 10 ? month : "0"+ month)
            + ""// "月"
            + (date.getDate() < 10 ? "0" + date.getDate() : date
              .getDate())
            + ""
            + (date.getHours() < 10 ? "0" + date.getHours() : date
              .getHours())
            + ""
            + (date.getMinutes() < 10 ? "0" + date.getMinutes() : date
              .getMinutes())
            + ""
            + (date.getSeconds() < 10 ? "0" + date.getSeconds() : date
              .getSeconds());
          return datetime;
        },
        getmessage(){
          var url = "http://route.showapi.com/341-1?showapi_appid=50343&showapi_timestamp="+this.formatterDateTime()+"&showapi_sign=4ff12d5d56e547578d669e9071126c76&page=1&maxResult=20&"
          this.$ajax
            .get(url)
/*          ({
            type: 'get',
            url: 'https://route.showapi.com/341-1',
            data: {
              showapi_timestamp: this.formatterDateTime(),
              showapi_appid: '50343',
              showapi_sign: '4ff12d5d56e547578d669e9071126c76'
            },
            timeout:5000
          })*/
            .then(response => {
            var json = response.data;
            var obj = eval(json);
            this.results = obj.showapi_res_body.contentlist
            console.log(this.results[0].title)
          })
        }
      },
    }
</script>
