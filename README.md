# githubtest BBBBBBBBBBBBBBBBBBBBBBBB
## githubの練習をしようとしたけどあきらめた  
### BBBBBB is BBBBBBBBBADDDDDDDDDDD
\
だれでもプルリク，イシュー大歓迎

## 初めに
Git と Github は別物です!!！
Git：アプリケーション (WindowsユーザーはGit_for_windows を導入しましょう)
Github : ウェブサイト

## Gitの始め方1--レポジトリを作ろう編--

0. git init *しよう*
    
    これを行うとGitに関する設定ファイル(.git)が作成されます。 これが存在するファイル以外でGitを使用しようとしても上手くいかない可能性があります
1. git add FILENAME *または* git add . *しよう*

    これを使うことで変更内容をインデックスに追加できます.  
2. git commit -m 'MESSAGE' *しよう*

    これを使うことでローカルリポジトリにコミットされます 
3. git push *しよう* 
 
    これを使うことでローカルリポジトリの内容をリモートリポジトリに送信できます 

## Gitの始め方2--レポジトリを自分のＰＣへ持ってこよう編--
1. git clone URL(これを持ってきたいなら)



## ブランチのやりかた
1. git checkout BRANCHNAME *で任意のブランチに移動出来る(ブランチは事前に作っておこう)* 
2. git branch *で今いるブランチを確認できる*


## commit したときに "Author identity unknown" と表示された場合
1. git config --global user.email "EMAIL" *しよう*


    実際のメアドを入力したくないときは貴方のプロフィールにある "Email" 欄の"Keep my email addresses private" にある "012345678+USERNAME@users.noreply.github.com" を入力しよう
2. git config --global user.name "USERNAME" *しよう*

    Githubに登録しているユーザー名を入力しよう※筆者ならabava00

## Git log に存在するusernameとEmailアドレスを書き換える場合

1. AUTHERを書き換える場合。
   ```
    git filter-branch -f --commit-filter '
         if [ "$GIT_AUTHER_EMAIL" = "書き換え元のEmailアドレス" ];
         then
                 GIT_AUTHER_NAME="書き換えた後に表示されるuser名";
                 GIT_AUTHER_EMAIL="書き換えた後に表示されるEmailアドレス";
                 git commit-tree "$@";
         else
                 git commit-tree "$@";
         fi' HEAD
   ```
2. COMMITERを書き換える場合
   ```
    git filter-branch -f --commit-filter '
         if [ "$GIT_COMMITTER_EMAIL" = "書き換え元のEmailアドレス" ];
         then
                 GIT_COMMITTER_NAME="書き換えた後に表示されるuser名";
                 GIT_COMMITTER_EMAIL="書き換えた後に表示されるEmailアドレス";
                 git commit-tree "$@";
         else
                 git commit-tree "$@";
         fi' HEAD
   ```
3. リモートブランチに反映するため、`git push -f`を行う。  
   これでメールアドレスが見られることはなくなるだろう...
