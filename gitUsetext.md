# git注册
- github地址：[https://github.com](https://github.com)</br>
- 注册：![注册git](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/T7*V*FHBvCc41j78iIIkSL3JiYUus.KKDSRfR0zJUwc!/b/dAgBAAAAAAAA&bo=EgT4AwAAAAADB88!&rf=viewer_4)</br>
- 登陆Git：![登陆git](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/OI3QbH.8ZQeoRkXQckymk8HDfnofR.9EJ.8bnw9Sd3Q!/b/dDYBAAAAAAAA&bo=ggPMAwAAAAADB2w!&rf=viewer_4)</br>
登陆账号可以是用户名或者邮箱</br>
- 创建仓库：![创建仓库](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/5D7bo1zbj9gMmdLtkSswbdOK*ARC6c2R0UVcvLAVVaE!/b/dFYAAAAAAAAA&bo=cAg4BAAAAAADB2Y!&rf=viewer_4)</br>

# 安装git
1. git下载地址：[https://git-scm.com/downloads](https://git-scm.com/downloads)</br>
	1. 选择自己想要下载的系统版本（以Windows10为例）</br>
	![选择系统](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/LAo0q99xYIJXPjlKweXZpiZ*2r1BnuTNHffGOrJ7Myw!/b/dEUBAAAAAAAA&bo=pAeQAgAAAAADBxM!&rf=viewer_4)</br>
	![选择系统版本](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/9gpMQf6tDz0G*o4heIZunvv1oJXXH7hNad0MpfGrWIU!/b/dDUBAAAAAAAA&bo=awc4BAAAAAADB3I!&rf=viewer_4)</br>
	2. 开始安装git</br>
	![开始安装git](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/iavaZ0qXQuwGwT*.wD3fYU2GGxIKwHlfPQhijJcZrek!/b/dAgBAAAAAAAA&bo=WgQ4AwAAAAADB0c!&rf=viewer_4)</br>
	选择安装路径.然后一路Next</br>
	![选择安装路径](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/lxY4vpYepbWsLSGgNAfN5Lu0DtoLP9jBORXGrFYZK9I!/b/dDYBAAAAAAAA&bo=GARAAwAAAAADJ10!&rf=viewer_4)</br>
	选择默认编辑器</br>
	![选择默认编辑器](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/VK9VPefnXipc5J.JRxnY7RDQOzHZB.IZ0B4838pDOCE!/b/dDQBAAAAAAAA&bo=JgQ0AwAAAAADJxc!&rf=viewer_4)</br>
	选择git自带的命令行工具</br>
	![选择命令工具](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/av1j6DwcB*r3ghbc.PscqP5J8DYsedi7x0B9leT2ZdU!/b/dDYBAAAAAAAA&bo=HAQyAwAAAAADNzs!&rf=viewer_4)</br>
	后面可以根据个人喜好选择安装，也可以选择一路默认Next安装</br>
	3. git初始化设置</br>
		1. 打开Git Bash </br>
		![打开git bash](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/aC2K5OG1Wc7ULRX*0KTITQ3OtIxN39lyztWMI4UdLIA!/b/dDUBAAAAAAAA&bo=YgIYBQAAAAADB18!&rf=viewer_4)</br>
		2. 使用以下命令，设置用户名和邮箱</br>
			- git config --global user.name '你在GitHub注册的用户名'</br>
			- git config --global email.name '你在GitHub注册的邮箱'</br>
		3. 使用以下命令，查看设置的用户名和邮箱</br>
			- git config user.name</br>
			- git config email.name</br>
		4. 生成SSH公钥</br>
			- ssh-keygen -t rsa -C '你在GitHub注册的邮箱'</br>
			![生成密钥](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/1SBDdnO66oNM1*RhDRceHEpb0lVgF88Itytj1Oq8x.k!/b/dDYBAAAAAAAA&bo=ngV4AwAAAAADR4I!&rf=viewer_4)</br>
	在Git Bash输入这条命令，回车之后再按三个回车（默认存储位置，密码为空，确认密码）</br>
		- 在GitHub配置SSH公钥 </br>
			- 在自己电脑路径C:\Users\你的用户名\.ssh中找到id_rsa.pub文件，并全选复制文件中的内容</br>
			![密钥位置](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/fYln4EdDQE7OQoFFHVvFL*2pst1f3FQGgznMgIWA.hY!/b/dDQBAAAAAAAA&bo=TgfcAQAAAAADB7Y!&rf=viewer_4)</br>
			- 在GitHub点击你的头像，选择”Settings”，选择右边的”SSH and GPG Keys”,选择New SSH Key，Title随便填，再把复制的公钥粘贴进Key里面，点击Add SSK key即完成。</br>
			![选择设置](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/FLeNXZaJplO6fySqpIgOOfbp3sY3QNJ7MNSeXfQChMM!/b/dDIBAAAAAAAA&bo=Vgh4AwAAAAADR0c!&rf=viewer_4)</br>
			![选择ssh设置](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/74kbQSYt87hacxK7qswrxKIna26p9KhiOJG4nzxKQbg!/b/dFUAAAAAAAAA&bo=ognOAwAAAAADRwQ!&rf=viewer_4)</br>
			
# 上传项目</br>
1. 在你想上传的项目文件夹右键，选中Git Bash Here，即会弹出命令行窗口</br>
	![选择文件夹](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/8aq4Xn2aW1GFi5weH1*8DSfh*eyH*XvW56yq0c1GQ3A!/b/dDABAAAAAAAA&bo=VgdCAgAAAAADBzM!&rf=viewer_4)</br>
2. 初始化仓库
	1. 在命令行中输入初始化命令</br>
	![初始化](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/dW2pIo7wtsKJR15SWa2XvHjRNIX1fJhTCyHxewsUZUE!/b/dDQBAAAAAAAA&bo=aAOcAAAAAAADF8U!&rf=viewer_4)</br>
	- 输入命令后，会在选中的文件夹中出现一个.git的隐藏文件夹</br>
	![.git文件夹](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/j.ad3uFmfXoMD1N37sac6upu8IPioCmeC**t*Xi8UKM!/b/dDUBAAAAAAAA&bo=jAaeAQAAAAADBzc!&rf=viewer_4)</br>
3. 上传文件
	1. 创建README.md，可以自己在文件夹中手动创建，也可以使用命令创建</br>
		- touch README.md</br>
	2. 使用以下命令将想要提交的文件添加到暂存区并提交</br>
		![git提交](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/VjwirsG9VpZHcyrXYrdWaAiueKN8h9W6KPGb2aSUhvU!/b/dDABAAAAAAAA&bo=HgNSAAAAAAADB20!&rf=viewer_4)
		- git add '你要提交的文件或文件夹'</br>
		- git commit -m '提交注释'</br>
		- ps:如果想要将文件夹中的全部文件或文件夹上传只需将add后面的文件或文件夹名称用'.'代替即可；commit -m后面的单引号内容为本次提交的注释，可以根据自己的要求填写。 </br>
	3. 本地仓库和远程仓库同步</br>
		1. 同步命令</br>
			![同步远程仓库](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/g4x428xGTA1DXal6uHAJ.JnDz*EAjVNGQBQ53Qo8NeE!/b/dDYBAAAAAAAA&bo=2gQuAAAAAAADF8I!&rf=viewer_4)</br>
			- git remote add origin git@github.com:用户名/项仓库名.git --origin 可以根据自己的爱好更改</br>
		2. 上传文件到远程仓库</br>
			![上传到远程仓库](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/0jCks7VIFawdSGyqqGuH1rMI6.Muvr15XPi6D43ygRs!/b/dDUBAAAAAAAA&bo=9AP2AAAAAAADNxM!&rf=viewer_4)</br>
			- git push -u origin master</br>
		3. 从远程仓库获取最新代码</br>
			![拉取代码](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/Nb55.CtpIptD.z3WBU1gnQpXd8uipR1imMcUQzgFZhE!/b/dDEBAAAAAAAA&bo=LAQkAQAAAAADNx8!&rf=viewer_4)</br>
			- git pull <远程主机名> <远程分支名>:<本地分支名></br>
			  例如：git pull origin master:master</br>
			  
		4. 将远程仓库克隆到本地
			- 选择克隆到本地的位置，右键选择 git bash </br>
			![远程库克隆](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/WyQ3jnMI6cSCyZOdXffpI3YBNvpAcC.JsqJKF72*4VQ!/b/dDQBAAAAAAAA&bo=mAP0AgAAAAADB08!&rf=viewer_4)
			- 输入命令 </br>
			 **git clone git@github.com:用户名/仓库名.git**</br>
			
			![克隆](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/hwcMRNMGQKv4xnNYWNPJWrr1P3.6Wyx12RH*0eNrZnY!/b/dDYBAAAAAAAA&bo=KgT0AAAAAAADB*g!&rf=viewer_4)
		5. 管理分支
			- 创建分支</br>
				**git branch 'name'**</br>
				![创建分支](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/TMX5hRL9auWyLg2mWgCD7jQsteMArugWLn5dsawIIc0!/b/dDcBAAAAAAAA&bo=cgKSAAAAAAADB8A!&rf=viewer_4)
			- 切换分支</br>
				**git checkout 'name'**</br>
				![切换分支](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/kDqHprOM1z2GVzzmoixQBrl60.V7YDbxsNec3zaMvqg!/b/dDYBAAAAAAAA&bo=8gKuAAAAAAADB3w!&rf=viewer_4)
			- 合并分支</br>
				**git merge 'name'**</br>
				![合并分支](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/wKVdDf3kGEky4MXFpfqWPDsVChkrqpOyav54*53oKIc!/b/dEYBAAAAAAAA&bo=jgK2AAAAAAADBxg!&rf=viewer_4)
			- 删除分支</br>
				**git branch -d 'name'**</br>
				![删除分支](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/avm6ngZ6O.FQdMzOWbRRGsivu1hBL8n4XGNyrTdZEqQ!/b/dDQBAAAAAAAA&bo=4gJ8AAAAAAADF64!&rf=viewer_4)
			- 查看分支</br>
				**git branch**</br>
				![查看分支](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/TMX5hRL9auWyLg2mWgCD7jQsteMArugWLn5dsawIIc0!/b/dDcBAAAAAAAA&bo=cgKSAAAAAAADF9A!&rf=viewer_4)
			- 创建+切换分支</br>
				**git checkout -b 'name'**</br>