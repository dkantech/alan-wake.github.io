### DK A.N.T 기술블로그 사용설명서

1. Log
    1. Logo
      * | Index | Type | Name | Size |
        |:---:|---|---|---|
        | 1 | PC      | tech_logo.png    | 123*21 |
        | 2 | Mobile  | tech_logo.png    | 99*17  |
        | 3 | Mobile  | tech_logo@2x.png | 198*34 |
        | 4 | Mobile  | tech_logo@3x.png | 297*51 |
        | 5 | favicon | favicon.ico      | 16*16  |

==============

> 주의: [GitHub Pages]와 [Jekyll]에 대해서 충분히 숙지할 것.
> 주의: [Collaborating on projects using issues and pull requests](https://help.github.com/categories/collaborating-on-projects-using-issues-and-pull-requests/)을 정독.


#
### 목차

기존 카카오 블로그 README을 DKANT 블로그에 맞게 수정함
다음의 과정으로 설치와 적용을 확인한다. (기본적으로 리눅스계열이 편함)
1. [Jekyll] 설치
2. github에서 블로그 소스 clone
3. 실행 (로컬개발환경)
4. 배포 (발행)
5. 필자 등록
6. 글쓰기

#
#### 1. [Jekyll] 설치
 ruby 먼저 설치 (OS에 맞춰서 알아서)
```console
$ gem install bundler jekyll
```
ruby를 설치했는데,  위의 명령으로 설치하다 실패하는 경우, ruby devkit이 설치됐는지 확인해야함
#
#### 2. github에서 블로그 소스 clone

```console
$ git clone https://github.com/dkantech/dkantech.github.io.git
$ cd dkantech.github.io
$ bundle install
```
#
#### 3. 실행 (로컬개발환경)
```
$ bundle exec jekyll serve
```
개발환경이 정상적으로 구동되면 웹브라우저에서 localhost:4000으로 접속하면 블로그 사이트가 열리는걸 확인할 수 있다.
#
#### 4. 배포(발행)

<https://github.com/dkantech/dkantech.github.io.git> push권한이 연구소직원에 한해서:

```
$ git commit -m '...'
$ git push origin master
````
#
#### 5. 필자 등록

1. `_authors` 디렉토리에 `nickname.md` 이름으로 필자 정보 파일 추가
 - 참고: 최종적으로 사용자 포스트 목록 페이지의 url은 http://tech.dkant.net/authors/nickname/
2. 파일 상단에 [front matter] 작성
 - layout: author # 레이아웃(필수)
 - name: `nickname` # 그냥 쓰고싶은거 씀(필수)
 - title: ... # 왠만하면 한글이름 사용(필수)
 - image: http://... # 프로필 이미지(필수)
 - cover: http://... # 작성자 커버 이미지(선택)
3. 내용은 필요없음
#
#### 6. 글 쓰기

1. `_posts` 디렉토리에 `yyyy-mm-dd-slug.md` 파일로 복사(or 이동).
 - slug: 해당 포스트의 고유 키로 url의 일부로 사용. 왠만하면 특수문자없이 영문자,숫자,-(하이픈),.(점)...만 사용.
 - yyyy,mm,dd: 발행 년,월,일.
 - 참고: 최종적으로 포스트의 url(permalink)는 http://tech.dkant.net/yyyy/mm/dd/slug/
2. 파일 상단에 [front matter] 작성
 - layout: post # 레이아웃(필수). `page` 레이아웃을 사용하면 목록에 보이지 않는 글을 쓸 수 있음.
 - title: '제목' # 제목(필수)
 - author: `lastname.firstname` # 필자(필수). 위에서 등록한 필자와 매치되야 나중에 필자로 게시글을 검색할 수 있음.
 - tags: `[tag1,tag2,tag3,...]` # 태그 목록(선택). 왠만하면 특수문자없이 영소문자,숫자,-(하이픈),.(점)...만 사용.
 - image: http://... # 커버이미지 url(선택)
 - date: `YYYY-MM-DD HH:MM:SS` # 발행일(필수)
3. 처음 글을 쓰는 필자이라면 **글쓴이 등록**(필수)
4. 유력한(?) 태그가 새로 등장했다면 **태그 등록**(선택)
#
#### 7. 태그 등록

1. `_tags` 디렉토리에 `tag-name.md` 이름으로 필자 정보 파일 추가
 - 참고: 최종적으로 사용자 포스트 목록 페이지의 url은 http://tech.dkant.net/tags/tag-name/
2. 파일 상단에 [front matter] 작성
 - layout: tag # 레이아웃(필수)
 - name: `tag-name` # post의 tags 배열의 항목과 매칭(필수). 왠만하면 특수문자없이 영소문자,숫자,-(하이픈),.(점)...만 사용.
 - title: ... # 좀 더 길고 구체적인 설명(필수)
 - image: http://... # 태그 이미지(선택)
3. 내용은 필요없음

##
##### 요 아래는 이 소스의 fork의 근원인 kakao의 apache라이선스 명시
저작권에 문제되는건 대부분 지웠음

---

[GitHub Pages]: https://pages.github.com
[Jekyll]: https://jekyllrb.com
[front matter]: https://jekyllrb.com/docs/frontmatter/
[gfm]: https://guides.github.com/features/mastering-markdown/
[kramdown]: http://kramdown.gettalong.org
[rouge]: http://rouge.jneen.net


## License

This software is licensed under the [Apache 2 license](LICENSE.txt), quoted below.

Copyright 2017 Kakao Corp. <http://www.kakaocorp.com>

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this project except in compliance with the License. You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0.

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.

##### Fork from kakao-tech blog repository
