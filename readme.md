# һ������git�̳�  
https://www.liaoxuefeng.com/wiki/896043488029600/898732792973664   

## �����÷�
��ʼ���ֿ⣨���ڵ�ǰĿ¼������.git�ļ���  
```git init  ```
  
����ļ���git�ֿ�  
`git add �ļ���`   
`git commit -m "ע��"`
  
## ��Ҫ����
git�ļ�����Ҫ����  
��������Working Directory��  
���ؿ���ֱ�ӿ�����Ŀ¼������ǰֱ�������޸ĵ�Ŀ¼��  
  
�汾�⣬��.git�ļ��У������ݴ�����stage ���� index���ͷ�֧��HEADָ�롣  
  
�ݴ�����stage ���� index��  
`git add �ļ���`�����ǽ��ļ��ӹ�������ӵ��ݴ���  
  
��֧  
`git commit -m "ע��"`�����ǽ��������е��ļ�һ���ύ����ǰ��֧�����Զ��ʹ��add���ݴ�����Ӷ���ļ���Ȼ��ʹ��commitһ�ν��ݴ������ļ��ύ����ǰ��֧��  
  
## ��������
�鿴�ֿ�״̬  
`git status` 
  
�鿴��ͬ��Ĭ�ϱȽϹ��������ݴ���  
`git diff`  
  
## �汾����
`git log`  
��ʾ���������Զ���ύ��־������--pretty=oneline����ʹ��git log --pretty=oneline�����Լ�����ʾ��ʷ��ÿ����ʾһ���ύ
���£�  
```
git log --pretty=oneline  
564d04c8f8385f22cc1baea9cc382e0f73e77c6f (HEAD -> master, origin/master) ��readme.md�Ļ�readme.txt  
829155b770b8ceffdebc65bb4e7870c2feb23aa3 ��readme.txt��Ϊreadme.md�������뷽ʽ����ΪGBK  
a1cb6c1e405014f34b795c858f6c99d8ace5b578 ���git�ļ�����������  
8a1cabb27f016dc8ab3b6ea2e30ac546c15344df �����ύ  
```
ǰ�ߵ�һ�����ֺ���ĸ��commit id���汾�ţ�����һ��SHA1���������һ���ǳ�������֣���ʮ�����Ʊ�ʾ  












<br /><br /><br /><br /><br /><br /><br /><br />
�����ϴ�
git init
git remote add origin ��ַ
git add .
git commit -m "ע��"
// git push ��ַ ��֧��
git push origin master

��ͨ�ϴ�
git add .
git commit -m "ע��"
// git push ��ַ ��֧��
git push origin master

��Զ�̿��¡��Զ�ֿ̲�Ĭ����origin
git clone ��ַ



��or create a new repository on the command line
echo "# learngit" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/StrongerL/learngit.git
git push -u origin master

��or push an existing repository from the command line
git remote add origin https://github.com/StrongerL/learngit.git
git push -u origin master

��or import code from another repository
You can initialize this repository with code from a Subversion, Mercurial, or TFS project.


hh 

