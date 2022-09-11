## VUE 父子模块之间的参数调用

- 父模块向子模块传递

  1. 在父模块使用`v-bind:`标签传递参数
     ```vue
     <UserProfileInfo :user="user"/>
     ```

  2. 在子模块用props接受

     - 使用对象接受

       ```javascript
       export default {
           props: {
               user: {
                   type: Object,
                   required: true
               }
           }
       }
       ```

     - 使用数组接受
       ```javascript
       props: ['inventory', 'addToCart']  // 方法也可以作为传递的对象，这也可以作为修改父级对象的参数的方法
       ```

- 子模块修改父模块的数据

  1. 父模块传入参数
     ```vue
     @Param method1 -> 子模块触发的函数
     @Param method2 -> 父模块对应的函数
     <father @method1="method2" />
     ```

  2. 子模块调用父模块的函数
     ```vue
     <button @click="method3" > click </button>
     
     <script>
     export default {
         setup(props, context) {
             const method3 = () => {
                 context.emit('method1')
             },
             return {
                 method3
             }
         }
     }
     </script>
     ```

     