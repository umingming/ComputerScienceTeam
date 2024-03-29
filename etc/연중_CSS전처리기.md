# 주제: CSS 전처리기

### CSS 전처리기가 뭐에요?

전처리기의 자신만의 특별한 문법으로 CSS를 생성하도록 하는 프로그램이다.  
CSS 전처리기는 기존 CSS이 가지고 있지 못한 여러 기능을 사용할 수 있고, 이를 통하여 CSS 구조를 가독성있고 유지보수에 유리하게 관리할 수 있다.

<br>
<br>

### 왜 생겨났는가?

**css는 웹의 규모가 커질수록 복잡해진다.**

웹페이지를 만들 때 css파일에 스타일을 정의하게 되는데, 웹 페이지가 점점 커지고 복잡해지면 정의하는 스타일도 굉장히 많아지고, 선택자를 불필요하게 과다 사용하게 되는 등 코드가 지저분해질 수 있고, 유지 보수 측면에서 불리한 점이 생길 수 있다.

이를 해결하기 위해 등장한 것이 CSS Preprocessor (CSS 전처리기).

<br>
<br>

### 어떻게 쓰는건가요?

1. 전처리기 문법으로 CSS를 코딩한다.
2. 브라우저가 이해하는 표준 CSS로 컴파일 해준다.

우리가 아는 순수한 CSS는 CSS 전처리기 문법을 이해할 수 없다.
때문에, 코딩 후 컴파일된 CSS파일이 필요하다.

CSS 전처리기를 사용하기 위해서는, 웹서버에 CSS 컴파일러를 설치해야 한다.

<br>
<br>

### CSS 전처리기의 장단점

**장점**

-   CSS 코드를 여러 파일로 나눠 유지보수성이 향상(CSS파일도 나눌 수 있지만, CSS를 다운로드하기 위한 HTTP 요청이 다수 발생)
-   중첩 선택자를 작성하기 쉬움
-   일관된 테마를 위한 변수사용. 여러 프로젝트에 걸쳐 테마 파일을 공유할 수 있음.
-   반복되는 CSS를 위한 Mixins 생성.
-   Less는 자바스크립트로 작성되어, Node와 잘 작동합니다.

**단점**

-   전처리기를 위한 도구가 필요, 다시 컴파일하는 시간이 느릴 수 있음
-   Less에서는 변수 이름의 접두어가 @이며, @media, @import, @font-face 규칙과 같은 고유 CSS 키워드와 혼동될 여지가 있음
-   Sass에서는 노드 버전을 바꿀 때 자주 다시 컴파일해야 함

<br>
<br>

### CSS 전처리기 모듈 종류

-   Sass/SCSS
-   less
-   Stylus
-   PostCSS

대부분 비슷하지만 각자의 문법이 다르다.

<br>
<br>

### 가볍게 알아보는 Sass와 SCSS

가장 많이 사용되고 가장 오래된 CSS 전처리기.

SCSS는 Sass(Syntactically Awesome Style Sheets)의 버전 3에서 나옴. 즉, Sass에 포함되었던 SCSS.
Sass의 모든 기능을 지원하며 CSS구문과 완전 호환되는 CSS의 상위 집합 개념.
SCSS는 CSS와 거의 같은 문법으로 Sass의 기능을 지원한다.

<br>
<br>

**문법적 구조의 차이**

Sass

```Sass

.list
	width: 100px
    float: left
    li
    	color: red
        background: url("./image.jpg")
        &:last-child
        	margin-right: -10px

```

SCSS

```SCSS

.list{
	width: 100px;
    float: left;
    li {
		color: red;
        background: url("./image.jpg");
        &:last-child {
			margin-right: -10px;
        }
    }
}
```

Sass는 코드를 작성할 때 중괄호({})를 사용하는 대신 파이썬과 같이 들여쓰기로 구문을 감지하며, 세미콜론(;)을 사용하지 않음.

CSS 와 거의 비슷한 문법으로 Sass를 작성하기 위해 SCSS를 따로 출시함.
SCSS 는 코드 작성 시 css와 동일하게 중괄호나 세미콜론 등을 사용

<br>

**유지보수성의 이점**
아래처럼 스타일시트를 여러 개로 쪼개 놓더라도 최종적으로는 컴파일된 1개의 스타일시트만을 서버에서 불러오게 되므로, CSS @import의 장점은 흡수하고 단점은 줄일 수 있다.

```scss
// index.scss
@import "variables";
@import "mixins";
@import "modules";
@import "main/layouts";
@import "main/theme";
@import "sidebar/ads";
@import "sidebar/widgets";
```

```less
// less
@color-black: #000000; // 변수선언
@color-white: #ffffff;
#header {
    color: @color-black; // 위에 선언한 변수를 불러온다.
    background-color: @color-white;
}
```

<br>

**셀렉터 중첩(연결)**
CSS에서 반복해 선언해야만 했던 셀렉터(선택자)들을 한꺼번에 묶어 단순화시킬 수 있다.

구문이 좀 더 짧아지고, 부모 자식의 상하구조도 더욱 쉽게 파악할 수 있다.

```css
// CSS
.link {
    color: #1a0dab;
}
.link:hover,
.link:focus {
    text-decoration: underline;
}
.no-hover > .link:hover,
.no-hover > .link:focus {
    text-decoration: none;
}
.link-external::after {
    content: "^";
    margin-left: 0.25em;
}
```

```Scss
// Scss
.link {
	color: #1A0DAB;
    &:hover,
    &:focus {
    	text-decoration: underline;
        .no-hover > & {
        	text-decoration: none;
        }
    }
    // 선택자도 연결 가능
    &-external {
    	&::after {
        	content: "^";
            margin-left: .25em;
        }
    }
}
@mixin box ($color:blue){ //@mixin 키워드를 이용해 정의
    border : 1px solid $color;
    background-color : #fdd;
}
#box a{
  @include box //@include 키워드를 이용해 믹스인을 포함시킴
}
```

```less
// less

@color-black: #000000;
@color-pink: #f96d9c;
@color-red: #ff0000;
@width-default: 500px;
div {
    width: @width-default;
    color: @color-black;
    h3 {
        width: @width-default;
        color: @color-pink;
        a {
            color: @color-black;
        }
    }
    h1 {
        width: 300px;
        color: @color-red;
    }
}

.mixinEx (@pad:5px, @color-bg :#ffffff) {
    padding-top: @pad;
    padding-bottom: @pad;
    padding-right: @pad;
    padding-left: @pad;
    background-color: @color-bg;
}
h3 {
    .mixinEx;
}
h2 {
    .mixinEx(10px,#000000);
}

h3 {
    padding-top: 5px;
    padding-bottom: 5px;
    padding-right: 5px;
    padding-left: 5px;
    background-color: #ffffff;
}
h2 {
    padding-top: 10px;
    padding-bottom: 10px;
    padding-right: 10px;
    padding-left: 10px;
    background-color: #000000;
}
```

<br>
<br>
<br>
<br>

### 출처

https://fathory.tistory.com/30  
https://orbit-orbit.tistory.com/18  
https://velog.io/@eunoia/CSS-%EC%A0%84%EC%B2%98%EB%A6%AC%EA%B8%B0%EB%9E%80
