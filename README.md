# 회전하는 사각형 로딩 애니메이션

콘텐츠 로딩 중임을 나타내기에 이상적인, 두 개의 회전하는 사각형으로 이루어진 간단한 CSS 전용 로딩 애니메이션입니다.

---

![bandicam 2025-05-30 16-50-32-863](https://github.com/user-attachments/assets/2b6a1547-23a0-4a1c-be2f-37da7633a8a7)

---

## 사용 방법

### HTML

이 애니메이션을 사용하려면 `<body>`에 다음 HTML 구조를 포함하세요:

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <title>2) 도형 로딩 애니메이션-02</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <div class="loading">
    <span></span>
    <span></span>
  </div>
  
</body>
</html>
CSS
style.css 파일을 생성하고 다음 CSS 규칙을 추가하세요:

CSS

/* Google Web Font */
@import url('https://fonts.googleapis.com/css?family=Raleway&display=swap');

body {
  font-family: 'Raleway', sans-serif;
  line-height: 1.5em;
  margin: 0;
  font-weight: 300;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
a {
  text-decoration: none;
}

.loading {
  width: 30px;
  height: 30px;
  position: relative;
}
.loading span {
  position: absolute;
  width: 10px;
  height: 10px;
  background-color: gray;
  top: 0;
  left: 0;
  animation: loading 1.5s infinite;
}
.loading span:nth-child(1) {
  background-color: crimson;
}
.loading span:nth-child(2) {
  animation-delay: 0.8s;
}

@keyframes loading {
  0% {
    top: 0;
    left: 0;
  }
  25% {
    top: 0;
    left: calc(100% - 10px);
    background-color: dodgerblue;
  }
  50% {
    top: calc(100% - 10px);
    left: calc(100% - 10px);
    background-color: orange;
  }
  75% {
    top: calc(100% - 10px);
    left: 0;
    background-color: yellowgreen;
  }
  100% {
    top: 0;
    left: 0;
  }
}
사용자 정의
CSS 변수를 수정하여 애니메이션을 쉽게 사용자 정의할 수 있습니다:

.loading의 width 및 height: 컨테이너의 크기를 변경합니다.
.loading span의 width 및 height: 개별 사각형의 크기를 조정합니다.
.loading span 및 :nth-child(1)의 background-color: 사각형의 초기 색상을 수정합니다.
.loading span:nth-child(2)의 animation-delay: 두 사각형의 움직임 사이의 지연 시간을 제어합니다.

animation 

@keyframes loading의 animation 속성: 애니메이션의 속도와 타이밍을 세밀하게 조정합니다. 키프레임 내의 background-color 속성은 사각형이 움직일 때 색상을 변경합니다.
궁금한 점이 있거나 추가 수정이 필요하시면 언제든지 문의해 주세요!
