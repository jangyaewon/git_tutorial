20180716_ Git

https://github.com/neovansoarer/TIL

$ echo hello

hello



매뉴얼

$man echo

NAME

       echo - display a line of text

SYNOPSIS

       echo [SHORT-OPTION]... [STRING]...

       echo LONG-OPTION

DESCRIPTION

       Echo the STRING(s) to standard output.



help

$\help

n을 누르면 다음, shift + n은 이전으로

ctrl + a를 누르면 커맨드 맨 앞으로 돌아간다.  = Home

ctrl + e는 맨 뒤로 가는!! = END

ctrl + l은 clear

ctrl + u는 커맨드 모두 날리기

ctrl + w는 가장 나중에 나온 한 단어를 지운다.

alt + 원하는 위치에 커서를 올리면 그곳으로 바로 간다.



리다이렉트 ( > )

$ echo 'newline' > command.txt     command.txt에 'newline'를 집어넣어라

$ ls  리스트의 줄임말

$ less command.txt   내용을 보여준다.

 $ echo 'append'>> command.txt   이전까지 조장된 내용 밑으로 'append'가 박힌다.



 $ pwd >> command.txt는 이를 호출하는 경로를 저장라

$ ls 시리즈 알아두기 

$ rm 파일이름  _. 해당 파일 삭제

$cat command.txt   가장 작은 인터레션에 필욯

newlineappend

reverse

/home/ubuntu/workspace



curl

어디에 무엇이 있는 지 알려주는

$ which sh    

/bin/sh

$ which curl

/usr/bin/curl



$ curl -OL neovansoarer.github.io/files/sonnets.txt

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current

                                 Dload  Upload   Total   Spent    Left  Speed

100   178  100   178    0     0   5855      0 --:--:-- --:--:-- --:--:--  5933

100 95635  100 95635    0     0   765k      0 --:--:-- --:--:-- --:--:--  765k

$ ls

README.md  command.txt  sonnets.txt



$ curl -I https://google.com

HTTP/1.1 301 Moved Permanently

Location: https://www.google.com/

Content-Type: text/html; charset=UTF-8

Date: Mon, 16 Jul 2018 02:13:06 GMT

Expires: Wed, 15 Aug 2018 02:13:06 GMT

Cache-Control: public, max-age=2592000

Server: gws

Content-Length: 220

X-XSS-Protection: 1; mode=block

X-Frame-Options: SAMEORIGIN

권한 (루트, 그룹원, 게스트) 

drwxr-xr-x  -> 디렉토리를 루트는 읽고 쓰고 실행할 수 있다



$ wc sonnets.txt 

 2620 17670 95635 sonnets.txt -> 글자수

 $ head sonnets.txt 

앞 10줄을 뽑아온다.

$ tail sonnets.txt   

$ tail -5 sonnets.txt     



앞 10줄의 글자수 구하기

$ head sonnets.txt  > 10_sonnets.text

$ wc 10_sonnets.text 

 10  46 294 10_sonnets.text

$ head sonnets.txt | wc

10      46     294



$ tail -f command.txt 를 키고 있는 동안에 파일을 켜서 수정하면 결과가 반영된다.

$ ping google.com >google.log

$ tail -f google.log



원하는 단어를 찾아서 프린트시켜라

$ grep  spring sonnets.txt 

$ grep rose sonnets.txt | wc   rose를 몇번 썼는지

     10      82     419

     

프로세스

컴퓨터에서 계속 돌고 있는 프로그램??

ps aux는 돌고 있는 모든 프로세스,  그중에서 puma가 들어간 것을 골라라

    $ ps aux | grep puma
    ubuntu      2942  0.0  0.0  10568  1576 pts/3    S+   02:37   0:00 grep --color=auto puma

    내 밑에 있는 txt파일을 다 가져와라
    $ find . -name '*.txt'
    ./.c9/metadata/workspace/command.txt
    ./command.txt
    ./sonnets.txt

- 명령어 1 ; 명령어 2
  - 명령어 1이 성공 못하더라도 명령어 2를 실행한다.
- 명령어 1 && 명령어 2
  - 명령어 1이 성공 못한 경우에는 명령어 2도 실행 안 한다.

 



    $ ls -a .gitconfig
    .gitconfig
    
    wonwon:~ $ cat .gitconfig
    
    [user]
        name = Jang Yaewon
        email = rainsimple@naver.com
    
    [core]
        editor =  vim
        whitespace = off
        excludesfile = ~/.gitignore
    
    [advice]
        statusuoption = false
    
    [color]
        ui = true
    
    [push]
        default = currentwonwon:~ $ 

- 글로벌 셋업
  - c9 기준으론 하나의 워크스페이스당 한번 씩만 하면 된다.

    $ git config --global user.name "wonwon"
    wonwon:~ $ git config --global user.email "rainonebba@gmail.com"
    wonwon:~ $ cat .gitconfig
    [user]
            name = wonwon
            email = rainonebba@gmail.com
    [core]
        editor = vim
        whitespace = off
        excludesfile = ~/.gitignore
    [advice]
        statusuoption = false
    [color]
        ui = true
    [push]
        default = current



GIT

diff

    (master) $ git diff
    (master) $ touch index.html
    (master) $ git diff
    (master) $ git add index.html    ->untrack 상태에 add를 하니 staged단계로 변함
    (master) $ git diff
    ------------------------------------index에 글자 추가
    (master) $ git status

    On branch master
    
    No commits yet
    
    Changes to be committed:
      (use "git rm --cached <file>..." to unstage)
    
            new file:   index.html
    
    Changes not staged for commit:
      (use "git add <file>..." to update what will be committed)
      (use "git checkout -- <file>..." to discard changes in working directory)
    
            modified:   index.html

    $ git commit -m 'init repo'
    [master (root-commit) 6bf6208] init repo
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 index.html
    
    (master) $ git log
    commit 6bf620874897c244824749bc4892b95780488bad (HEAD -> master)
    Author: wonwon <rainonebba@gmail.com>
    Date:   Mon Jul 16 05:38:47 2018 +0000
    
        init repo

    (master) $ touch fake.html
    (master) $ touch foo.html
    (master) $ git add foo.html
    
    (master) $ rm --cached foo.html

add

- 새 파일을 올리는 것
- 이전에 올린 파일 중 달라진 걸 올리는 걸
  $ cat ~/.ssh/id_rsa.pub에서 ssh키를 가져오고 이를 bitbucket에 등록한다.



branch

    (master) $ git branch about-page
    (master) $ git branch
      about-page
    (master) $ git branch -d about-page
    Deleted branch about-page (was 8d95df6).
    (master) $ git branch
    
    (master) $ git checkout -b about-page    -> 없는 걸 생성하면 옮겨가는 것
    Switched to a new branch 'about-page'
    (about-page) $ git checkout master
    Switched to branch 'master'
    Your branch is up-to-date with 'origin/master'.
    
    (master) $ git checkout about-page
    Switched to branch 'about-page'
    (about-page) $ git add . && git commit -m 'Add about page'
    [about-page 5d8606b] Add about page
     1 file changed, 9 insertions(+)
     create mode 100644 about.html 
     
     (master) $ git branch -d about-page
    error: The branch 'about-page' is not fully merged.
    If you are sure you want to delete it, run 'git branch -D about-page'.
    (master) $ git branch -D about-page
    Deleted branch about-page (was 5d8606b).
    (master) $ git branch 



merge

    (about-page) $ git diff master
    diff --git a/index.html b/index.html
    index a1e59e4..aba7124 100644
    --- a/index.html
    +++ b/index.html
    @@ -1,7 +1,7 @@
     <html>
         <head>
             <title>
    -        GIT TUTORIAL
    +        GIT TUTORIAL222
             </title>
         </head>
         <body>gitgit</body>
         
    (master) $ git merge about-page 
    Updating 8d95df6..5ae0fdf
    Fast-forward
     index.html | 2 +-
     1 file changed, 1 insertion(+), 1 deletion(-)     



되돌아가기

- (master) $ git checkout -f  
  - (HEAD -> master, origin/master, about-branch)가 붙는 가장 최근에 커밋한 상태로 넘어간다.
- branch에서 활동했을 때

    (master) $ git checkout -b test-branch
    Switched to a new branch 'test-branch'
    (test-branch) $ echo ''>about.html
    (test-branch) $ git add .
    (test-branch) $ git commit -m 'WTF'
    [test-branch ce989a4] WTF
     1 file changed, 1 insertion(+)
     create mode 100644 about.html
    
    (test-branch) $ git checkout master
    Switched to branch 'master'
    Your branch is up-to-date with 'origin/master'.
    
    (master) $ git branch -D test-branch
    Deleted branch test-branch (was ce989a4).

- git branch 커밋ID


