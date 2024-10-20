# 프리코스 1주차 미션 - 문자열 덧셈 계산기

---
우아한테크코스 7기 프리코스 1주차 미션, 문자열 덧셈 계산기를 구현한 저장소입니다.
문자열 덧셈 계산기는 사용자로부터 구분자와 양수로 구성된 문자열을 입력받아 구분자를 기준으로 분리한 각 숫자의 합을 반환하는 계산기입니다.

## 패키지 목록

```
main/
└── java/
    ├── calculator/
    │   └── Application.java               // 실행 파일
    └── custom/
        ├── controller/
        │   └── CalculatorController.java  // 컨트롤러
        ├── service/
        │   └── CalculatorService.java     // 모델(서비스)
        └── view/
            └── CalculatorView.java        // 뷰어
```

## 기능 목록

### 1. 입력: 사용자로부터 구분자와 양수로 구성된 문자열을 입력받기

- **입력형식**:

```입력형식
덧셈할 문자열을 입력해 주세요.
(문자열 입력)
```

### 2. 입력받은 문자열의 유효성 검사하기

- **유효성 case 1**: `""`은 숫자 0으로 판단한다.

- **유효성 case 2**: 입력받은 문자열이 `"//"`로 시작할 때
    - 문자열의 3번 인덱스 위치에 `'\'`, 4번 인덱스 위치에 `'n'`이 없는 경우 예외 처리한다.
    - 문자열의 2번 인덱스 위치에 숫자 또는 `'-'` 있는 경우 예외 처리한다.
    - 이때, 공백(`' '`) 또한 문자로 간주한다.

- **유효성 case 3**: 입력받은 문자열이 `"//"`로 시작하지않을 때
    - 문자열에 숫자와 기본구분자(쉼표(`,`)와 콜론(`:`))를 제외한 다른 문자가 있으면 예외 처리한다.

### 3. 입력받은 문자열에서 숫자를 분리하기

- 기본구분자는 쉼표(`,`)와 콜론(`:`)이다.
- 커스텀 구분자는 문자열 앞부분의 `"//"`와 `"\n"` 사이에 위치하는 **문자**이다.
- 문자열 앞부분에 `"//"`가 있으면 커스텀 구분자 추출 후, 기본 구분자와 커스텀 구분자로 문자열을 분리한다.
- 문자열 앞부분에 `"//"`가 없으면 기본 구분자만을 기준으로 문자열을 분리한다.

### 4. 분리된 문자열 배열을 숫자 배열로 변환하기

-숫자에 해당하는 문자열 배열을 정수로 변환하여 배열에 저장한다.

### 5. 각 숫자의 합을 계산하기

- 숫자 배열을 받아 숫자들의 합을 계산한다.

### 6. 출력: 덧셈의 결과를 출력하기

- **출력형식**:

```출력형식
결과 : (덧셈 결과)
```

## 예외 처리

- 사용자가 잘못된 값을 입력할 경우 `IllegalArgumentException` 을 발생시킨 후 애플리케이션은 종료

## 테스트 케이스

**테스트 case 1**: 기본 구분자 사용

- 입력: `1,2:3`
- 출력: `결과 : 6`

**테스트 case 2**: 구분자 연속 입력

- 입력: `1::2,,3,::4`
- 출력: `결과 : 10`

**테스트 case 3**: 단일 양수 입력

- 입력: `5`
- 출력: `결과 : 5`

**테스트 case 4**: 한 자리 이상의 숫자 입력

- 입력: `10,5:201`
- 출력: `결과 : 216`

**테스트 case 5**: 정해진 구분자 이외의 문자 입력 (1)

- 입력: `1,2a3`
- 출력: `IllegalArgumentException` 발생 후 종료

**테스트 case 6**: 정해진 구분자 이외의 문자 입력 (2)

- 입력: `//b\n1b2a3,4`
- 출력: `IllegalArgumentException` 발생 후 종료

**테스트 case 7**: 커스텀 구분자가 숫자

- 입력: `//1\n2,3`
- 출력: `IllegalArgumentException` 발생 후 종료

**테스트 case 8**: 커스텀 구분자가 문자열

- 입력: `//AW\n2AW3,4`
- 출력: `IllegalArgumentException` 발생 후 종료

**테스트 case 9**: 커스텀 구분자 미입력

- 입력: `//\n1,2,3`
- 출력: `IllegalArgumentException` 발생 후 종료

**테스트 case 10**: 커스텀 구분자가 '-'

- 입력: `//-\n1-2,3`
- 출력: `IllegalArgumentException` 발생 후 종료 ('-'는 음수 표현에 사용)

**테스트 case 11**: 숫자0 입력

- 입력: `0,5`
- 출력: `IllegalArgumentException` 발생 후 종료 (양수가 아니므로 예외 처리)

**테스트 case 12**: 커스텀 구분자가 공백

- 입력: `// \n1 2 3,4`
- 출력: `결과 : 10` (공백도 문자이므로 구분자 설정 가능)