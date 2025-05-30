멋진 로딩 애니메이션을 만드셨네요! 두 개의 움직이는 사각형으로 시각적인 피드백을 주는 훌륭한 CSS 애니메이션 예시입니다.

아래는 이 코드를 GitHub 저장소에 올릴 때 사용하기 좋은 설명으로, 애니메이션이 어떻게 작동하는지 자세히 알려줍니다.

기하학 로딩 애니메이션
이 프로젝트는 HTML과 CSS만으로 만들어진 간단하지만 매력적인 로딩 애니메이션을 보여줍니다. 두 개의 작은 사각형이 보이지 않는 큰 사각형 주변을 동기화된 움직임으로 돌면서, 전환될 때마다 색상이 변하여 콘텐츠가 로딩 중임을 나타냅니다.

작동 방식
애니메이션은 <div> 컨테이너 안에 배치된 두 개의 <span> 요소로 구성됩니다. 각 <span>은 움직이는 사각형 중 하나를 나타내며, .loading div는 이들의 경계 역할을 합니다.

HTML 구조
HTML

<div class="loading">
  <span></span>
  <span></span>
</div>
loading 클래스를 가진 바깥쪽 div는 애니메이션의 무대 역할을 합니다. 이것은 내부 <span> 요소가 움직일 30x30 픽셀의 컨테이너입니다.
두 개의 <span> 태그는 실제로 애니메이션되는 요소들입니다.
CSS 스타일링 및 애니메이션
마법은 CSS에서 일어납니다. 여기서 사각형의 모양과 움직임을 정의합니다.

CSS

.loading {
  width: 30px;
  height: 30px;
  position: relative; /* 자식 요소의 절대 위치 지정을 허용 */
}

.loading span {
  position: absolute; /* 부모(.loading)에 상대적으로 사각형 위치 지정 */
  width: 10px;
  height: 10px;
  background-color: gray; /* 기본 색상 */
  top: 0;
  left: 0;
  animation: loading 1.5s infinite; /* 'loading' 애니메이션 적용 */
}

.loading span:nth-child(1) {
  background-color: crimson; /* 첫 번째 사각형의 기본 색상 재정의 */
}

.loading span:nth-child(2) {
  animation-delay: 0.8s; /* 두 번째 사각형의 애니메이션 시작을 지연 */
}

@keyframes loading {
  0% {
    top: 0;
    left: 0;
  }
  25% {
    top: 0;
    left: calc(100% - 10px); /* 오른쪽 위 모서리로 이동 */
    background-color: dodgerblue;
  }
  50% {
    top: calc(100% - 10px); /* 오른쪽 아래 모서리로 이동 */
    left: calc(100% - 10px);
    background-color: orange;
  }
  75% {
    top: calc(100% - 10px); /* 왼쪽 아래 모서리로 이동 */
    left: 0;
    background-color: yellowgreen;
  }
  100% {
    top: 0;
    left: 0; /* 왼쪽 위 모서리로 돌아옴 */
  }
}
주요 CSS 속성:
.loading의 position: relative;: 이 속성은 매우 중요합니다. position: absolute;를 가진 <span> 요소들이 body가 아닌 .loading 컨테이너에 상대적으로 배치될 수 있도록 합니다.
.loading span의 position: absolute;: 이 속성은 span 요소들을 일반적인 문서 흐름에서 제외시켜 top, left, right, bottom 속성을 사용하여 정확하게 배치할 수 있도록 합니다.
animation: loading 1.5s infinite;: 이것은 각 <span>에 loading 키프레임 애니메이션을 적용합니다.
loading: @keyframes 규칙의 이름입니다.
1.5s: 한 번의 애니메이션 주기(cycle)의 지속 시간입니다.
infinite: 애니메이션이 무한히 반복됩니다.
span:nth-child(2)의 animation-delay: 0.8s;: 이것이 "추격" 효과를 만들어냅니다. 두 번째 사각형은 첫 번째 사각형보다 0.8초 늦게 애니메이션을 시작하여 서로를 따라가는 것처럼 보이게 합니다.
@keyframes loading: 이 규칙은 애니메이션의 다양한 단계를 정의합니다:
0%: 시작 지점입니다. 두 사각형 모두 .loading 컨테이너의 왼쪽 위 모서리(top: 0; left: 0;)에서 시작합니다.
25%: 사각형들이 오른쪽 위 모서리로 이동합니다. calc(100% - 10px)는 사각형 자체의 10px 너비/높이를 고려하여 컨테이너 가장자리에 정확히 위치하도록 합니다.
50%: 사각형들이 오른쪽 아래 모서리로 이동합니다.
75%: 사각형들이 왼쪽 아래 모서리로 이동합니다.
100%: 사각형들이 왼쪽 위 모서리로 돌아와 주기를 완료하고 다시 시작합니다.
background-color 변경: 각 키프레임에서 사각형의 background-color가 변경되어 움직임에 동적인 시각적 요소를 추가합니다. 첫 번째 <span>은 초기에는 crimson이고, 두 번째 <span>은 기본적으로 gray이며, 애니메이션 중에 둘 다 색상이 변합니다.
