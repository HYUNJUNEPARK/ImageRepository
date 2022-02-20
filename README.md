# Git
---
0. <a href = "#content1">리눅스 명령</a></br>
1. <a href = "#content2">깃 버전 만들기</a></br>
2. <a href = "#content3">브랜치</a></br>
3. <a href = "#content4">병합</a></br>
4. <a href = "#content5">깃허브로 백업</a></br>
5. <a href = "#content6">깃허브로 협업</a></br>
6. <a href = "#content7">깃허브 리포지토리 합치기</a></br>
7. <a href = "#content8">README 마크 다운 문법</a></br>
---

# <a id = "content1">[ 0. 리눅스 명령 ]</a>

사용자 정보 입력</br>
`git config --global user.name "HYUNJUNE"`</br>
`git config --global user.email "june2ac4dev@gmail.com"`</br>

사용자 정보 삭제</br>
`git config --unset user.name`</br>
`git config --unset user.email`</br>

*global로 설정된 config 사용자인 경우</br>
`git config --unset --global user.name`</br>
`git config --unset --global user.email</br>

`pwd`</br>
//현재 디렉토리의 경로 확인(Print Working Directory)</br>

`ls`</br>
//현재 디렉토리에 있는 파일이나 디렉토리 확인</br>
**[ls와 함께 쓰이는 옵션]**</br>
-l</br>
//파일과 디렉터리의 상세 정보까지 표시하는 옵션 추가</br>
-a</br>
//숨긴 파일과 디렉터리를 표시하는 옵션 추가</br>
-r</br>
//파일 정렬 순서를 거꾸로 하는 옵션 추가</br>
-t</br>
//파일 작성 시간 순으로(내림차순) 표시</br>

`cd ..`</br>
//상위 디렉토리로 이동</br>
`cd 하위 디렉토리 이름`</br>
//하위 디렉토리로 이동</br>
`cd ~`</br>
//홈 디렉토리(처음 출발했던 디렉토리)로 돌아감</br>

`mkdir 디렉토리 이름`</br>
//디렉토리 생성</br>
`rm -r 디렉토리 이름`</br>
//디렉토리 안에 있는 하위 디렉토리와 파일까지 삭제(삭제할 디렉토리의 상위 디렉토리에서 명령어 입력)</br>

`vim 파일이름`</br>
//빔 편집기를 사용한 파일 생성(I or A 키 입력(입력모드 전환) -> 데이터를 입력 후 :wq 로 저장 및 종료)</br>
**[빔 편집기 명령어]**</br>
:w</br>
//편집 중이던 문서를 저장</br>
:q</br>
//편집기를 종료</br>
:wq(파일명)</br>
//편집 중이던 문서를 저장하고 종료. 파일 이름을 함께 입력하면 그 이름으로 저장</br>
:q!</br>
//문서를 저장하지 않고 편집기 종료</br>

`cat 파일`</br>
//파일의 내용을 화면에 표시</br>
`cat 파일1 파일2 ... 파일n > 새파일`</br>
//파일 n개를 차례로 연결해 새로운 파일 생성 *파일이름 사이에 , 없음</br>
`cat 파일1 >> 파일2`</br>
//파일1의 내용을 파일2 끝에 연결(파일2만 수정됨)</br>

`clear`</br>
//터미널 창의 내용 지움</br>
`exit`</br>
//터미널 창 종료</br>

---
# <a id = "content2">[ 1. 깃 버전 만들기 ]</a>

.gitignore 파일을 만들고 '특정 파일' 또는 '특정 디렉토리' 를 만들어 저장하면 버전관리에서 제외할 수 있음</br>

`git init`</br>
//깃파일 생성</br>

`git init 디렉토리 이름`</br>
//디렉토리를 생성함과 동시에 git 파일도 생성</br>

`git status`</br>
//깃파일이 관리하는 파일 상태 확인 *깃에 올라기지 않은 파일 목록이 빨간색으로 보임</br>

`git add -A`</br>
//깃 관리 대상 아래 있는 '모든 파일' 을 스테이지(버전으로 만들 파일이 대기하는 곳)에 올림</br>

`git add 파일이름`</br>
//깃 관리 대상 아래 있는 '특정 파일' 을 스테이징 영역에 올림</br>

`git add .`</br>
//현재 저장소에 수정된 파일을 한번에 스테이지에 올림</br>

`git commit -m "설명"`</br>
//스테이지에 대기하고 있던 파일들을 버전으로 만들어 리포지토리에 커밋</br>

**[commit과 함께 쓰이는 옵션]**</br>
-a `git commit -a -m "설명"`</br>
//add와 commit 작업을 한번에 할 수 있음. 새로 만든 파일은 커밋이 한번 된 이후에 사용할 수 있음 </br>
--amend `git commit --amend`</br>
//커밋 메시지를 잘못 입력했다면 커밋을 만든 '즉시' 커밋 메세지를 수정할수 있음 </br>

`git log`</br>
//버전 기록을 볼 수 있음</br>
//'commit 68e829...'(커밋 해시, 깃 해시)를 볼 수 있는데 reset, revert 에서 사용됨</br>

**[log와 함께 쓰이는 옵션]**  `git log --oneline --branches --graph` </br>
--oneline</br>
//한 줄에 하나의 커밋을 나타내 줘 간략하게 log를 볼 수 있음</br>
--branches</br>
//각 브랜치의 커밋을 함께 볼 수 있음</br>
--graph</br>
//브랜치와 커밋의 관계를 그래프 형태로 표시</br>

`git diff`</br>
//변경 사항 확인</br>

`git checkout --파일이름`</br>
//스테이지에 올라가 있는 파일을 이전 상태로 되돌림(디렉토리가 파일의 디렉토리랑 같아야함)</br>
//파일을 수정한 뒤 소스가 정상적으로 동작하지 않을 때 최신 버전 상태로 되돌릴 수 있음</br>

`git restore 파일이름`</br>
`git restore MainActivity.kt, git checkout MainActivity.kt`</br>

`git checkout 이동할 버전의 커밋해시`</br>
//지정 버전으로 이동</br>

`git reset HEAD 파일이름 OR git reset HEAD^`</br>
//가장 최근 커밋 취소</br>

`git restore --staged 파일이름`</br>
//스테이징을 취소 ex)git reset HEAD MainActivity.kt, git restore --staged MainActivity.kt</br>

`git reset 이동할 버전 커밋해시`</br>
//커밋해시 시점으로 이동(이동한 버전 이후 커밋은 삭제됨)</br>

`git revert 취소할 커밋해시`</br>
//커밋해시로 취소할 시점을 찾는다(다시 돌아갈 수 있음)</br>
//가장 최근 커밋해시를 입력하면 최근 커밋해시가 취소되고 직전 작업으로 이동됨</br>
//git log 보면 revert 가 붙은 로그가 기존 로그를 지우지 않고 스택처럼 쌓임</br>

`git stash`</br>
//특정 파일을 커밋하지 않고 잠시 감춰 둠. 당장 필요한 파일을 먼저 커밋하고 감춰 둔 파일을 꺼내서 작업 *파일이 한번은 커밋된 상태여야함</br>
`git stash list`</br>
//감춘 파일의 리스트를 볼 수 있음. stash@{n} 형태로 담기며 가장 최근에 보관한 파일이 stash@{0} 에 담김</br>
`git stash pop`</br>
//감춰둔 파일을 꺼내옴</br>
`git stash drop`</br>
//감춘 파일 리스트에서 가장 최근 항목을 삭제</br>

---
# <a id = "content3">[ 2. 브랜치 ]</a>

`git branch 브랜치 이름`</br>
//브랜치 생성</br>

`git branch`</br>
//브랜치 확인(*가 앞에 붙어 있는 브랜치에서 작업 중)</br>
*HEAD는 작업 중인 브랜치를 가리키는 포인터</br>

git checkout 브랜치 이름 `git checkout master`</br>
//다른 브랜치로 이동 </br>

-b `git checkout -b 브랜치 이름`</br>
// 브랜치를 만들고 체크아웃하는 것을 한번에 진행 </br>

`git log A브랜치 ..B브랜치`
//A브랜치에는 없고 B브랜치에만 있는 커밋 출력</br>

`git branch -d 브랜치 이름`</br>
//브랜치 삭제</br>

`git branch -D 브랜치 이름`</br>
//master 브랜치에 병합하지 않은 브랜치를 삭제하려면 오류 메세지가 나타남. 이때 -D를 사용하면 브랜치 강제 삭제</br>
//브랜치는 완전히 삭제되는 것이 아니라 같은 이름의 브랜치를 만들면 예전 내용을 다시 볼 수 있음</br>
//git branch 로 브랜치가 삭제된 것을 확인할 수 있으나, `git log --branches` 로 브랜치의 흔적을 볼 수 있음</br>

---
# <a id = "content4">[ 3. 병합 ]</a>

`git merge 가져올 브랜치 이름`</br>
//HEAD가 위치한 브랜치에 다른 브랜치를 가져와 병합시킴</br>
//가져올 브랜치는 삭제되지 않으며 master 브랜치만 갱신됨</br>
//conflict 발생을 막기위해 협업 시에는 가능한 다른 브랜치에서 같은 파일을 수정하는 일이 없어야함

**[merge와 함께 쓰이는 옵션]**</br>
`--no-edit`</br>
//빔이 자동으로 실행되지 않으며 깃에서 지정하는 커밋메세지를 그대로 사용함</br>
`git merge 가져올 브랜치 이름 --no-edit`</br>

**[conflict 발생 시]**</br>
`<<<<<<< HEAD`</br>
현재 브랜치에서 충돌하는 내용</br>
`=======`</br>
가져올 브랜치에서 충돌하는 내용</br>
`>>>>>>> 가져올 브랜치 이름`</br>

---
# <a id = "content5">[ 4. 깃허브로 백업 ]</a>

깃 기본 브랜치 : master, 기본 원격 저장소 : origin </br>

`git remote add origin 깃허브 저장소 주소`</br>
//로컬 저장소를 깃허브 원격 저장소에 연결, origin 은 '깃허브 저장소 주소'를 의미함</br>
`git remote -v`</br>
//원격 저장소 연결 확인</br>
`git remote remove <name>`</br>
`git remote remove origin`</br>
//리포지토리 연결 해제 </br>

`git push -u origin master`</br>
//지역 저장소의 브랜치(master)를 원격 저장소의 master 브랜치(origin)로 올림(push)</br>
//지역 저장소의 브랜치와 origin 의 master 브랜치를 연결한 후에는 git push 만 입력</br>
`-u`</br>
//지역 저장소의 브랜치를 원격 저장소의 master 브랜치에 연결하기 위한 옵션으로 처음 한 번만 사용하고 이후 git push 만으로 master 브랜치에 커밋을 올릴 수 있음</br>
`git push origin 브랜치 이름`</br>
//원격 저장소(origin)에 브랜치를 올림</br>
//push 된 브랜치는 pull reqeust 를 통해 병합해야 원격 저장소에 반영됨</br>

`git pull origin master`</br>
//원격 저장소(origin)의 내용을 master 브랜치로 가져옴. 수정사항이 있다면 'Create 파일이름' 으로 커밋 로그가 생김</br>
//협업 시 다른 작업자의 변경 내용을 바로 반영하기 위해 항상 git pull 부터 한 다음 내 작업을 진행할 것</br>

`SSH(Secure Shell)`</br>
-Private Key(사용자 컴퓨터에 저장되는 키) 와 Public Key(외부에 공개되는 키) 를 한 쌍으로 묶어서 컴퓨터를 인증</br>
-원격 저장소를 사용하는 동안 로그인 정보를 요구하지 않음</br>
-ssh-keygen //SSH 키 생성</br>

**[깃허브에 SSH 원격 접속 절차]**</br>
(1) SSH 방식으로 접근 시 먼저 사용자 컴퓨터에 만들어져 있는 Public Key 를 깃허브 서버로 전송한 다음 저장</br>
ㄴid_rsa.pub 파일에 Public Key 가 담겨있음. ssh-rsa부터 문자열 끝까지 Copy</br>
ㄴ깃허브 접속 후 오른쪽 프로필 아이콘의 Settings 를 선택</br>
ㄴAccess -> SSH and GPG keys -> New SSH key 에 Title 과 Copy 한 Public Key 입력</br>
(2) 사용자 컴퓨터에서 깃 허브 저장소 접속 시 사용자 컴퓨터에 있는 Private Key 와 Public Key 를 비교함</br>
ㄴ원격 저장소에서 SSH 주소를 복사</br>
ㄴgit remote add origin 복사한 SSH 주소</br>
(3) Priavate Key 와 Public Key 가 일치하면 사용자 컴퓨터와 깃 허브 저장소가 연결됨</br>
ㄴgit remote -v 로 연결 확인</br>

---
# <a id = "content6">[ 5. 깃허브로 협업 ]</a>

`git clone 깃허브 저장소 주소 디렉토리 이름`</br>
`git clone https://github.com/HYUNJUNEPARK/SlideShowApp.git SlideShowApp`</br>
//원격 저장소 내용을 지역 저장소로 복사</br>

//현재 디렉토리에 복제 하려면 디렉토리 이름에 . 을 입력</br>
//git log 로 지역 저장소와 원격 저장소의 커밋 상태를 확인할 수 있음. HEAD -> master 는 지역 저장소의 최종 커밋. origin/master 는 원격 저장소의 최종 커밋</br>

`git fetch`</br>
//원격 저장소의 정보를 가져옴(FETCH_HEAD) *pull 은 원격 저장소의 커밋을 가져와 무조건 지역 저장소와 합친다면 fetch 는 원격 브랜치에 어떤 변화가 있는지 그 정보만 가져옴</br>


`FETCH_HEAD`</br>
//fetch 로 가져온 정보가 담기는 브랜치</br>

**[git fetch 로 가져온 원격 저장소의 최신 커밋을 보고 싶을 때]**</br>
(1) `git checkout FETCH_HEAD`</br>
(2) `git log` 로 최신 커밋 확인</br>
(3) 내용을 확인해보고 상황에 따라 `git pull` 이나 `git merge FETCH_HEAD` 를 사용</br>
ㄴ최신 커밋을 현재 브랜치에 합칠 때 : `git pull`</br>
ㄴFETCH_HEAD 에 있는 커밋을 병합할 때 : `git checkout master` -> `git merge FETCH_HEAD`</br>
//`git pull` 명령은 `git fetch` 명령과 `git merge FETCH_HEAD` 명령 두개를 합친 것과 같은 기능을 함</br>

---

# <a id = "content7">[ 6. 깃허브 리포지토리 합치기 ]</a>

(1) 깃허브에 기존 리포지토리를 합칠 새로운 리포지토리를 만든다.(상위 디렉터리로 쓰일 리포지토리 *이하 RepoA)</br>
(2) `git clone RepoA 주소`</br>
//터미널에서 RepoA를 clone 한다.</br>
(3) `cd RepoA`</br>
//RepoA 디렉터리로 이동한다</br>
(4) `git add . → git commit -m"init"`</br>
//커밋 기록을 하나 만든다</br>
(5) `git subtree add --prefix=(해당 Repository 하위의 디렉터리 구조) (옮겨올 Repository 주소) (옮겨올 Repository의 branch)`</br>
`git subtree add --prefix=SubRepo SubRepo주소 main`</br>
//subtree를 이용하는 방법으로 리포지토리를 합친다</br>
(6) `git push`</br>

---
# <a id = "content8">[ 7. README 마크 다운 문법 ]</a>

`#`</br>
제목을 입력할 때 1~6개까지 텍스트 앞에 붙여 크기를 정할 수 있음.</br>
`#` 과 텍스트 사이에는 여백이 있어야함</br>
`# 마크다운 테스트`</br>

`--- or ***`</br>
//가로 줄 생성</br>

`+` or `-` or `*`</br>
//위 기호를 붙여 나열하면 자동으로 글머리 기호가 붙으며 순서 없는 목록이 생성됨</br>
//순서 없는 목록에서 Tab 을 눌러 항목을 들여 쓸 수 있음</br>

`**텍스트 굵게**` **텍스트 굵게**</br>
`*텍스트 기울임*` *텍스트 기울임*</br>
`***텍스트 굵은 기울임***` ***텍스트 굵은 기울임 </br>
`~~취소선~~` ~~취소선~~</br>

`> 인용문 삽입1`</br>
`>> 인용문 삽입2`</br>

```kotlin
`한줄 짜리 소스코드`
```

```kotlin
```프로그래밍 언어 //javascropt 나 pyton 등 프로그래밍 언어를 함께 지정하면 해당 언어에 맞는 소스 형태로 표시됨
여러 줄 소스코드
\```
```

```kotlin
<링크주소>
[링크 텍스트](링크 주소)
[링크 텍스트]{링크 주소, "부가 설명"}
```

```kotlin
1. 이미지 마크다운 형식
![대체 텍스트](이미지 파일 경로)

2. 이미지 HTML 태그 방식
<img src="이미지 주소" width="200" height="400"/>

1.마크다운 형식은 이미지 사이즈 조절 불가하지만 2.HTML 태그 방식은 이미지 사이즈 조절 가능
```

---

