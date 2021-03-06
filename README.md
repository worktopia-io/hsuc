## 语言
[中文](https://github.com/kszitt/hsuc/blob/master/README_ZH.md)

## describe
Upload the files generated by web pack to the cloud to improve the loading speed  
Currently, Alibaba cloud, Huawei cloud, Tencent cloud, qiniu cloud and remake cloud, as well as user-defined extensions are supported.

## install
```bash
npm install hsuc --save-dev
```

## required
### Node
Node.js >= 10.10.0 required

## use
#### webpack.config.js
```bash
// webpack.config.js
const Hsuc = require('hsuc');

...
plugins: [
    ...
    new Hsuc({
        cloudFolder: "<Cloud folder>",
        domain: "<domain name>",
        enable: true,
        // Alicloud (Choose one)
        aliyun: {
            region: "<OSS region>",
            accessKeyId: "<Your accessKeyId>",
            accessKeySecret: "<Your accessKeySecret>",
            bucket: "<Your bucket name>"
        }
        // Hua Weiyun (Choose one)
        huawei: {
            accessKeyId: "<Provide your Access Key>",
            secretAccessKey: "<Provide your Secret Key>",
            server: "<https://your-endpoint>",
            bucket: "<Bucket>"
        },
        // Tencent cloud (Choose one)
        tencent: {
            secretId: "<SecretId>",
            secretKey: "<SecretKey>",
            bucket: "<Bucket>",
            region: "<Region>"
        },
        // Qiniu cloud (Choose one)
        qiniu: {
            accessKey: "<ACCESS_KEY>",
            secretKey: "<SECRET_KEY>",
            bucket: "<Bucket>"
        },
        // Clapping clouds again (Choose one)
        upyun: {
            serviceName: "<service name>",
            operatorName: "<operator name>",
            operatorPassword: "<operator password>",
        }
    })
]
```

## hsuc(options) supported options
- `aliyun` - Initialize alicloud OSS parameters
- `huawei` - Initialize Huawei cloud OBS parameters.
- `tencent` - Initialize Tencent cloud cos parameters.
- `qiniu` - Initialize the Qiniu cloud parameter.
- `upyun` - Initialize the re shooting cloud parameter.
- `enable[boolean]` - Enable at the beginning, default`true`。
- `removePrevVersion[boolean]` - Delete previous versions of cloud or not, default`false`
- `log[boolean]` - Display log, default`true`
- `cover[boolean|RegExp]` - Overwrite file, default`false`. Please refer to`/\.(png|jpe?g|gif|ico|woff2?|svg|ttf|eot)$/`。
- `custom[js文件，例如require("./template.js")]` - User defined upload file, you can refer to the `template.js` in the project


## Object store CORS rule settings
- `aliyun` Set according to [CORS](https://help.aliyun.com/document_detail/44570.html?spm=5176.8465980.0.0.12871450vh6n2z)
- `huawei` Set according to [CORS](https://support.huaweicloud.com/sdk-browserjs-devg-obs/obs_24_0201.html)
- `tencent` Set according to [CORS](https://cloud.tencent.com/document/product/436/13318)
- `qiniu` Set according to [CORS](https://console.upyun.com/services/kszitt/antileechFile/)
- `upyun` Set according to [CORS](http://docs.upyun.com/cdn/feature/#cors)

## matters needing attention
- Please set the cloud access to "public read / write" or "public read"
- In the options parameter, `aliyun`, `huawei`, `tencent`, `qiniu` and `upyun` are configured at the same time, only the first one is valid
- The plug-in is disabled in development mode
- `options.deletePrevBuildFile` Enabling this item will delete the previous version. Please be careful.

#### deploy
``` hash
webpack
// Deploy the index.html file under the package folder to the server, and you can access
```

