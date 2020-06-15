# styled-component 이용해서 기존 UI 라이브러리 커스텀

기존 UI 라이브러리에 `Button` 이 있다고 할 때,

 ```jsx
import styled, { css } from "styled-components";

const ButtonWithCustomDisabled = styled(Select)`
  ${props =>
    props.disabled &&
    css`
      background: #black;
      color: #black;
    `};
`;
```

위와 같은 방식으로 wrapping 해줄 수 있다.

단 사용하는 라이브러리의 `Button` 컴포넌트의 props 에 `disabled` 값이 있어야 한다.