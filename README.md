# bbhcar-start
打开软件后，调用启动器效果，GIF（打包后要合并到软件中）

在GIF中间显示文字，内容如下：（下面文字我需要可以手动调整位置）

- 固定显示：BBH Share Tool

- 动态显示：如果有更新或下载显示下载百分比，完成后变成Start...。如果没有更新和下载直接显示Start...。

  
软件设置：

- 保证软件以管理员身份运行

- 高DPI显示模式

首先调用接口获取数据 https://www.bbhcar.top/api/anonymous/program/b4eaea61ffd64bd4964ab1edb6d8ada1  GET请求

返回：

```
{
    "id": "b4eaea61ffd64bd4964ab1edb6d8ada1",
    "changeVersion": 0,
    "createdBy": "admin",
    "createdDate": 1741530457000,
    "lastModifiedBy": "admin",
    "lastModifiedDate": 1743349938000,
    "programName": "BBHSTART",
    "programVersion": "1.0.0",
    "programMD5": "447923733cc749f3a788c06ceef2f105",
    "programKey": "4bfc5dd6d61a42ff9de23483d5a38679",
    "updateUrl": "https://oss.bbhcar.top/bbhserver/BBHClientTools/bbhtool/BBHsharetool.exe",
    "clientKeepalive": 0,
    "serverKeepalive": 0,
    "programStatus": 1,
    "programDesc": "启动器"
}
```

然后检测：C:\ProgramData\BBHsharetool\BBHsharetool.exe

- 如果不存在则创建文件夹并通过"updateUrl":中下载到C:\ProgramData\BBHsharetool\BBHsharetool.exe路径,然后进行下面逻辑。
- 如果存在，则查询本地软件的MD5和通过"programMD5":的数据对比，如果一致则不下载直接打开，如果不一致则通过"updateUrl":下载

