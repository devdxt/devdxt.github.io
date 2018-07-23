### 1. Set Variant

```js
Method    : POST
Syntax    : {host}:{port}/shifu/api/route/{routeId}
Rest API  : curl -H "Content-Type: application/json" -X POST -d '{"variant":"preorder"}' http://localhost:8000/_admin/api/route/getCollection?returnConfig=true

shifu.route({
    id: 'getCollection',
    label: 'Get Collection',
    path: '/product/grouping/api/collection/{collectionId}',
    variantLabel: 'default',
    handler: function(req, reply) {
        var response = getResponseData('/product/grouping/api/collection', 'default');
        reply(response);
    }
})
.variant({
    id: 'preorder',
    label: 'Get Pre-order Collection',
    handler: function (req, reply) {
        reply({message: 'hello pre-order'});
    }
});
```
> To get the config back as a response, add query parameter `returnConfig=true` as shown in example above

### 2. Set Mock Id

```
Method    : GET
Syntax    : {host}:{port}/shifu/api/setMockId/{mockid}/{sessionid}
Rest API  : curl http://localhost:8000/shifu/api/setMockId/1234/default
```

### 3. Get Mock Id

```
Method    : GET
Syntax    : {host}:{port}/shifu/api/getMockId/{sessionid}
Rest API  : curl http://localhost:8000/shifu/api/getMockId/default
```

### 4. Reset Mock Id

```
Method    : GET
Syntax    : {host}:{port}/shifu/api/resetMockId/{sessionid}
Rest API  : curl http://localhost:8000/shifu/api/resetMockId/default
```

### 5. Get Url Count

```
Method    : GET
Syntax    : {host}:{port}/shifu/api/getURLCount/{sessionid}
Rest API  : curl http://localhost:8000/shifu/api/getURLCount/default
```

### 6. Reset Url Count

```
Method    : GET
Syntax    : {host}:{port}/shifu/api/resetURLCount/{sessionid}
Rest API  : curl http://localhost:8000/shifu/api/resetURLCount/default
```

### 7. Re-set the state of Mock Server

```
Method    : POST
Syntax    : {host}:{port}/shifu/api/state/reset
Rest API  : curl -X POST http://localhost:8000/shifu/api/state/reset
```

### 8. Register Session

```
Method    : GET
Syntax    : {host}:{port}/shifu/api/registerSession
Rest API  : curl http://localhost:8000/shifu/api/registerSession
```

### 9. Get Sessions
```
Method    : GET
Syntax    : {host}:{port}/shifu/api/getSessions
Rest API  : curl http://localhost:8000/shifu/api/getSessions
```

### 10. Check Session
```
Method    : GET
Syntax    : {host}:{port}/shifu/api/checkSession/{sessionid}
Rest API  : curl http://localhost:8000/shifu/api/checkSession/{sessionid}
```

### 11. Close Session
```
Method    : GET
Syntax    : {host}:{port}/shifu/api/closeSession/{sessionid}
Rest API  : curl http://localhost:8000/shifu/api/closeSession/{sessionid}
```