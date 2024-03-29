*问题1**:

  vue中使用iview选择器模板一直发出警告;
已解决:子option添加value值.

**问题2**:

  eslint校验工具默认cols是自动闭合标签,end-tag会报错
**原因:**

   iview将标签渲染成原生html标签时,这些标签是自动闭合的.所有有闭合标签会报错
**已解决:**

   修改配置文件:eslintrc.js-rules添加

   “vue/no-parsing-error”: [2, { “x-invalid-end-tag”: false }]
​    重启 npm run dev
**最终解决方案** :关闭eslint校验

​    在vscode菜单中，文件->首选项->设置
找到 “vetur.validation.template”: true 将其改为false，就可关闭eslint的检查，错误消失



**问题10**:   token超时刷新的问题

目前(token过期不会自动刷新,导致token过期不能去请求别的页面)

 已解决: 

1:token过期自动退出(不可行)

2:[判断用户是否在活跃期(实现无缝刷新)](https://www.cnblogs.com/laozhang-is-phi/p/10462316.html#autoid-1-0-0)



**记录1:** 

put方法请求体是data

post方法请求体是parmas

请求体错误-415

请求参数解构错误-404

请求参数错误 - 400

**记录2:**  tree组件点击树高亮

[[iview 中tree组件使用render自定义内容树显示问题]](https://segmentfault.com/q/1010000013668855/a-1020000015863793)

```
renderContent (h, { root, node, data }) {
      return h('span', {
        style: {
          display: 'inline-block',
          padding: '5px 10px',
          width: '100%',
          cursor: 'pointer'
        },
        domProps: {
          className: 'btn'
        },
        on: {
          click: (e) => {
            console.log(e)
            let btns = this.$refs.tree.$el.querySelectorAll('.btn')
            for (let i = 0; i < btns.length; i++) {
              btns[i].style.backgroundColor = '#fff'
            }
            // let btns = this.$refs.tree.$el.querySelectorAll('.ivu-tree-children')
            // for (let i = 0; i < btns.length; i++) {
            //   btns[i].style.backgroundColor = '#fff'
            // }
            // e.path[2].style.backgroundColor = '#2db7f5'// 当前点击的元素
            e.path[0].style.backgroundColor = '#2db7f5'// 当前点击的元素
            this.table(data)
          }
        }
      }, data.depName)
    },
```

**记录3** iview自定义验证器的问题

[验证示例](https://blog.csdn.net/IT_hejinrong/article/details/79170351)

**记录4:**  表单自定义验证问题-1.png

![](D:\Project\markdown\1.png)

**记录5:**  [时间范围验证](https://blog.csdn.net/IT_hejinrong/article/details/79170351)

**记录6:** 正则表达式

示例: [常用正则](https://www.cnblogs.com/bluesky1024/p/8609196.html)   [常见密码验证](http://www.aijquery.cn/Html/jqueryjiqiao/200.html)  [必须包含数字,字母,特殊符号中至少俩种](http://www.aijquery.cn/Html/jqueryjiqiao/200.html)

模板: [菜鸟工具](https://c.runoob.com/front-end/854)

**记录7:** 登录组件传userId

  动态传参,组件传值不可行,解决方法localstorage

**记录8**: 子级默认不展开 - 2.png

![](C:\Users\admin\Desktop\markdown\2.png)

![](D:\Project\markdown\2.png)

**记录9:**  人员编辑-部门下拉框 -3.png

![](D:\Project\markdown\3.png)

**记录10:** 人员基本信息,只显示不可编辑,取消保存按钮 - 4.png,5.png

![](D:\Project\markdown\4.png)

![](D:\Project\markdown\5.png)

**记录11:** new Date+ 20minutes- 6.png

![](D:\Project\markdown\6.png)

**记录12:** - token --login.vue -7.png

![](D:\Project\markdown\7.png)

api.js(调用,request=>http.request,routerbeforeeach) -8.png

![](D:\Project\markdown\8.png)

response=> 判断浏览器返回的状态码 -9.png

![](D:\Project\markdown\9.png)



**记录13:** [http状态码](https://www.jianshu.com/p/b23e2ea636f2)

**记录14:** [IE不支持es6语法:](https://blog.csdn.net/Calla_Lj/article/details/84402221)

解决:  1:npm install --save babel-polyfill 或者 yarn add babel-polyfill - 

2: ![](C:\Users\admin\Desktop\markdown\10.png)   10.png,

![](D:\Project\markdown\10.png)

3: 11.png ![](C:\Users\admin\Desktop\markdown\11.png)

![](D:\Project\markdown\11.png)

**记录15:** table的render函数checkbox默认选中  12.png

![](D:\Project\markdown\12.png)

**记录16**: 下载文件 - 13.png

![](D:\Project\markdown\13.png)

**记录17**: 上传文件 - 14.png

![](D:\Project\markdown\14.png)

**记录18:** 设置文件夹权限

```
<!-- 设置文件夹权限对话框 -->
      <Modal
        width='1082px'
        v-model='permodal'
        :title='pername'
        @on-ok="ok"
        @on-cancel="cancel">
        <Table :columns="Percolumns" :data="Perdata"></Table>
        <Checkbox style="float: right; margin-top: 20px" v-model="SelectedPermission.allSubFolder">应用到子文件夹</Checkbox>
      </Modal>
```

**记录19:** axios get方法传递数组

```js

// 在request拦截器里面添加下面的代码,(qs库,axios安装自带的)
if(config.method === 'get'){
// 如果是get请求，且params是数组类型如arr=[1,2]，则转arr=1&arr=2
   config.paramsSerializer = function(params) {
      return qs.stringify(params, {arrayFormat: 'repeat'})
   }
}
```

**记录20:**  [qs库](https://segmentfault.com/q/1010000010323643)

qs是一个url参数转化（parse和stringify）的js库。

将url中的参数转为对象；

将对象转为url参数形式

```js
import qs from 'qs';
const url = 'method=query_sql_dataset_data&projectId=85&appToken=7d22e38e-5717-11e7-907b-a6006ad3dba0';
// 转为对象
console.log(qs.parse(url));
const a = {name:'hehe',age:10};
// 转为url参数形式
console.log(qs.stringify(a))
// 输出 name=hehe&age=10
```

**记录21:** 执行npm run build 报错

原因: 之前执行过npm audit fix 和 npm audit 升级了所有安装的依赖项,但是和webpack打包版本冲突

解决方案: 还原以前的版本. 附上[链接](https://www.jianshu.com/p/3f8f60e01797)



**知识1:** vue中的watch函数

​    [watch监测的是一个对象的话,可以借助于computed计算属性来完成](https://www.cnblogs.com/jin-zhe/p/9319648.html)

对象需要借助computed

数组的变化不需要深度监听

对象内部的属性监听(深度监听)



**知识3**:  获取tree的整条数据链

```
Array.prototype.remove = function (val) {
        let index = this.indexOf(val)
        if (index > -1) {
          this.splice(index, 1)
        }
      }
      function getParent (array, childs, ids) {
        for (let i = 0; i < array.length; i++) {
          let item = array[i]
          if (Number(item.id) === Number(ids)) {
            childs.push(item)
            return childs
          }
          if (item.children && item.children.length > 0) {
            childs.push(item)
            let rs = getParent(item.children, childs, ids)
            if (rs) {
              return rs
            } else {
              childs.remove(item)
            }
          }
        }
        return false
      }
      let params = this.$refs.editTree.getCheckedNodes()
      console.log(params)
      let allData = this.AllTree
      let arr1 = []
      for (let i = 0; i < params.length; i++) {
        let aData = getParent(allData, [], params[i].id)
        for (let y = 0; y < aData.length; y++) {
          arr1.push(aData[y])
        }
      }
      function dedupe (array) {
        return Array.from(new Set(array))
      }
      arr1 = dedupe(arr1)
      console.log(arr1)
      var perArr = []
      for (var i = 0; i < arr1.length; i++) {
        perArr.push(arr1[i].id)
      }
      const EditperArrs = dedupe(perArr)
      this.Editpermissions = EditperArrs
      console.log(this.Editpermissions)
```

**需求1:** 用户密码连续输入三次错误,锁定账号10分钟

解决: 后台操作

**知识4:** 权限控制按钮

```
if (this.permissions.indexOf(`${event.target.innerText}`) > -1) {
      } else {
        this.Editdis = true
        return this.$Message.error('抱歉,您暂无权限操作~')
      }
```



知识5: Git基本指令 - Git.png

![](D:\Project\markdown\Git.png)



