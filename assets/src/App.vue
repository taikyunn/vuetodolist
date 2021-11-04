<template>
  <div id="app">
    <h1>ToDoList</h1>
    <div>
      <label for="title">タイトル:</label>
      <input type="text" v-model="title" placeholder="タイトル">
    </div>
    <div>
      <label for="body">内容：</label>
      <input type="text" v-model="body" placeholder="内容">
    </div>
    <div>
      <input type="submit" value="追加" @click="addList">
    </div>
    <ul v-for="(list, i) in lists" v-bind:key='i'>
      <li>タイトル：{{list.title}}
          内容：{{list.body}}
          <button @click="deleteList(i)">削除</button>
      </li>
    </ul>
  </div>
</template>

<script>

export default {
  data:() => ({
    lists:[
      {title: 'mytodo',body:'test'}
    ]
  }),
  methods: {
    addList: function() {
      //push 配列に値を追加するときに使用する
      this.lists.push({title:this.title, body:this.body})
      this.title = ''
      this.body = ''
    },
    deleteList: function(i) {
      // splice:要素の変更に使用
      // 要素の変更構文：<配列>.splice(<始まりのインデックス>, <変更する要素数>, <変更後の要素>)
      // 要素の削除構文：<配列>.splice(<始まりのインデックス>, <削除する要素数>)
      this.lists.splice(i,1)
    }
  }
}
</script>

