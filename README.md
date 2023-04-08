# 🧩 React Testing Library (RTL) vs Jest

## RTL

- RTL은 테스트를 위한 가상 돔을 제공한다.
- 브라우저없이 테스트를 진행하면 클릭 요소와 같은 작업을 할 때 가상 돔이 필요하다.
- 그리고 가상 돔이 원하는대로 작동하는지 확인 가능

## Jest

- 테스트를 찾고 실행하는 것과 테스트 통과 여부를 결정하는 역할을 한다.

## 테스트 시작

> 테스트 할 때는 `npm test` 라는 명령어로 하면 된다. npm test는 Jest에서 Watch 모드 실행으로 시작한다.

![](https://velog.velcdn.com/images/leemember/post/45a7efad-1b80-4c84-b9ec-0b43e8429c60/image.png)

여기서 테스트할 것은 a를 입력하면 a에 관한 테스트 결과가 나온다.

![](https://velog.velcdn.com/images/leemember/post/2c962e81-566d-4b04-a515-421e61628761/image.png)

테스트 성공 ! 했다는 뜻이다. `src/App.test.js` 파일이 테스트 파일이다.
`q`를 입력하면 jest의 Watch 모드가 종료된다.

#### src/App.test.js 파일 코드

```javascript
import { render, screen } from "@testing-library/react";
import App from "./App";

test("renders learn react link", () => {
  render(<App />);
  const linkElement = screen.getByText(/learn testing library/i);
  expect(linkElement).toBeInTheDocument();
});
```

위 코드가 `npm test`를 실행했을 때 실행되던 테스트다. 위 코드를 한 줄 한 줄 살펴보자!

- render : 테스트 함수에서는 첫 번째로 이 render라는 메서드를 실행한다. render 메서드는 인수로 제공하는 JSX에 관한 가상돔을 생성한다. (= 컴포넌트)
- screen.getByText : 메서드를 실행하며 표시되는 모든 텍스트를 기반으로 DOM에서 요소를 찾는다.
- `(/learn react/i)` : geyByText의 인수는 정규 표현식이다. App.js 파일 안에
  ![](https://velog.velcdn.com/images/leemember/post/7883613e-1ed4-46cf-aba0-ab4606daf310/image.png)

이렇게 `learn react` 이 단어가 없으면 테스트는 실패된다.

![](https://velog.velcdn.com/images/leemember/post/39a7976d-9542-4666-b15f-c3d721cf7e9f/image.png)

실패된 모습

- `expect(linkElement).toBeInTheDocument();` : Jest의 단언이다. 단언은 테스트 성공과 실패의 원인이다. 복잡하면서도 중요하다.

---

## Jest 단언(Assertion)

테스트의 통과 여부를 결정한다.
Jest에서 전역 메서드인 expect 메서드로 시작한다. 그리고 인수가 있는데, 인수는 단언이 단언하는 것으로 예측에 들어맞는지 확인하기 위해 Jest에서 확인한다.

### Jest-dom

이것은 CRA와 제공되며 CRA와 함께 설치된다.
setupTests.js 파일을 사용해 각 테스트 전에 jest-dom을 가져온다.
즉, 모든 테스트에서 jest-dom 매처를 사용할 수 있는 것이다.

### ⭐️ Jest를 본격적으로 배워보자 ⭐️

테스트 러너가 필요하다. 테스트를 찾고 실행하며 단언할 무언가가 필요. -> 이때 Jest를 사용한다. <br>
Jest가 유일한 테스트 러너는 아니다. Mocha나 Jasmine(제스민)도 있지만, **테스팅 라이브러리에서 Jest를 권장하며 CRA와 함께 제공된다.** <br>
그 외에도 **효율적이고 사용이 쉽다.** `npm test`를 하면 `npm script`를 실행했고 그 스크립트가 Jest를 Watch 모드로 실행되게 한다. <br>
`pagekage.json` 파일에 가면 `script`가 있는데 test를 실행하면 `react-scripts test`를 실행하는 것이다.

```javascript
"scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    📍"test": "react-scripts test",
    "eject": "react-scripts eject"
  },
```

이면에서는 Jest가 Watch 모드로 실행 중이다. <br>
`Watch 모드란?` Jest를 실행하는 방법으로 마지막 커밋 이후 파일의 모든 변경 사항을 확인해서 마지막 커밋 이후 변경된 파일과 연관된 테스트만 실행한다.
