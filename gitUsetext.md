#git注册
- github地址：[https://github.com](https://github.com)</br>
- 注册：![注册git](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/T7*V*FHBvCc41j78iIIkSL3JiYUus.KKDSRfR0zJUwc!/b/dAgBAAAAAAAA&bo=EgT4AwAAAAADB88!&rf=viewer_4)</br>
- 登陆Git：![登陆git](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/OI3QbH.8ZQeoRkXQckymk8HDfnofR.9EJ.8bnw9Sd3Q!/b/dDYBAAAAAAAA&bo=ggPMAwAAAAADB2w!&rf=viewer_4)</br>
登陆账号可以是用户名或者邮箱</br>
- 创建仓库：![创建仓库](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/5D7bo1zbj9gMmdLtkSswbdOK*ARC6c2R0UVcvLAVVaE!/b/dFYAAAAAAAAA&bo=cAg4BAAAAAADB2Y!&rf=viewer_4)</br>

#安装git
- git下载地址：[https://git-scm.com/downloads](https://git-scm.com/downloads)</br>
	1. 选择自己想要下载的系统版本（以Windows10为例）</br>
	![选择系统](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/LAo0q99xYIJXPjlKweXZpiZ*2r1BnuTNHffGOrJ7Myw!/b/dEUBAAAAAAAA&bo=pAeQAgAAAAADBxM!&rf=viewer_4)</br>
	![选择系统版本](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/9gpMQf6tDz0G*o4heIZunvv1oJXXH7hNad0MpfGrWIU!/b/dDUBAAAAAAAA&bo=awc4BAAAAAADB3I!&rf=viewer_4)</br>
	- 开始安装git</br>
	![开始安装git](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/iavaZ0qXQuwGwT*.wD3fYU2GGxIKwHlfPQhijJcZrek!/b/dAgBAAAAAAAA&bo=WgQ4AwAAAAADB0c!&rf=viewer_4)</br>
	选择安装路径.然后一路Next</br>
	![选择安装路径](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/lxY4vpYepbWsLSGgNAfN5Lu0DtoLP9jBORXGrFYZK9I!/b/dDYBAAAAAAAA&bo=GARAAwAAAAADJ10!&rf=viewer_4)</br>
	选择默认编辑器</br>
	![选择默认编辑器](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/VK9VPefnXipc5J.JRxnY7RDQOzHZB.IZ0B4838pDOCE!/b/dDQBAAAAAAAA&bo=JgQ0AwAAAAADJxc!&rf=viewer_4)</br>
	选择git自带的命令行工具</br>
	![选择命令工具](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/av1j6DwcB*r3ghbc.PscqP5J8DYsedi7x0B9leT2ZdU!/b/dDYBAAAAAAAA&bo=HAQyAwAAAAADNzs!&rf=viewer_4)</br>
	后面可以根据个人喜好选择安装，也可以选择一路默认Next安装</br>
	- git初始化设置
		1. 打开Git Bash 
		![打开git bash](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/aC2K5OG1Wc7ULRX*0KTITQ3OtIxN39lyztWMI4UdLIA!/b/dDUBAAAAAAAA&bo=YgIYBQAAAAADB18!&rf=viewer_4)
		- 使用以下命令，设置用户名和邮箱
			- git config --global user.name '你在GitHub注册的用户名'
			- git config --global email.name '你在GitHub注册的邮箱'
		- 使用以下命令，查看设置的用户名和邮箱
			- git config user.name
			- git config email.name
		- 生成SSH公钥
			- ssh-keygen -t rsa -C '你在GitHub注册的邮箱'</br>
			![生成密钥](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/1SBDdnO66oNM1*RhDRceHEpb0lVgF88Itytj1Oq8x.k!/b/dDYBAAAAAAAA&bo=ngV4AwAAAAADR4I!&rf=viewer_4)
	在Git Bash输入这条命令，回车之后再按三个回车（默认存储位置，密码为空，确认密码）
		- 在GitHub配置SSH公钥 
			- 在自己电脑路径C:\Users\你的用户名\.ssh中找到id_rsa.pub文件，并全选复制文件中的内容
			![密钥位置](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/fYln4EdDQE7OQoFFHVvFL*2pst1f3FQGgznMgIWA.hY!/b/dDQBAAAAAAAA&bo=TgfcAQAAAAADB7Y!&rf=viewer_4)
			- 在GitHub点击你的头像，选择”Settings”，选择右边的”SSH and GPG Keys”,选择New SSH Key，Title随便填，再把复制的公钥粘贴进Key里面，点击Add SSK key即完成。
			![选择设置](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/FLeNXZaJplO6fySqpIgOOfbp3sY3QNJ7MNSeXfQChMM!/b/dDIBAAAAAAAA&bo=Vgh4AwAAAAADR0c!&rf=viewer_4)
			![选择ssh设置](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/74kbQSYt87hacxK7qswrxKIna26p9KhiOJG4nzxKQbg!/b/dFUAAAAAAAAA&bo=ognOAwAAAAADRwQ!&rf=viewer_4)
			
#上传项目
- 在你想上传的项目文件夹右键，选中Git Bash Here，即会弹出命令行窗口
	![选择文件夹](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/8aq4Xn2aW1GFi5weH1*8DSfh*eyH*XvW56yq0c1GQ3A!/b/dDABAAAAAAAA&bo=VgdCAgAAAAADBzM!&rf=viewer_4)
- 初始化仓库
	1. 在命令行中输入初始化命令
	![初始化](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/dW2pIo7wtsKJR15SWa2XvHjRNIX1fJhTCyHxewsUZUE!/b/dDQBAAAAAAAA&bo=aAOcAAAAAAADF8U!&rf=viewer_4)
	- 输入命令后，会在选中的文件夹中出现一个.git的隐藏文件夹
	![.git文件夹](http://m.qpic.cn/psb?/V10sTJNc3PWHJb/j.ad3uFmfXoMD1N37sac6upu8IPioCmeC**t*Xi8UKM!/b/dDUBAAAAAAAA&bo=jAaeAQAAAAADBzc!&rf=viewer_4)
- 上传文件
	1. 创建README.md，可以自己在文件夹中手动创建，也可以使用命令创建
		- touch README.md
	- 使用以下命令将想要提交的文件添加到暂存区并提交
		- git add '你要提交的文件或文件夹'
		- git commit -m '提交注释'
		- ps:如果想要将文件夹中的全部文件或文件夹上传只需将add后面的文件或文件夹名称用'.'代替即可；commit -m后面的单引号内容为本次提交的注释，可以根据自己的要求填写。 
	- 本地仓库和远程仓库同步
		1. 同步命令
			- git remote add origin git@github.com:用户名/项仓库名.git --origin 可以根据自己的爱好更改
		- 上传文件到远程仓库
			- git push -u origin master

