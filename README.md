# blog
![Ghost Support](https://img.shields.io/badge/ghost-powered-brightgreen.svg)
![License MIT](https://img.shields.io/github/license/mashape/apistatus.svg)

The blog source code based on ghost, with aliyun oss support.

## Contain
- Theme: [Cuckoo](https://github.com/SwiftHow/cuckoo)
- OSS Storage: [GhostChina](https://github.com/ghostchina/Ghost-zh)

## Note
~~This project have **NO VALUE** for develop, and based on official ghost release, and merged with ghostchina's storage part.~~

### Support Aliyun CDN
in config file:
```javascript
{
    storage: {
        provider: 'oss',
        bucketname: 'your-bucket-name',
        ACCESS_KEY: 'xxxxxx',
        SECRET_KEY: 'xxxxxx',
        root: '/files/',
        prefix: 'https://your-bucket-name.oss-cn-qingdao.aliyuncs.com',
        cdnPrefix: 'https://your-cdn-alise.alikunlun.com'          // Set cdnPrefix here.
    }
}
```

use this project `/core/storage/oss.js` file.
you can see:
```javascript
// prefix + targetFilename
var fullUrl = (ossConfig.cdnPrefix ? ossConfig.cdnPrefix : ossConfig.prefix) + targetFilename;
return fullUrl;
```
This will save link in ghost db with `cdnPrefix` first, but still upload file to oss with `prefix`.
