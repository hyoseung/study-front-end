# 비동기 예제

## `created`에서 `async` `await`

-&gt; created에서 async await를 사용하면 호출완료된 다음 mounted가 호출되지 않음 \(주의\)

```javascript
async created() {
    console.log('[created] start');
    this.$store.commit('order/setSelectedProductList', []); // 데이터 초기화

    let params = {
        searchCode: "all",
        searchKeyword: ""
    };
    
    try {
        var data = await API.GET_ALL_PRODUCTS(params);
        this.productList = data.data;
        console.log('[created] async await complete');
    } catch (error) {
        console.log(error);
        this.$emit('fnSearchProductResult', []);
    }

    console.log('[created] end');
},
mounted() {
    console.log('[mounted]');
},
```

![](../../../.gitbook/assets/image%20%2823%29.png)

## `created`에서 `Promise`

```javascript
created() {
    console.log('[created] start');
    this.$store.commit('order/setSelectedProductList', []); // 데이터 초기화

    let params = {
        searchCode: "all",
        searchKeyword: ""
    };

    API.GET_ALL_PRODUCTS(params)
         .then(res => {
             this.productList = res.data;
             console.log('[created] Promise complete');
         })
         .catch(err => {
             this.$emit('fnSearchProductResult', []);
             console.log(err);
         });

    console.log('[created] end');
},
mounted() {
    console.log('[mounted]');
},
```

![](../../../.gitbook/assets/image%20%2824%29.png)

## 일반함수에서 `async` `await`

```javascript
<button @click="testAsyncAwait">async await</button>
...
methods: {
    async testAsyncAwait() {
        console.log('[testAsyncAwait] start');
        
        let params = {
            searchCode: "all",
            searchKeyword: ""
        };
    
        try {
            var data = await API.GET_ALL_PRODUCTS(params);
            this.productList = data.data;
            console.log('[testAsyncAwait] async await complete');
        } catch (error) {
            console.log(error);
            this.$emit('fnSearchProductResult', []);
        }

        console.log('[testAsyncAwait] end');
    },
    ...
}
```

![](../../../.gitbook/assets/image%20%2821%29.png)

## 일반함수에서 `Promise`

```javascript
<button @click="testPromise">promoise</button>
...
methods: {
    testPromise() {
        console.log('[testPromise] start');
        
        let params = {
            searchCode: "all",
            searchKeyword: ""
        };

        API.GET_ALL_PRODUCTS(params)
        .then(res => {
            console.log('[testPromise] Promise complete');
            this.productList = res.data;
        })
        .catch(err => {
            this.$emit('fnSearchProductResult', []);
            console.log(err);
        });

        console.log('[testPromise] end');
    },
    ...
}
```

![](../../../.gitbook/assets/image%20%2825%29.png)

