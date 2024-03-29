## 费用（月还管理费、担保费、服务费、逾期管理费）减免

* 流程已经迁移到贷后，记得当初胡绍展迁移的  
* 结算目前有2个接口：
* /repay/derate/derateSplit：费用拆分
* /repay/derate/derateDoAccount：减免入账
* 核心需要将上述2个接口迁移到结算微服务
  
### 注意点  

* 快贷、秒贷、优贷 减免结清需要通知平台。  

## 追偿减免

* 流程还在核心，接口：
* /repay/derate/derateFee :追偿减免复核通过（新代偿、老代偿减免入账）
* /repay/derate/derateFeeFail :追偿减免复核不通过，取消申请
* /repay/guaranteeDerate/getDerateReviewList: 追偿减免列表
* /repay/guaranteeDerate/addDerateFee:添加追偿减免
* /repay/guaranteeDerate/applyDerateFee：提交申请追偿减免
* 复核通过、不通过、取消、添加、提交申请、列表这些接口迁移到贷后
* 拆分和入账迁移到结算微服。

### 注意点

* 新追偿可以减免追偿还款记录里的任何费用项（本利管理费等等）
* 追偿减免在提交申请时进行拆分。
  
## 特殊减免

* 流程在贷后，目前核心还有2个接口：
* /repay/specialDerate/derateSplit:特殊减免拆分
* /repay/specialDerate/checkPass：特殊减免复核通过  
* 核心需要将上述2个接口迁移到结算微服务

### 注意点

* 特殊减免的使用场景是提前还款。在提还复核通过之后需要去使用复核通过特殊减免记录-状态由复核通过变成减免成功
* 支持特殊减免产品：快贷、秒贷、优贷、力合担保、石嘴山、中关村、西格玛、力合小贷、向上、南京
* 提还使用特殊减免后入账，通知贷后让复核通过但没有使用上的减免变成失效。

## 综合费用减免

* 流程在贷后，结算微服有2个接口
* solid-repay/derate/loanOutFee/derateSplit：减免拆分
* solid-repay/derate/loanOutFee/derateDoAccount：减免入账  
