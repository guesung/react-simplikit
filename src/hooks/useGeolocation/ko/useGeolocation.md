# useGeolocation

`useGeolocation`는 사용자의 지리적 위치를 검색하고 추적하는 리액트 훅이에요. 이는 브라우저의 `Geolocation API`를 사용하여 한 번의 위치 검색과 지속적인 위치 추적 모두를 지원해요.

## 인터페이스

```ts
function useGeolocation(options: GeolocationOptions): Object;
```

### 파라미터

<Interface
  name="options"
  type="GeolocationOptions"
  description="위치 정보 옵션 설정이에요"
  :nested="[
    {
      name: 'options.mountBehavior',
      type: 'GeolocationMountBehaviorType',
      required: false,
      description:
        '훅이 마운트될 때 동작 방식이에요: <br />- 제공되지 않으면 자동 위치 가져오기가 발생하지 않아요 <br />- <code>get</code>: 컴포넌트가 마운트될 때 위치를 자동으로 한 번 가져와요 <br />- <code>watch</code>: 컴포넌트가 마운트될 때 위치 변경 추적을 자동으로 시작해요',
    },
    {
      name: 'options.enableHighAccuracy',
      type: 'boolean',
      required: false,
      defaultValue: 'false',
      description:
        '만약 true이면, 더 정확한 위치 정보를 제공해요 (배터리 소모 증가)',
    },
    {
      name: 'options.maximumAge',
      type: 'number',
      required: false,
      defaultValue: '0',
      description:
        '허용 가능한 캐시된 위치의 최대 연령 (밀리초)예요',
    },
    {
      name: 'options.timeout',
      type: 'number',
      required: false,
      defaultValue: 'Infinity',
      description:
        '위치 요청에 허용되는 최대 시간 (밀리초)예요',
    },
  ]"
/>

### 반환 값

<Interface
  name=""
  type="Object"
  description="위치 데이터 및 관련 함수들을 포함하고 있어요"
  :nested="[
    {
      name: 'loading',
      type: 'boolean',
      required: false,
      description: '현재 위치 데이터를 가져오는 중인지 여부예요.',
    },
    {
      name: 'error',
      type: 'CustomGeoLocationError|null',
      required: false,
      description:
        '문제가 발생하면 에러 객체예요, 또는 null이에요. 이 훅은 표준 Geolocation API 오류 코드 (<code>1-3</code>)를 사용하고, 사용자 정의 코드 (<code>0</code>)를 추가해요 <br />  : <code>0</code> - 환경이 위치 정보를 지원하지 않아요 <br />  : <code>1</code> - 사용자가 위치 정보 접근 권한을 거부했어요 <br />  : <code>2</code> - 위치를 찾을 수 없어요 <br />  : <code>3</code> - 시간 초과 - 위치 요청에 너무 오래 걸렸어요.',
    },
    {
      name: 'data',
      type: 'GeolocationData|null',
      required: false,
      description:
        '위치 데이터 객체 또는 null이에요 <br />  : latitude <code>number</code> - 위도는 십진수로 제공돼요 <br />  : longitude <code>number</code> - 경도는 십진수로 제공돼요 <br />  : accuracy <code>number</code> - 위치의 정확도는 미터 단위로 제공돼요 <br />  : altitude <code>number|null</code> - 고도는 WGS84 타원체 위의 미터 단위로 제공돼요 <br />  : altitudeAccuracy <code>number|null</code> - 고도의 정확도는 미터 단위로 제공돼요 <br />  : heading <code>number|null</code> - 진정한 북쪽에서 시계 방향으로의 방위각이예요 <br />  : speed <code>number|null</code> - 속도는 초당 미터 단위로 제공돼요 <br />  : timestamp <code>number</code> - 위치가 검색된 시간을 나타내요.',
    },
    {
      name: 'getCurrentPosition',
      type: 'Function',
      required: false,
      description: '현재 위치를 한 번 가져오는 함수예요.',
    },
    {
      name: 'startTracking',
      type: 'Function',
      required: false,
      description: '위치 변경 추적을 시작하는 함수예요.',
    },
    {
      name: 'stopTracking',
      type: 'Function',
      required: false,
      description: '위치 추적을 멈추는 함수예요.',
    },
    {
      name: 'isTracking',
      type: 'boolean',
      required: false,
      description: '현재 위치 추적이 활성화되어 있는지 여부예요.',
    },
  ]"
/>

## 예시

```tsx
// 기본 사용법
const {
  loading,
  error,
  data,
  getCurrentPosition
} = useGeolocation();

// 컴포넌트가 마운트될 때 자동 위치 가져오기
const {
  loading,
  error,
  data
} = useGeolocation({ mountBehavior: 'get' });

// 위치 추적
const {
  loading,
  error,
  data,
  startTracking,
  stopTracking,
  isTracking
} = useGeolocation();

const handleStartTracking = () => {
  startTracking();
};

const handleStopTracking = () => {
  stopTracking();
};
```

