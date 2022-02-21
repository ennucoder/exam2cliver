<template>
  <div id="app">
    <div>

      <table id="table1" class="table1">
        <tr>
          <th>編集</th>
          
          <th>name</th>
          <th>calories</th>
          <th>sugar</th>
          <th>sodium</th>

        </tr>
        <tr id="tr1">
          <td>
            <button v-on:click="editData(0)" class="btn1">編集</button>
            <button id="btn1" v-on:click="deletefunc($event)" class="btn2">削除</button>
          </td>
          
          <td>{{ name[0]}}</td>
          <td>{{ value[0]}}</td>
          <td>21</td>
          <td>34</td>
        </tr>
        <tr id="tr2">
          <td>
            <button v-on:click="editData(1)" class="btn1">編集</button>
            <button id="btn2" v-on:click="deletefunc($event)" class="btn2">削除</button>
          </td>
         
          <td>{{ name[1]}}</td>
          <td>{{ value[1]}}</td>
          <td>21</td>
          <td>34</td>
        </tr>
        <tr id="tr3">
          <td>
            <button v-on:click="editData(2)" class="btn1">編集</button>
            <button id="btn3" v-on:click="deletefunc($event)" class="btn2">削除</button>
          </td>
        
          <td>{{ name[2]}}</td>
          <td>{{ value[2]}}</td>
          <td>21</td>
          <td>34</td>
        </tr>
        <tr id="tr4">
          <td>
            <button v-on:click="editData(3)" class="btn1">編集</button>
            <button id="btn4" v-on:click="deletefunc($event)" class="btn2">削除</button>
          </td>
         
          <td>{{ name[3]}}</td>
          <td>{{ value[3]}}</td>
          <td>21</td>
          <td>34</td>
        </tr>
        <tr id="tr5">
          <td>
            <button v-on:click="editData(4)" class="btn1">編集</button>
            <button id="btn5" v-on:click="deletefunc($event)" class="btn2">削除</button>
          </td>
        
          <td>{{ name[4]}}</td>
          <td>{{ value[4]}}</td>
          <td>21</td>
          <td>34</td>
        </tr>
      </table>
    </div>

    <div class="modal" v-if="number">
      <div>name</div>
      <textarea id="textarea1" class="textarea"></textarea>
      <div>calories</div>
      <textarea id="textarea2" class="textarea"></textarea>
      <div class="toright">
      <button class="modalClose" v-on:click="updatatable">編集完了</button>
      </div>
    </div>
    <div>
      <div class="mask" v-if="number"></div>
    </div>
    
    
  </div>
</template>

<script>


export default {
  el:'#app',
  data(){
    return{
      number: 0,
      tr1: 1,
      tr2: 1,
      tr3: 1,
      tr4: 1,
      tr5: 1,
      
      name:[
        'リンゴ',
        'イチゴ',
        'バナナ',
        'キウイ',
        'オレンジ',
        ],
      value: [
        '1000',
        '2300',
        '3221',
        '420',
        '756',
        ],
        hanteichi1: '',
        hanteichi2: '',
        element1: '',
        element2: '',
        wherenumber1: 0,
        tableinfo:'',
        table1info:'',
        elementrownumber:0,
        some:'',
        someinfo:'',
        someinfoparent:'',
        element:'',

    }
  },
  methods:{
    editData: function (e) {
    this.number = 1
    console.log(e)
    this.hanteichi1 = e
    console.log(this.hanteichi1)

    },
    updatatable: function () {
    this.number = 0
    this.element1 = document.getElementById('textarea1')
    this.element2 = document.getElementById('textarea2')

    this.wherenumber1 = this.hanteichi1

    this.name[this.wherenumber1] = this.element1.value
    this.value[this.wherenumber1] = this.element2.value
    },
    deletefunc: function (event) {
    this.some = event.target.id
    this.someinfo = document.getElementById(this.some)

    this.someinfoparent = this.someinfo.parentElement

    this.someinfograndparent = this.someinfoparent.parentElement


    this.tableinfo = this.someinfograndparent.id
    this.element = document.getElementById(this.tableinfo)

    this.elementrownumber = this.element.rowIndex


    this.table1info = document.getElementById('table1')
    this.table1info.deleteRow(this.elementrownumber)
    }


  },

}
</script>

<style>
.app1{
    
    padding: 20px;
    border-radius: 5px;
    
    
    height: 200vh;
    width: 100%;

    
}
.modal{
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #fff;
    padding: 20px;
    border-radius: 5px;
    min-width: 500px;
    z-index: 2;
    

}
.mask{
    position: fixed;
    top:0;
    left:0;
    width:100%;
    height: 100%;
    background-color: black;
    opacity: 0.7;
    z-index: 1;
}
.textarea{
    resize: none;
    width:500px;
    height:80px
}
.table1{
    width: 100%;
    text-align: center;
    border-collapse: collapse;
    border-spacing: 0;
    width: 100%;


}
.table1 th {
    padding: 10px;
    border-bottom: solid 4px #778ca3;
    color: #778ca3
   }
   .table1 td {
    padding: 10px;
    border-bottom: solid 1px #778ca3;
   }
.btn1{
    border: 1px solid #09f;
    color:#09f;
}
.btn2{
    border: 1px solid #f30;
    color:#f30;
}
.modalClose{
    
    text-align: right;

    
}
.toright{
    text-align: right;
}
</style>
