# 基于MongoDB和NodeJS的舞蹈培训管理系统

## 摘要：
本应用为基于**NodeJS、Express Web Framework、Jade、MongoDB、MongoSkin**等技术构建的Alibaba舞蹈培训管理系统。目前以舞蹈培训报名管理功能为主。
## 功能描述
本应用分前台、后台两部分：前台以production模式启动，用户免登陆访问；后台以development模式启动，兼有会员管理功能。具体描述如下：
### 用户前台功能：
* **实现网上报名：**<br/>
	- 报名页显示当前开设课程实时信息（舞种、额定人数，已申请人数、报名成功人数等）。<br/>
	- 新用户：填写基本信息：工号、姓名、邮箱、旺旺等；选择培训课程；提交；系统存入数据库。
	- 老用户：输入工号后，系统根据工号自动获取显示相关信息；会员选择培训课程；提交报名；同时可以修改个人信息。<br/>
	- 会员申请报名后需管理员手工审核，也可以由系统根据一定规则：是否男士优先、课程总容量、当前报名成功人数等，对课程进行自动审核。<br/>
	- 课程审核通过前用户可自行取消，审核通过后用户可申请退课。<br/>
	- 退课需管理员审核：可以拒绝退课；或者线下退费、退课（后台）。<br/>
* 用户可以查看个人信息及参加的培训课程等。
* 用户可以查询课程报名情况：根据工号、部门、性别、课程、报名状态、缴费状态等条件进行组合查询、筛选。
* 查询结果分页展示，可以对某些字段进行排序。
* 可以生成满足特定条件的会员的邮件列表。
### 后台功能：
* **课程生命周期管理：**<br/>
	- 新申请报名课程状态为待审核--------------------------------(waiting)；<br/>
	- 管理员审核前用户可以自助取消-------------------------(cancelled)；<br/>
	- 管理员可以审核拒绝-------------------------------------------(refused)；<br/>
	- 或者审核通过则报名成功----------------------------------(approved)；<br/>
	- 报名成功后会员可以申请退课--------------------------(quitApplied)；<br/>
	- 退课需要管理员审核，审核拒绝则回到报名成功-------(approved)；<br/>
	- 退课审核通过则处于退课成功---------------------------------------(quit)；<br/>
**注意：**对于课程生命状态转换系统会验证是否满足前置条件：比如waiting状态不能直接转为quit，但是可以转换为cancelled，只有waiting或者quiteApplied状态的可以转换为approved, 而approved不能转为waiting，只有quitApplied的课程可以转为quit，并且需要先退费等。

* **课程缴费状态设置：**<br/>
	- 报名成功的会员在缴费后管理员可以将其设为已缴费。
	- 申请退课的会员可以线下退费并修改其状态为未缴费，然后退课。

* **管理员修改会员信息：**<br/>
	- 会员可以修改自身基本信息，管理员可以修改其基本及高级属性比如：
level(<=9)、vip等级(<=5)、forever状态（年卡）、lock状态等。

# 应用部署说明：
1. 安装NodeJs；
2. 安装MongoDB并启动；
3. Clone代码：git clone ……git;
4. cd latinode & npm install -d & node app.js;
5. That's All! 访问：http://localhost:3000 即可。
<br/>
