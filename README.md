后端返回参数格式：
参数名	参数类型	备注
success	Boolean	操作是否成功
message	String	例：“登录成功！”
State	String	例：“0001”表示登陆成功
Data	JSONObject	返回的数据信息，如果没有数据需要返回则没有这一项
1、	注册
前端传入参数：
参数名	参数类型	备注
username	String	
gender	Integer	
roomNum	String	
phoneNum	String	
email	String	
password	String	
groupName	Integer	现在传的是String，要改成id
depName	Integer	
companyName	Integer	
roleId	Integer	
answer_1	String	
answer_2	String	
answer_3	String	
后端返回参数：
Success	message	state	data
false	用户名已存在，请重新注册！	0001	无
false	未知原因注册失败，请重新注册！	0002	无
True	注册成功！	0003	无
2、	登录
前端传入参数：
参数名	参数类型	备注
user	String	用户名
pass	String	密码
后端返回参数：
Success	message	state	data
false	登录失败，用户名不存在！	0001	无
false	登录失败，用户数据已删除！	0002	无
false	登录失败，密码错误！	0003	无
true	登录成功！	0004	见下表
登陆成功时返回的data：
参数名	参数类型	备注
userId	Integer	用户id
username	String	用户名
Gender	Integer	性别
roomNum	String	办公房间号
phoneNum	String	电话
Email	String	邮箱
Salt	String	盐值
Password	String	加密后的密码
groupId	Integer	小组Id
companyId	Integer	中心id
depId	Integer	部门id
roleId	Integer	角色id
Status	Integer	在职状态
lineLeader	Integer	直线领导id
leaderName	Integer	直线领导名
createTime	datetime	创建时间
updateTime	datetime	更新时间
groupName	String	小组名
depName	String	部门名
companyName	String	公司名
Ext1	String	密保答案1
Ext2	String	密保答案2
Ext3	String	密保答案3
3、	修改密码
前端传入参数：
参数名	参数类型	备注
user	String	用户名/邮箱
oldPass	String	原始密码
newPass	String	新密码
后端返回参数：
Success	message	state	data
False	原始密码错误，修改密码失败！	0001	无
true	密码修改成功！	0002	无
4、	找回密码
前端传入参数：
参数名	参数类型	备注
Email	String	用户名/邮箱
quesNum	Integer	问题编号
Ans	String	密保答案
pass	String	新密码
后端返回参数：
Success	message	state	data
False	密保答案错误，修改密码失败！	0001	无
true	密码修改成功！	0002	无
5、	用户管理：显示当前小组/部门/中心所有人员信息、分页查询
前端传入参数：
参数名	参数类型	备注
Role_id	Integer	角色id：
1：小组长：
2：部门领导
3：中心领导
（可改）
Ops_id	Integer	小组长则返回小组id
部门领导则返回部门id
中心领导则返回中心id
后端返回参数：
Success	message	state	data
True	已显示当前小组/部门/中心全部成员	0001	见下表
   查询成功时返回的data：
参数名	参数类型	备注
username	String	用户名
Gender	Integer	性别
roomNum	String	办公房间号
phoneNum	String	电话
Email	String	邮箱
groupId	Integer	小组Id
companyId	Integer	中心id
depId	Integer	部门id
roleId	Integer	角色id
RoleName	String	角色名
Status	Integer	在职状态
lineLeader	Integer	直线领导id
leaderName	Integer	直线领导名
createTime	datetime	创建时间
updateTime	datetime	更新时间
groupName	String	小组名
depName	String	部门名
companyName	String	公司名
Ext1	String	密保答案1
Ext2	String	密保答案2
Ext3	String	密保答案3
6、	用户管理：按条件查询相关人员信息
前端传入参数：
参数名	参数类型	备注
User	String	姓名
Gender	Integer	性别
roomNum	String	房间号
Phone	String	电话
Email	String	邮箱
grpId	Integer	小组id
depId	Integer	部门id
comId	Integer	中心Id
roleId	Integer	角色id
leaderName	String	删掉！！！数据库里领导名会重名！！！
isDelete	Integer	在职状态
后端返回参数：
Success	message	state	data
True	已显示满足当前条件的所有员工信息	0001	同5
7、	用户管理：编辑用户信息-小组长
前端传入参数：
参数名	参数类型	备注
oldEmail	String	原始邮箱
Username	String	用户名
Gender	Integer	性别
roomNum	String	房间号
Phone	String	电话
newEmail	String	新邮箱
depId	Integer	部门Id
comId	Integer	中心Id
grpId	Integer	小组id
roleId	Integer	角色id
status	Integer	在职状态
后端返回参数：
Success	message	state	data
false	更新失败，未知原因！	0001	无
true	修改成功！	0002	无
8、	用户管理：编辑用户信息-超管
前端传入参数：
参数名	参数类型	备注
Email	String	用户名/邮箱
lineleader	Integer	直系领导id（此处只能是id，name数据库会重名）
后端返回参数：
Success	message	state	data
false	更新失败，未知原因！	0001	无
true	更新直线领导信息成功！	0002	无
9、	用户管理：删除用户信息
前端传入参数：
参数名	参数类型	备注
username	String	用户名/邮箱
后端返回参数：
Success	message	state	data
False	删除用户信息失败，未知原因！	0001	无
false	删除成功！	0002	无

