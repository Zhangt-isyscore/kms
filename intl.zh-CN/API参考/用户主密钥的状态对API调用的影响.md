# 用户主密钥的状态对API调用的影响 {#concept_44211_zh .concept}

在KMS服务中，用户的每个主密钥都拥有启用（Enabled）、禁用（Disabled）、待删除（PendingDeletion）三个状态。

如果密钥是**外部密钥**（也叫**用户自带密钥**，[KeyMetadata](intl.zh-CN/API参考/API列表/DescribeKey.md#section_28952_03)中Origin为EXTERNAL的），还可能处于待导入（PendingImport）状态。

通常情况下，新建的主密钥默认处于启用状态。当新建一个**外部密钥**时会处于等待导入状态。

只有处于启用状态的密钥才可以用于加密、解密操作。其它API根据密钥状态的不同，会有不同的返回结果。

处于待删除（PendingDeletion）状态的密钥，在预删除时间过后，会被永久删除。

密钥状态与API调用期望返回结果如下表所示。

|期望结果|HttpStatusCode|
|:---|:-------------|
|Success|200|
|Rejected.Enabled|409|
|Rejected.Disabled|409|
|Rejected.PendingDeletion|409|
|Rejected.PendingImport|409|
|Rejected.StateModifiedFailed|409|

## 普通API {#section_6v9_4u8_6l2 .section}

|API|启用（Enabled）|禁用（Disabled）|待删除（PendingDeletion）|待导入（PendingImport）|
|:--|:----------|:-----------|:-------------------|:-----------------|
|CreateKey|Success|Success|Success|Success|
|GenerateDataKey|Success|Rejected.Disabled|Rejected.PendingDeletion|Rejected.PendingImport|
|GenerateDataKeyWithoutPlaintext|Success|Rejected.Disabled|Rejected.PendingDeletion|Rejected.PendingImport|
|Encrypt|Success|Rejected.Disabled|Rejected.PendingDeletion|Rejected.PendingImport|
|Decrypt|Success|Rejected.Disabled|Rejected.PendingDeletion|Rejected.PendingImport|
|ListKeys|Success|Success|Success|Success|
|DescribeKey|Success|Success|Success|Success|
|UpdateKeyDescription|Success|Success|Rejected.PendingDeletion|Success|
|EnableKey|Success|Success|Rejected.StateModifiedFailed|Rejected.StateModifiedFailed|
|DisableKey|Success|Success|Rejected.StateModifiedFailed|Rejected.StateModifiedFailed|
|ScheduleKeyDeletion|Success|Success|Rejected.StateModifiedFailed|Success|
|CancelKeyDeletion|Rejected.StateModifiedFailed|Rejected.StateModifiedFailed|Success|Rejected.StateModifiedFailed|
|CreateAlias|Success|Success|Rejected.StateModifiedFailed|Success|
|DeleteAlias|Success|Success|Success|Success|
|ListAliases|Success|Success|Success|Success|
|TagResource|Success|Success|Rejected.PendingDeletion|Success|
|UntagResource|Success|Success|Rejected.PendingDeletion|Success|
|ListResourceTags|Success|Success|Success|Success|
|CreateKeyVersion|Success|Rejected.Disabled|Rejected.PendingDeletion|Rejected.PendingImport|
|DescribeKeyVersion|Success|Success|Success|Success|
|ListKeyVersions|Success|Success|Success|Success|
|UpdateRotationPolicy|Success|Rejected.Disabled|Rejected.PendingDeletion|Rejected.PendingImport|

## 特殊API {#section_6p7_h5c_13h .section}

UpdateAlias 

-   只受到“目标密钥”的状态影响，与“原密钥”状态无关。
-   当“目标密钥”处于待删除状态时，返回Rejected.PendingDeletion，否则返回Success。

外部密钥专属API 

|API|启用（Enabled）|禁用（Disabled）|待删除（PendingDeletion）|待导入（PendingImport）|
|:--|:----------|:-----------|:-------------------|:-----------------|
|GetParametersForImport|Success|Success|Success|Success|
|ImportKeyMaterial|Success|Success|Rejected.StateModifiedFailed|Success|
|DeleteKeyMaterial|Success|Success|Success|Success|

