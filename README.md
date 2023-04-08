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
  const linkElement = screen.getByText(/learn react/i);
  expect(linkElement).toBeInTheDocument();
});
```

위 코드가 `npm test`를 실행했을 때 실행되던 테스트다. 위 코드를 한 줄 한 줄 살펴보자!

- render : 테스트 함수에서는 첫 번째로 이 render라는 메서드를 실행한다. render 메서드는 인수로 제공하는 JSX에 관한 가상돔을 생성한다.
