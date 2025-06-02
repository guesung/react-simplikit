# ImpressionArea

`ImpressionArea`는 특정 DOM 요소가 화면에 보이는 시간을 측정하고, 요소가 뷰포트에 들어오거나 나갈 때 콜백을 실행하는 컴포넌트예요. 이 컴포넌트는 `useImpressionRef` 훅을 사용하여 요소의 가시성을 추적해요.

## 인터페이스

```ts
function ImpressionArea<T extends ElementType>(
  as: T = 'div',
  rootMargin: string,
  areaThreshold: number,
  timeThreshold: number,
  onImpressionStart: () => void,
  onImpressionEnd: () => void,
  ref: Ref<Element<T>>,
  children: React.ReactNode,
  className: string
): JSX.Element;
```

### 파라미터

<Interface
  name="as"
  type="T"
  description="렌더링할 HTML 태그예요. 기본값은 <code>div</code>예요."
/>

<Interface
  name="rootMargin"
  type="string"
  description="감지 영역을 조정하는 여백이에요."
/>

<Interface
  name="areaThreshold"
  type="number"
  description="요소가 얼마나 보여야 하는지에 대한 최소 비율이에요 (0부터 1까지)."
/>

<Interface
  name="timeThreshold"
  type="number"
  description="요소가 얼마 동안 보여야 하는지에 대한 최소 시간이예요 (밀리 초 단위)."
/>

<Interface
  name="onImpressionStart"
  type="() => void"
  description="요소가 뷰에 들어가는 순간 실행되는 콜백 함수예요."
/>

<Interface
  name="onImpressionEnd"
  type="() => void"
  description="요소가 뷰에서 나가는 순간 실행되는 콜백 함수예요."
/>

<Interface
  name="ref"
  type="Ref<Element<T>>"
  description="요소에 대한 참조예요."
/>

<Interface
  name="children"
  type="React.ReactNode"
  description="컴포넌트 내부에 렌더링될 자식 요소들이에요."
/>

<Interface
  name="className"
  type="string"
  description="스타일링을 위한 추가 클래스명이에요."
/>

### 반환 값

<Interface
  name=""
  type="JSX.Element"
  description="자식 요소들의 가시성을 추적하는 React 컴포넌트예요."
/>

## 예시

```tsx
function App() {
  return (
    <ImpressionArea
      onImpressionStart={() => console.log('Element entered view')}
      onImpressionEnd={() => console.log('Element exited view')}
      timeThreshold={1000}
      areaThreshold={0.5}
    >
      <div>나를 추적하세요!</div>
    </ImpressionArea>
  );
}
```

