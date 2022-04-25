# 파일 구조도

#### 폴더

- [\_includes](#includes)
- [\_layouts](#layout)
- \_plugins
- \_posts
- \_site
- \_tags
- \_assets
- business
- dest
- files
- introduction
- product
- technote

#### 파일

- index
- run.bat

# layout

## business.html

- 사업소개 탭의 메인 페이지. business 폴더 안의 파일들로 연결됨

`<head>`

- include: head

`<body>`

- include: sub_header
- include: default_banner
- `<main>` (비즈니스 메뉴바/비즈니스내용)
- include: footer

<br>
<br>

## product.html

- 제품소개 탭의 메인 페이지. product 폴더 안의 파일들로 연결됨

`<head> `

- include: head

`<body> `

- include: sub_header
- include: default_banner
- `<main>`(제품 메뉴바/제품 내용)
- include: footer

<br>
<br>

## introduction.html

- 회사소개 탭의 메인 페이지. introduction 폴더 안의 파일들로 연결됨

`<head>`

- include: head

`<body>`

- include: sub_header
- include: default_banner
- `<main>`(회사소개 메뉴바/회사소개 내용)

<br>
<br>

## default.html

`<head>`

- include: head

`<body>`

- include: sub_header
- include: default_banner
- `<main>`({{ content }})
- include: footer

<br>
<br>

## home.html

`<head>`

- include: head

`<body>`

- `<div>`(팝업창)
- include: header
- `<main>`(파악못함)
- include: footer

<br>
<br>
<br>

# includes

## head.html

- 헤드

## business_banner.html

- 타이틀과 그림 둘 다 있는 배너
- 현재 사용 x

```
<div class="busi-header {{ page.id }}">
  <div class="busi-text">
    <h1>{{ page.title }} </h1>
  </div>
  <div class="busi-img" >
    <img src="{{ page.image }}" >
  </div>
</div>
```

<br>
<br>

## default_banner.html

- 타이틀만 있는 배너

```
<div class="sub-header-wrap">
  <div class="sub-header">
    <h1>{{ page.title }}</h1>
  </div>
  <div class="triangle-bottomleft"></div>
</div>
```

<br>
<br>

## header.html

- 메인 메뉴바 + 메인 페이지 배너(2021.02.17 기준)

<br>
<br>

## sub_header.html

- 메인 메뉴바

<br>
<br>

## item.html

- 테크노트로 추정. 파악 x
