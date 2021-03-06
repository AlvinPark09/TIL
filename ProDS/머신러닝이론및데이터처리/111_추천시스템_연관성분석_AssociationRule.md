## 추천시스템_연관선 분석 _AssociationRule

- 연관성 분석
  - 연관성 규칙을 통해 하나의 거래나 사건에 포함되어 있는 둘 이상의 품목 간 상호 연관성을 발견하는 과정
  - 고객이 동시에 구매하는 상품 간의 관계를 분석한다는 의미에서 장바구니 분석(market basket analysis)이라고도 함
- 연관 규칙(Association Rule)
  - 항목들 간의 if them A -> then item B형태로 표현되는 유용한 패턴
  - 예. {onion, potato} => {meat}
- 고객의 구매시점에 기록된 트랜젝션 자료를 분석
  - 장바구니 하나에 포함된 품목들의 집합 형태로 주어짐
- 연관규칙을 파악하기 위한 측도
  - 지지도
    - 전체 구매 건수 가운데 상품A와 B를 동시에 구매한 비율로 P[A*B]로 나타냄(A와 B를 동시에 고려한 비율)
    - 지지도(A->B): A와 B가 동시에 포함된 거래 수 / 전체 거래 수
    - 상품 A하나에 대한 지지도는 지지도(A): A의 거래 수 / 전체 거래 수
  - 신뢰도(confidence)
    - 상품 A를 구매한 건수 가운데 B도 같이 구매한 비율로 조건부 확률, P[B|A]로 나타냄
    - 신뢰도(A->B): A와 B가 동시에 포함된 거래 수 / A의 거래 수 
    - 예: 신뢰도(기 -> 맥) = 지지도(기->맥) / 지지도(기)
  - 향상도(lift)
    - 전체에서 상품 B를 구매한 비율에 비해, A를 구매한 고객이 B를 구매한 비율이 몇 배인가를 의미, P[B|A] / P[B]로 나타냄
    - 향상도(A->B) : 신뢰도(A->B) / 지지도(B)
    - 향상도의 해석
      - 향상도(A->B) = 1: 상품 A와 상품B의 구매는 상호 연관성이 없음 (독립적임)
      - 향상도(A->B) > 1: 상품 A와 상품B의 구매는 양(+)의 영향력이 있음
      - 향상도(A->B) < 1: 상품 A와 상품B의 구매는 음(-)의 영향력이 있음
- 연역적 알고리즘
  - 품목들의 집합 별로 지지도, 신뢰도, 향상도 지표를 구해야 하는데, 품목의 수가 많을 때는 연관 규칙의 탐색 비용이 크게 증가함
  - 연역적 알고리즘은 더 이상 탐색하지 않아도 될 품목의 조합을 찾고, 그 조합을 부분집합으로 갖는 품목의 집합들을 가지치기(pruning)하여, 효율적인 탐색을 하도록 함
  - 최소 지지도 가지치기(minimum support pruning: MSP)
    - 어떤 품목(집합)에 대한 지지도가 일정 수준(문턱기준, threshold criterion)을 넘지 못하면 그 품목(집합)이 포함된 조합들은 더 이상 탐색하지 않음
