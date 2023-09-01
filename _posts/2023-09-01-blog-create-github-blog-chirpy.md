---
title: "[Blog] Chirpy 테마로 GitHub 블로그 만들기 How I Created a GitHub Blog with Chirpy Theme"
date: 2023-09-01 19:00:00 +09:00
categories: [Tech Notes, ETC]
# image: "/assets/img/post/2023-09-01-blog-create-github-blog-chirpy.gif"
tags: [github blog, chirpy]
---

## 개요

---

- 2023년 9월 1일 기준
- Mac M1 (2020) Venture 13.5.1

## Step by step

---

### 1. Ruby 설치

```
brew install ruby
brew install rbenv ruby-build
rbenv global 3.0.5
vim ~/.zshrc # 파일 열어서 아래 내용 넣고 저장

[[ -d ~/.rbenv  ]] && \
  export PATH=${HOME}/.rbenv/bin:${PATH} && \
  eval "$(rbenv init -)"

source ~/.zshrc
```

### 2. bundler, jekyll, github-pages 설치

```
gem install bundler
gem install jekyll
gem install github-pages
```

### 3. 레포지터리 Fork

```
https://github.com/cotes2020/jekyll-theme-chirpy >> Fork >> `본인유저네임.github.io` 레포지터리명으로 설정
```

### 4. 레포지터리 배포 설정

```
Repository >> Settings >> Pages >> Build and deployment >> `GitHub Actions`으로 설정 >> configure >> commit `Create jekyll.yml`
```

### 5. 로컬에 클론

```
(원하는 디렉토리 이동) >> git clone 유저네임.github.io.git
```

### 6. 패키지 설치

```
npm i
```

### 7. 환경변수 수정

```
NODE_ENV=production npx rollup -c --bundleConfigAsCjs
```

### 9. `./github/workflows/pages-deploy.yml` 수정

```
branches:
  - main
```

마스터 제거

```
pages-deploy.yml.hook => pages-deploy.yml
```

확장자 수정

### 10. `./_config.yml` 수정

```
lang: en
timezone: Asia/Seoul
title: renie # the main title
tagline: will manifest some benevolent value out here.
description: >- # used by seo meta and the atom feed
  renie's dev blog
url: "https://reniev9b.github.io"
github:
  username: reniev9b
social:
  name: renie
  email: reniev9b@gmail.com # change to your email address
  links:
    # The first element serves as the copyright owner's link
    # - https://twitter.com/username # change to your twitter homepage
    - https://github.com/reniev9b # change to your github homepage
    # Uncomment below to add more social links
    # - https://www.facebook.com/username
    # - https://www.linkedin.com/in/username
```

### 11. `./gitignore` 수정

```
# assets/js/dist
```

주석처리

### 12. 서버 설치, 이용

```
bundle install
bundle exec jekyll serve
```

### 13. Commit, Push
