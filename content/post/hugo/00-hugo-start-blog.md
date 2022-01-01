---
title: "Hugo로 시작하는 Github pages 블로그!"
date: 2021-12-28T01:06:19+09:00
categories: 
- "기타/etc"
tags:
- "Hugo"
- "Github pages"
keywords:
- tech
---

# 블로그를 시작하는 이유
```
- 연구, 개발자로서의 꾸준한 동기부여.
- 스스로 배워서 완성해가는 지식.
- 배운것을 공유하는 즐거움.
```

사람 저마다 여러가지 이유로 블로그를 시작하는 이유가 있겠지만,
나는 위 3가지만으로도 블로그를 시작하는 충분한 이유가 된다고 생각한다.

### # 대세는 Hugo!
과거에도 그렇고 지금도 Jekyll은 정적 페이지를 만들때 대표적으로 나오는 정적 페이지 생성기이다.
그래서 예전에 jekyll로 github pages를 만드려보려고 했었다.
다른 기술블로그에서 알려준 방법대로 테마를 넣고, 커스텀도 시도해보았는데 생각보다 
배워야할 것들도 많고 어렵게만 느껴졌다. 
<span style='background-color: #FFF2CC;'> (지금도 그렇지만 그때는 FE 지식이 전무)</span>
그러다 겨우 몇개의 포스트만 올리고 jekyll과는 멀어지게 되었다... :cry:

<br>
<script type="text/javascript" src="https://ssl.gstatic.com/trends_nrtr/2790_RC04/embed_loader.js"></script> <script type="text/javascript"> trends.embed.renderExploreWidget("TIMESERIES", {"comparisonItem":[{"keyword":"jekyll","geo":"","time":"today 5-y"},{"keyword":"hexo","geo":"","time":"today 5-y"},{"keyword":"hugo","geo":"","time":"today 5-y"}],"category":31,"property":""}, {"exploreQuery":"cat=31&date=today%205-y&q=jekyll,hexo,hugo","guestPath":"https://trends.google.com:443/trends/embed/"}); </script> 
<br>
<br>

그래서 Hugo를 왜 선택했나?
+ **약간이지만 요즘은 Hugo가 jekyll보다 대세이다..!**
+ **`Golang`으로 구현되어있어 빌드도 빨라 거의 실시간으로 렌더링해볼 수 있다.**
  > 

재미있는 점은 국가별로 트렌트가 확실히 나뉘는걸 알 수 있다.
`Google Trends`을 클릭하여 페이지를 이동하여 <ins>지역별 비교 분석</ins>에서 확인할 수 있는데,
<ins>2021.12 기준으로 Jekyll은 미국, 호주, <span style='background-color: #FFF2CC;'>**한국**</span>에서,
Hugo는 러시아, 북미, 남미, Hexo는 중국에서 많은 관심을 보였다.</ins>


아무튼 잡설이 길었는데 Hugo로 Github pages 블로그를 시작하는 것을 공유해보고자 한다.
이미 여러 기술블로그에서 Hugo로 블로그를 만드는 방법이 잘 기술되어있다.
하지만 디테일한 부분이 생략된 경우가 더러있어 아래 두개의 블로그를 참고하여
보완 작성하였다. <span style='background-color: #CCFFCC;'>귀찮더라고 순서대로 따라해보자!</span>

- [gurumee92님 블로그 구축기 (1) Hugo + Github으로 개인 블로그 만들기](https://gurumee92.github.io/2020/08/%EB%B8%94%EB%A1%9C%EA%B7%B8-%EA%B5%AC%EC%B6%95%EA%B8%B0-1-hugo-github%EC%9C%BC%EB%A1%9C-%EA%B0%9C%EC%9D%B8-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EB%A7%8C%EB%93%A4%EA%B8%B0/)
- [sangm1n님［기타 / Etc］ Hugo와 Github pages를 이용한 새 블로그 시작](https://sangm1n.github.io/start-new-blog/)

<br>

### # Hugo 설치 (Mac)
설치 전 준비해야할 것은 다음과 같다. 
- Github 가입
- Golang 설치 - [Golang 설치방법](https://go.dev/doc/install)

Terminal을 띄운 후 다음을 입력한다.
```shell
# hugo 설치
$ brew install hugo
```

만일 Mac이 아닌 다른 OS(Linux, Windows)라면 [여기](https://gohugo.io/getting-started/installing/)를 참고하여 Hugo를 설치하자.

설치가 완료되었다면, 다음을 터미널에 입력하여 제대로 설치되었는지 확인해보자.
```shell
# hugo 버전체크
$ hugo version

hugo v0.91.2+extended darwin/amd64 BuildDate=unknown
```

<br>

### # Github repository 2개 생성
+ `<PROJECT>` : hugo의 소스파일 및 포스트가 저장될 장소
+ `<USERNAME>.github.io` : 배포되는 Github pages

> <PROJECT>이름은 맘대로 정해도 된다. 필자는 `blog`로 정함.

<br>

### # Hugo 프로젝트 생성

```shell
# Github repository 생성할때 설정한 PROJECT 이름으로 프로젝트를 만들어주자.
$ hugo new site <PROJECT>

# 프로젝트 생성이 완료된다면, 아래가 출력된다.
Congratulations! Your new Hugo site is created in /Users/user/Desktop/study/blog.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```

<br>

### # 원격저장소 연결
```shell
# 프로젝트 루트 경로
$ pwd
/Users/user/Desktop/study/blog

# git 레포 초기화 
$ git init

# Github에서 생성한 <PROJECT> 레포를 프로젝트 루트 경로에 remote 등록 
# git remote add origin https://github.com/<USERNAME>/<PROJECT>.git
$ git remote add origin https://github.com/blacknwhite5/blog.git
```

<br>


### # Submodule 연결 (Github pages)
```shell
# <ROOT_DIRECTORY>/public 디렉토리와 <USERNAME>.github.io 연결
$ git submodule add -b master http://github.com/blacknwhite5/blacknwhite5.github.io.git public
```

<br>


### # 마음에 드는 테마 적용
Hugo 테마는 jekyll보다 수가 적지만 심플한 테마가 많다.
테마는 [여기](https://themes.gohugo.io/)서 확인할 수 있다.
필자는 심플한 것을 좋아하기 때문에 4개의 테마를 추리고 최종적으로 `hugo-PaperMod`를 선택하였다.

+ 어떤걸 고를까 고민했던 후보들🤔
  - [LoveIt](https://hugoloveit.com/)
  - [KeepIt](https://suspicious-archimedes-ab369d.netlify.app/)
  - [Monochrome](https://kaiiiz.github.io/hugo-theme-monochrome/)
  - [PaperMod](https://adityatelange.github.io/hugo-PaperMod/)


```shell
# theme을 submodule로 설정
# git submodule add https://github.com/<theme 경로>.git themes/<theme 이름>
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/hugo-PaperMod
```

#### <ROOT_DIRECTORY>/config.toml
```toml
baseURL = 'http://example.org/'
languageCode = 'en-us'
title = 'My New Hugo Site'
```
방금 막 생성된 Hugo 프로젝트에는 위처럼 초기화된 `config.toml`이 있다. 
여기서 설정한 것에 따라 블로그의 모습이 바뀌게 된다.
설정값은 theme에 따라 다르기 때문에 해당 theme github에 방문하여 설정들이 무엇이 있는지 찾아보자.


> hugo는 `toml`뿐만 아니라 `yaml`, `json`로도 config파일을 설정할 수 있다.
`toml`의 syntax가 불편하다면 `yaml`로 변경하여 사용하여도 된다.
필자는 `yaml`로 변환하여 `config.yaml`로 설정하였다.
`toml -> yaml`로 변환은 [여기](https://www.convertsimple.com/convert-toml-to-yaml/)에서 쉽게 할 수 있다.

#### <ROOT_DIRECTORY>/config.yaml
다음은 필자가 설정한 `config.yaml`이다.
```yaml
baseURL: <GITHUB_PAGES_URL>  # 'https://blacknwhite5.github.io/'
languageCode: en-us
title: <블로그 타이틀>  # jackdaw@blog ~/home
theme: <THEME_NAME>  # hugo-PaperMod
```

<br>


### # 로컬서버 열기

```shell
$ hugo server  # or hugo serve

                   | EN  
-------------------+-----
  Pages            |  3  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     |  0  
  Processed images |  0  
  Aliases          |  0  
  Sitemaps         |  1  
  Cleaned          |  0  

Built in 2 ms
Watching for changes in /Users/user/Desktop/study/aaa/{archetypes,content,data,layouts,static}
Watching for config changes in /Users/user/Desktop/study/aaa/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:58619/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

명렁어 입력이후 출력되는 로컬주소(`http://localhost:58619/`)를
`CMD + double click`하거나 브라우저에 복붙하면 로컬서버가 열린걸 볼 수 있다.

> `hugo`는 실시간 렌더링이 장점이므로 `config.yaml` 설정을 바꿔볼때나
포스트를 작성할때 바로바로 확인해볼 수 있다. 
그러니 <span style='background-color: #CCFFCC;'>무언가를 바꿔서 확인해보고 싶을땐 로컬서버를 항상 열어두는 편이 좋다..!<span> 

<br>

### # 배포
배포할때는 아래처럼 프로젝트 빌드 후 `public` 폴더에 연결된 submodule에 `commit/push` 하고,
다시 프로젝트 루트로 돌아와 `commit/push`를 진행한다.

```shell
$ hugo -t <THEME_NAME> 
$ cd public
$ git add .
$ git commit -m "COMMIT_MESSAGE"
$ git push origin master

$ cd ../
$ git add .
$ git commit -m "COMMIT_MESSAGE"
$ git push origin master
```

이 과정이 꽤 귀찮은데, [gurumee92님 블로그 구축기 (1) Hugo + Github으로 개인 블로그 만들기](https://gurumee92.github.io/2020/08/%EB%B8%94%EB%A1%9C%EA%B7%B8-%EA%B5%AC%EC%B6%95%EA%B8%B0-1-hugo-github%EC%9C%BC%EB%A1%9C-%EA%B0%9C%EC%9D%B8-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EB%A7%8C%EB%93%A4%EA%B8%B0/)에
한번에 `commit/push`할 수 있도록 shell script를 작성해주셨다. 한번 방문해서 확인해보길 바란다.(매우 편리함:smile:)

<br>


### # 포스트 작성
여기까지 왔다면 Github pages 블로그에 글을 올릴 준비가 끝난 것이다.👏
이제 글을 작성하는 일만 남았다.
터미널에 다음과 같이 입력해보자.
```shell
# hugo new post/<디렉토리 패스>/<포스트 파일 이름>.md
$ hugo new post/test.md
```
그러면 `<ROOT_DIRECTORY>/content/post/test.md`가 생성된다.
생성된 `markdown` 파일에는 다음과 같이 이미 작성이 되어 있다.
`---` 아래에 아무 내용을 추가하여 렌더링이 잘 되는지 확인해보자.

```markdown
---
title: "Test"
date: 2022-01-02T01:04:18+09:00
---

테스트.
```

쓸 내용을 완성하면, 
[배포](http://localhost:1313/2021/12/hugo%EB%A1%9C-%EC%8B%9C%EC%9E%91%ED%95%98%EB%8A%94-github-pages-%EB%B8%94%EB%A1%9C%EA%B7%B8/#-%EB%B0%B0%ED%8F%AC)에 설명한 방법으로 배포하면 된다. 

<br>


## 마치며...
파이썬만 주구장창하니 배워야할게 산더미이다.
블로그를 계속 발전시켜나가기 위해 js, css 등 필요한 것들을 배워갈 것이고 
그 기록들을 이 블로그에 남겨보려한다.
우선 다음 포스트는 `PaperMod` 테마에서 `config.yaml` 설정하는 것을 써볼 계획이다.
앞으로 블로그가 발전해나가는 모습을 기대된다.
