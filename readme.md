# git �ʼ�
## ��������

### ��������Working Directory��

���ؿ���ֱ�ӿ�����Ŀ¼������ǰֱ�������޸ĵ�Ŀ¼��   

### �ݴ�����stage ���� index��

`git add �ļ���`�����ǽ��ļ��ӹ�������ӵ��ݴ���  

### ��֧

`git commit -m "ע��"`�����ǽ��������е��ļ�һ���ύ����ǰ��֧�����Զ��ʹ��add���ݴ�����Ӷ���ļ���Ȼ��ʹ��commitһ�ν��ݴ������ļ��ύ����ǰ��֧��  

### �汾��

��.git�ļ��У������ݴ�����stage ���� index���ͷ�֧��HEADָ�롣 

## �����÷�

### `git init`

��ʼ���ֿ⣨���ڵ�ǰĿ¼������.git�ļ���������ǰĿ¼��ʼ��Ϊһ��git�ֿ⡣

### `git add �ļ���`

���ļ��ӹ�������ӵ��ݴ�����

### `git commit -m "ע��"`

���ļ����ݴ����ύ��git�ֿ⵱ǰ�汾��

### `git status`

�鿴�ֿ�״̬  

### `git diff`

�鿴��ͬ��Ĭ�ϱȽϹ��������ݴ���

### `git rm �ļ���`

�൱��`rm �ļ���` + `git add �ļ���` �����������ļ�ɾ��֮�󣬽������޸Ĵӹ������ύ���ݴ�����

### `git rm --cached �ļ���`

ɾ��git�е��ļ��������ڱ��ر������ļ���

## �����޸�

### `git restore �ļ���`

�������������޸ģ�����ݴ��������ݣ��ͻ��˵��ݴ���������ݴ���û�����ݣ��ͻ��˵���ǰ��֧���µ�commit��  

### `git restore --staged  �ļ���`

�����ݴ������޸ģ���ֱ�Ӷ�����  

### `git reset --hard HEAD`

�������������ݴ������޸ġ�  



## �汾����

### `HEAD`

HEAD ��һ���Ե�ǰ�����¼�ķ������� ���� Ҳ����ָ��������������Ͻ��й������ύ��¼��HEAD һ��ָ��ǰ�ķ�֧��HEAD Ҳ����ֱ��ָ���ύ��¼�����ǳ�Ϊ����� HEAD��

HEAD��һ��commit��������reset��Ϊ HEAD^ ������һ��Ϊ HEAD^^ ����10��Ϊ HEAD~10 ��  

### `git log`

��ʾ���������Զ��commit��־������--pretty=oneline����ʹ��git log --pretty=oneline�����Լ�����ʾ��ʷ��ÿ����ʾһ���ύ�����£�  

```
git log --pretty=oneline  
564d04c8f8385f22cc1baea9cc382e0f73e77c6f (HEAD -> master, origin/master) ��readme.md�Ļ�readme.txt  
829155b770b8ceffdebc65bb4e7870c2feb23aa3 ��readme.txt��Ϊreadme.md�������뷽ʽ����ΪGBK  
a1cb6c1e405014f34b795c858f6c99d8ace5b578 ���git�ļ�����������  
8a1cabb27f016dc8ab3b6ea2e30ac546c15344df �����ύ  
```
ǰ�ߵ�һ�����ֺ���ĸ��commit id���汾�ţ�����һ��SHA1���������һ���ǳ�������֣���ʮ�����Ʊ�ʾ��  

### `git reset`

���ĵ�ָ���汾���������Ͱ汾�⣨�汾����ͨ������HEADָ�룩�������

### `git reset --hard HEAD`

�ǻ��˵��汾�����µ�һ���ύ

### `git reset --hard commit-id`

���˵�ָ��commit id�İ汾commit-id����Ҫдȫ��дǰ��λ�Ϳ��ԡ�Ҳ���Բ���commit-id��ֻҪ��git����ʶ�����λ�ü��ɡ�

### `git reflog`

��ʾ�汾���ĵ�������־������commit��reset��������ǻ��˵�֮ǰ�İ汾����Ҫ�ٻص������µİ汾���Ϳ���ʹ��������������ҵ���Ӧ��commit id��ʹ��`git reset`�����ָ���汾��  



## Զ�ֿ̲�
### SSH��Կ

1. ����SSH��Կ������Ѿ����˿���������

   `ssh-keygen -t rsa -C "�ʼ���ַ"` �����������û���Ŀ¼������.sshĿ¼��������id_rsa��id_rsa.pub�����ļ�������������SSH Key����Կ�ԣ�id_rsa��˽Կ������й¶��ȥ��id_rsa.pub�ǹ�Կ�����Է��ĵظ����κ��ˡ�

2. ��½GitHub���򿪡�Account settings������SSH Keys��ҳ�棬Ȼ�󣬵㡰Add SSH Key������������Title����Key�ı�����ճ��id_rsa.pub�ļ������ݡ�github�����ж��SSH Key��

### ���Զ�̿�

1. github�ϴ���Զ�̿⣨��ʹ��github�Խ�������Ҳ���ԣ�

2. �ڱ��ش���git�ֿ⣨���вֿ������������һ����
   
   ```shell
   git init
   git add .
   git commit -m "ע��"
   ```
   
3. �ڱ���git�汾�������Զ�̿���ַ����ַ�ж������ͬ����ַ��Ӧ��ͬ�Ĵ���Э�顣

   ```shell
   git remote add origin ��ַ
   ```

4. �����ؿ�push��Զ�̿�

   ```shell
   # ����pushʹ��
   git push -u origin master
   # ֮��ʹ��
   git push origin master
   ```


### ��Զ�̿��¡

1. `git clone ��ַ`

2. �����ؿ�push��Զ�̿�

   ```shell
   # ����pushʹ��
   git push -u origin master
   # ֮��ʹ��
   git push origin master
   ```

`git remote [-v]`���鿴Զ�̿���Ϣ��  




## ��֧
### ��֧�������

#### git branch

�鿴��֧����ǰ���ڷ�֧ǰ��һ��*���š�

#### git branch ��֧��

������֧��

#### git checkout ��֧��

�л���֧���л���֧ʱ��ñ�֤git��״̬��clean��������ܻ�������¼��������

1. δ����/δ��ӵ��ݴ���/δ�ύ ���޸����л���Ŀ�ķ�֧�г�ͻ���л�ʧ��
2. δ����/δ��ӵ��ݴ���/δ�ύ ���޸����л���Ŀ�ķ�֧�޳�ͻ���л��ɹ���������·�֧�Ϸ����������޸ģ��л�ԭ��֧����Щ�޸�Ҳ�ᶪʧ��
3. �����֮���л���ֻ֧��ָ�Ŀ�ķ�֧�ύ�����޸ġ�

#### git checkout -b ��֧��

�����µķ�֧���л����µķ�֧����ͬ��`git branch ��֧��`  +  `git checkout ��֧��`��

#### git merge ��֧��

��ǰ��֧�ϲ�ָ����֧��

#### git rebase ��֧��

����ǰ��֧���޸������Եķ�ʽ�ϲ���������֧��

#### git branch -d ��֧��

ɾ��ָ����֧�������δ�ϲ���Ҫɾ������Ҫʹ��`git branch -D ��֧��`��



### �����ͻ

������֧������ֳ�ͻ����ôִ��`git merge ��֧��`ʱ����ִ��󣬿���ִ��`git merge --abort`�����ϲ���Ҳ�����ֶ������ͻ��ִ��`git add �ļ���`+`git commit -m "ע�͡�`������ɺϲ���
`git log --graph`������Կ�����֧�ϲ�ͼ��

### Զ�̷�֧

#### `git push origin master`  

��Զ�ֿ̲�����ָ����֧��  

#### `git push origin --delete ��֧��`  

ɾ��Զ�ֿ̲��ָ����֧������ɾ�����صķ�֧��  

#### `git checkout -b ��֧�� origin/��֧��`  

��Զ�ֿ̲�ץȡ��֧����¡Զ�ֿ̲�֮��ֻ�ܿ���master��֧��������֧��Ҫ�ֶ�ץȡ��  

#### `git pull`  

push���ֳ�ͻʱ��Զ�ֿ̲�pull�������µİ汾���Ա��޸�֮��add��commit��push���ɡ��������"There is no tracking information for the current branch. Please specify which branch you want to merge with."�Ĵ���˵���Ǳ��صķ�֧��Զ�ֿ̲�ķ�֧û�ж�Ӧ��ʹ��`git branch --set-upstream-to=origin/Զ�ֿ̲��֧�� ���ط�֧��`��Ӧ����push��  

#### `rebase`  

�������ύ��ʷ�����ֱ�ߡ�  

### BUG��֧

��ǰ��֧����δ�����˲���commit��������Ҫ�л���������֧������ʹ��`stash`���  

#### `git stash`

���浱ǰ�����ռ䡣  

#### `git stash list`  

�鿴��ǰ���е�stash�����0�������µ�stash��  

#### `git stash pop`  

Ĭ�ϻָ����µ�stash��ɾ�����൱��`git stash apply`���ָ�stash�� + `git stash drop`��ɾ��stash����Ҳ�����ڸ���������stash��Żָ�ָ��stash��



## ��ǩ

### `git tag`

�鿴��ǩ��Ϣ��  

### `git tag ��ǩ�� [commit id]`  

Ϊָ����commit���ǩ��Ĭ�ϴ������µ�commit�ϡ�   

### `git tag -a ��ǩ�� -m "ע��" [commit id]`  

����ע�͡�  

### `git show ��ǩ��`  

�鿴ָ����ǩ����Ϣ��  

### `git tag -d ��ǩ��`  

ɾ��ָ����ǩ��  

### `git push origin ��ǩ��`  

���ͱ�ǩ��Զ�̣�Ҳ����ʹ��`git push origin --tags`һ�����������б�ǩ��  

### `ɾ��Զ�̱�ǩ`  

����ʹ��`git tag -d ��ǩ��`ɾ�����ر�ǩ��Ȼ��ʹ��`git push origin :refs/tags/��ǩ��`ɾ��Զ�̱�ǩ��  


## �Զ���git
1. .gitignore�ļ�

   ��git����ָ���ļ���  

2. `cd > .gitignore`

   �½�.gitignore�ļ���  

3. �༭.gitignore�ļ�

   ÿ��һ������һ���ļ�������ʹ�����򣬿��Բο���[��վ](https://github.com/github/gitignore)��  

4. `git add -f �ļ���`

   ǿ����ӱ����Ե��ļ���  

5. `git checkout-ignore -v �ļ���`

   �鿴.gitinore�е��ĸ��ط�������ָ���ļ���  

6. `git config [--global] alias.���� ԭ����`

   ���ñ���������`--global`����ֻ��Ե�ǰ�ֿ⣬����������вֿ⡣ÿ���ֿ��Git�����ļ�������.git/config�ļ��У���������[alias]���棬Ҫɾ��������ֱ�ӰѶ�Ӧ����ɾ�����ɡ�  

## �ο�����

- [https://www.liaoxuefeng.com/wiki/896043488029600](https://www.liaoxuefeng.com/wiki/896043488029600)
- [https://github.com/pcottle/learnGitBranching](https://github.com/pcottle/learnGitBranching)