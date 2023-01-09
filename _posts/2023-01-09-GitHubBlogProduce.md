---
title:  "[GitHubBlog] Windows 환경 깃허브 블로그 생성"
excerpt: "윈도우 환경에서 깃허브 블로그 생성"

categories:
  - GitHubBlog
tags:
  - [Blog, Git, GitHub]

toc: true
toc_sticky: true
 
date: 2023-01-09
last_modified_at: 2023-01-09
---

# **1. Github Blog 생성 준비**
---

## ruby 설치하기
  GitHub Blog를 생성하는 과정에서 **Jekyll**을 사용해야합니다.
  Jekyll은 **ruby**라는 언어로 만들어졌기 때문에 Jekyll을 설치하기 위해서 먼저 Ruby를 설치해야합니다.
  ruby 설치는 해당 [링크](https://rubyinstaller.org/downloads/)를 클릭해서 받아주세요.

 ![루비 설치](https://user-images.githubusercontent.com/93432326/211231490-bb3c0c7f-2494-4ce4-8368-86a32e9f86a4.PNG)

  Jekyll은 32bit라서 ruby 또한 x64가 아닌 x86으로 설치를 해주셔야합니다.
  <br>

## Jekyll 설치하기
  Jekyll을 설치하기 위해 ruby를 설치하였으니 이제 Jekyll을 설치 할 차례입니다.
  cmd창에서 다음의 명령어를 입력해 설치를 진행합니다.
  ```
  gem install jekyll
  ```
  > 설치가 완료되면 cmd에 `ruby -v`와 `jekyll -v`를 명령어를 입력해 설치가 잘 되었는지 확인합니다.
  <br>
  <br>

# **2. Jekyll 테마 선택하기**
---
## 사용할 Jekyll 테마를 선택한다.
자신이 사용할 마음에 드는 Jekyll 테마를 찾아 선택합니다. 
보편적으로 [chipy](https://github.com/cotes2020/jekyll-theme-chirpy) 또는 [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)을 사용합니다. 
<br>
<br>

# **3. GitHub Repository 생성과 GitClone 생성**
---
## GitHub Repository 생성하기

![주소복사](https://user-images.githubusercontent.com/93432326/211233651-0d9eb480-f59f-48e1-897f-de1529920449.PNG)

위의 Jekyll 테마 링크 또는 자신이 선택한 Jekyll 테마의 GitHub Repository의 URL를 복사해줍니다.

![임포트](https://user-images.githubusercontent.com/93432326/211233650-3fea6bcf-ee89-4262-a474-e223e7eb5363.PNG)

그 이후 새로운 Repository를 만들어 임포트를 해줍니다.

![임포트 상세](https://user-images.githubusercontent.com/93432326/211233646-8c938f7d-3684-46fe-a07c-45dab2717797.PNG)

Clone URL에는 복사해 온 URL을 넣어주고
Repository Name에는 **`자신의 아이디.github.io`**를 입력하고 import 버튼을 눌러줍니다.
생성 후, **https://[자신의 아이디].github.io**로 접속했을 때 이동하면 성공
<br>
<br>

## <mark style='background-color: #ffdce0'> 만약 페이지 접속 오류가 뜰 경우 </mark>
만약 저장소를 만들었음에도 접속 오류가 뜬다면 깃허브에서 호스팅 시키는 과정에서 서버에 원활한 통신이 이루어지지 않을 가능성이 큽니다.

![페이지 액션](https://user-images.githubusercontent.com/93432326/211240976-1c9a0216-3638-4b90-a5bf-f26bac22b687.PNG)

그럴 경우 Repositorty>Setting>Pages로 들어가 Build and deployment에서 **GitHubActions**으로 수정해줍니다. 그러면 페이지 접속 오류가 해결될 것 입니다.
<br>
<br>

## Local환경으로 Git Clone 생성하기
GitHub에서 Repository를 생성했다면 Clone을 생성 할 차례입니다.
Git bash에서 다음 명령어를 수행해 사용자 등록을 실행합니다.
```
git config --global user.name "GitHub이름"
git config --global user.email "GitHub이메일"
```

등록이 완료되었으면 자신의 GitHub URL을 복사하고 Local환경에서 Clone을 생성해줍니다.
```
git clone [URL]
```
그 이후 필요없는 파일들을 삭제하거나 초기화시키기 위해 다음 명령어를 수행합니다.
```
tools/init.sh
```
위의 명령어를 수행할 경우 posts폴더의 샘플 파일들과 docs폴더 등이 초기화가 됩니다.

<br>
<br>

# **4. Local환경에서 실행해보기**
---
Jekyll을 로컬에서 실행시키기 위해 필요한 모듈들을 설치해줍니다.
cmd에서 자신의 Repository 경로로 이동 한 후 다음 명령어를 실행해줍니다.
```
bundle install
bundle update
bundle install
```
설치 후 로컬 실행 명령어를 입력합니다.
```
jekyll s
```
정상적으로 수행됐다면 **`http://127.0.0.1:4000`** 이라는 주소가 출력되고 사이트로 이동하면 성공적으로 사이트가 출력됩니다.


# **5. GitHub 서버와 연결하기**
---
`git bash`에서 `cd`명령어를 이용해 Local환경의 Repository 폴더로 이동 후 다음의 명령어들을 수행해줍니다.

```
git add .
git comit -m "메시지"
git push
```
***git add .***는 폴더 내 파일들의 수정 사항들을 stage area에 업로드하는 명령어이며 `.`은 모든 파일을 의미합니다.

***git commit -m "메시지"***는 파일들을 올릴 준비를 하고

***git push***는 폴더 내 수정사항들을 GitHub Repository에 반영한다.
<br>
<br>


---
# Reperence
[공부하는 식빵맘](https://ansohxxn.github.io/blog/i-made-my-blog/)

[Ingyung Blog](https://iingang.github.io/posts/windows-github-set/#jekyll-%EC%9D%B4%EB%9E%80)

[하얀눈길 블로그](https://www.irgroup.org/posts/jekyll-chirpy/)

---

#### 
    개인적인 실행결과와 구글링 등을 통해 작성한 내용들입니다.
    오류나 수정할 부분이 있을 경우 알려주시면 수정하겠습니다.



[맨 위로 이동하기](#){: .btn .btn--primary }{: .align-right}




