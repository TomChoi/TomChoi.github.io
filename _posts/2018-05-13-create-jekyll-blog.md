---
title: Github Page와 Jekyll을 이용해 개인 블로그 만들기
date: 2018-05-13
tags:
  - github
  - blog
  - Jekyll
category: blog
---
System Environment
```
OS : macOS High Sierra(10.13.1)
```

## 1. What is Jekyll
Jekyll은 심플하고 블로그 지향적인 정적 사이트 생성기로 쉽게 정적 웹사이트를 만들어 준다. 큰 장점 중에 Github Page에 내장된 엔진이기 때문에 Github을 통해 개인 블로그를 무료로 호스팅 할 수 있다.

## 2. 프로그램 설치
#### Install Ruby
Mac OS X는 기본적으로 시스템에서 사용하기 위해 Ruby가 설치되어 있다. 하지만 나는 시스템용 Ruby를 사용하지 않고 따로 Ruby를 설치하여 사용한다.
- #### 시스템 Ruby 버전 확인
  ```
  $ ruby -v
  ruby 2.3.3p222 (2016-11-21 revision 56859) [universal.x86_64-darwin17]
  ```
  MacOS에 기본으로 설치된 Ruby가 2.3.3 이고, 이와 다른 버전의 루비를 설치해 보자.

- #### rbenv 설치
  ```
  $ brew update
  $ brew install rbenv
  ```
  Ruby를 설치하기 위해선 rbenv를 설치해야 한다. [Homebrew](https://brew.sh/index_ko)를 이용해 설치하자. brew가 없는 경우는 링크를 통해 설치하자.

- #### rbenv를 이용해 ruby 설치하기
  rbenv 설치가 끝났으면 설치 가능한 Ruby 버전을 확인한다.
  ```
  $ rbenv install -l
  ```
  나는 최신 버전인 2.5.0을 설치함
  ```
  $ rbenv install 2.5.0 && rbenv rehash
  ```
  global 옵션을 이용해 버전을 지정한다.
  ```
  & rbenv gloval 2.5.0
  ```

  이제 rbenv를 이용해 설치한 Ruby를 기본으로 지정하기 위해 환경변수에 등록해 줘야 한다. Bash를 사용하는 경우 ~/.bash_profile 에 다음 코드를 등록한다.
  ```
  export PATH="$HOME/.rbenv/bin:$PATH"
  eval "$(rbenv init -)"
  ```
  입력한 환경변수를 적용한다.
  ```
  & source ~/.bash_profile
  ```
  잘 설치가 되었는지 확인한다.
  ```
  $ ruby -v
  ruby 2.5.0p0 (2017-12-25 revision 61468) [x86_64-darwin17]
  ```
  2.5.0으로 버전이 보이면 정상적으로 설치가 된 것이다.
#### Install Jekyll & bundle
위에서 설치한 Ruby에 포함된 RubyGems을 이용해 Jekyll을 설치한다.
  ```
  $ gem install jekyll bundler
  ```

#### nokogiri 설치 에러가 발생할 경우
간혹 bundle install을 실행할 때 다음과 같이 nokogiri 설치 에러가 발생하는 경우가 있다. 이는 nokogiri에서 시스템 라이브러리를 참조하는데 참조를 못해서 발생하는 에러이다. 다음과 같이 해결할 수있다.
```
An error occurred while installing nokogiri (1.8.1), and Bundler cannot continue.
Make sure that `gem install nokogiri -v '1.8.1'` succeeds before bundling.
```
$ gem uninstall nokogiri
$ xcode-select --install
$ gem install nokogiri
```

## Reference
[Minimal Mistakes Quick-Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
[Dev.Hundred's Blog](https://junhobaik.github.io/jekyll-apply-theme/#%ED%85%8C%EC%8A%A4%ED%8A%B8-%EB%B0%B0%ED%8F%AC)
[Jekyll official site](https://jekyllrb-ko.github.io/)
