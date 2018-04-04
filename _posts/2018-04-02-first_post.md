---
title: Jekyll + Github + minimal Theme 적용하기
data : 2018-04-02
tags : 
    blogs
---


Google 블로그를 사용해오다가 꾸미는 방법도 잘 모르겠고 , 활용도 제대로 못하는것 같아서 이뻐보이는 github 블로그를 사용하기로 결정하였다.<br>


> 주의 , 본 게시글은 windows 사용자를 위한 글임<br>


빠르게 본론으로 들어가보자.<br>

**1. GitHub 가입**

GitHub를 활용해 수 많은 오픈 테마 들을 활용하고 version 관리를 위해 GitHub에 회원 가입하자 !<br>

[깃허브 홈페이지](https://github.com)

**2. Minimal Theme fork & Re-name repository**

Minimal 테마를 적용하고 블로그를 호스팅하기 위해서 해야 할 일은 딱 **2가지**이다.

테마를 적용하기 위해 [Minimal Repository](https://github.com/mmistakes/minimal-mistakes)로 이동해 fork를 활용하자.

![github_fork](https://Minwoo-kang.github.io/assets/images/fork.png)

fork 를 완료하면 내 repository 목록에 생기게 되고 , 여기서 중요한점은 fork 된 repository의 이름을 `Yourusername.github.io`형태로 바꿔야 한다. 

![github_rename](https://Minwoo-kang.github.io/assets/images/rename.png)


5분 가량을 기다리면 아래와 같은 화면이 나오면서 hosting + theme 적용이 완료된다.

![generate_complete](https://Minwoo-kang.github.io/assets/images/generate_complete.PNG)


적용이 완료되었다면 , 해당 링크로 가서 자신의 첫 github 블로그를 즐겨보자.

**3. Local 영역 작업 환경 구성하기(난이도 3/5)**

이제 중요한 부분은 생성된 블로그를 나만의 스타일로 , 나만의 글들로 채워 나가야 한다. 해당 작업은 github 홈페이지에서 직접적으로 여러 설정들을 edit 함으로써 자동 적용 할 수 있다.

그러나 효율성 , 편리성(~~실제로 설치하는데 매우 힘들었다.~~)을 위해 local 영역에서 글을 작성하고 testing 후에 호스팅 서버에 올리는 방법을 추천한다.

local에서 jekyll을 돌리기 위해선 아래와 같은 것들이 필요하다.

`* Ruby`<br>
`* RubyDevKit`<br>
`* Jekyll`<br>

Ruby 및 Ruby devkit + Jekyll 설치 과정은 자세하게 나와 있는 [document](http://jekyll-windows.juthilo.com/1-ruby-and-devkit/)를 참조하자. (Step 1 , 2 만 참조함)

> 다만 syntax highlight 의 경우 나는 다운 받지 않았다. 다운받지 않아도 무방함.

여기까지 완료 하였다면 , 이제 github에 있는 remote repository(username.github.io)를 pull 하여 로컬에 다운 받자. 

 블로그 폴더를 만들 장소로 이동해 사용하고 있는 git command line을 이용해 아래와 같은 명령어를 치자.
    
    $git init      
    $git remote add origin https://github.com/Yourname/Yourname.github.io
    $git pull origin master

**4.초기 설정하기**

이제 복사된 파일들을 수정하여 나만의 블로그를 만들어 보자.

설정에 앞서 불필요한 파일들은 삭제하자. 삭제할 리스트는 다음과 같다.

* `.editorconfig`
* `.gattributes`
* `.github`
* `/docs`
* `/test`
* `CHANGELOG.md`
* `minimal-mistakes-jekyll.gemspec`
* `README.md`
* `screenshot-layouts.png`
* `screenshot.png`

블로그와 관련된 설정은 여러가지가 있지만, Jekyll 테마에 대해서 자세하게 알진 못하기 때문에 여기저기 검색을 통해서 최소한의 설정만 해보았다. 설명에서 이해가지 않거나 오류가 나는 부분은 [minimal-Theme document](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)를 참조하자.

첫 번째로 할 설정 파일은 `Gemfile` 파일이다.

`Gemfile`을 아래와 같이 설정하자.

```
source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins

gem "jekyll", "~> 3.5"
gem "minimal-mistakes-jekyll"
```

Gemfile을 설정했으면 Gemfile이 있는 곳으로 이동해 cmd 창을 열고 ruby 명령어를 이용해 관련 패키지를 다운받자.

    $bundle install

이 과정 까지 마쳤으면 수정되지 않은 나의 블로그를 Local에서 실행해보자.

아까 cmd 창을 이용하여 아래 명령어를 실행하자. 명령어를 실행하고 localhost:4000에 접속하게 되면 나의 블로그가 정상적으로 떠있는 모습을 볼 수 있다.

    $bundle exec jekyll serve
    
>TroubleShooting 
>![CP949_error]({{ site.url }}/assets/images/CP949_error.PNG)
>위 명령어를 사용하면 CP949에러가 발생한다. 해당 에러는 아래와 같은 방법으로 해결하자.<br>

    $chcp 65001

두 번째로 `_config.yml` 이다.

해당 파일에서 블로그의 Author , Baseurl 등 여러가지를 설정 할 수 있다. 

`_config.yml`파일에 대한 자세한 설정은 [minimal-theme document](https://mmistakes.github.io/minimal-mistakes/docs/configuration/)를 참조하고 아주 심플한 부분만 설정하도록 하겠다.<br>


**Site settings**

국가 , 블로그 이름 등을 설정 할 수 있다.


![site_setting](https://Minwoo-kang.github.io/assets/images/site_setting.PNG)




**Site Author**

블로그의 좌측에 나타나는 블로그 주인에 대한 설정을 할 수 있다.

![site_author](https://Minwoo-kang.github.io/assets/images/site_author.PNG)



**Defaults**

그 외의 Navigation 설정 , comment 설정은 많은 자료들을 참조하도록하자. 


![site_default](https://Minwoo-kang.github.io/assets/images/site_default.PNG)



> 주의 , 기술적인 문제로 `_config.yml`파일에 대한 수정 사항은 서버를 re-run해야 적용된다. 그러니 cmd창을 열어 프로세스를 종료하고 다시 실행하도록하자.


세 번째로 , 좌우 여백 설정을 위한 `_saas/minima-mistakes/_variables.scss` 파일이 있다.


![grid_setting](https://Minwoo-kang.github.io/assets/images/grid_setting.PNG)




**5. 글쓰기**

블로그 설정을 마쳤으면 이젠 글쓰기만 남았다.

여태까지의 모든 과정은 이 과정을 위해 이루어진 것이다. 글쓰는 방법은 간단하다.

먼저 블로그 디렉토리에 `_posts`폴더를 만들자. 앞으로 모든 글은 해당 디렉토리 아래에 쓰면 된다.

다만 특이 한것은 포스트를 쓸 때 특정한 형식에 맞춰써야한다는 것이다. 포스트의 제목은 `YYYY-MM-DD-postName.md`와 같은 형태를 지녀야한다.

한가지 더 , 포스트의 상단 부분에 아래와 같은 내용을 써넣어줘야 한다.

![post_header](https://Minwoo-kang.github.io/assets/images/post_header.PNG)

>tags는 opional한 설정이다. tags외에도 categories 등 여러가지 설정이 있으니 document를 참조하자

해당 header 를 써주고 그 아래 부터 본인이 원하는 글을 써주면 끝이다.


**6. 배포하기**

로컬에서 원하는 만큼 글쓰기를 완료 한후 hosting을 위해 git 에 `commit & push` 함으로써 수정된 작업이 반영되고 글이 올라간다. 반드시 이 과정을 까먹지 않기로 한다.



### References
- - -

* [Junho Baik 블로그 - Minimal Theme 적용하기](https://junhobaik.github.io/jekyll-apply-theme/)
* [Minimal-Theme sites](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
* [Ruby,Ruby Devkit install 가이드](http://jekyll-windows.juthilo.com/1-ruby-and-devkit/)
* [CP949 error trouble shooting](https://jprogram.github.io/articles/2017-12/Windows)


    






