# 키친포스

## 퀵 스타트

```sh
cd docker
docker compose -p kitchenpos up -d
```

## 요구 사항

- 메뉴
    - 생성
        - [ ] 사용자는 `메뉴`를 생성할 수 있다.
        - [ ] `메뉴` 생성 시, 메뉴 이름, 가격, `메뉴 그룹`, `메뉴 상품`들을 지정해야 한다.
        - [ ] `메뉴`의 이름은 비어있을 수 없다.
        - [ ] `메뉴`의 이름은 비속어를 포함할 수 없다.
        - [ ] `메뉴`의 가격은 0 이상이어야 한다.
        - [ ] `메뉴`는 특정 `메뉴 그룹`에 속해야 한다.
        - [ ] `메뉴`는 1개 이상의 `메뉴 상품`을 포함해야 한다.
    - 가격변경
        - [ ] 사용자는 `메뉴`의 가격을 변경할 수 있다.
        - [ ] `메뉴`의 가격 변경 시, 변경된 가격은 `메뉴 상품`들의 가격 총합을 초과할 수 없다.
    - 메뉴 노출 여부
        - [ ] 사용자는 `메뉴`를 노출시킬 수 있다.
        - [ ] `메뉴` 노출 시, `메뉴`의 가격이 `메뉴 상품`들의 가격 총합을 초과하면 안된다.
        - [ ] 사용자는 `메뉴`를 숨길 수 있다.
    - 메뉴 조회
        - [ ] 사용자는 모든 `메뉴`를 조회할 수 있다.

- 메뉴 상품
    - 생성
        - [ ] 사용자는 `메뉴 상품`을 생성할 수 있다.
        - [ ] `메뉴 상품` 생성 시, `상품`과 수량을 지정해야 한다.
        - [ ] `메뉴 상품`의 수량은 0 이상이어야 한다.
        - [ ] `메뉴 상품`의 가격은 `상품`의 가격과 수량을 곱한 값으로 계산된다.
    - 조회
        - [ ] 사용자는 모든 `메뉴 상품`을 조회할 수 있다.

- 메뉴 그룹
    - 생성
        - [ ] 사용자는 `메뉴 그룹`을 생성할 수 있다.
        - [ ] `메뉴 그룹` 생성 시, `메뉴 그룹` 이름을 지정해야 한다.
        - [ ] `메뉴 그룹`의 이름은 비어있을 수 없다.
    - 조회
        - [ ] 사용자는 모든 `메뉴 그룹`을 조회할 수 있다.

- 상품
    - 생성
        - [ ] 사용자는 `상품`을 생성할 수 있다.
        - [ ] `상품` 생성 시, 상품 이름과 가격을 지정해야 한다.
        - [ ] `상품`의 가격은 0 이상이어야 한다.
        - [ ] `상품`의 이름은 비어있을 수 없다.
        - [ ] `상품`의 이름은 비속어를 포함할 수 없다.
    - 가격 변경
        - [ ] 사용자는 `상품`의 가격을 변경할 수 있다.
        - [ ] `상품`의 가격 변경 시, 변경된 가격은 0 이상이어야 한다.
        - [ ] `상품`의 가격이 변경되면, 해당 상품을 포함하는 모든 `메뉴`는 `메뉴 가격 정책`에 따라 노출 여부가 결정된다.
            - 변경된 상품 가격 기준으로 `메뉴 가격 정책`을 만족하지 못하면, 해당 `메뉴`는 숨김 처리한다.
            - 메뉴 가격 정책: `메뉴`의 가격은 해당 `메뉴`에 포함된 모든 `메뉴 상품`들의 가격 총합을 초과할 수 없다.
    - 조회
        - [ ] 사용자는 모든 `상품`을 조회할 수 있다.

- 주문
    - 공통 사항
        - [ ] `주문`은 존재해야 한다.
    - 생성
        - [ ] 사용자는 `주문`을 생성할 수 있다.
        - [ ] `주문`은 `주문 상태`를 가진다.
        - [ ] `주문`은 하나 이상의 `주문 항목(OrderLineItem)`을 포함해야 한다.
        - [ ] `주문 항목`에 포함된 모든 `메뉴` 는 존재해야하며 요청된 `주문 항목`의 수와 `메뉴`의 수는 일치해야 한다.
        - [ ] `주문 항목`의 수량은 0 이상이어야 한다. (단, `주문` 유형이 `매장식사(EAT_IN)`이 아닌 경우)
        - [ ] `주문 항목`에 포함된 `메뉴`는 노출 상태여야 한다.
        - [ ] `주문 항목`의 가격은 해당 `메뉴`의 가격과 일치해야 한다.
        - [ ] `주문` 유형이 배달(DELIVERY)인 경우, 배송 주소를 제공해야 한다. (이때, 배송 주소는 비어있을 수 없다.)
        - [ ] `주문` 유형이 매장식사(EAT_IN)인 경우, `주문 테이블`을 제공해야 한다. (이때, `주문 테이블`은 존재해야 하며 빈 테이블이어야 한다.)
    - 주문 수락
        - [ ] 사용자는 `주문`을 수락할 수 있다.
        - [ ] `주문`의 상태가 대기중(WAITING) 이어야 한다.
        - [ ] `주문` 유형이 배달(DELIVERY)인 경우, 배달 요청을 해야 한다.
        - [ ] `주문`의 상태를 수락됨(ACCEPTED)으로 변경해야 한다.
    - 주문 서빙
        - [ ] 사용자는 `주문`을 서빙할 수 있다.
        - [ ] `주문`의 상태가 수락됨(ACCEPTED) 이어야 한다.
        - [ ] `주문`의 상태를 서빙됨(SERVED)으로 변경해야 한다.
    - 배달 시작
        - [ ] 사용자는 `주문`을 배달을 시작할 수 있다.
        - [ ] `주문`의 유형이 배달(DELIVERY) 이어야 한다.
        - [ ] `주문`의 상태를 서빙됨(SERVED)으로 변경해야 한다.
        - [ ] `주문`의 상태를 배달중(DELIVERING)으로 변경해야 한다.
    - 배달 완료
        - [ ] 사용자는 `주문`의 배달을 완료할 수 있다.
        - [ ] `주문`의 상태가 배달중(DELIVERING) 이어야 한다.
        - [ ] `주문`의 상태를 배달됨(DELIVERED)으로 변경해야 한다.
    - 주문 완료
        - [ ] 사용자는 `주문`을 완료할 수 있다.
        - [ ] `주문`의 유형이 배달(DELIVERY)인 경우, 주문의 상태가 배달됨(DELIVERED) 이어야 한다.
        - [ ] `주문`의 유형이 테이크아웃(TAKEOUT) 또는 매장식사(EAT_IN)인 경우, `주문`의 상태가 서빙됨(SERVED) 이어야 한다.
        - [ ] `주문`의 상태를 완료됨(COMPLETED)으로 변경해야 한다.
        - [ ] `주문`의 유형이 매장식사(EAT_IN)인 경우, `주문 테이블`의 손님 수를 0으로 설정하고, `주문 테이블`을 빈 테이블로 설정해야 한다.
    - 조회
        - [ ] 사용자는 모든 `주문`을 조회할 수 있다.

- 주문 테이블
    - 생성
        - [ ] 사용자는 `주문 테이블`을 생성할 수 있다.
        - [ ] `주문 테이블` 생성 시, `주문 테이블` 이름을 지정해야 한다.
        - [ ] `주문 테이블`의 이름은 비어있을 수 없다.
    - 착석
        - [ ] 사용자는 `주문 테이블`에 착석할 수 있다.
        - [ ] `주문 테이블`은 존재해야 한다.
        - [ ] `주문 테이블`의 상태를 착석 상태로 변경해야 한다.
    - 테이블 초기화
        - [ ] 사용자는 `주문 테이블`을 초기화할 수 있다.
        - [ ] `주문 테이블`은 존재해야 한다.
        - [ ] `주문 테이블`에 완료되지 않은 `주문`이 존재하면 안된다.
        - [ ] `주문 테이블`의 손님 수를 0으로 설정해야 한다.
        - [ ] `주문 테이블`의 상태를 빈 상태로 변경해야 한다.
    - 손님 수 변경
        - [ ] 사용자는 `주문 테이블`의 손님 수를 변경할 수 있다.
        - [ ] `주문 테이블`은 존재해야 한다.
        - [ ] 변경하려는 손님 수는 0 이상이어야 한다.
        - [ ] `주문 테이블`이 착석 상태가 아니라면 손님 수를 변경할 수 없다.
    - 조회
        - [ ] 사용자는 모든 `주문 테이블`을 조회할 수 있다.

- 주문 항목 (OrderLineItem)
    - [ ] `주문 항목`은 `메뉴`와 수량을 포함해야 한다.
    - [ ] `주문 항목`의 수량은 0 이상이어야 한다.
    - [ ] `주문 항목`은 `주문`에 속해야 한다.

## 용어 사전

| 한글명      | 영문명             | 설명                                                |
|----------|-----------------|---------------------------------------------------|
| 메뉴       | Menu            | 메뉴는 메뉴 그룹에 속하며, 메뉴 상품들을 포함한다.                     |
| 메뉴 그룹    | MenuGroup       | 메뉴 그룹은 메뉴를 분류하는 단위이다.                             |
| 메뉴 상품    | MenuProduct     | 메뉴 상품은 상품과 수량을 포함한다.                              |
| 상품       | Product         | 상품은 상품 이름과 가격을 포함한다.                              |
| 주문       | Order           | 주문은 주문 테이블과 주문 상품들을 포함한다.                         |
| 주문 테이블   | OrderTable      | 주문 테이블은 주문을 받는 테이블이다.                             |
| 주문 항목    | OrderLineItem   | 주문 항목은 메뉴와 수량을 포함한다.                              |
| 주문 상태    | OrderStatus     | 주문 상태는 주문의 상태를 나타낸다.                              |
| 주문 유형    | OrderType       | 주문 유형은 주문의 유형을 나타낸다.                              |
| 메뉴 가격 정책 | MenuPricePolicy | 메뉴 가격 정책은 상품의 가격이 변경되었을 때, 메뉴의 가격이 변경되는 방식을 나타낸다. |

## 모델링
