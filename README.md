# Bugs and Stuff

## Firebase

### Issue with calling firebase functions?

![img](./img.png)
This issue comes up when you try calling a firebase function from the frontend (React). This literally just means that it does NOT detect any Firebase config in your frontend code. Maybe because of missing .env or just no configuration at all.


### Issue with firebase deploy functions
```
import firebase from 'firebase/compat/app'
^^^^^^

SyntaxError: Cannot use import statement outside a module
    at wrapSafe (internal/modules/cjs/loader.js:979:16)
    at Module._compile (internal/modules/cjs/loader.js:1027:27)
```

This issue is because you may be trying to import the `myFirebase.js` file into functions. Remove it in `index.js`



## Less
With less, there is sometimes where a .less file is made and is referenced in HMTL but is not being called. This is because the <less> library must come AFTER its call. like so
```
    <link rel="stylesheet/less" type="text/css" href="index.less" />
    <link rel="stylesheet/less" type="text/css" href="../index.less" />
    <script src="https://cdn.jsdelivr.net/npm/less@4"></script>
 ```
 and NOT like
```
    <script src="https://cdn.jsdelivr.net/npm/less@4"></script>
    <link rel="stylesheet/less" type="text/css" href="index.less" />
    <link rel="stylesheet/less" type="text/css" href="../index.less" />
 ```
    
# Calling NodeJS Cloud Functions from React
Frontend:
```
const res = await axios.post(
    "https://us-central1-quantifying-nft-communities.cloudfunctions.net/getFinancials", 
    { collectionAddress: "0x7de3085b3190b3a787822ee16f23be010f5f8686"}, 
    { "Content-Type": "application/json" })
```
Server
```
    res.set("Access-Control-Allow-Origin", "*");
    res.set('Access-Control-Allow-Origin', '*')
    res.set('Access-Control-Allow-Credentials', true)
    res.set('Access-Control-Allow-Methods', 'POST, GET, PUT, DELETE, OPTIONS')
    res.set('Access-Control-Allow-Headers', 'Content-Type')
```
    
    
