# 📚 구현 기능 목록

---

### 📌 사용자 입력 처리

- [x] 로또 구입 금액을 입력 받는다.
    - [ ] 구입 금액은 1,000원 단위로 입력 받는다.
    - [ ] 1,000원으로 떨어지지 않는 경우 예외처리한다.

```text
14000
```

<br>

- [ ] 당첨 번호를 입력 받는다.
    - [ ] 번호는 쉼표(,)를 기준으로 구분한다.

```text
1,2,3,4,5,6
```

<br>

- [ ] 보너스 번호를 입력 받는다.

```text
7
```

<br>

- [x] 사용자가 입력하는 값은 `camp.nextstep.edu.missionutils.Console`의 `readLine()`을 활용한다.   
  <br>

---

### 📌 실행

- [ ] 게임 조건
    - [ ] 로또 번호의 숫자 범위는 1~45까지이다.
    - [ ] 1개의 로또를 발행할 때 중복되지 않는 6개의 숫자를 뽑는다.
        - [ ] `Random` 값 추출은 `camp.nextstep.edu.missionutils.Randoms`의 `pickUniqueNumbersInRange()`를 활용한다.
    - [ ] 당첨 번호 추첨 시 중복되지 않는 숫자 6개와 보너스 번호 1개를 뽑는다.
    - [ ] 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다.
        - 1등: 6개 번호 일치 / 2,000,000,000원
        - 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
        - 3등: 5개 번호 일치 / 1,500,000원
        - 4등: 4개 번호 일치 / 50,000원
        - 5등: 3개 번호 일치 / 5,000원
    - [ ] 로또 구입 금액을 입력하면 구입 금액에 해당하는 만큼 로또를 발행해야 한다.
    - [ ] 로또 1장의 가격은 1,000원이다.
    - [ ] 당첨 번호와 보너스 번호를 입력받는다.

- [ ] 게임 종료
    - [ ] 사용자가 구매한 로또 번호와 당첨 번호를 비교하여 당첨 내역 및 수익률을 출력하고 로또 게임을 종료한다.

---

### 📌 실행 결과 출력

- [ ] 발행한 로또 수량 및 번호를 출력한다.
    - [ ] 로또 번호는 오름차순으로 정렬하여 보여준다.

```text
8개를 구매했습니다.
[8, 21, 23, 41, 42, 43] 
[3, 5, 11, 16, 32, 38] 
[7, 11, 16, 35, 36, 44] 
[1, 8, 11, 31, 41, 42] 
[13, 14, 16, 38, 42, 45] 
[7, 11, 30, 40, 42, 43] 
[2, 13, 22, 32, 38, 45] 
[1, 3, 5, 14, 22, 45]
```

- [ ] 당첨 내역을 출력한다.

```text
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
```

- [ ] 수익률을 출력한다.
    - [ ] 수익률은 소수점 둘째 자리에서 반올림한다.

```text
총 수익률은 62.5%입니다.
```

- [ ] 예외 상황 시 에러 문구를 출력해야 한다.
    - [ ] 단, 에러 문구는 "[ERROR]"로 시작해야 한다.

**실행 결과 예시**

```text
구입금액을 입력해 주세요.
8000

8개를 구매했습니다.
[8, 21, 23, 41, 42, 43] 
[3, 5, 11, 16, 32, 38] 
[7, 11, 16, 35, 36, 44] 
[1, 8, 11, 31, 41, 42] 
[13, 14, 16, 38, 42, 45] 
[7, 11, 30, 40, 42, 43] 
[2, 13, 22, 32, 38, 45] 
[1, 3, 5, 14, 22, 45]

당첨 번호를 입력해 주세요.
1,2,3,4,5,6

보너스 번호를 입력해 주세요.
7

당첨 통계
---
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
총 수익률은 62.5%입니다.
```

---

### 📌 제공 클래스

**Lotto 클래스**

- [ ] 제공된 `Lotto` 클래스를 사용하여 구현해야 한다.
    - [ ] `Lotto`에 `numbers` 이외의 필드(인스턴스 변수)를 추가할 수 없다.
    - [ ] `numbers`의 접근 제어자인 `private`은 변경할 수 없다.
    - [x] `Lotto`의 패키지를 변경할 수 있다.

```java
public class Lotto {
    private final List<Integer> numbers;

    public Lotto(List<Integer> numbers) {
        validate(numbers);
        this.numbers = numbers;
    }

    private void validate(List<Integer> numbers) {
        if (numbers.size() != 6) {
            throw new IllegalArgumentException("[ERROR] 로또 번호는 6개여야 합니다.");
        }
    }

    // TODO: 추가 기능 구현
}
```

### 🚫 예외 처리

- [ ] 사용자가 잘못된 값을 입력할 경우 IllegalArgumentException을 발생시키고, `[ERROR]`로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다.

> `Exception`이 아닌 `IllegalArgumentException`, `IllegalStateException` 등과 같은 명확한 유형을 처리한다.

- [ ] 로또 구입 금액 입력 시
    - `IllegalArgumentException`
        - [x] `빈 문자열` 또는 `Null` 또는 `공백으로만 이루어진 문자열` 값이 들어온 경우
        - [ ] 양의 정수가 아닌 값이 들어온 경우
        - [ ] 구매 금액이 1,000원 단위가 아닌 경우
- [ ] 당첨 번호 입력 시
    - `IllegalArgumentException`
    - [ ] `빈 문자열` 또는 `Null` 또는 `공백으로만 이루어진 문자열` 값이 들어온 경우
    - [ ] 구분자가 쉼표가 아닌 경우
    - [ ] 당첨 번호로 6개 값이 입력되지 않은 경우
    - [ ] 당첨 번호가 1 ~ 45 사이의 양의 정수가 아닌 경우
    - [ ] 당첨 번호가 중복되는 경우
- [ ] 보너스 번호 입력 시
    - [ ] `빈 문자열` 또는 `Null` 또는 `공백으로만 이루어진 문자열` 값이 들어온 경우
    - [ ] 보너스 번호가 1 ~ 45 사이의 양의 정수가 아닌 경우
    - [ ] 보너스 번호가 당첨 번호와 중복되는 경우