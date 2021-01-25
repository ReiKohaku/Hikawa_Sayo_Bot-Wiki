# Arcaea查分功能

此类目下面的功能均与Arcaea查分相关。

> Arcaea指由英国lowiro开发的名为“Arcaea”的移动应用，开发者与其并无任何从属关系。
>
> 您使用此功能时，默认您已悉知您违反了《Arcaea使用条款》。开发者不对此承担任何责任。
>
> 由于使用的API来自第三方，开发者不对功能的稳定性和数据的有效性做任何保证。
>
> 如果您是该API的开发者或利益相关者，您认为此功能侵犯了您的合法权益，请联系开发者。

### 绑定用户代码

#### 用途
将当前QQ与一个Arcaea用户代码绑定，以方便查询。

#### 书写格式
`arcbind <用户代码>`

#### 返回内容
绑定是否成功。

#### 示例
> arcbind 123456789

与123456789绑定。

### 解绑用户代码
#### 用途
解除将当前QQ与绑定的Arcaea用户代码的绑定关系。

#### 书写格式
`arcunbind`

#### 返回内容
解绑是否成功。

#### 示例

> arcunbind

解除绑定。

### 生成Arcaea Best30信息卡
> 该功能的API整合自[Arcaea查分器](https://redive.estertion.win/arcaea/probe/)所使用的查询后端。
>
> 如果您想要体验完整功能，欢迎前往[Arcaea查分器](https://redive.estertion.win/arcaea/probe/)。

#### 用途
生成对应用户的Best30信息卡。

#### 书写格式
`arcinfo [目标用户代码|目标QQ号|at目标]`

其中：

`目标用户代码`是目标的Arcaea用户代码。

`目标QQ号`是目标的QQ号，且只有在目标绑定了Arcaea用户代码后才可以这么查询。

`at目标`是使用QQ的@功能选择目标，只有在目标绑定了Arcaea用户代码后才可以这么查询。

#### 返回内容
一张图片，包含对应Arcaea用户的当前角色、用户名、潜力值、Best30列表。

> 同一账号的查询结果有1分钟的查询冷却：在完成查询的1分钟之内，查询该账号的B30信息，都会返回被缓存的图片。

#### 示例
`arcinfo`

生成自己的Arcaea Best30信息卡。

`arcinfo 771929708`

生成QQ号为771929708的用户绑定的Arcaea用户代码的Arcaea Best30信息卡。

`arcinfo @灵喵`

生成@灵喵 绑定的Arcaea用户代码的Arcaea Best30信息卡。

> 请注意：此处的@只是at的表现形式。您在实际使用中，必须是通过列表选中了目标才有效，直接输入文本是不起作用的。

### 查询单曲定数

#### 用途

查询指定曲目的各难度真实定数。

#### 书写格式

`(arcc|arcconst|arcconstant) <歌曲名|歌曲ID|歌曲俗称>`

其中：

`歌曲名`是歌曲的完整名称，如`Tempestissimo`。

`歌曲ID`是歌曲在Arcaea包体的内部名称，如《Grievous Lady》的歌曲ID是`grievouslady`。

`歌曲俗称`是歌曲在玩家群体中常用的名称，如《GLORY：ROAD》的俗称是`里红`、《Fracture Ray》的俗称是`骨折光`、`高达`、`高达光`。

> 如果您想要协助补全歌曲的俗称，欢迎向[仓库](https://gitee.com/ReiKohaku/sayo)提交Pull Request或Issue，仿照格式修改[别名文件](https://gitee.com/ReiKohaku/sayo/blob/master/alias.json)即可。

#### 返回内容

包含曲目各难度的定数，尚未计算出结果的难度的定数用`？？？`表示。

#### 示例

`arcc 衔尾蛇`

查询《ouroboros -twin stroke of the end-》各难度的定数。

### 查询单曲成绩

#### 用途

查询个人指定单曲的历史最佳成绩。

#### 书写格式

`(arcr|arcrating) <歌曲名|歌曲ID|歌曲俗称> [难度]`

其中：

`歌曲名`、`歌曲ID`、`歌曲俗称`参见[查询单曲定数](arcaea#查询单曲定数)的同名参数。

`难度`可以填写难度的全名（即`past`、`present`、`future`、`beyond`），也可填写难度简称（即`pst`、`prs`、`ftr`、`byd`），亦可直接填写难度序号（即`0`、`1`、`2`、`3`）。不填或提供错误的难度，将自动查询**Future**难度的成绩。

#### 返回内容

该曲目对应难度的历史最佳成绩，包含玩家名、分数、完成时间、PURE数、MAX PURE数、FAR数、LOST数、完成等级（Rating）、单曲定数（Constant）。

#### 示例

`arcr 衔尾蛇`

查询自己已绑定的账号《ouroboros -twin stroke of the end-》的Future难度历史最佳成绩。

`arcrating 风暴 byd`

查询自己已绑定的账号《Tempestissimo》的Beyond难度历史最佳成绩。