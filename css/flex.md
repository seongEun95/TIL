# CSS Flexbox 정리

## display: flex
옛날의 table 코딩, float, inline 속성으로 정렬을 하는 시대가 지나고 flex 속성으로 이제는 쉽게 레이아웃을 배치할 수 있게 되었다.

## flex-direction
컨테이너 내 아이템들의 배치 방향을 결정
- **row** (기본값): 가로 행으로 배치 (왼쪽에서 오른쪽)
- **row-reverse**: 가로 행의 반대 방향으로 배치 (오른쪽에서 왼쪽)
- **column**: 세로 열로 배치 (위에서 아래)
- **column-reverse**: 세로 열의 반대 방향으로 배치 (아래에서 위)

## justify-content
메인축(주축)을 따라 아이템들을 정렬하는 방법을 지정
- **flex-start**: 시작점을 기준으로 정렬
- **flex-end**: 끝점을 기준으로 정렬
- **center**: 중앙 정렬
- **space-between**: 첫 아이템은 시작점, 마지막 아이템은 끝점에 배치하고 나머지 공간을 균등 분배
- **space-around**: 각 아이템의 좌우 여백을 균등하게 분배
- **space-evenly**: 모든 아이템 사이와 양끝 공간을 균등하게 분배

## align-items
교차축을 따라 아이템들을 정렬하는 방법을 지정
- **stretch** (기본값): 컨테이너의 교차축을 채우도록 아이템들을 늘림
- **flex-start**: 교차축의 시작점을 기준으로 정렬
- **flex-end**: 교차축의 끝점을 기준으로 정렬
- **center**: 교차축의 중앙에 정렬
- **baseline**: 텍스트 베이스라인을 기준으로 정렬

## flex-wrap
아이템들의 줄바꿈 처리 방식을 지정
- **nowrap** (기본값): 한 줄에 모든 아이템을 표시
- **wrap**: 공간이 부족하면 다음 줄로 넘김
- **wrap-reverse**: wrap과 동일하나 역순으로 줄바꿈

## gap
flex 아이템들 사이의 간격을 설정합니다. row-gap과 column-gap의 단축 속성으로, 행과 열의 간격을 한번에 지정할 수 있습니다.

## flex-grow / flex-shrink / flex-basis
개별 flex 아이템의 크기 조절하는 속성
- **flex-grow**: 컨테이너에 여분의 공간이 있을 때 아이템의 확장 비율 지정
- **flex-shrink**: 컨테이너가 작아질 때 아이템의 축소 비율 지정
- **flex-basis**: flex 아이템의 기본 크기 지정

## align-self
개별 flex 아이템의 교차축 정렬을 설정합니다. 
align-items 속성을 아이템별로 개별 지정할 수 있으며 컨테이너의 align-items 속성보다 우선 적용된다.
- **auto** (기본값): 부모 컨테이너의 align-items 값을 상속받음
- **stretch**: 컨테이너의 교차축을 채우도록 아이템을 늘림
- **flex-start**: 교차축의 시작점을 기준으로 정렬
- **flex-end**: 교차축의 끝점을 기준으로 정렬  
- **center**: 교차축의 중앙에 정렬
- **baseline**: 텍스트 베이스라인을 기준으로 정렬

## order
flex 아이템의 배치 순서를 지정한다.
기본값은 0이며, 숫자가 클수록 뒤쪽에 배치된다.
음수 값도 사용 가능하며 양수보다 앞쪽에 배치된다.


참고사이트 (이번에야말로 CSS Flex를 익혀보자)
- https://studiomeal.com/archives/197