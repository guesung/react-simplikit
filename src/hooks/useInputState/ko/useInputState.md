# useInputState

`useInputState`는 선택적인 값 변환을 가진 입력 상태를 관리하는 리액트 훅이에요.

## 인터페이스

```ts
function useInputState(
  initialValue: string = '',
  transformValue: (value: string) => string = (v: string) => v
): [value: string, onChange: ChangeEventHandler<HTMLInputElement>];
```

### 파라미터

<Interface
  name="initialValue"
  type="string"
  description='입력의 초기 값이에요. 기본값은 빈 문자열 (<code>""</code>)이에요.'
/>

<Interface
  name="transformValue"
  type="(value: string) => string"
  description="입력 값을 변환하는 함수예요. 기본값은 입력을 변경하지 않고 그대로 반환하는 함수예요."
/>

### 반환 값

<Interface
  name=""
  type="[value: string, onChange: ChangeEventHandler<HTMLInputElement>]"
  description="다음을 포함하는 튜플이에요:"
  :nested="[
    {
      name: 'value',
      type: 'string',
      required: false,
      description: '현재 상태 값이에요.',
    },
    {
      name: 'onChange',
      type: 'ChangeEventHandler<HTMLInputElement>',
      required: false,
      description: '상태를 업데이트하는 함수예요.',
    },
  ]"
/>

## 예시

```tsx
function Example() {
  const [value, onChange] = useInputState('');
  return <input type="text" value={value} onChange={onChange} />;
}
```

