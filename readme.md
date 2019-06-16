# һ������git�̳�  
https://www.liaoxuefeng.com/wiki/896043488029600/898732792973664   
  
## ��Ҫ����
git�ļ�����Ҫ����  
��������Working Directory��  
���ؿ���ֱ�ӿ�����Ŀ¼������ǰֱ�������޸ĵ�Ŀ¼��   
  
�ݴ�����stage ���� index��  
`git add �ļ���`�����ǽ��ļ��ӹ�������ӵ��ݴ���  
  
��֧  
`git commit -m "ע��"`�����ǽ��������е��ļ�һ���ύ����ǰ��֧�����Զ��ʹ��add���ݴ�����Ӷ���ļ���Ȼ��ʹ��commitһ�ν��ݴ������ļ��ύ����ǰ��֧��  
  
�汾��  
��.git�ļ��У������ݴ�����stage ���� index���ͷ�֧��HEADָ�롣 
  
## �����÷�
`git init`  
��ʼ���ֿ⣨���ڵ�ǰĿ¼������.git�ļ���������ǰĿ¼��ʼ��Ϊһ��git�ֿ⡣    
  
`git add �ļ���`  
���ļ��ӹ�������ӵ��ݴ�����  
  
`git commit -m "ע��"`  
���ļ����ݴ����ύ��git�ֿ⵱ǰ�汾��  
  

## ��������
`git status`  
�鿴�ֿ�״̬  
  
`git diff`  
�鿴��ͬ��Ĭ�ϱȽϹ��������ݴ���  
  
## �汾����
`HEAD`  
��git��ʹ��HEAD����汾���е�ǰ�汾��HEAD��һ��commit��������reset��ΪHEAD^������һ��ΪHEAD^^����10��ΪHEAD~10��  
  
`git log`  
��ʾ���������Զ��commit��־������--pretty=oneline����ʹ��git log --pretty=oneline�����Լ�����ʾ��ʷ��ÿ����ʾһ���ύ
���£�  
```
git log --pretty=oneline  
564d04c8f8385f22cc1baea9cc382e0f73e77c6f (HEAD -> master, origin/master) ��readme.md�Ļ�readme.txt  
829155b770b8ceffdebc65bb4e7870c2feb23aa3 ��readme.txt��Ϊreadme.md�������뷽ʽ����ΪGBK  
a1cb6c1e405014f34b795c858f6c99d8ace5b578 ���git�ļ�����������  
8a1cabb27f016dc8ab3b6ea2e30ac546c15344df �����ύ  
```
ǰ�ߵ�һ�����ֺ���ĸ��commit id���汾�ţ�����һ��SHA1���������һ���ǳ�������֣���ʮ�����Ʊ�ʾ��  
  
`git reset`  
���ĵ�ָ���汾���������Ͱ汾�⣨�汾����ͨ������HEADָ�룩�������  
`git reset --hard HEAD`�ǻ��˵��汾�����µ�һ���ύ  
`git reset --hard commit id`���˵�ָ��commit id�İ汾commit id����Ҫдȫ��дǰ��λ�Ϳ��ԡ�
  
`git reflog`  
��ʾ�汾���ĵ�������־������commit��reset��������ǻ��˵�֮ǰ�İ汾����Ҫ�ٻص������µİ汾���Ϳ���ʹ��������������ҵ���Ӧ��commit id��ʹ��`git reset`�����ָ���汾��  
  
## �����޸�
`git checkout -- �ļ���`  
�����������޸ģ����������  
�ݴ�����Ϊ�գ����˵��ݴ�����״̬��   
�ݴ���Ϊ�գ����˵��汾�⵱ǰ״̬��  
  
`git reset HEAD �ļ���`  
�����ݴ������޸ġ�  
  
`git reset --hard HEAD`  
�Ѿ��ύ���汾�⣬����ʹ��`git reset`���˵�֮ǰ�汾��  
  
## ɾ���ļ�
`git rm �ļ���`  
�൱��`rm �ļ���` + `git add �ļ���` �����������ļ�ɾ��֮�󣬽������޸Ĵӹ������ύ���ݴ�����  

`git rm --cached �ļ���`  
ɾ��git�е��ļ��������ڱ��ر������ļ���  
  
## Զ�ֿ̲�
**SSH��Կ**  
1. ����SSH��Կ������Ѿ����˿���������  
`ssh-keygen -t rsa -C "�ʼ���ַ"` �����������û���Ŀ¼������.sshĿ¼��������id_rsa��id_rsa.pub�����ļ�������������SSH Key����Կ�ԣ�id_rsa��˽Կ������й¶��ȥ��id_rsa.pub�ǹ�Կ�����Է��ĵظ����κ��ˡ�
2. ��½GitHub���򿪡�Account settings������SSH Keys��ҳ�棬Ȼ�󣬵㡰Add SSH Key������������Title����Key�ı�����ճ��id_rsa.pub�ļ������ݡ�github�����ж��SSH Key��
  
**���Զ�̿�**  
1. github�ϴ���Զ�̿⣨��ʹ��github�Խ�������Ҳ����Ҳ���ԣ�
2. �ڱ��ش���git�ֿ⣨���вֿ������������һ����
   `git init`  
   `git add .`  
   `git commit -m "ע��"`    
3. �ڱ���git�汾�������Զ�̿���ַ����ַ�ж������ͬ����ַ��Ӧ��ͬ�Ĵ���Э�顣   
   `git remote add origin ��ַ `  
4. �����ؿ�push��Զ�̿�
   ����pushʹ��`git push -u origin master`  
   ֮��ʹ��`git push origin master`  
  
**��Զ�̿��¡**  
1. `git clone ��ַ`  
2. �����ؿ�push��Զ�̿�
   ����pushʹ��`git push -u origin master`  
   ֮��ʹ��`git push origin master`   
  
`git remote [-v]`  
�鿴Զ�̿���Ϣ��  

  
## ��֧����
**��֧�������**  
`git branch`  
�鿴��֧����ǰ���ڷ�֧ǰ��һ��*���š�  
  
`git checkout -b ��֧��`  
�����µķ�֧���л����µķ�֧����ͬ��`git branch ��֧��`�������µķ�֧�� + `git checkout ��֧��`���л���ָ����֧����  
  
`git merge ��֧��`  
����ǰ��֧��ָ����֧�ϲ���  
  
`git branch -d ��֧��`  
ɾ��ָ����֧�������δ�ϲ���Ҫɾ������Ҫʹ��`git branch -D ��֧��`   
  
  
**��֧��ͻ����**  
������֧������ֳ�ͻ����ôִ��`git merge ��֧��`ʱ����ִ��󣬿���ִ��`git merge --abort`�����ϲ���Ҳ�����ֶ������ͻ��ִ��`git add �ļ���`+`git commit -m "ע�͡�`������ɺϲ���
`git log --graph`������Կ�����֧�ϲ�ͼ��  
  
  
**��֧�ϲ��ķ�ʽ**  
Ĭ��ΪFast Forward�����޳�ͻ�Ļ�ֱ�Ӹ���ָ�룬�������commit��  
����ʹ��`git merge --no-ff`ǿ�ƽ���Fast Forward���ںϲ�ʱ�����һ��commit��  
  
  
**BUG��֧**  
��ǰ��֧����δ�����˲���commit��������Ҫ�л���������֧������ʹ��`stash`���  

`git stash`  
���浱ǰ�����ռ䡣  

`git stash list`  
�鿴��ǰ���е�stash�����0�������µ�stash��  

`git stash pop`  
Ĭ�ϻָ����µ�stash��ɾ�����൱��`git stash apply`���ָ�stash�� + `git stash drop`��ɾ��stash����Ҳ�����ڸ���������stash��Żָ�ָ��stash��


